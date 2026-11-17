# Sales Management Demo

Giao diện quản lý bán hàng viết bằng HTML, CSS và JavaScript thuần, chạy trực tiếp trong trình duyệt.

![Màn hình tổng quan](docs/dashboard.png)

## Tổng quan

Sales Management Demo mô phỏng các thao tác thường gặp trong một màn hình quản trị cửa hàng: theo dõi số liệu tổng quan, quản lý danh mục sản phẩm, cập nhật đơn hàng và tổ chức nội dung hiển thị. Dự án dùng HTML, CSS và JavaScript thuần, phù hợp để tìm hiểu cách xây dựng giao diện quản trị và xử lý trạng thái ngay trên trình duyệt.

Các màn hình được đặt trong cùng một trang và chuyển đổi bằng thanh điều hướng. Biểu mẫu và bảng dữ liệu phối hợp với JavaScript để cập nhật giao diện sau mỗi thao tác. Bộ dữ liệu mẫu giúp người đọc có thể mở ứng dụng và khám phá luồng hoạt động ngay sau khi clone.

## Chức năng

- Tổng quan số sản phẩm, đơn hàng, thương hiệu và doanh thu từ dữ liệu trong trang.
- Thêm, sửa và xóa sản phẩm.
- Hiển thị đơn hàng, thay đổi trạng thái đơn hàng.
- Quản lý thương hiệu và hình logo.
- Quản lý slide, hình ảnh và đường dẫn.

## Công nghệ và cấu trúc

| Thành phần | Vai trò |
|---|---|
| HTML | Các màn hình, biểu mẫu và bảng dữ liệu |
| CSS | Bố cục, thanh điều hướng và hiển thị nội dung |
| JavaScript | Trạng thái, xử lý biểu mẫu và cập nhật DOM |
| `index.html` | Điểm vào của toàn bộ ứng dụng |
| `docs/dashboard.png` | Ảnh giao diện tổng quan |

Ứng dụng không yêu cầu bước biên dịch hoặc cài package JavaScript. Có thể dùng trình duyệt để chạy và công cụ dành cho nhà phát triển để theo dõi sự kiện, trạng thái và thay đổi giao diện.

## Chạy demo

```bash
git clone https://github.com/daotrunghieuk4/Sales-Management-Demo.git
cd Sales-Management-Demo
python -m http.server 8080
```

Mở `http://localhost:8080`. Cũng có thể mở trực tiếp `index.html` trong trình duyệt. Toàn bộ giao diện, style và logic nằm trong tệp này, không cần cài thư viện JavaScript.

## Hướng dẫn sử dụng

### Tổng quan

Màn hình đầu tiên hiển thị số sản phẩm, số đơn hàng, doanh thu, thương hiệu và slide từ dữ liệu trong phiên. Dùng thanh điều hướng để mở từng nhóm quản lý.

### Sản phẩm

Nhập tên, mô tả, giá và số lượng trong biểu mẫu để thêm sản phẩm. Danh sách bên dưới cung cấp các thao tác sửa và xóa. Khi chỉnh sửa, thông tin sản phẩm được đưa trở lại biểu mẫu để cập nhật.

### Đơn hàng

Xem danh sách đơn hàng và sử dụng điều khiển trạng thái tương ứng. Các thông tin tổng quan được tính từ dữ liệu đơn hàng của trang.

### Thương hiệu và slide

Thêm thông tin thương hiệu cùng logo hoặc chuẩn bị slide với tiêu đề, hình ảnh và liên kết. Hình được chọn từ máy người dùng để hiển thị trong phiên làm việc. Các thao tác sửa/xóa giúp thử cách tổ chức nội dung quản trị.

## Dữ liệu và vòng đời phiên

Dữ liệu mẫu được khởi tạo khi mở trang. Sản phẩm, đơn hàng, thương hiệu và slide được quản lý trong bộ nhớ JavaScript, vì vậy tải lại trang sẽ khởi tạo lại dữ liệu mẫu. Cách hoạt động này tạo một môi trường tương tác độc lập để thử các thao tác quản trị.

Demo hoạt động hoàn toàn ở phía trình duyệt. Khi tích hợp với một hệ thống cửa hàng, lớp dữ liệu có thể được nối với API và cơ sở dữ liệu để lưu thay đổi giữa các phiên; phần giao diện và biểu mẫu là điểm xuất phát cho bước tích hợp này.

## Luồng xử lý

```text
Thao tác trên biểu mẫu
        ↓
Xử lý sự kiện JavaScript
        ↓
Cập nhật dữ liệu trong phiên
        ↓
Hiển thị lại bảng và số liệu tổng quan
```

Các hàm trong `index.html` được nhóm theo sản phẩm, đơn hàng, thương hiệu và slide. Khi tìm hiểu mã nguồn, bắt đầu từ `showSection` để theo dõi điều hướng, sau đó xem các hàm xử lý biểu mẫu và cập nhật bảng của từng nhóm.

## Kiểm tra thủ công

1. Mở trang và ghi nhận số sản phẩm trên màn hình tổng quan.
2. Thêm một sản phẩm, kiểm tra dòng mới trong bảng và số lượng tổng quan.
3. Sửa giá hoặc số lượng, xác nhận dữ liệu mới hiển thị đúng.
4. Xóa sản phẩm vừa tạo và kiểm tra danh sách được cập nhật.
5. Thử thay đổi trạng thái đơn hàng và chọn ảnh cho thương hiệu/slide.
6. Tải lại trang để bắt đầu lại với bộ dữ liệu mẫu.

## Hướng mở rộng

Các hướng tích hợp phù hợp gồm lưu trữ dữ liệu qua API, phân quyền theo tài khoản và bổ sung tìm kiếm/lọc danh sách. Khi kết nối backend, giữ thống nhất quy tắc kiểm tra đầu vào giữa biểu mẫu và API, đồng thời bổ sung phản hồi cho trạng thái đang tải, thành công và lỗi.
