# AnhNg's journal — Hugo

Blog tối giản, riêng tư (noindex), host trên GitHub Pages qua GitHub Actions.
Mỗi "cuốn sổ" là một thư mục trong `content/` (một section). Sổ 1 là trang chủ.

## Cấu trúc

    hugo.toml                  cấu hình
    content/
      _index.md                trang chủ = sổ "Ghi chú" + mục nav
      about.md                 trang "Giới thiệu"  (giữ nội dung của bạn)
      posts/                   SỔ 1: app Zettel Notes ghi vào đây
        _index.md              chỉ để ẩn trang /posts/ thừa
      ghi-chu-2/               SỔ 2: notebook thứ 2 của app ghi vào đây
        _index.md              trang /ghi-chu-2/ + mục nav
    data/                      (không còn dùng — nav qua menu trong front matter)
    assets/scss/               main.scss + _custom.scss
    static/robots.txt
    layouts/
      baseof.html              khung chung
      home.html                liệt kê sổ 1
      section.html             liệt kê sổ bất kỳ (sổ 2, 3...)
      page.html                trang đơn + bài viết (tự hiện ngày nếu là bài trong sổ)
      404.html
      _partials/{head,header,footer,post-list}.html
      _shortcodes/img.html
    .github/workflows/hugo.yml

## Chạy thử cục bộ

    hugo server

Mở http://localhost:1313/ . (CSP chỉ bật khi build production nên livereload chạy bình thường khi xem cục bộ.)

## Build production (giống CI)

    hugo --minify

## Thêm cuốn sổ mới (vd "Ghi chú 3")

1. Tạo thư mục `content/ghi-chu-3/` và file `_index.md`:

       ---
       title: "Ghi chú 3"
       menus:
         main:
           name: Ghi chú 3
           weight: 30
       ---

2. Trong app Zettel Notes, thêm một notebook mới đồng bộ vào `content/ghi-chu-3/`.
   Không cần sửa template.

## Thêm trang tĩnh mới (vd "Nhạc", "Link")

Tạo một file ở gốc `content/`, vd `content/nhac.md`:

    ---
    title: "Nhạc"
    menus:
      main:
        name: Nhạc
        weight: 40
    ---
    Nội dung...

`weight` quyết định thứ tự trên thanh nav (số nhỏ đứng trước).

## Chèn ảnh trong bài

    {{< img url="https://i.ibb.co/xxx/abc.webp" cap="Chú thích" w="80%" ratio="3/2" >}}

Nên nén ảnh sang WebP và luôn truyền `ratio` để trang không nhảy khi ảnh tải.
