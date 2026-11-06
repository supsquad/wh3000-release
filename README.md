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

Manifest có chữ ký ed25519 đi kèm (`latest.json.sig`). Router bỏ qua manifest nào không kiểm được chữ ký.
Không sửa tay các file này: script phát hành ghi chúng sau khi đăng bản build.

Manifest của bản app không nằm ở đây. Script phát hành đăng ký từng bản app với máy chủ WH3000, và máy chủ
chọn bản router nên chạy (bản mới nhất chưa bị thu hồi). Manifest vẫn được ký bằng cùng khoá, router kiểm
chữ ký trước khi tải binary từ Release.
