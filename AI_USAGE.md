# AI Usage Log

## 1. Công cụ AI
Tên công cụ: Claude (Anthropic) – claude.ai

## 2. Mục đích sử dụng
- Phân tích giao diện website Shopee.vn theo 5 khu vực yêu cầu
- Đề xuất vấn đề cần cải tiến trên thẻ sản phẩm
- Hỗ trợ tạo bố cục HTML/CSS cho giao diện cải tiến
- Giải thích vai trò của các thành phần HTML/CSS

## 3. Prompt đã sử dụng

### Prompt 1 – Phân tích website
```
Bạn là chuyên gia phân tích nghiệp vụ và thiết kế trải nghiệm người dùng
cho website thương mại điện tử.

Tôi đang khảo sát website: Shopee Việt Nam (https://shopee.vn).

Hãy giúp tôi lập bảng phân tích các khu vực:
1. Trang chủ.
2. Danh mục sản phẩm.
3. Chi tiết sản phẩm.
4. Tìm kiếm.
5. Giỏ hàng.

Với mỗi khu vực, hãy nêu:
- Mục đích của chức năng.
- Thành phần giao diện cần có.
- Điểm thuận tiện đối với khách hàng.
- Một vấn đề có thể phát sinh.
- Một đề xuất cải tiến.
```

### Prompt 2 – Đề xuất giao diện cải tiến
```
Tôi đang thực hiện bài tập phát triển giao diện website thương mại điện tử
bằng HTML5 và CSS3.

Tôi muốn cải tiến khu vực: thẻ sản phẩm (product card) trên trang danh mục
của Shopee – cụ thể là cách hiển thị giá gốc, giá khuyến mãi và tỷ lệ % giảm giá.

Đối tượng sử dụng: khách hàng mua sắm trực tuyến tại Việt Nam.

Hãy đề xuất:
1. Bố cục giao diện.
2. Các thành phần HTML cần sử dụng.
3. Cách tổ chức CSS.
4. Cách hiển thị trên máy tính và điện thoại.
5. Những điểm cần kiểm tra về khả năng sử dụng.

Trước tiên, hãy giải thích phương án thiết kế.
Chưa tạo toàn bộ mã nguồn cho đến khi tôi yêu cầu.
```

### Prompt 3 – Tạo mã nguồn
```
Dựa trên phương án đã thống nhất, hãy tạo một trang giao diện
thương mại điện tử bằng HTML5 và CSS3.

Yêu cầu:
- Giao diện có tiêu đề và khu vực sản phẩm.
- Có tối thiểu 4 sản phẩm mẫu.
- Mỗi sản phẩm có hình ảnh, tên, giá và nút thao tác.
- Bố cục phù hợp với màn hình máy tính và điện thoại.
- Mã HTML có cấu trúc rõ ràng.
- CSS được tách thành file riêng.
- Không sử dụng backend hoặc cơ sở dữ liệu.
```

## 4. Kết quả AI đề xuất

AI phân tích Shopee và xác định vấn đề chính trên thẻ sản phẩm:
- Trang chủ hiển thị banner flash sale nhưng % giảm giá không thống nhất trên các thẻ
- Thẻ sản phẩm trên desktop thiếu badge % giảm giá rõ ràng ở chế độ duyệt danh mục
- Trên mobile, dòng giá gốc + giá sale đôi khi bị cắt do không đủ chiều rộng

AI đề xuất phương án thiết kế:
- Badge `−XX%` nổi bật góc trên trái ảnh sản phẩm (absolute positioning)
- Hàng giá 2 dòng: dòng 1 = giá sale (nổi bật đỏ), dòng 2 = giá gốc gạch ngang + tag inline
- CSS Grid responsive: 5 cột desktop → 3 cột tablet → 2 cột mobile
- Thêm `free-ship` pill và rating để đủ thông tin quyết định mua

## 5. Kiểm tra và điều chỉnh

| Điểm AI đề xuất | Kết quả kiểm tra | Quyết định |
|---|---|---|
| Badge % góc trên ảnh | Kiểm tra trên Chrome: hiển thị rõ ✓ | Giữ lại |
| Hàng giá 2 dòng | Kiểm tra mobile 375px: vừa đủ, không bị cắt ✓ | Giữ lại |
| Grid 5 cột desktop | Kiểm tra 1200px: OK ✓ | Giữ lại |
| Nút "Thêm vào giỏ" trên mỗi card | Shopee thực tế không có nút này trên card danh mục | **Giữ lại** như đề xuất cải tiến – thuận tiện hơn |
| Hover scale ảnh | Kiểm tra: animation mượt ✓ | Giữ lại |
| Font chữ: `Segoe UI / Roboto` | Render tốt trên Windows và Mac ✓ | Giữ lại |

**Điểm tự điều chỉnh (không từ AI):**
- Thêm section "BEFORE" để so sánh trực tiếp với giao diện cũ — giúp giảng viên thấy rõ sự khác biệt
- Thêm màu placeholder ảnh theo màu sản phẩm thay vì màu xám mặc định — dễ nhìn hơn
- Thêm badge "MALL" cho sản phẩm Shopee Mall — phản ánh đúng thực tế Shopee

## 6. Phần tôi hiểu và có thể giải thích

**HTML:**
- `position: relative` trên `.product-card` + `position: absolute` trên `.discount-badge` → đặt badge chồng lên ảnh mà không ảnh hưởng layout
- `padding-top: 100%` trên `.product-img-wrapper` → tạo tỉ lệ khung hình vuông 1:1 responsive
- `display: -webkit-box` + `-webkit-line-clamp: 2` → giới hạn tên sản phẩm đúng 2 dòng

**CSS:**
- `grid-template-columns: repeat(5, 1fr)` → chia đều 5 cột, co dãn theo chiều rộng màn hình
- `@media (max-width: 600px)` → khi màn hình nhỏ hơn 600px, chuyển sang 2 cột
- `transition: transform 0.2s` trên `.product-card` → hiệu ứng hover nâng card mượt mà
- `text-decoration: line-through` trên `.price-original` → gạch ngang giá cũ
- `margin-top: auto` trên `.price-section` → đẩy phần giá xuống đáy card dù tên sản phẩm dài ngắn khác nhau
