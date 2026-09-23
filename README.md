# deepseek-harness-desktop

> Desktop packaging for deepseek-harness.
> This repo only stores packaging scripts and release download links.
> **No modifications to the upstream source code.**

本仓库仅存放 deepseek-harness 桌面打包脚本与 Release 安装包下载地址。
**不对上游 deepseek-harness 源码做任何修改。**

上游官方仓库：https://github.com/deepseek-ai/deepseek-harness

国内加速镜像（Gitee）：https://gitee.com/rqiancheng/deepseek-harness

当前打包版本：`0.1.7-alpha.2`（标签 `dsh-v0.1.7-alpha.2`）。

## 📦 下载安装包
前往 [Releases](../../releases) 页面，下载对应平台的安装包（Windows EXE）。

自行打包的 Windows 产物是未签名安装包 `deepseek-harness-0.1.7-alpha.2-win-x64-unsigned.exe`，方便本地使用，不是 DeepSeek 官方签名发布。

## 📁 仓库内容
- 打包脚本：用于拉取上游源码、构建桌面可执行程序
- Release：存放打包产物下载链接
- 不包含修改后的 deepseek-harness 源代码

## ⚖️ 许可与版权
所有二进制安装包由官方 deepseek-harness 源码直接打包生成。
本项目版权、开源协议完全遵从上游仓库。
请参阅上游仓库的 LICENSE 文件。

## ⚠️ 免责声明
本打包产物仅为方便使用，不属于 DeepSeek 官方发布版本。
如有任何问题，请优先在上游官方仓库提交 issue。

## 🛠️ 构建说明
> 如果你想自行打包 Windows x64 安装包

环境：Node.js 22.19+ 或 24+、Corepack 提供的 `pnpm@11.7.0`、Git、Python，以及 Visual Studio 2022 Build Tools。

1. 从国内加速镜像检出指定标签（不修改上游任何源码文件）：

```powershell
git clone --branch dsh-v0.1.7-alpha.2 --depth 1 https://gitee.com/rqiancheng/deepseek-harness.git
```

若镜像上还没有该标签，则克隆默认分支，并确认根目录 `package.json` 的 `version` 为 `0.1.7-alpha.2`。

2. 在检出目录启用锁定的 pnpm 并安装依赖：

```powershell
corepack prepare pnpm@11.7.0 --activate
pnpm install
```

国内网络可设置 `ELECTRON_MIRROR=https://npmmirror.com/mirrors/electron/`，以及 `DSH_DESKTOP_NPM_REGISTRY=https://registry.npmmirror.com`。若连不上 npmmirror，改用 npm 官方源 `https://registry.npmjs.org`，并去掉 `ELECTRON_MIRROR`。

3. 生成未签名桌面安装包（上游命令自带运行时、dsh 与安装器准备，不需要代码签名证书）：

```powershell
pnpm run package:desktop:win:x64:unsigned
```

产物路径：

`apps/desktop/.desktop-build/targets/win-x64/unsigned-artifacts/deepseek-harness-0.1.7-alpha.2-win-x64-unsigned.exe`

> 提示：构建过程不会修改上游任何源码文件。该安装包仅为方便使用，不属于 DeepSeek 官方签名发布版本。
