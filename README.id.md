# YozhProxificator untuk Mac

[English](README.md) · [Русский](README.ru.md) · [Українська](README.uk.md) · [Español](README.es.md) · [Português](README.pt.md) · [Tiếng Việt](README.vi.md) · Bahasa Indonesia · [简体中文](README.zh-Hans.md) · [繁體中文](README.zh-Hant.md)

Lalu lintas Mac Anda melalui proxy: seluruh Mac, atau hanya aplikasi yang Anda pilih.

- **Seluruh Mac.** “Semua lalu lintas” mengirim semua yang dikirim Mac melalui proxy, bahkan dari aplikasi yang mengabaikan pengaturan proxy.
- **Setiap aplikasi dengan caranya sendiri.** Arahkan aplikasi melalui proxy atau rantainya sendiri, langsung, atau tanpa jaringan sama sekali, dan lakukan hal yang sama untuk seluruh daftar situs.
- **Tanpa kebocoran.** Pemutus darurat menjaga aplikasi yang punya aturan tetap tidak terhubung ke jaringan kecuali lewat proxy-nya, bahkan saat Anda tidak terhubung. Dalam “Semua lalu lintas”, proxy sendiri yang mencari alamat situs, jadi uji kebocoran DNS menampilkan sisi proxy.
- **Proxy apa pun.** HTTP, HTTPS, dan SOCKS5; tautan dan langganan VLESS, VMess, Trojan, Shadowsocks, dan Hysteria2; rantai dua proxy.
- **Pemeriksaan sekali klik.** “Periksa” menunjukkan apakah proxy berfungsi, secepat apa koneksinya, dan keluar di negara mana.
- **Untuk pelanggan CyberYozh.** Proxy yang Anda beli dimuat dengan kunci API. Generator membuat proxy rotasi berdasarkan negara, kota, dan penyedia, dan dapat memberinya OS pilihan serta sidik jari TLS browser. Proxy seluler mengganti IP dengan sekali klik.

## Unduh

Tautan ini selalu memberikan rilis terbaru:
**[YozhProxificator.dmg](https://github.com/CyberYozh/yozh-proxificator-mac-releases/releases/latest/download/YozhProxificator.dmg)**

Persyaratan: Mac dengan Apple silicon, macOS 15 atau lebih baru.

Unduhannya berupa image disk. Isinya aplikasi dan pintasan ke folder Aplikasi, tidak ada yang lain. Buka image tersebut
lalu seret YozhProxificator ke Aplikasi, atau buka aplikasi dari image: aplikasi menawarkan untuk memindahkan dirinya
ke sana. Aplikasi memperbarui diri dari repositori ini; pembaruan bertanda tangan, dan pemeriksaan otomatis dapat
dimatikan di pengaturan aplikasi.

## Periksa file yang Anda unduh

Setiap rilis publik, `vX.Y.Z`, memiliki file `SHA256SUMS` berisi SHA-256 dari file-filenya. Unduh file itu ke folder
tempat image berada, lalu jalankan, di Terminal, di folder tersebut:

    shasum -a 256 -c SHA256SUMS --ignore-missing

Build uji di rilis `acceptance` sebaliknya memiliki file `SHA256SUMS-X.Y.Z` sendiri: unduh file itu di samping image dan
tulis namanya di perintah.

Image ditandatangani dengan Developer ID dan dinotarisasi Apple. Ganti `YozhProxificator.dmg` dengan nama file Anda:

    spctl -a -t open --context context:primary-signature -v YozhProxificator.dmg

Jawabannya `accepted` dan `source=Notarized Developer ID`.

## Kode sumber

YozhProxificator adalah perangkat lunak bebas di bawah GNU GPL v3, tanpa garansi. Setiap rilis publik `vX.Y.Z` dan setiap
build uji di rilis `acceptance` menyertakan kode sumber lengkap dari apa yang dikirimkannya:

- `yozh-proxificator-mac-X.Y.Z-source.tar.gz` — aplikasi, komponen sistemnya, dan skrip build;
- `yozh-xray-<commit>-source.tar.gz` — mesin proxy, fork dari Xray-core, pada commit yang dikunci build
  (`<commit>` adalah dua belas karakter pertama commit itu);
- `sparkle-<version>-source.tar.gz` — framework pembaruan.

## Cara menghapus instalasi

1. Di **Pengaturan → Semua lalu lintas** pada aplikasi, tekan **Hapus komponen**.
2. Pindahkan aplikasi ke Tong Sampah.
3. Jika program tetap tanpa jaringan, buka **Yozh Unblock** dari folder Aplikasi. Jika jaringan hilang setelah
   penghapusan, jalankan `sudo /Library/PrivilegedHelperTools/com.cyberyozh.proxyficator/yozh-helper restore` di Terminal.

## Feed pembaruan

Aplikasi membaca sebuah feed — daftar versi, beserta image dan catatan yang ditunjuknya — untuk mengetahui apakah ada
versi yang lebih baru. Ada dua feed, masing-masing di rilisnya sendiri:

- `acceptance` adalah pra-rilis berisi build uji internal (0.9.x) dan feed-nya, tidak untuk penggunaan umum. Setiap
  build disertai arsip kode sumbernya dan `SHA256SUMS-X.Y.Z` sendiri; arsip mesin atau framework yang dipakai bersama
  oleh beberapa build disimpan sekali saja. Build uji membaca feed ini, dan 1.0.0 juga dipublikasikan ke dalamnya,
  sehingga build uji berpindah ke feed publik bersamanya.
- `updates` adalah feed rilis publik. Feed ini untuk aplikasi, bukan untuk diunduh; kode sumber setiap versi di
  dalamnya ada di rilis `vX.Y.Z` versi itu.
