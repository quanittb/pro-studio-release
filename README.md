# Pro Studio AI — Release Repository

Đây là repo phân phối bản build cho **Pro Studio AI**.
Repo này được cập nhật tự động từ CI/CD pipeline của repo dev.

## Cách hoạt động

1. Dev push tag `vX.Y.Z` lên repo chính `quanittb/pro-studio`
2. GitHub Actions tự động build Electron app (Windows x64)
3. Installer `.exe` được tạo release tại repo này
4. File `version.json` được cập nhật, ứng dụng đang chạy sẽ tự phát hiện bản mới

## Cấu trúc `version.json`

```json
{
  "version": "1.0.1",
  "tag": "v1.0.1",
  "releasedAt": "2026-10-03T03:08:58.706Z",
  "mandatory": false,
  "notes": "Mô tả thay đổi"
}
```

- `mandatory: true` → Người dùng thường BẮT BUỘC cập nhật trước khi dùng tiếp
- `mandatory: false` → Thông báo tùy chọn, có thể bỏ qua (PROMAX luôn tùy chọn)

## Phát hành thủ công

Vào GitHub Actions của repo `quanittb/pro-studio` → Run workflow **Build & Release** → nhập version.

## Yêu cầu secrets (trong repo `quanittb/pro-studio`)

- `RELEASE_TOKEN`: GitHub Personal Access Token với quyền `repo` (full) trên cả hai repo