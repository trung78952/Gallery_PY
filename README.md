# Gallery Ver2

Trang web gallery hình ảnh/video với masonry layout, nhóm theo địa điểm + thời gian, có trang quản trị upload nhiều file và lưu dữ liệu bằng SQLite local.

## Tính năng

- Gallery public hiển thị theo group (địa điểm + thời gian)
- Masonry layout cho cả ảnh và video
- Lazy scroll: tải group theo trang khi cuộn xuống
- Video tự động phát/tạm dừng theo viewport
- Animation nhẹ cho tên group khi cuộn tới
- Trang admin chỉ có đăng nhập (1 tài khoản duy nhất)
- Admin tạo group mới với nhiều file upload cùng lúc
- Admin sửa tên/địa điểm/thời gian, thêm/xóa media trong group
- Trường địa điểm là tuỳ chọn (không bắt buộc)
- Admin xóa từng group
- Lưu dữ liệu local vào SQLite, không dùng cloud

## Cấu trúc

- `frontend/`: Vue 3 (CDN, không cần build tool)
- `server/app.py`: Flask API + static files + SQLite
- `server/uploads/`: file media upload
- `server/gallery.db`: database SQLite (tự tạo khi chạy)

## Chạy dự án

1. Cài Python 3.10+ (khuyến nghị).
2. Tạo môi trường ảo và cài dependency:

```bash
cd server
python -m venv .venv
source .venv/Scripts/activate
pip install -r requirements.txt
```

3. Tạo file `.env` từ `.env.example` (tuỳ chọn):

```bash
copy .env.example .env
```

4. Chạy server:

```bash
python app.py
```

## Chạy production (khuyến nghị)

Production mode dùng Flask dev server với `FLASK_DEBUG=0` (ổn định và responsive):

```bash
cd server
python -m venv .venv
source .venv/Scripts/activate
pip install -r requirements.txt
set FLASK_DEBUG=0
python app.py
```

Hoặc trên Windows, chạy nhanh:

```bat
run_production.bat
```

**Để stop server:** Nhấn `Ctrl+C` trong terminal.

5. Mở trình duyệt:

- Public gallery: `http://localhost:4000/`
- Admin: `http://localhost:4000/admin`

## Public bằng Cloudflare Tunnel

Nếu đã cài `cloudflared`, bạn có thể chạy file sau để mở app local và tunnel public trong 1 lần:

```bat
run_public_gallery.bat
```

File này sẽ tự mở 2 cửa sổ riêng:

- `Gallery Server`
- `Cloudflare Tunnel`

Link public `trycloudflare.com` sẽ hiện trong cửa sổ tunnel.

## Tài khoản admin mặc định

- Username: `admin`
- Password: `admin123`

Bạn nên đổi bằng biến môi trường `ADMIN_USERNAME` và `ADMIN_PASSWORD` trước khi deploy.
# Gallery_PY
