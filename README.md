# chrome_user_exp_report

# Báo cáo trải nghiệm người dùng Chrome

Báo cáo trải nghiệm người dùng Chrome cung cấp chỉ số trải nghiệm người dùng cho cách người dùng Chrome trong thế giới thực trải nghiệm các điểm đến phổ biến trên web.

### Phương pháp luận
Báo cáo trải nghiệm người dùng Chrome  được hỗ trợ bởi các đo lường người dùng thực tế dựa trên các chỉ số trải nghiệm người dùng qua các trang web cộng đồng,  được tổng hợp từ những người dùng được lựa chọn để đồng bộ lịch sự duyệt web, chưa  cài đặt cụm mật khẩu Sync, và có sử dụng báo cáo thống kê. Kết quả dữ liệu thông qua:
1. PageSpeed Insights, cung cấp các chỉ số trải nghiệm người dùng mức -URL cho các URL phổ biến với các con crawler web của Google.
2. Dự án Public Google BigQuery  thu thập các số liệụ trải nghiệm người dùng từ mọi nguồn, với tất cả những nguồn được biết bởi các con crawler web của Google, và được chia thành nhiều khía cạnh được liệt kê bên dưới.

### Các chỉ số
Các chỉ số cun cấp bởi Báp cáo trải nghiệm người dùng Chrome  được lưu trữ trên Google BigQuery Metrics được hỗ trợ bởi các API chuẩn nền tảng web  đói với các trình duyệt hiện đại và được tổng hợp  đến các  nguồn. Chủ các trạng muốn các phân tích và đánh giá chi tiết hơn về hiệu năng trang web của họ ( các thông số mức URL) và có thể sử dụng cùng API để thu thập các dữ liệu đo lường người dùng thực tế (RUM) 1 cách chi tiết trên các trang nguồn của họ.

Ví dụ, bảng bên trên hiển thị 1 mẫu bản ghi từ báo cáo trải nghiệm người dùng Chrome, chỉ ra rằng 12.3% lượt tải trạng có 1 độ đo "first paint time" nằm trong khoảng 1000-1200 milli giây khi tải "http://example.com" trên thiết bị điện thoại qua kết nối dạng "4g". Để đạt các  các giá trị tổng hợp trải nghiệm người dùng  lần đầu dưới 1200 mili giây, bạn có thể tăng lên các bản ghi mà có biểu đồ giá trị "end" nhỏ hơn hoặc bằng 1200.

### Bắt đầu
Báo cáo trải nghiệm người dùng Chrome được cung cấp như 1 dự án công khai trên Google BigQuery. Để truy cập vào dự án, bạn sẽ cần 1 tài khoản Google và 1 dự án google Cloud: theo các bước hướng dẫn  và quá trình hướng dẫn cách để truy vấn dự án.

### Các mẹo khi nghiên cứu và cách thực hành tốt nhất.
##### Giả sử có sự khác biệt  truy cập giữa các nguồn trang
Các chỉ số cung cấp bởi Báo cáo trải nghiệm người dùng Chrome được cung cấp thông qua các dữ liệu đo lường trên người dùng thực tế.  Dữ liệu sẽ phản ảnh cách người dùng thực tế trải nghiệm các nguồn trang họ đã truy cập, và không giống với việc kiểm thử tổng hợp hay nội bộ khi quá trình kiểm thử được thực hiện dưới các điều kiện cố định  và mô phỏng, bắt được tất cả các khía cạnh bên ngoài ảnh hưởng đến trải nghiệm người dùng cuối cùng.
Ví dụ, sự khác nhau về lượng người dùng truy cập 1 nguồn trang  cụ thể có thể góp phần tạo ra sự khác biệt đến trải nghiệm người dùng. Nếu trang web thường xuyên có nhiều gười dùng với những thiết bị hiện đại hay truy cập qua 1 mạng tốc độ cao, kết quả có thể xuất hiện "nhanh" ngay cả khi trang web không được tối ưu tốt. Ngược lại, 1 trang được tối ưu tốt sẽ thu hút lượng lớn truy cập người dùng, hay 1 lượng trong đó phần lớn  là những người dùng  trên các thiết bị hoặc mạng mẽo chậm, có thể lại xuất hiện "chậm".

Khi biểu hiện các so sánh trực tiếp giữa các trang nguồn, điều quan trọng là phải thống kê và kiểm soát lưu lượng người dùng khác nhau: phân chia từ những khía cạnh được cung cấp,

When performing head-to-head comparisons across origins, it is important to account and control for the population differences: segment by provided dimensions, such as device type and connection type, and consider external factors such as size of the population, countries from which the origin is accessed, and so on.















a
