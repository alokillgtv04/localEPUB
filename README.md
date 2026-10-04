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

```
┌────────────────────────────────────────────────────────────┐
│  📚 EPUB LIST EDITOR 1.1     [🔄 Đồng bộ] [📥 Nhập] ...    │  ← Header
├────────────┬───────────────────────────────────────────────┤
│ Thể loại   │  Tên thể loại · N truyện    [+ Thêm truyện]   │
│ ─────────  │  ─────────────────────────────────────────    │
│ ▸ Kim Dung │  ┌──────┐  ┌──────┐  ┌──────┐                │
│ ▸ Tiên Hiệp│  │ Book │  │ Book │  │ Book │                │
│ ▸ Huyền Huyễn│ └──────┘  └──────┘  └──────┘               │
│ ▸ ...      │                                                │
└────────────┴───────────────────────────────────────────────┘
     Sidebar                  Main (book grid)
```

**Header (trên cùng):**
- 🔄 **Đồng bộ** — kéo dữ liệu mới từ server về
- 📥 **Nhập** — nhập JSON từ file/clipboard
- 📤 **Xuất file** — tải file `listepub.txt` về máy
- 📋 **Copy** — copy JSON vào clipboard
- 🗑 **Reset** — xoá toàn bộ (cẩn thận!)

**Sidebar (trái):** danh sách thể loại, có nút ▲▼ để đổi thứ tự.

**Main (phải):** lưới truyện của thể loại đang chọn.

---

## 🗂 Quản lý thể loại

### Thêm thể loại
Bấm **`+ Thêm`** ở đầu sidebar → nhập tên → Enter.

### Sắp xếp
Hover lên thể loại → hiện ▲▼ → bấm để di chuyển lên/xuống.

### Đổi tên / Xoá thể loại
> ⚠️ Bản 1.1 **chưa có UI** cho 2 việc này. Cách xử lý:
> - **Xoá:** xuất JSON → sửa bằng tay → nhập lại (dùng chế độ ghi đè bằng Reset trước).
> - **Đổi tên:** cũng sửa JSON tương tự.

---

## 📚 Quản lý truyện

### Thêm truyện
1. Chọn thể loại bên trái (bắt buộc).
2. Bấm **`+ Thêm truyện`** ở góc phải.
3. Điền form:
   - **Tên truyện** *(bắt buộc)*
   - **URL Ebook** *(bắt buộc)* — chỉ cần gõ `banlong` → hệ thống tự sinh `epub/banlong.epub`
   - **URL Ảnh bìa** — tương tự, gõ `banlong` → `img/banlong.jpg`
   - **Tác giả** *(tuỳ chọn)*
   - **Định dạng** — EPUB/TXT/HTML/DOCX/ODT/RTF
   - **Giới thiệu** *(tuỳ chọn)*
4. Bấm **💾 Lưu** hoặc `Ctrl+S`.

### Sửa truyện
Hover lên card truyện → bấm ✏️.

### Xoá truyện
Hover lên card truyện → bấm 🗑 → xác nhận.

### Sắp xếp truyện
Hover card → bấm ▲▼ để di chuyển.

---

## ✨ Auto-fill URL

Hệ thống tự sinh URL theo **slug hoá tên truyện** (bỏ dấu, viết thường, bỏ ký tự đặc biệt).

**Ví dụ:**

| Tên nhập | URL sinh ra | Cover sinh ra |
|---|---|---|
| `Bàn Long` | `epub/banlong.epub` | `img/banlong.jpg` |
| `Thiên Long Bát Bộ` | `epub/thienlongbatbo.epub` | `img/thienlongbatbo.jpg` |
| `Ỷ Thiên Đồ Long Ký` | `epub/ythiendolongky.epub` | `img/ythiendolongky.jpg` |
| `Bắt Đầu 100 Triệu Năm Tu Vi` | `epub/batdau100trieunamtuvi.epub` | `img/batdau100trieunamtuvi.jpg` |

**Cách hoạt động:**
- **Tự động:** khi bạn gõ tên, sau 400ms hệ thống tự điền URL (nếu URL đang trống hoặc vẫn là auto-fill cũ).
- **Thủ công:** bấm nút **✨ Auto-fill từ tên** ở chân modal → ghi đè luôn.
- **Đổi format:** đổi dropdown EPUB→TXT → URL tự đổi đuôi `.epub` → `.txt`.

> 🔒 Nếu bạn **tự tay sửa URL** khác đi, hệ thống sẽ **không ghi đè** nữa.

---

## 🔄 Đồng bộ dữ liệu

### Cơ chế
Khi mở trang, hệ thống tự động:

1. Fetch JSON từ server remote:
   ```
   https://vaxplugin.alokillgtv02.workers.dev/tv/novel/listepub.txt?cache=false
   ```
2. So sánh với dữ liệu **localStorage** của bạn.
3. **Gộp thông minh:**
   - Thể loại trùng tên (không phân biệt hoa/thường) → gộp truyện.
   - Thể loại chưa có → thêm mới.
   - Truyện trùng **URL** hoặc **tên** → bỏ qua.
   - Truyện cũ thiếu `author`/`description`/`cover` mà bản mới có → tự bổ sung.
4. Báo toast `+N truyện, +M thể loại` nếu có cái mới.
5. Lưu vào localStorage.

### Đồng bộ thủ công
Bấm nút **🔄 Đồng bộ** trên header bất kỳ lúc nào để force refresh (tự thêm `?_t=timestamp` phá cache).

### Khi nào cần đồng bộ?
- Server admin vừa thêm truyện mới → bạn bấm 🔄 để cập nhật.
- Mở trên máy mới → tự động fetch lần đầu.
- Nghi ngờ dữ liệu local cũ → bấm 🔄 để so lại.

> 💡 **Dữ liệu của bạn không bị mất** khi đồng bộ — chỉ có thêm, không ghi đè, không xoá.

---

## 📤 Xuất file để chia sẻ

### Xuất ra file
Bấm **📤 Xuất file** → tải về file **`listepub.txt`**.

File này là JSON pretty-printed, có thể:
- Gửi qua Zalo/Messenger/Telegram/Email.
- Upload lên Google Drive, Dropbox.
- Commit vào Git repo.
- Đặt trên server remote để người khác đồng bộ.

### Copy vào clipboard (nhanh hơn)
Bấm **📋 Copy** → toàn bộ JSON vào clipboard → dán vào đâu cũng được (chat, notepad, form web…).

### Nội dung file xuất ra trông như thế nào?

```json
{
  "version": 1,
  "categories": [
    {
      "name": "Kim Dung",
      "items": [
        {
          "title": "Anh Hùng Xạ Điêu",
          "url": "epub/anhhungxadieu.epub",
          "cover": "img/anhhungxadieu.jpg",
          "author": "Kim Dung",
          "description": "",
          "format": "epub"
        }
      ]
    }
  ]
}
```

### 📌 Muốn tự host để người khác đồng bộ?
1. Đặt file JSON tại URL công khai (GitHub raw, Cloudflare Worker, CDN…).
2. Sửa biến `REMOTE_DATA_URL` trong `<script>` của `index.html`:
   ```js
   var REMOTE_DATA_URL = 'https://your-server.com/path/listepub.txt';
   ```
3. Push lại. Ai mở trang cũng sẽ tự đồng bộ từ URL mới.

---

## 📥 Nhập file từ người khác

### Cách 1 — Dán JSON
1. Bấm **📥 Nhập**.
2. Tab **📋 Dán JSON** (mặc định).
3. Paste nội dung JSON vào textarea.
4. Bấm **📥 Nhập**.

### Cách 2 — Chọn file
1. Bấm **📥 Nhập** → tab **📁 Chọn file**.
2. **Kéo thả** file `.txt`/`.json` vào khung, **hoặc** bấm vào khung để chọn file.
3. File sẽ được đọc và tự chuyển qua tab Dán JSON.
4. Bấm **📥 Nhập**.

### Cơ chế gộp khi nhập
Từ bản 1.1, **nhập luôn luôn gộp** (không còn tuỳ chọn ghi đè):

- Thể loại trùng tên → gộp items.
- Truyện trùng URL **hoặc** tên → bỏ qua.
- Metadata thiếu → bổ sung.
- Kết quả báo cáo: `📥 Đã gộp: +N truyện, +M thể loại` hoặc `✓ Không có gì mới`.

### Muốn ghi đè hoàn toàn?
1. Bấm **🗑 Reset** trước (xoá sạch).
2. Rồi mới **📥 Nhập** file mới.

---

## 🧬 Cấu trúc dữ liệu JSON

```jsonc
{
  "version": 1,                       // Số phiên bản schema
  "categories": [                     // Mảng thể loại
    {
      "name": "Kim Dung",             // Tên thể loại (bắt buộc)
      "items": [                      // Mảng truyện
        {
          "title": "Anh Hùng Xạ Điêu",    // Tên truyện (bắt buộc)
          "url": "epub/anhhungxadieu.epub", // Đường dẫn file (short hoặc full URL)
          "cover": "img/anhhungxadieu.jpg", // Đường dẫn ảnh bìa (short hoặc full)
          "author": "Kim Dung",           // Tác giả (tuỳ chọn)
          "description": "",              // Mô tả (tuỳ chọn)
          "format": "epub"                // epub | txt | html | docx | odt | rtf
        }
      ]
    }
  ]
}
```

**Quy tắc đường dẫn:**
- Nếu là **short path** (không có `http://`) → tự động ghép với `DEFAULT_RAW_BASE`:
  - `epub/abc.epub` → `https://raw.githubusercontent.com/alokillgtv-gif/newtest/main/book/epub/abc.epub`
- Nếu là **full URL** → dùng nguyên xi (không ghép base).
- Khi lưu, hệ thống **tự rút gọn** URL thuộc base mặc định về short path.

---

## ⚙️ Cấu hình

Mở `index.html`, tìm block `CONFIG` trong `<script>`:

```js
var DEFAULT_RAW_BASE = 'https://raw.githubusercontent.com/alokillgtv-gif/newtest/main/book/';
var REMOTE_DATA_URL  = 'https://vaxplugin.alokillgtv02.workers.dev/tv/novel/listepub.txt?cache=false';
var LS_KEY           = 'epub_editor_data_v1';
var LS_KEY_ACTIVE    = 'epub_editor_active_cat';
```

| Biến | Ý nghĩa |
|---|---|
| `DEFAULT_RAW_BASE` | Base URL để expand short path. Đổi sang repo/CDN của bạn. |
| `REMOTE_DATA_URL` | URL server để đồng bộ tự động. |
| `LS_KEY` | Key lưu dữ liệu chính trong localStorage. |
| `LS_KEY_ACTIVE` | Key lưu thể loại đang chọn. |

> 💡 Sau khi đổi `DEFAULT_RAW_BASE`, **xoá localStorage cũ** (Reset) để tránh xung đột path.

---

## ❓ FAQ

Xem file **`faq.html`** để có bản FAQ đầy đủ với UI đẹp.

Tóm tắt vài câu hỏi hay gặp:

- **Dữ liệu lưu ở đâu?** → Trong `localStorage` của trình duyệt.
- **Mở máy khác có dữ liệu không?** → Không, trừ khi đồng bộ từ server hoặc nhập file.
- **Reset có hoàn tác được không?** → Không. Nên Xuất file backup trước.
- **Server remote là gì?** → URL JSON bạn cấu hình ở `REMOTE_DATA_URL`.
- **Thêm truyện vào server remote như thế nào?** → Sửa file JSON trên server/repo, không phải sửa trong web này.

---

## ⌨️ Phím tắt

| Phím | Tác dụng |
|---|---|
| `Ctrl + S` (hoặc `⌘ + S`) | Lưu form đang mở |
| `Esc` | Đóng modal |
| `Enter` trong prompt tên thể loại | Xác nhận |

---

## 🐛 Báo lỗi / Góp ý

Liên hệ admin repo hoặc tạo Issue trên GitHub.

---

**Version:** 1.1 · **License:** MIT · **Author:** alokillgtv
