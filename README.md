<p align="center"><img src="assets/MediaGlean.png" width="72" alt="媒拾（MediaGlean）"></p>
<h1 align="center">媒拾（MediaGlean）</h1>
<p align="center">Windows 原生媒体下载工具 · WinUI 3 · ParseHub</p>
<p align="center"><a href="https://github.com/evan-dev0608/MediaGlean/releases/tag/client-0.3.0-beta.2">下载安装</a> · <a href="docs/user-guide.md">使用说明</a> · <a href="https://github.com/evan-dev0608/MediaGlean/issues">问题反馈</a> · <a href="CONTRIBUTING.md">参与开发</a></p>
<p align="center"><a href="LICENSE"><img alt="许可证：MIT" src="https://img.shields.io/badge/license-MIT-blue"></a> <img alt="平台：Windows x64" src="https://img.shields.io/badge/platform-Windows%20x64-blue"></p>

## 关于项目

媒拾（MediaGlean）是一款面向 Windows 的开源媒体下载工具。粘贴作品链接或分享文案，即可预览视频、图片、图集、音频和图文，再将选中的内容下载并按作品归档。

桌面界面使用 WinUI 3，链接解析由 ParseHub 提供。MediaGlean 的源码以 MIT 许可证发布。[ParseHub](https://github.com/z-mio/ParseHub) · [MIT 许可证](LICENSE)

## 下载与安装

**系统要求**：Windows 10 2004（内部版本 19041）或更新版本，x64。

1. 打开 [0.3.0 Beta 2](https://github.com/evan-dev0608/MediaGlean/releases/tag/client-0.3.0-beta.2)，在 Assets 中下载 `MediaGlean-*-win-x64-Setup.exe` 和 `SHA256SUMS.txt`。
2. 用 PowerShell 运行 `Get-FileHash .\MediaGlean-*-win-x64-Setup.exe -Algorithm SHA256`，将摘要与 `SHA256SUMS.txt` 中同名文件的记录比较。
3. 运行安装程序。安装按当前用户进行，自带所需运行组件。安装程序为 Beta 版，尚未进行 Windows 产品代码签名。

升级步骤见 [用户指南](docs/user-guide.md#安装与升级)。

## 主要功能

- **先预览，再下载**：识别分享文案中的链接，一次提交多个作品，展示解析流程和结果。
- **统一下载管理**：查看进行中、已完成和失败任务，重试、打开文件或定位文件夹。
- **按作品归档**：按平台和作品创建目录，图集保持原帖顺序，图文可保存为 Markdown。
- **Windows 原生界面**：WinUI 3，支持浅色、深色及跟随系统主题。
- **平台连接设置**：按平台配置 Cookie 和代理；Cookie 在本机加密保存，默认隐藏。
- **独立组件更新**：ParseHub 官方包单独更新；Worker、Python 环境和媒体工具仅下载变化部分，验证后切换，失败回滚。
- **本地媒体工具**：使用自带 FFmpeg / ffprobe，或在设置中指定本地 x64 工具目录。

## 平台与文件类型

当前接入 24 个平台：

哔哩哔哩、抖音、小红书、快手、微博、知乎、百度贴吧、今日头条、微信公众号、微信视频号、酷安、豆瓣、Bangumi、小黑盒、皮皮虾、最右、YouTube、TikTok、Instagram、Facebook、X / Twitter、Threads、Snapchat、Medium。

支持视频、图片、图集、音频、文本和 Markdown。各平台的文件类型及连接设置见 [平台支持表](docs/platforms.md)。

## 快速上手

1. 安装并启动，在“设置”中选择保存位置；需要登录的平台在“平台连接”中配置。
2. 打开“新建下载”，粘贴链接或分享文案，点击“解析并预览”。
3. 确认解析结果，点击“开始下载”。
4. 在“下载管理”中查看进度、重试或打开文件。

## 从源码构建

开发环境需要 Windows x64、Python 3.12、uv、7-Zip、Windows SDK 10.0.26100，以及 [native/global.json](native/global.json) 指定的 .NET SDK。在项目根目录运行：

```powershell
./build.ps1 -Stage app
```

运行 `./build.ps1` 可构建完整安装包，输出位于 `dist/release`。开发环境、应用输出路径和测试命令见 [贡献指南](CONTRIBUTING.md)。

## 反馈与贡献

- 使用或安装遇到问题时，先查看 [常见问题](docs/user-guide.md#常见问题)。
- 提交 [GitHub Issue](https://github.com/evan-dev0608/MediaGlean/issues) 时，请附上应用版本、Windows 版本、复现步骤和错误码。下载问题可附公开作品链接。**请勿提交 Cookie、Token 或含凭据的日志。**
- 欢迎提交代码修复和文档改进。提交前请阅读 [贡献指南](CONTRIBUTING.md)。

## 项目文档

| 文档 | 内容 |
| --- | --- |
| [使用说明](docs/user-guide.md) | 安装、连接设置、下载和常见问题 |
| [平台能力](docs/platforms.md) | 平台、文件类型与连接要求 |
| [贡献指南](CONTRIBUTING.md) | 环境、测试、构建与提交 |
| [组件架构](docs/components.md) | 五个发布单元与更新机制 |
| [发布维护](docs/releasing.md) | 命名、Actions 与更新渠道 |
| [更新记录](CHANGELOG.md) | 面向用户的版本变化 |

## 许可与致谢

本项目自有代码采用 [MIT 许可证](LICENSE)。感谢 [ParseHub](https://github.com/z-mio/ParseHub)、[Windows App SDK](https://github.com/microsoft/WindowsAppSDK)、[Python](https://www.python.org/)、[FFmpeg](https://ffmpeg.org/) 和 [yt-dlp](https://github.com/yt-dlp/yt-dlp)。

第三方源码、依赖和随包工具保留各自许可证，不因本项目采用 MIT 而改变。详见 [第三方说明](THIRD_PARTY_NOTICES.md)。
