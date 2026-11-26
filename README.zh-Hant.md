# 適用於Mac的YozhProxificator

[English](README.md) · [Русский](README.ru.md) · [Українська](README.uk.md) · [Español](README.es.md) · [Português](README.pt.md) · [Tiếng Việt](README.vi.md) · [Bahasa Indonesia](README.id.md) · [简体中文](README.zh-Hans.md) · 繁體中文

透過代理轉送這台Mac的流量：整台Mac，或只轉送你選擇的應用程式。

- **整台Mac**。「全部流量」會讓這台Mac送出的一切都經代理轉送，即使是不遵循代理設定的應用程式。
- **每個應用程式各走各的路**。可以讓某個應用程式走自己的代理或代理鏈、直連，或完全不連網，對整個網站清單也可以這樣處理。
- **沒有洩漏**。斷網保護只允許設有規則的應用程式透過其代理連網，即使在未連線時也是如此。在「全部流量」模式下，由代理自己解析網站位址，所以DNS洩漏測試看到的是代理一側。
- **任何代理**。HTTP、HTTPS和SOCKS5；VLESS、VMess、Trojan、Shadowsocks和Hysteria2的連結與訂閱；兩個代理組成的代理鏈。
- **一鍵檢查**。「檢查」會顯示代理是否可用、連線有多快，以及出口在哪個國家。
- **面向CyberYozh用戶**。購買的代理可透過API金鑰載入。產生器可依國家、城市和供應商產生輪換代理，並可為其指定作業系統和瀏覽器的TLS指紋。行動代理一鍵更換IP。

## 下載

此連結始終指向最新版本：
**[YozhProxificator.dmg](https://github.com/CyberYozh/yozh-proxificator-mac-releases/releases/latest/download/YozhProxificator.dmg)**

系統需求：搭載Apple silicon的Mac，macOS 15或更新版本。

下載的是一個磁碟映像檔，裡面只有應用程式和指向「應用程式」檔案夾的捷徑，別無其他。開啟映像檔，把YozhProxificator拖到「應用程式」，或直接從映像檔中開啟應用程式：它會提示把自己移到那裡。應用程式會從此儲存庫自動更新；更新均已簽署，自動檢查可以在應用程式的設定中關閉。

## 驗證下載的檔案

每個公開版本`vX.Y.Z`都有一個檔案`SHA256SUMS`，其中記錄了該版本各檔案的SHA-256。把它下載到映像檔所在的檔案夾，然後在「終端機」中，在該檔案夾裡執行：

    shasum -a 256 -c SHA256SUMS --ignore-missing

`acceptance`版本中的測試建置則有自己的檔案`SHA256SUMS-X.Y.Z`：把它下載到映像檔旁邊，並把它的名稱寫進指令。

映像檔使用Developer ID簽署，並經Apple公證。請把指令中的`YozhProxificator.dmg`換成你的檔案名稱：

    spctl -a -t open --context context:primary-signature -v YozhProxificator.dmg

它應回覆`accepted`和`source=Notarized Developer ID`。

## 原始碼

YozhProxificator是自由軟體，採用GNU GPL v3，不提供任何擔保。每個公開版本`vX.Y.Z`和`acceptance`版本中的每個測試建置，都附帶其所發布內容的完整原始碼：

- `yozh-proxificator-mac-X.Y.Z-source.tar.gz`——應用程式、其系統元件和建置腳本；
- `yozh-xray-<commit>-source.tar.gz`——代理引擎，即Xray-core的一個分支，位於該建置所固定的提交（`<commit>`是該提交的前十二個字元）；
- `sparkle-<version>-source.tar.gz`——更新框架。

## 如何解除安裝

1. 在應用程式的**設定 → 全部流量**中，點按**移除元件**。
2. 把應用程式移到垃圾桶。
3. 如果程式一直沒有網路，請從「應用程式」中開啟**Yozh Unblock**。如果移除後網路中斷，請在「終端機」中執行`sudo /Library/PrivilegedHelperTools/com.cyberyozh.proxyficator/yozh-helper restore`。

## 更新來源

應用程式會讀取一個更新來源——一份版本清單，以及這些版本所指向的映像檔和說明——來判斷是否有更新的版本。共有兩個更新來源，各在自己的版本中：

- `acceptance`是一個預發布版本，內含內部測試建置（0.9.x）及其更新來源，不供一般使用。每個建置都附帶其原始碼壓縮檔和自己的`SHA256SUMS-X.Y.Z`；多個建置共用的引擎或框架壓縮檔只保存一份。測試建置讀取這個更新來源，1.0.0也會發布到其中，所以它們會隨之轉到公開更新來源。
- `updates`是公開版本的更新來源。它供應用程式使用，不用於下載；其中每個版本的原始碼，都在該版本的`vX.Y.Z`版本中。
