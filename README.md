# Sakura Mobile

在手机浏览器中与 [Sakura](https://github.com/Rvosy/Sakura) 聊天。通过局域网或 Tailscale 连接电脑，无需安装手机应用。

## 功能

- 发送文字和图片，与 Sakura 当前角色对话。
- 查看聊天历史，手机与桌面共用同一份会话数据。
- 回复同时显示在桌面字幕中，并按桌面语音设置朗读；语音在电脑播放。
- 在插件设置中管理访问地址、端口和访问令牌，查看服务状态。

手机聊天由电脑上的 Sakura 处理，使用时需要保持 Sakura 运行。

## 使用

1. 在符合下方运行要求的 Sakura 中，通过“设置 → 插件 → 更多 → 从 ZIP 安装…”导入 `1.1.0-rc.1` 插件包，再到“已安装”中启用。预发布版本不会作为市场默认安装或更新推荐。
2. 打开插件设置，设置访问令牌，开启手机网页服务并保存。
3. 将手机和电脑接入同一局域网，或通过 Tailscale 互通。
4. 在手机浏览器中打开插件设置显示的访问地址。

## 配置

| 设置 | 说明 |
| --- | --- |
| 启用手机网页端 | 开启或关闭网页服务 |
| 监听地址 | 默认 `0.0.0.0`，允许通过电脑的网络地址访问；`127.0.0.1` 仅允许本机访问 |
| 端口 | 默认 `8765`，可改为其他未占用端口 |
| 访问 token | 访问网页和接口所需的令牌，请将默认值改为自己的令牌 |

访问地址包含令牌，请勿公开分享。远程使用建议通过 Tailscale 连接，不要将服务端口直接暴露到公网。

## 运行要求

`1.1.0-rc.1` 是预发布版本，需要包含 [Sakura #230](https://github.com/Rvosy/Sakura/pull/230) 的宿主。它使用新的 `sakura.host.conversation` 发送用户消息，并通过 `sakura.host.character` 和 `sakura.host.timeline` 读取角色与历史。Sakura `v1.2.1` 未提供 conversation 服务，不能运行此版本；使用该正式版时请保留插件 `1.0.0`。

插件使用 Plugin API v4，还依赖 `sakura.host.artifacts` 和 `sakura.host.settings`；完整声明见 `plugin.yaml`。无需额外安装 Python 依赖。

从内置版本升级时，支持迁移的 Sakura 会保留原设置和启停选择。迁移失败时，可按 [插件升级指南](https://github.com/Rvosy/Sakura/blob/main/docs/userdocs/RUNTIME_V2_PLUGINS.md#升级已有安装)从市场修复。

## 许可证

作者：pa1n9。使用 [MIT 许可证](LICENSE)。
