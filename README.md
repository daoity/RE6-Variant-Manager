# RE6 实时差分管理器

适用于 Steam PC 版《生化危机 6》的游戏内差分管理器。将同一个模型的部件显隐保存为分组预设，在游戏中即时切换。插件通过 Direct3D 9 控制子网格的绘制，按材质归类，也支持逐个子网格调整。

## 安装

1. 从 [Releases](https://github.com/daoity/RE6-Variant-Manager/releases/latest) 下载 `RE6-Variant-Manager-v0.2.5.zip`。
2. 退出游戏，在 Fluffy Mod Manager 中停用旧版 RE6 实时差分管理器以及其它提供 `d3d9.dll` 的 Mod。将 ZIP 导入 Fluffy，刷新列表并启用 **RE6 Variant Manager**。
3. 启动游戏，进入角色可见的场景，按 **F3** 打开面板。顶部下拉框列出当前检测到的模型。

安装使用 Releases 中的独立 ZIP 附件。GitHub 自动生成的仓库归档包含说明和许可文件。

## 使用

- 选择模型和分组，按材质或子网格调整显隐。材质显示为 `MAT_…` 时，可用旁边的「预览」定位部件，再右键名称添加备注。
- 点击「保存新预设」。勾选「勾选全部部件」后，保存并显示当前分组的全部部件。留空则保存当前显隐。
- **F1** 切到上一个预设，**F2** 切到下一个预设，按预设栏的编号循环。选中的模型仍在画面中时，关掉面板也可以切换。**Shift + F2** 恢复所有模型的部件显示。
- 血量差分默认关闭。启用后可为本地主角的 0–25%、高于 25% 至 50%、高于 50% 三档指定预设。空置的低血量档维持当前穿着。回到 50% 以上时，应用指定的默认预设，或恢复血量切换前的穿着。

预设和备注保存在 `%LOCALAPPDATA%\RE6VariantManager`。Mod 作者可将 Blender RE6 Model Editor 生成的材质名缓存随 Mod 分发，放在 `RE6VariantManager/MaterialNames/<mod-name>.json`。

## 兼容范围

插件识别受支持的 MOD211 模型、索引数据和绘制调用。能切换的部件取决于已加载模型的网格拆分和绘制方式。索引数据无法区分的匹配会跳过，血量功能需要匹配受支持的 `BH6.exe`。0.2.5 在独立 Direct3D 9 测试中验证了显隐、预设保存和循环逻辑，实际战役和联机兼容性仍待验证。

## 致谢与许可

感谢 **明月别枝（moon / moon135246）**。分组、显隐预设、部件面板和条件切换的交互参考了 [《怪物猎人：世界／冰原》差分管理器（ArmorVariantManager-World）](https://github.com/moon135246/ArmorVariantManager-World)。RE6 的模型识别、Direct3D 9 挂钩和血量读取针对《生化危机 6》实现。

参考版本、实际随包分发的第三方组件和许可原文见 [第三方署名](THIRD_PARTY_NOTICES.md) 与 [许可证目录](licenses/)。
