# 🧭 Hướng Dẫn Nhập Nội Dung

## 1. Nhóm `fixed_type` – Cài đặt lịch

Dùng cho các nội dung cần được hiển thị theo thời gian cố định hoặc lặp lại.

### 🟩 Trường `welcome` (true / false)

- **`true`**  
  - Bỏ qua các trường: `hour`, `minute`, `daysOfWeek`, `startAfterMinutes`, `repeatIntervalMinutes`.  
  - Chỉ hiển thị **một lần duy nhất** khi người dùng mở app **lần đầu tiên**.  

- **`false`**  
  - Hệ thống sẽ xác định đây là **lịch hàng tuần** hoặc **lịch lặp custom**, tùy vào các trường được khai báo.

---

### 🗓️ Lịch Hàng Tuần

Các trường **bắt buộc**:

| Trường | Kiểu dữ liệu | Mô tả |
|--------|---------------|-------|
| `hour` | `number` | Giờ bắn thông báo |
| `minute` | `number` | Phút bắn thông báo |
| `daysOfWeek` | `array<number>` | Mảng ngày trong tuần cần bắn |

#### Quy ước `daysOfWeek`:
```
1 -> Chủ nhật  
2 -> Thứ 2  
3 -> Thứ 3  
...  
7 -> Thứ 7  
```

**Ví dụ:**
```json
"daysOfWeek": [1, 2, 3]
```
> Thông báo sẽ bắn vào **Chủ nhật, Thứ 2 và Thứ 3**.

---

### 🔁 Lịch Lặp Custom

Các trường **bắt buộc**:

| Trường | Kiểu dữ liệu | Mô tả |
|--------|---------------|-------|
| `hour` | `number` | Giờ bắn thông báo |
| `minute` | `number` | Phút bắn thông báo |
| `startAfterMinutes` | `number` | Thời gian (phút) bắt đầu vòng lặp sau khi cài đặt |
| `repeatIntervalMinutes` | `number` | Thời gian (phút) giữa các lần lặp |

**Ví dụ:**
```json
"startAfterMinutes": 4320,  
"repeatIntervalMinutes": 1440
```
> Nghĩa là bắt đầu bắn sau **3 ngày (4320 phút)** kể từ khi cài đặt, và **lặp lại mỗi ngày (1440 phút)**.

---

## 2. Nhóm `event_type` – Theo Sự Kiện

Dùng cho các thông báo xuất hiện khi có sự kiện đặc biệt như:

- **Kill app** (đóng ứng dụng)  
- **Mở điện thoại**

👉 Không cần khai báo thời gian (`hour`, `minute`, ...).  
Hệ thống sẽ **ưu tiên theo thứ tự từ trên xuống dưới** trong danh sách cấu hình.
