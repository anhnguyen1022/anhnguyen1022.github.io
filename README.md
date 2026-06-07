# AnhNg's journal — Hugo

Blog tối giản chuyển từ Jekyll sang Hugo. Host trên GitHub Pages qua GitHub Actions.

## Cấu trúc
- `hugo.toml`              — cấu hình (thay cho `_config.yml`)
- `content/about.md`       — trang About (thay cho `about.markdown`)
- `content/_index.md`      — nội dung đầu trang chủ (để trống)
- `_posts/`                — **giữ nguyên**: nơi app Zettel Notes ghi bài (mount vào content/posts)
- `data/navigation.yml`    — menu (thay cho `_data/navigation.yml`)
- `assets/scss/`           — `main.scss` + `_custom.scss` (thay cho `_sass/` + `assets/main.scss`)
- `layouts/`               — template (thay cho `_layouts/` + `_includes/`)
- `.github/workflows/hugo.yml` — build & deploy

## Chạy thử cục bộ
    hugo server
Mở http://localhost:1313/

## Build
    hugo --minify
