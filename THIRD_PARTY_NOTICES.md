# 第三方署名与许可 / Third-party notices

## ArmorVariantManager-World · 设计参考

感谢 **明月别枝（moon）**。本插件参考了其《怪物猎人：世界／冰原》差分管理器的分组、部件显隐、预设与条件切换交互。RE6 的 MOD211 模型识别、Direct3D 9 绘制拦截和本地主角血量读取采用面向 RE6 的实现。

Design reference for groups, visibility controls, presets and condition-driven switching. The reference project credits Monkeysama's ArmorVariantManager for its series design and Mi1ice's MHWI-VisualControllerExtended for its transformation conditions. See the original acknowledgements for that attribution chain.

- [ArmorVariantManager-World README（核对版本 5a5e4d8）](https://github.com/moon135246/ArmorVariantManager-World/blob/5a5e4d810bfff93527b8549504bc6ae0b757ff3a/README.md)
- [上游源码许可范围](https://github.com/moon135246/ArmorVariantManager-World/blob/5a5e4d810bfff93527b8549504bc6ae0b757ff3a/LICENSE_STATUS.md)
- [上游第三方署名](https://github.com/moon135246/ArmorVariantManager-World/blob/5a5e4d810bfff93527b8549504bc6ae0b757ff3a/THIRD_PARTY_NOTICES.md)
- 上游原创部分采用 MIT。完整版权声明和许可原文见 [ArmorVariantManager-World-MIT.txt](licenses/ArmorVariantManager-World-MIT.txt)。

## 随插件分发的库 / Bundled libraries

| 组件 | 用途 | 许可原文 |
| --- | --- | --- |
| [Dear ImGui 1.92.9b](https://github.com/ocornut/imgui) | 界面与 Win32、Direct3D 9 后端。核心和 Win32 后端取自上述 World 仓库所附的 Dear ImGui 副本 | [MIT · Omar Cornut](licenses/DearImGui.txt) |
| [MinHook 1.3.4](https://github.com/TsudaKageyu/minhook/tree/v1.3.4) | x86 函数挂钩，含 MinHook 所附的 HDE 代码 | [BSD-2-Clause 及附带声明](licenses/MinHook.txt) |
| [miniz 3.1.0](https://github.com/richgel999/miniz/tree/3.1.0) | 解压 ARC 内的资源数据 | [MIT](licenses/miniz.txt) |

各组件继续适用各自的许可。上述许可文本的授权范围以原文为准。此页及许可证也放在安装包内的 `RE6VariantManager/` 下。
