# 📚 EPUB List Editor 1.1

Công cụ web (chạy offline, chỉ cần 1 file `.html`) để **quản lý danh sách truyện EPUB/TXT/HTML** theo thể loại, có **đồng bộ tự động từ server** và **nhập/xuất JSON** để chia sẻ với người khác.

---

## 📑 Mục lục

1. [Giới thiệu](#-giới-thiệu)
2. [Cài đặt & chạy](#-cài-đặt--chạy)
3. [Giao diện](#-giao-diện)
4. [Quản lý thể loại](#-quản-lý-thể-loại)
5. [Quản lý truyện](#-quản-lý-truyện)
6. [Auto-fill URL](#-auto-fill-url)
7. [🔄 Đồng bộ dữ liệu](#-đồng-bộ-dữ-liệu)
8. [📤 Xuất file để chia sẻ](#-xuất-file-để-chia-sẻ)
9. [📥 Nhập file từ người khác](#-nhập-file-từ-người-khác)
10. [Cấu trúc dữ liệu JSON](#-cấu-trúc-dữ-liệu-json)
11. [Cấu hình](#-cấu-hình)
12. [FAQ](#-faq)
13. [Phím tắt](#-phím-tắt)

---

## 🎯 Giới thiệu

**EPUB List Editor** là một trang HTML đơn lẻ, không cần server, không cần cài đặt. Bạn mở file là dùng được.

**Tính năng chính:**

| Tính năng | Mô tả |
|---|---|
| ✅ Quản lý thể loại | Thêm/sửa/xoá/sắp xếp thể loại |
| ✅ Quản lý truyện | Thêm/sửa/xoá/sắp xếp truyện trong mỗi thể loại |
| ✅ Auto-fill URL | Tự sinh URL ebook + ảnh bìa từ tên truyện |
| ✅ Lưu tự động | Mọi thay đổi lưu vào `localStorage` của trình duyệt |
| ✅ Đồng bộ remote | Tự động tải danh sách mới từ server, gộp không trùng |
| ✅ Xuất/Nhập JSON | Chia sẻ dữ liệu qua file hoặc clipboard |
| ✅ Copy nhanh | Copy toàn bộ JSON vào clipboard 1 click |
| ✅ Đường dẫn rút gọn | Lưu `banlong.epub` thay vì URL dài ngoằng |

---

## 🚀 Cài đặt & chạy

### Cách 1 — Mở trực tiếp (đơn giản nhất)

1. Tải file `index.html` (hoặc bất kỳ tên nào bạn muốn).
2. **Nhấp đôi** để mở bằng trình duyệt (Chrome, Edge, Firefox, Safari…).
3. Xong. Không cần cài gì.

### Cách 2 — Host online (chia sẻ cho người khác dùng)

Đẩy file lên **GitHub Pages / Netlify / Vercel / Cloudflare Pages** — bất kỳ static host nào. Ai có link cũng mở được.

> ⚠️ **Lưu ý:** dữ liệu lưu trong `localStorage` **của từng trình duyệt**. Mở trên máy khác, browser khác → danh sách trống trơn (trừ khi server remote có dữ liệu). Muốn chia sẻ → dùng **Xuất/Nhập JSON**.

---

## 🖥 Giao diện
