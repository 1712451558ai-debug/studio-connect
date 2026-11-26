# AICINEPro Studio Connect

Studio Connect 是 AICINEPro 的外部工具连接客户端。它把 Studio 画布接入 Codex、支持 OAuth 的 MCP 客户端或命令行。客户端只能在用户指定的画布、权限和期限内工作。

**当前是预览版。** 下载包可离线检查；默认正式站尚未完成连接验收。下载、解压或安装不代表已经开通授权，不需要提供模型供应商密钥。

## 下载

在仓库右侧打开 **Releases**，找到 `v0.3.0-beta.3`，从 **Assets** 下载 `Studio-Connect-0.3.0-beta.3.zip`。请不要下载 GitHub 自动生成的 **Source code (zip)**，那是仓库资料归档，不是客户端。

解压后进入 `Studio-Connect-0.3.0-beta.3` 目录，按[安装与首次连接](INSTALL.md)操作。如需核对下载文件，Release 同时提供 SHA-256 清单。

## 可用范围

- **读取画布**：只读用户授权的画布、节点和受支持的参考图片。
- **修改现有节点**：需要单独的写权限；不会通过该权限创建或删除节点。
- **报价和生成**：仅在服务和模型开放后可用。生成需要独立权限和费用确认，回填到画布需要另行确认。模型和价格以连接环境返回为准。

本仓库用于分发客户端及说明，不包含平台服务端或用户数据。一般问题可以在 Issues 提交，请先阅读[安全与反馈说明](SECURITY.md)。

[AICINEPro 官网](https://aicinepro.com/)
