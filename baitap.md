# Bài tập 7: Gỡ Lỗi Tài Liệu Kế Hoạch Hội Nghị Khoa Học Sinh Viên PTIT 2026

## Phần 1. Phân Tích Lỗi Cấu Trúc Tài Liệu

### 1. Phân tích nguyên nhân Auto TOC không hoạt động
- **Cơ chế hoạt động của Auto TOC:** Chức năng Auto TOC (Table of Contents) trong Microsoft Word / Google Docs chỉ hoạt động dựa trên việc cào và thu thập các khối văn bản được gán nhãn **Heading Styles** (Heading 1, Heading 2, Heading 3,...).
- **Nguyên nhân lỗi:** Tất cả 7 dòng tiêu đề trong file kế hoạch đều mang nhãn **Normal** (văn bản thường) hoặc được định dạng thủ công (chỉnh font size 16, 14, màu xanh, tô vàng). Vì hệ thống không tìm thấy bất kỳ nhãn Heading nào, công cụ Auto TOC trả về kết quả rỗng (blank).
- **Chi tiết lỗi của từng dòng tiêu đề:**
  - `1. Thông tin chung hội nghị`: Mang nhãn Normal, định dạng thủ công (size 16, tô vàng).
  - `1.1. Tên hội nghị`: Mang nhãn Normal, định dạng thủ công (size 14, in đậm).
  - `1.2. Thời gian & địa điểm`: Mang nhãn Normal, định dạng thủ công (size 14, in đậm).
  - `2. Cơ cấu ban tổ chức`: Mang nhãn Normal, định dạng thủ công (size 16, tô vàng).
  - `2.1. Ban Nội dung`: Mang nhãn Normal, định dạng thủ công (size 13, màu xanh).
  - `2.1.1. Tiểu ban Kỹ thuật`: Mang nhãn Normal, định dạng thủ công (size 13, màu xanh) — Bị phân cấp sai (thuộc cấp 3 nhưng cấu trúc cây lại ngang hàng với mục 2.1).
  - `3. Lịch trình sự kiện`: Mang nhãn Normal thô, hoàn toàn không được định dạng.

### 2. Phân tích ảnh hưởng của việc nhầm cấp Heading (H2 vs H3)
- **Tác động lên giao diện mục lục:** Auto TOC hiển thị cấp độ phân nhánh (Hierarchy) dựa trên độ thụt lùi đầu dòng (Indentation). 
- **Sự sai lệch:** Mục `2.1.1. Tiểu ban Kỹ thuật` là tiểu ban con thuộc `2.1. Ban Nội dung`. Nếu gán lầm nhãn **H2** thay vì **H3**, Auto TOC sẽ hiển thị lùi đầu dòng ngang hàng với mục cha `2.1`, làm mất đi cấu trúc phân cấp logic của tài liệu. Ngược lại, nếu chọn đúng nhãn **H3**, mục lục sẽ thụt vào trong 1 nấc rõ ràng, thể hiện đúng mối quan hệ phụ thuộc.

---

## Phần 2. Hướng Dẫn Sửa Lỗi & Nghiệm Thu

### 1. Bảng quy đổi cấu trúc Heading Styles chuẩn

| Dòng tiêu đề | Định dạng lỗi hiện tại | Nhãn Style chuẩn | Phím tắt gán nhanh |
| :--- | :--- | :--- | :--- |
| **1. Thông tin chung hội nghị** | Chữ thường, cỡ 16, in đậm, tô vàng | **Heading 1** | `Ctrl + Alt + 1` |
| **1.1. Tên hội nghị** | Normal + in đậm + cỡ 14 | **Heading 2** | `Ctrl + Alt + 2` |
| **1.2. Thời gian & địa điểm** | Normal + in đậm + cỡ 14 | **Heading 2** | `Ctrl + Alt + 2` |
| **2. Cơ cấu ban tổ chức** | Chữ thường, cỡ 16, in đậm, tô vàng | **Heading 1** | `Ctrl + Alt + 1` |
| **2.1. Ban Nội dung** | Normal + cỡ 13 + màu xanh | **Heading 2** | `Ctrl + Alt + 2` |
| **2.1.1. Tiểu ban Kỹ thuật** | Normal + cỡ 13 + màu xanh | **Heading 3** | `Ctrl + Alt + 3` |
| **3. Lịch trình sự kiện** | Normal, không định dạng | **Heading 1** | `Ctrl + Alt + 1` |

---

### 2. Các bước thao tác sửa cấu trúc & chèn Auto TOC

1. **Chuẩn hóa nhãn tiêu đề (Sử dụng phím tắt):**
   - Đặt con trỏ chuột tại dòng `1. Thông tin chung hội nghị`, nhấn `Ctrl + Alt + 1` để gán nhãn **Heading 1**.
   - Đặt con trỏ chuột tại dòng `1.1. Tên hội nghị` và `1.2. Thời gian & địa điểm`, nhấn `Ctrl + Alt + 2` để gán nhãn **Heading 2**.
   - Đặt con trỏ chuột tại dòng `2. Cơ cấu ban tổ chức`, nhấn `Ctrl + Alt + 1` để gán nhãn **Heading 1**.
   - Đặt con trỏ chuột tại dòng `2.1. Ban Nội dung`, nhấn `Ctrl + Alt + 2` để gán nhãn **Heading 2**.
   - Đặt con trỏ chuột tại dòng `2.1.1. Tiểu ban Kỹ thuật`, nhấn `Ctrl + Alt + 3` để gán nhãn **Heading 3**.
   - Đặt con trỏ chuột tại dòng `3. Lịch trình sự kiện`, nhấn `Ctrl + Alt + 1` để gán nhãn **Heading 1**.
2. **Chèn Mục lục tự động:**
   - Đặt con trỏ chuột tại trang đầu tài liệu.
   - Vào thẻ `References` ➔ Chọn `Table of Contents` ➔ Chọn `Automatic Table 1` (hoặc `Automatic Table 2`).

---

### 3. Sửa bẫy dữ liệu (Cập nhật số trang khi thay đổi nội dung)

- **Vấn đề:** Khi gõ thêm nội dung khiến mục `3. Lịch trình sự kiện` bị đẩy từ trang 2 sang trang 4, bảng Auto TOC **không tự động cập nhật số trang thời gian thực** nếu người dùng không thực hiện lệnh làm mới.
- **Thao tác xử lý:**
  1. Click chuột vào vùng bảng Mục lục tự động (Auto TOC).
  2. Nhấn phím **`F9`** (hoặc nhấp chuột phải ➔ chọn `Update Field`).
  3. Chọn option **`Update entire table`** (Cập nhật toàn bộ bảng) ➔ Nhấn **OK**. Số trang của mục 3 sẽ ngay lập tức được cập nhật thành trang 4.
