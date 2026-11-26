# 适用于Mac的YozhProxificator

[English](README.md) · [Русский](README.ru.md) · [Українська](README.uk.md) · [Español](README.es.md) · [Português](README.pt.md) · [Tiếng Việt](README.vi.md) · [Bahasa Indonesia](README.id.md) · 简体中文 · [繁體中文](README.zh-Hant.md)

通过代理转发这台Mac的流量：整台Mac，或只转发你选择的应用。

- **整台Mac**。“全部流量”会让这台Mac发出的一切都经代理转发，即使是不遵循代理设置的应用。
- **每个应用各走各的路**。可以让某个应用走自己的代理或代理链、直连，或完全不联网，对整个网站列表也可以这样处理。
- **没有泄漏**。断网保护只允许设有规则的应用通过其代理联网，即使在未连接时也是如此。在“全部流量”模式下，由代理自己解析网站地址，所以DNS泄漏测试看到的是代理一侧。
- **任何代理**。HTTP、HTTPS和SOCKS5；VLESS、VMess、Trojan、Shadowsocks和Hysteria2的链接与订阅；两个代理组成的代理链。
- **一键检查**。“检查”会显示代理是否可用、连接有多快，以及出口在哪个国家。
- **面向CyberYozh用户**。购买的代理可通过API密钥加载。生成器可按国家、城市和提供商生成轮换代理，并可为其指定操作系统和浏览器的TLS指纹。移动代理一键更换IP。

## 下载

此链接始终指向最新版本：
**[YozhProxificator.dmg](https://github.com/CyberYozh/yozh-proxificator-mac-releases/releases/latest/download/YozhProxificator.dmg)**

系统要求：搭载Apple silicon的Mac，macOS 15或更高版本。

下载的是一个磁盘映像，里面只有应用和指向“应用程序”文件夹的快捷方式，别无其他。打开映像，把YozhProxificator拖到“应用程序”，或直接从映像中打开应用：它会提示把自己移到那里。应用会从此仓库自动更新；更新均已签名，自动检查可以在应用的设置中关闭。

## 校验下载的文件

每个公开版本`vX.Y.Z`都有一个文件`SHA256SUMS`，其中记录了该版本各文件的SHA-256。把它下载到映像所在的文件夹，然后在“终端”中，在该文件夹里运行：

    shasum -a 256 -c SHA256SUMS --ignore-missing

`acceptance`版本中的测试构建则有自己的文件`SHA256SUMS-X.Y.Z`：把它下载到映像旁边，并把它的名称写进命令。

映像使用Developer ID签名，并经Apple公证。请把命令中的`YozhProxificator.dmg`换成你的文件名：

    spctl -a -t open --context context:primary-signature -v YozhProxificator.dmg

它应回答`accepted`和`source=Notarized Developer ID`。

## 源代码

YozhProxificator是自由软件，采用GNU GPL v3，不提供任何担保。每个公开版本`vX.Y.Z`和`acceptance`版本中的每个测试构建，都附带其所发布内容的完整源代码：

- `yozh-proxificator-mac-X.Y.Z-source.tar.gz`——应用、其系统组件和构建脚本；
- `yozh-xray-<commit>-source.tar.gz`——代理引擎，即Xray-core的一个分支，位于该构建所固定的提交（`<commit>`是该提交的前十二个字符）；
- `sparkle-<version>-source.tar.gz`——更新框架。

## 如何卸载

1. 在应用的**设置 → 全部流量**中，点按**移除组件**。
2. 把应用移到废纸篓。
3. 如果程序一直没有网络，请从“应用程序”中打开**Yozh Unblock**。如果移除后网络中断，请在“终端”中运行`sudo /Library/PrivilegedHelperTools/com.cyberyozh.proxyficator/yozh-helper restore`。

## 更新源

应用会读取一个更新源——一份版本列表，以及这些版本所指向的映像和说明——来判断是否有更新的版本。共有两个更新源，各在自己的版本中：

- `acceptance`是一个预发布版本，内含内部测试构建（0.9.x）及其更新源，不供一般使用。每个构建都附带其源代码压缩包和自己的`SHA256SUMS-X.Y.Z`；多个构建共用的引擎或框架压缩包只保存一份。测试构建读取这个更新源，1.0.0也会发布到其中，所以它们会随之转到公开更新源。
- `updates`是公开版本的更新源。它供应用使用，不用于下载；其中每个版本的源代码，都在该版本的`vX.Y.Z`版本中。
