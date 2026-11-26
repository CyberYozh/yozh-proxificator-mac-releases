# YozhProxificator for Mac

English · [Русский](README.ru.md) · [Українська](README.uk.md) · [Español](README.es.md) · [Português](README.pt.md) · [Tiếng Việt](README.vi.md) · [Bahasa Indonesia](README.id.md) · [简体中文](README.zh-Hans.md) · [繁體中文](README.zh-Hant.md)

Your Mac's traffic through proxies: the whole Mac, or only the apps you choose.

- **The whole Mac.** “All traffic” sends everything the Mac sends through the proxy, even apps that ignore proxy settings.
- **Each app its own way.** Send an app through its own proxy or chain, directly, or nowhere at all, and do the same for whole lists of sites.
- **No leaks.** The kill switch keeps an app with a rule off the network except through its proxy, even while you are disconnected. In “All traffic” the proxy itself finds site addresses, so a DNS leak test shows the proxy's side.
- **Any proxy.** HTTP, HTTPS and SOCKS5; VLESS, VMess, Trojan, Shadowsocks and Hysteria2 links and subscriptions; chains of two proxies.
- **One-click check.** “Check” shows whether a proxy works, how fast it connects and which country it comes out in.
- **For CyberYozh customers.** Your bought proxies load by API key. The generator makes rotating proxies by country, city and ISP, and can give them a chosen OS and a browser's TLS fingerprint. Mobile proxies change IP in one click.

## Download

This link always gives the latest release:
**[YozhProxificator.dmg](https://github.com/CyberYozh/yozh-proxificator-mac-releases/releases/latest/download/YozhProxificator.dmg)**

Requirements: a Mac with Apple silicon, macOS 15 or later.

The download is a disk image. It holds the app and a shortcut to the Applications folder, nothing else. Open the image
and drag YozhProxificator to Applications, or open the app from the image: it offers to move itself there.
The app updates itself from this repository; updates are signed, and automatic checks can be turned off in its
settings.

## Check what you downloaded

Each public release, `vX.Y.Z`, has a file `SHA256SUMS` with the SHA-256 of its files. Download it into
the folder where the image is, then run, in Terminal, in that folder:

    shasum -a 256 -c SHA256SUMS --ignore-missing

A test build in the release `acceptance` has a file `SHA256SUMS-X.Y.Z` of its own instead: download that one beside the
image and put its name in the command.

The image is signed with Developer ID and notarized by Apple. Put the name of your file in place of
`YozhProxificator.dmg`:

    spctl -a -t open --context context:primary-signature -v YozhProxificator.dmg

It answers `accepted` and `source=Notarized Developer ID`.

## Source code

YozhProxificator is free software under the GNU GPL v3, with no warranty. Each public release `vX.Y.Z`
and each test build in the release `acceptance` carries the complete source of what it ships:

- `yozh-proxificator-mac-X.Y.Z-source.tar.gz` — the app, its system component and the build scripts;
- `yozh-xray-<commit>-source.tar.gz` — the proxy engine, a fork of Xray-core, at the commit the build pins (`<commit>`
  is the first twelve characters of that commit);
- `sparkle-<version>-source.tar.gz` — the update framework.

## How to uninstall

1. In the app's **Settings → All traffic**, press **Remove component**.
2. Move the app to the Trash.
3. If programs stay offline, open **Yozh Unblock** from Applications. If the network is gone after the removal, run
   `sudo /Library/PrivilegedHelperTools/com.cyberyozh.proxyficator/yozh-helper restore` in Terminal.

## The update feeds

The app reads a feed — a list of versions, with the images and notes they point to — to find out whether a newer
version exists. There are two feeds, each in a release of its own:

- `acceptance` is a pre-release with the internal test builds (0.9.x) and their feed, not for general use. Each build
  comes with its source archives and its own `SHA256SUMS-X.Y.Z`; an engine or framework archive that several builds
  share is stored once. The test builds read this feed, and 1.0.0 is published into it as well, so they move on to the
  public feed with it.
- `updates` is the feed of the public releases. It is for the app, not for download; the source of each version in it
  is in that version's release `vX.Y.Z`.
