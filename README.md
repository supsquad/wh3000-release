# wh3000-release

Kênh phát hành công khai của **WH3000**, gồm app quản trị và firmware cho router Huasifei WH3000 eMMC.
Mã nguồn nằm ở repo riêng. Repo này chỉ chứa bản build (GitHub Releases) và manifest mà router đọc để
tự cập nhật.

## Cài đặt

- **Firmware**: tải `wh3000-firmware-<version>-sysupgrade.bin` ở Release `firmware-v…` mới nhất, rồi flash
  ở trang *Firmware* của app. Flash luôn xoá mọi cấu hình, đưa router về mặc định. Ảnh đã có sẵn app.
- **App**: router chạy firmware WH3000 tự cập nhật app từ Release `app-v…` mới nhất, không cần tải tay.

## Manifest tự cập nhật

| File | Nội dung |
|---|---|
| `app/latest.json` | Bản app mới nhất: `version`, URL, SHA256 và kích thước của `wh3000-app-arm64`. App trên router đọc file này |
| `firmware/latest.json` | Bản firmware mới nhất: URL, SHA256 và kích thước của ảnh sysupgrade, theo board (`huasifei,wh3000-emmc`) |

Mỗi manifest có chữ ký ed25519 đi kèm (`latest.json.sig`). Router bỏ qua manifest nào không kiểm được chữ ký.

Không sửa tay các file này: script phát hành ghi chúng sau khi đăng bản build.
