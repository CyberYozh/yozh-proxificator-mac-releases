# YozhProxificator cho Mac

[English](README.md) · [Русский](README.ru.md) · [Українська](README.uk.md) · [Español](README.es.md) · [Português](README.pt.md) · Tiếng Việt · [Bahasa Indonesia](README.id.md) · [简体中文](README.zh-Hans.md) · [繁體中文](README.zh-Hant.md)

Lưu lượng của máy Mac qua proxy: toàn bộ máy Mac hoặc chỉ những ứng dụng bạn chọn.

- **Toàn bộ máy Mac.** “Toàn bộ lưu lượng” đưa mọi thứ máy Mac gửi đi qua proxy, kể cả những ứng dụng bỏ qua cài đặt proxy.
- **Mỗi ứng dụng một đường riêng.** Bạn có thể cho một ứng dụng đi qua proxy hoặc chuỗi proxy riêng, đi thẳng, hoặc không có mạng nào cả, và làm tương tự với cả danh sách trang web.
- **Không rò rỉ.** Ngắt mạng khẩn cấp không cho ứng dụng có quy tắc ra mạng trừ khi qua proxy của nó, kể cả khi bạn đang ngắt kết nối. Ở chế độ “Toàn bộ lưu lượng”, chính proxy tìm địa chỉ của trang web, nên bài kiểm tra rò rỉ DNS hiển thị phía proxy.
- **Proxy nào cũng được.** HTTP, HTTPS và SOCKS5; liên kết và gói đăng ký VLESS, VMess, Trojan, Shadowsocks và Hysteria2; chuỗi hai proxy.
- **Kiểm tra bằng một lần bấm.** “Kiểm tra” cho biết proxy có hoạt động không, kết nối nhanh đến đâu và thoát ra ở quốc gia nào.
- **Dành cho khách hàng CyberYozh.** Proxy đã mua được tải bằng khóa API. Trình tạo tạo proxy xoay vòng theo quốc gia, thành phố và nhà cung cấp, và có thể gán cho chúng hệ điều hành đã chọn cùng dấu vân tay TLS của trình duyệt. Proxy di động đổi IP chỉ bằng một lần bấm.

## Tải về

Liên kết này luôn cho bản phát hành mới nhất:
**[YozhProxificator.dmg](https://github.com/CyberYozh/yozh-proxificator-mac-releases/releases/latest/download/YozhProxificator.dmg)**

Yêu cầu: máy Mac dùng Apple silicon, macOS 15 trở lên.

Tệp tải về là một ảnh đĩa. Trong đó có ứng dụng và lối tắt tới thư mục Ứng dụng, không có gì khác. Hãy mở ảnh đĩa rồi
kéo YozhProxificator vào Ứng dụng, hoặc mở ứng dụng ngay từ ảnh đĩa: ứng dụng sẽ đề nghị tự chuyển vào đó. Ứng dụng tự
cập nhật từ kho này; các bản cập nhật đều được ký, và có thể tắt việc kiểm tra tự động trong cài đặt của ứng dụng.

## Kiểm tra tệp bạn đã tải

Mỗi bản phát hành công khai `vX.Y.Z` có một tệp `SHA256SUMS` chứa SHA-256 của các tệp của nó. Hãy tải tệp đó vào thư mục
đang chứa ảnh đĩa, rồi chạy trong Terminal, ngay trong thư mục đó:

    shasum -a 256 -c SHA256SUMS --ignore-missing

Bản dựng thử trong bản phát hành `acceptance` thì có tệp `SHA256SUMS-X.Y.Z` riêng: hãy tải tệp đó cạnh ảnh đĩa và ghi tên
của nó vào lệnh.

Ảnh đĩa được ký bằng Developer ID và được Apple công chứng. Hãy thay `YozhProxificator.dmg` bằng tên tệp của bạn:

    spctl -a -t open --context context:primary-signature -v YozhProxificator.dmg

Lệnh trả lời `accepted` và `source=Notarized Developer ID`.

## Mã nguồn

YozhProxificator là phần mềm tự do theo GNU GPL v3, không kèm bảo hành. Mỗi bản phát hành công khai `vX.Y.Z` và mỗi bản
dựng thử trong bản phát hành `acceptance` đều kèm mã nguồn đầy đủ của những gì nó phát hành:

- `yozh-proxificator-mac-X.Y.Z-source.tar.gz` — ứng dụng, thành phần hệ thống của nó và các tập lệnh dựng;
- `yozh-xray-<commit>-source.tar.gz` — bộ máy proxy, một nhánh tách của Xray-core, ở commit mà bản dựng cố định
  (`<commit>` là mười hai ký tự đầu của commit đó);
- `sparkle-<version>-source.tar.gz` — khung cập nhật.

## Cách gỡ cài đặt

1. Trong ứng dụng, vào **Cài đặt → Toàn bộ lưu lượng** và bấm **Gỡ thành phần**.
2. Chuyển ứng dụng vào Thùng rác.
3. Nếu các chương trình vẫn không có mạng, hãy mở **Yozh Unblock** từ thư mục Ứng dụng. Nếu sau khi gỡ mà mất mạng, hãy
   chạy `sudo /Library/PrivilegedHelperTools/com.cyberyozh.proxyficator/yozh-helper restore` trong Terminal.

## Các nguồn cấp cập nhật

Ứng dụng đọc một nguồn cấp — danh sách các phiên bản, kèm ảnh đĩa và ghi chú mà chúng trỏ tới — để biết có phiên bản mới
hơn hay không. Có hai nguồn cấp, mỗi nguồn nằm trong một bản phát hành riêng:

- `acceptance` là bản phát hành thử nghiệm chứa các bản dựng thử nội bộ (0.9.x) và nguồn cấp của chúng, không dành cho
  mọi người dùng. Mỗi bản dựng kèm các tệp lưu trữ mã nguồn và `SHA256SUMS-X.Y.Z` riêng; tệp lưu trữ bộ máy hoặc khung
  mà nhiều bản dựng dùng chung chỉ được lưu một lần. Các bản dựng thử đọc nguồn cấp này, và 1.0.0 cũng được đăng vào đó,
  nên chúng chuyển sang nguồn cấp công khai cùng với bản này.
- `updates` là nguồn cấp của các bản phát hành công khai. Nó dành cho ứng dụng chứ không để tải về; mã nguồn của từng
  phiên bản trong đó nằm ở bản phát hành `vX.Y.Z` của phiên bản ấy.
