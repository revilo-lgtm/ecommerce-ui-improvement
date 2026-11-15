# E-commerce UI Improvement

**Bài tập cá nhân – Phát triển ứng dụng WEB/TMĐT – Chương 1**  
Giảng viên: TS Nguyễn Mạnh Tuấn – tuannm@ueh.edu.vn

---

## 1. Giới thiệu

Dự án này cải tiến giao diện thẻ sản phẩm (product card) của website thương mại điện tử **Shopee Việt Nam** (shopee.vn).

**Vấn đề phát hiện:** Trên trang danh mục sản phẩm Shopee, phần trăm giảm giá (%) không xuất hiện nhất quán trên mọi thẻ sản phẩm ở chế độ duyệt thông thường (không phải Flash Sale). Người dùng phải tự tính nhẩm mức giảm. Trên màn hình điện thoại, hàng thông tin giá gốc + giá sale đôi khi bị cắt bớt.

**Giải pháp:** Thiết kế lại thẻ sản phẩm với badge `−XX%` nổi bật, hàng giá 2 dòng (giá sale + giá gốc gạch ngang + tag % inline), và bố cục responsive 2 cột trên mobile không làm mất thông tin.

---

## 2. Website tham khảo

- **Tên website:** Shopee Việt Nam
- **URL:** https://shopee.vn
- **Nhóm sản phẩm kinh doanh:** Đa ngành hàng — thời trang, điện tử, mỹ phẩm, thực phẩm, đồ gia dụng và hàng nghìn danh mục khác
- **Khách hàng mục tiêu:** Người tiêu dùng Việt Nam từ 18–45 tuổi, mua sắm online qua điện thoại và máy tính; ưu tiên giá tốt, giao hàng nhanh và khuyến mãi thường xuyên
- **Các chức năng mua sắm chính:** Tìm kiếm và lọc sản phẩm, xem chi tiết sản phẩm, thêm vào giỏ hàng, áp mã giảm giá/voucher, thanh toán đa phương thức (COD, ví ShopeePay, thẻ ngân hàng), theo dõi đơn hàng
- **Khu vực đã khảo sát:** Trang chủ, Danh mục sản phẩm, Chi tiết sản phẩm, Tìm kiếm, Giỏ hàng

### Bảng khảo sát – 5 khu vực Shopee.vn

| Khu vực | Chức năng hiện có | Điểm hợp lý | Điểm có thể cải thiện | Đề xuất cải tiến |
|---|---|---|---|---|
| **Trang chủ** | Banner quảng cáo slideshow, danh mục icon theo ngành hàng, Flash Sale countdown timer, gợi ý "Có thể bạn thích" dựa theo lịch sử | Icon danh mục rõ ràng, Flash Sale tạo tính cấp bách, banner full-width bắt mắt | Popup khuyến mãi xuất hiện ngay khi vào trang che nội dung chính; người dùng phải đóng mới thấy được sản phẩm | Cho popup tự đóng sau 3–5s hoặc thu nhỏ thành banner dọc không che nội dung |
| **Danh mục sản phẩm** | Grid sản phẩm 2 cột (mobile) / 5 cột (desktop), lọc theo giá/đánh giá/vị trí, nút scroll-to-top | Layout grid gọn, card sản phẩm đủ ảnh + tên + giá + số lượng bán | % giảm giá chỉ hiện trong section Flash Sale, không hiện nhất quán trên card duyệt thông thường; trên mobile giá gốc dễ bị cắt | **→ Chính là điểm cải tiến của dự án này:** thêm badge % và hàng giá 2 dòng trên mọi card |
| **Chi tiết sản phẩm** | Ảnh sản phẩm gallery nhiều góc, chọn phân loại (màu/size), số lượng, nút "Mua ngay" và "Thêm vào giỏ", đánh giá sao + bình luận | Ảnh chất lượng cao, thông tin đầy đủ, khu vực đánh giá phong phú | Phần mô tả sản phẩm thường dài và không có mục lục, khó scan nhanh; thông tin size guide ẩn sâu | Thêm summary box tóm tắt thông số kỹ thuật cốt lõi ngay dưới giá |
| **Tìm kiếm** | Ô tìm kiếm sticky trên header, gợi ý autocomplete, lọc kết quả theo nhiều tiêu chí | Autocomplete nhanh và chính xác, lọc và sắp xếp linh hoạt, kết quả hiển thị ngay không tải lại trang | Trang kết quả tìm kiếm yêu cầu đăng nhập khi không có session, gây gián đoạn trải nghiệm khách chưa đăng ký | Cho phép xem kết quả tìm kiếm cơ bản mà không cần đăng nhập |
| **Giỏ hàng** | Danh sách sản phẩm theo shop, checkbox chọn từng sản phẩm hoặc toàn bộ, chỉnh số lượng inline, hiển thị voucher, tổng tiền cập nhật tức thì | Nhóm sản phẩm theo shop tiện lợi, tổng tiền live update, áp voucher trực tiếp trên trang | Không có nút "lưu để mua sau" – xóa sản phẩm là mất hẳn; trên mobile cột số lượng và giá đôi khi chật chội | Thêm tính năng "Lưu để mua sau" thay vì chỉ có "Xóa" |

---

## 3. Chức năng trang cải tiến

- Hiển thị lưới sản phẩm 5 cột (desktop) → 3 cột (tablet) → 2 cột (mobile)
- Mỗi thẻ sản phẩm: ảnh, tên (giới hạn 2 dòng), giá sale nổi bật, giá gốc gạch ngang, badge % giảm giá, đánh giá sao, số lượng bán, nhãn miễn phí vận chuyển, nút thêm giỏ hàng
- Section "BEFORE / AFTER" so sánh trực tiếp giao diện cũ và mới
- Hiệu ứng hover nâng card, zoom nhẹ ảnh sản phẩm
- Nút "Thêm vào giỏ" có phản hồi tương tác

---

## 4. Công nghệ

- HTML5
- CSS3 (CSS Grid, Flexbox, Media Queries, CSS Transitions)
- Không sử dụng thư viện ngoài, không có backend

---

## 5. Cách chạy

```
Mở file index.html bằng trình duyệt (Chrome, Firefox, Edge...).
Không cần server, không cần cài đặt thêm gì.
```

Để kiểm tra giao diện mobile: mở Chrome DevTools (F12) → Toggle Device Toolbar (Ctrl+Shift+M) → chọn kích thước 375px.

---

## 6. Cải tiến đã thực hiện

| # | Vấn đề gốc (Shopee) | Thay đổi đã thực hiện |
|---|---|---|
| 1 | % giảm giá không nhất quán trên mọi card | Badge `−XX%` đỏ, absolute positioned góc trên trái ảnh, hiện trên 100% card |
| 2 | Giá gốc không hiển thị rõ trên mobile | Hàng giá 2 dòng: giá sale (lớn, đỏ) + giá gốc gạch ngang + tag inline, không bao giờ bị cắt |
| 3 | Mobile layout đôi khi mất thông tin giá | Grid 2 cột responsive với padding đủ rộng, `price-sale` luôn đủ chỗ |
| 4 | Không có nút mua nhanh trên card danh mục | Thêm nút "Thêm vào giỏ" trực tiếp trên mỗi card |
| 5 | Hover effect không rõ ràng trên desktop | Card nâng lên + bóng đổ khi hover, ảnh zoom nhẹ |

**Điểm tự điều chỉnh (không từ gợi ý AI):**
- Thêm section "BEFORE" hiển thị card cũ cạnh card mới để so sánh trực tiếp
- Thêm badge "MALL" cho sản phẩm Shopee Mall — phản ánh đúng thực tế
- Màu placeholder ảnh khác nhau theo sản phẩm (không dùng màu xám chung chung)

---

## 7. Hỗ trợ từ AI

AI (Claude – claude.ai) hỗ trợ:
- Phân tích 5 khu vực giao diện Shopee và xác định vấn đề chính
- Đề xuất phương án bố cục và cách tổ chức CSS
- Tạo bản nháp HTML/CSS ban đầu

Phần tôi kiểm tra và điều chỉnh:
- Mở trang trên Chrome, kiểm tra ở kích thước 375px, 768px, 1200px
- Phát hiện card cũ thiếu section "BEFORE" → tự thêm vào để bài rõ ràng hơn
- Thêm badge "MALL" và màu ảnh theo sản phẩm
- Xác nhận `margin-top: auto` trên `.price-section` giải quyết đúng vấn đề tên sản phẩm dài ngắn không đều

Chi tiết đầy đủ: xem [AI_USAGE.md](./AI_USAGE.md)

---

## 8. GitHub Pages

Truy cập trang web trực tiếp:  
👉 **https://revilo-lgtm.github.io/ecommerce-ui-improvement/**
