# 安装与首次连接

## 1. 下载并检查安装包

下载 Release 的 `Studio-Connect-0.3.0-beta.3.zip`，完整解压后进入解压出的同名目录。CLI 及包内检查需要 **Node.js 22+**，无需执行 `npm install`。本包不包含 Windows EXE 或 macOS 应用；它也不是 AICINEPro 独立桌面版。

```sh
node scripts/verify-package.mjs
node clients/studio-agent.mjs help
```

上述两条命令不联网。可对照同一 Release 的 `SHA256SUMS.txt` 核对 ZIP；Windows 可用 `Get-FileHash`，macOS 可用 `shasum -a 256`。校验值不是数字签名，请从官方仓库获取文件。

## 2. 选择连接方式

**现在可先检查安装文件。正式站的授权服务确认开放前，请不要进行真实账号配对。**

### Codex 插件

1. 在支持自定义 marketplace 的新版 Codex CLI 中，从解压目录注册本包的本地 marketplace：

   ```sh
   codex plugin marketplace add ./plugin-marketplace
   ```

2. 在支持该来源的 Codex 桌面客户端的插件目录中，选择 `AI CINE Studio · Connect 候选版`，安装 `studio-connect`。若客户端提示刷新或重启，按提示完成。注册 marketplace 并不会自动授予 Studio 画布权限。
3. 服务开放后，在客户端发起浏览器授权。核对域名 `aicinepro.com`，首次建议只授权一个画布的读取权限。授权后，先让插件检查实际的授权画布和范围。

入口与版本支持见 [OpenAI 插件打包与本地安装文档](https://developers.openai.com/plugins/build/plugins)。本次仅检查包结构、CLI 帮助和离线用例，未把插件装进你的 Codex 会话。

### 其他 HTTP MCP 客户端

使用支持 OAuth 的客户端。待服务开放后可参考包内 `examples/mcp-http.production.example.json` 添加 `https://aicinepro.com/mcp`，并按客户端提示在浏览器授权。不要复制网站 Cookie 或把令牌写进连接配置。

### CLI

解压目录中可随时运行 `help`。服务开放且账号获准后，使用以下流程：

```sh
node clients/studio-agent.mjs login
node clients/studio-agent.mjs access
node clients/studio-agent.mjs canvases
```

如果浏览器未自动打开，可用 `login --no-open`，自行打开终端给出的授权页。首次只连接自己指定的画布；推荐先读，不勾选修改或生成。若之前设置过 `STUDIO_AGENT_BASE_URL`，先用 `help` 检查实际连接地址。不要把测试环境的授权移用到正式站。

## 3. 使用与停止连接

- 编辑、生成和回填是不同操作。提交前要核对服务端报价和自己的上限；不要把示例里的占位符当成有效请求。
- 请求超时或任务变成「待核对」时，按原任务或原提交编号查看，不换编号重提。
- 连接开放后，可在 Studio 授权管理页撤销；用 CLI 的 `logout` 同样需要服务端确认。撤销连接不会自动取消已提交的任务。

遇到问题，请附客户端版本、系统、发生时间和脱敏错误码，不要上传个人画布内容或任何登录资料。
