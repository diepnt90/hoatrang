# Hoatrang

Trang HTML tĩnh, tệp chính: [`index.html`](./index.html).

## Triển khai bằng Cloudflare Workers (Static Assets)

1. Vào [Cloudflare Dashboard](https://dash.cloudflare.com/) → **Workers & Pages** → **Create** → **Import a repository** (hoặc **Connect to Git**).
2. Chọn repository `diepnt90/hoatrang` và nhánh `main`.
3. Giữ file `wrangler.jsonc` trong thư mục gốc. Nếu được hỏi build/deploy commands, không cần build và dùng lệnh deploy `npx wrangler deploy`.
4. Deploy. Truy cập tên miền `*.workers.dev` mà Cloudflare cung cấp.

Cấu hình Worker dùng `assets.directory: "./"` để phục vụ `index.html` ở root. `.assetsignore` giúp loại các tệp cấu hình khỏi nội dung public khi deploy qua Wrangler.

## Phương án Cloudflare Pages (không cần Worker script)

1. Vào **Workers & Pages** → **Create** → **Pages** → **Connect to Git**.
2. Chọn repository `diepnt90/hoatrang`, production branch `main`.
3. Framework preset: **None**; build command: **để trống** (hoặc `exit 0`); build output directory: `.`; root directory: `/` (mặc định).
4. Chọn **Save and Deploy**. Địa chỉ sẽ có dạng `*.pages.dev`.

> Trang tĩnh không có máy chủ lưu dữ liệu: nếu cần đăng nhập/lưu kết quả sinh viên dùng chung giữa nhiều máy, phải kết nối backend/database, chẳng hạn Cloudflare D1 + Worker API.
