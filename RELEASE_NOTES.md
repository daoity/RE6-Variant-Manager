# RE6 实时差分管理器 v0.3.2

- **自定义血量预设**。按分组增删 0%–99% 的整数阈值，支持掉血、回血跨档切换和高于最高阈值后的恢复。旧版血量绑定会自动迁移。
- **模型热重读**。按 **F3 → 重新读取**，无需重启游戏即可重扫资源并重新匹配当前画面。
- **重复模型识别**。兼容 Ada 的菜单与战役副本、Leon 的战役与过场头部副本。遇到共用索引的冲突时，优先读取唯一可判定的角色专用 ARC。全库扫描相比 0.3.1 多恢复了 5 组匹配，包括 Ada 双手和一块过场头部。

退出游戏后，在 Fluffy Mod Manager 中停用旧版并启用附件 `RE6-Variant-Manager-v0.3.2.zip`。以上改动已通过独立 Direct3D 9 和资源扫描测试，实际战役和联机兼容性仍待验证。若场景同时绘制索引和绘制范围相同的副本，显隐可能同时作用于两份。

感谢 **明月别枝（moon）**。分组、部件显隐和预设交互参考了 [ArmorVariantManager-World](https://github.com/moon135246/ArmorVariantManager-World)。上游许可原文、第三方署名和各库许可随安装包一同分发。详见 [第三方署名](https://github.com/daoity/RE6-Variant-Manager/blob/main/THIRD_PARTY_NOTICES.md)。
