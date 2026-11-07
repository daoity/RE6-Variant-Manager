# v1.0.1-test.4 — 测试版本 / Pre-release

**这是测试版本，不是正式版。最新正式版仍为 v1.0.0。**

本次汇总 1.0 之后四轮本地测试更新，附件为 `RE6-Variant-Manager-v1.0.1-test.4.zip`。通过 Fluffy 更新；无需安装中间测试版本。

## 更新内容

- 新增「举枪瞄准」「体术 / QTE」预设绑定和独立动作开关，默认关闭。身体、独立头部和自建分组分别设置；空绑定不触发。
- 动作结束、关闭开关、玩家更换或读取持续丢失时撤销动作覆盖。血量预设在动作下继续更新，结束动作后显示当前血量对应穿着。
- 动作期间手动切换预设或恢复显示，会暂停当前这一轮动作覆盖，下次动作状态改变后再触发。
- 模型归属增加实际加载的模型家族核对；新增当前组尚未绑定动作预设提示。Leon 原反馈为未绑定，用户绑定后已确认正常。
- 新增手动、动作、血量分类过渡时长，以及单个预设的独立时长，范围 0.1–5.0 秒。优先级为单个预设 → 类别 → 默认。这是溶解时间，不是预设保持计时。
- 新增举枪、体术 / QTE 各自的遮罩和特效贴图方案。即使两种动作绑定相同显隐预设，也可以选择不同方案。

## 贴图方案怎么实现

插件沿本地主角的引擎动作链读取当前动作类型，在触发状态变化时应用预设。部件的过渡记录包含开始时间、时长、方向和贴图方案；绘制时使用各部件自己的记录，不通过全局换图覆盖其他动作。

Direct3D 9 绘制层对支持的模型绘制临时应用裁剪着色器：灰度遮罩的红色通道决定不同位置何时消失，过渡进度决定当前阈值。黑色先消失、白色最后消失；恢复使用对应恢复文件并反向推进。没有作者遮罩时采用内置噪声；关闭白热效果时采用原细密渐隐。

发光在独立绘制通道中完成。特效图 RGB 提供颜色、Alpha 提供强度，沿溶解边缘和尾迹绘制。它改变视觉，不会生成新的模型或模拟真实燃烧。兼容时，贴图按变化部件的模型 X/Y 范围投射；不是重新导出角色，也不是切换不同模型文件。完成后恢复原着色器、纹理、采样器、混合与深度等状态。

完整技术细节：[特效实现说明](https://github.com/daoity/RE6-Variant-Manager/blob/main/EFFECT_IMPLEMENTATION.zh-CN.md)。

## 放置和启用

在 BH6.exe 所在目录放置，每套方案一个文件夹：

```text
RE6VariantManager/Effects/Packs/
  Aim_Fire/
    damage_mask.png
    restore_mask.png
    damage_effect.png
    restore_effect.png
  Melee_Blue/
    damage_mask.png
    restore_mask.png
    damage_effect.png
    restore_effect.png
```

四个文件均可选。`damage_` 对应消失，`restore_` 对应恢复；`mask` 为灰度形状，`effect` 为带 Alpha 的颜色光效。方案名使用英文字母、数字、下划线、短横线，最长 64 字符。每张 PNG 单边最多 2048 像素、文件最多 16 MiB。

按 F3 → 选模型和分组 → 保存预设 →「动作切换（测试）」绑定动作预设及贴图方案 → 刷新方案并重读贴图 → 保存。然后启用动作差分、溶解和白热碎光与余烬。命名方案独立使用有效 PNG；顶部两个自定义贴图开关继续控制默认方案。

缺图或损坏槽位单独回退内置效果，不借用其他方案贴图。改图后需手动重读。没有显隐变化不会强行重播溶解。

**附件不包含示例 PNG、火焰素材、角色模型、存档或用户预设。** `Aim_Fire`、`Melee_Blue` 只是命名示例，需要放入自己的图片。

- [动作贴图方案使用说明](https://github.com/daoity/RE6-Variant-Manager/blob/main/Action-Textures.zh-CN.md)
- [遮罩与特效贴图的 Photoshop 制作方法](https://github.com/daoity/RE6-Variant-Manager/blob/main/Custom-Textures.zh-CN.md)
- [测试版设置与回退](https://github.com/daoity/RE6-Variant-Manager/blob/main/TESTING.zh-CN.md)
- [快捷键说明](https://github.com/daoity/RE6-Variant-Manager/blob/main/SHORTCUTS.zh-CN.md)

## 配置与验证范围

兼容导入旧配置。独立预设时长使用 v6，动作命名方案使用 v7，首次升级前保留 `.pre-timing.bak` / `.pre-effects.bak`；回退旧插件时需按说明恢复对应配置备份。

723 项隔离 Direct3D 9 检查通过，包含实际像素回读、方案交替、坏图回退、缓存淘汰、动作恢复、时长和配置兼容。Ada 动作读数已核对；Leon 绑定后的动作切换已有用户确认。战役和佣兵的常规人物与四个 L4D 客串模型家族经过资源审计，**不等于所有角色、服装、特殊体术及剧情 QTE 已实机通过**。本版新贴图方案的安装后视觉仍需玩家测试，未识别的特殊 QTE 不猜测触发。

## 来源与许可

感谢 **明月别枝（moon / moon135246）的 [ArmorVariantManager-World](https://github.com/moon135246/ArmorVariantManager-World)**，本插件参考其分组、显隐、预设与条件切换交互。RE6 的识别、动作读取与 Direct3D 9 绘制为面向 RE6 的实现。

保留上游 MIT 声明及 Dear ImGui、MinHook、miniz 的完整许可。参见 [第三方署名](https://github.com/daoity/RE6-Variant-Manager/blob/main/THIRD_PARTY_NOTICES.md) 和 [许可原文](https://github.com/daoity/RE6-Variant-Manager/tree/main/licenses)。

附件 SHA-256：`d06a6ac897e4c742fabd3a837da202b03f0566c6e36a47e376b0be33916dbc14`。
