# wh3000-release

Kênh phát hành công khai của **WH3000**, gồm app quản trị và firmware cho router Huasifei WH3000 eMMC.
Mã nguồn nằm ở repo riêng. Repo này chỉ chứa bản build (GitHub Releases) và manifest của bản firmware
mới nhất.

## Cài đặt

- **Firmware**: tải `wh3000-firmware-<version>-sysupgrade.bin` ở Release `firmware-v…` mới nhất, rồi flash
  ở trang *Firmware* của app. Flash luôn xoá mọi cấu hình, đưa router về mặc định. Ảnh đã có sẵn app.
- **App**: router chạy firmware WH3000 cập nhật app ở trang *Firmware*, không cần tải tay. Router hỏi máy chủ
  WH3000 nên chạy bản nào, rồi tải binary từ Release `app-v…` của bản đó.

## Manifest tự cập nhật

| File | Nội dung |
|---|---|
| `firmware/latest.json` | Bản firmware mới nhất: URL, SHA256 và kích thước của ảnh sysupgrade, theo board (`huasifei,wh3000-emmc`) |

Không sửa tay file này: script phát hành ghi nó sau khi đăng bản build.

Bản app không có manifest ở đây. Script phát hành đăng ký từng bản app với máy chủ WH3000, và máy chủ chọn
bản router nên chạy (bản mới nhất chưa bị thu hồi). Router tải binary từ Release và kiểm SHA256 trước khi
cài.
