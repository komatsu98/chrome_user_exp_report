# chrome_user_exp_report

# Báo cáo trải nghiệm người dùng Chrome

Báo cáo trải nghiệm người dùng Chrome cung cấp chỉ số trải nghiệm người dùng về cách người dùng Chrome trải nghiệm các điểm đến phổ biến trên web trong thực tế.

### Phương pháp luận
Báo cáo trải nghiệm người dùng Chrome  được hỗ trợ bởi các đo lường người dùng thực tế dựa trên các chỉ số trải nghiệm người dùng qua các trang web cộng đồng,  được tổng hợp từ những người dùng được lựa chọn để đồng bộ lịch sự duyệt web, chưa  cài đặt cụm mật khẩu Sync, và có sử dụng báo cáo thống kê. Kết quả dữ liệu thông qua:
1. PageSpeed Insights, cung cấp các chỉ số trải nghiệm người dùng mức -URL cho các URL phổ biến với các con crawler web của Google.
2. Dự án Public Google BigQuery  thu thập các số liệụ trải nghiệm người dùng từ mọi nguồn, với tất cả những nguồn được biết bởi các con crawler web của Google, và được chia thành nhiều khía cạnh được liệt kê bên dưới.

### Các chỉ số
Các chỉ số cung cấp bởi Báp cáo trải nghiệm người dùng Chrome được lưu trữ trên Google BigQuery Metrics được hỗ trợ bởi các API chuẩn nền tảng web đối với các trình duyệt hiện đại và được tổng hợp đến các  nguồn. Chủ các trạng muốn các phân tích và đánh giá chi tiết hơn về hiệu năng trang web của họ (các thông số mức URL) và có thể sử dụng cùng API để thu thập các dữ liệu đo lường người dùng thực tế (RUM) 1 cách chi tiết trên các trang nguồn của họ.

Về hướng dẫn cách theo dõi và tối ưu các chỉ số, và cách tốt nhất để hiểu những dữ liệu đo lường trên người dùng thật, xem tài liệu về hiệu suất ở phần giữa.

### First Paint
Được định nghĩa bằng Paint Timing API và khả dụng trên Chrome M60+:

“First Paint báo cáo thời gian khi trình duyệt render lần đầu sau khi chuyển trang. Ở đây không bao gồm màn nền mặc định, nhưng bao gồm nhưng màn nền không mặc định. Đây là thời khắc quan trọng đầu tiên những dev phải quan tâm về vấn đề tải trang - khi trình duyệt bắt đầu render trang web. 

###  First Contentful Paint
Được định nghĩa bằng Paint Timing API và khả dụng trên Chrome M60+:

“First Contentful Paint báo cáo thời gian trình duyệt lần đầu render bất kỳ chữ, ảnh (bao gồm ảnh nền), non-white canvas hay SVG lần đầu. Ở đây bao gồm văn bản với webfonts đang chờ xử lý. Đây là lần đầu người dùng có thể đọc nội dung trang"

### DOMContentLoaded
Định nghĩa bởi HTML cụ thể:

“ DOMContentLoaded báo cáo thời gian tài liệu HTML được hoàn toàn tải lên và xử lý, mà không phải đợi các stylesheets, ảnh, và subframe để hoàn thành việc tải" - MDN

### onload
Định nghĩa bởi  HTML cụ thể:

“ Sự kiện được bắn ra khi trang web và các nguồn phụ thuộc được tải xong" -MDN

###  Các khía cạnh
Hiệu năng của nội dung web có thể ảnh hưởng rất nhiều bởi loại thiết bị, thuộc tính của mạng, và các biến khác. Để giúp việc chia nhỏ và hiểu hơn về trải nghiệm người dùng qua các phần quan trọng, Báo cáo trải nghiệm người dùng Chrome cung cấp những khía cạnh sau


##### Hiệu quả loại kết nối
Định nghĩa bởi Network Information API và khả dụng trên Chrome M62+:

“ Cho thấy hiệu quả loại kết nối (“slow-2g”, “2g”, “3g”, “4g”, hay “offline”) bằng việc xác định các giá trị round-trip và bandwidth dựa trên quan sát đo lường trên người dùng thực.”

##### Loại thiết bị
Phân loại các thiết bị (“phone”, “tablet”, hay “desktop”), kết nối thông qua User-Agent.

##### Quốc gia
Vị trí địa lý của người  dùng tại country-level,  suy ra từ địa chỉ IP. Các nước được định danh  bằng  các code ISO 3166-1 alpha-2 tương ứng.

##### Định dạng dữ liệu
Báo cáo được cung cấp bởi Google BigQuery là 1 bộ các tập dữ liệu chứa các chỉ số trải nghiệm người dùng tổng hợp đến các quyết định nguồn. Mỗi tập dữ liệu đại diện cho 1 nước, country_rs đại diện dữ liệu trải nghiệm người dùng với các người dùng ở Serbia(rs là mã ISO 31611-1 của Serbia) Thêm vào đó, có 1 tập dữ liệu  tổng hợp toàn cầu(tất cả)  thể hiện trải nghiệm toàn cầu. Mỗi dòng của tập dữ liệu bao gồm 1 bản ghi liên kết của trải nghiệm người dùng  cho 1 nguồn cụ thể, phân tách bằng khóa của các  khía cạnh.

Ví dụ, bảng bên trên hiển thị 1 mẫu bản ghi từ báo cáo trải nghiệm người dùng Chrome, chỉ ra rằng 12.3% lượt tải trạng có 1 độ đo "first paint time" nằm trong khoảng 1000-1200 milli giây khi tải "http://example.com" trên thiết bị điện thoại qua kết nối dạng "4g". Để đạt các  các giá trị tổng hợp trải nghiệm người dùng  lần đầu dưới 1200 mili giây, bạn có thể tăng lên các bản ghi mà có biểu đồ giá trị "end" nhỏ hơn hoặc bằng 1200.

### Bắt đầu
Báo cáo trải nghiệm người dùng Chrome được cung cấp như 1 dự án công khai trên Google BigQuery. Để truy cập vào dự án, bạn sẽ cần 1 tài khoản Google và 1 dự án google Cloud: theo các bước hướng dẫn  và quá trình hướng dẫn cách để truy vấn dự án.

### Các mẹo khi nghiên cứu và cách thực hành tốt nhất.
##### Xem xét sự khác biệt truy cập giữa các nguồn trang
Các chỉ số cung cấp bởi Báo cáo trải nghiệm người dùng Chrome được cung cấp thông qua các dữ liệu đo lường trên người dùng thực tế.  Dữ liệu sẽ phản ảnh cách người dùng thực tế trải nghiệm các nguồn trang họ đã truy cập, và không giống với việc kiểm thử tổng hợp hay nội bộ khi quá trình kiểm thử được thực hiện dưới các điều kiện cố định  và mô phỏng, bắt được tất cả các khía cạnh bên ngoài ảnh hưởng đến trải nghiệm người dùng cuối cùng.
Ví dụ, sự khác nhau về lượng người dùng truy cập 1 nguồn trang  cụ thể có thể góp phần tạo ra sự khác biệt đến trải nghiệm người dùng. Nếu trang web thường xuyên có nhiều gười dùng với những thiết bị hiện đại hay truy cập qua 1 mạng tốc độ cao, kết quả có thể xuất hiện "nhanh" ngay cả khi trang web không được tối ưu tốt. Ngược lại, 1 trang được tối ưu tốt sẽ thu hút lượng lớn truy cập người dùng, hay 1 lượng trong đó phần lớn  là những người dùng  trên các thiết bị hoặc mạng mẽo chậm, có thể lại xuất hiện "chậm".

Khi biểu hiện các so sánh trực tiếp giữa các trang nguồn, điều quan trọng là phải thống kê và kiểm soát lưu lượng người dùng khác nhau: phân chia từ những khía cạnh được cung cấp, ví dụ như là loại thiết bị và loại kết nối, cùng với đó cấn nhắc những yếu tốt bên ngoài như là lượng kết nối, các nước truy cập vào trang nguồn, vân vân.

### Xem xét sự khác biệt mật độ truy cập giữa các nguồn trang
Báo cáo trải nghiệm người dùng Chrome tổng hợp dữ liệu cho mỗi nguồn, với giá trị "density" qua các biểu đồ chỉ số- khía cạnh tổng bằng 1. Điều này cung cấp cái nhìn khách quan đến ảnh hưởng của trải nghiệm qua các khía cạnh quan trọng đối với 1 nguồn cụ thể


Tuy nhiên, khi tổng hợp dữ liệu từ nhiều nguồn, ví dụ dọc theo 1 ngành công nghiệp hay 1 vùng địa lý, hãy cẩn thận với các loại tổng kết được vẽ ra: thêm  vào mật độ với cùng chỉ số cho các nguồn trang  không tính toán lưu lượng tương đối khác nhau qua các nguồn.

Ví dụ, trang A có thể có 10 triệu truy cập, trong khi trang B có 10 ngàn. Trong cả 2 trường hợp, biểu đồ mật độ với mỗi trang có tổng là 1, và tập dữ liệu không cung cấp bất kỳ số liệu tuyệt đối nào về kích thước lưu lượng của từng nguồn riêng biệt, hay kích thước lưu lượng tương đối khác nhau giữa các nguồn. Dĩ nhiên, nếu bạn thêm mật độ từ A và B, và giá trị trung bình của các kết quả, bạn sẽ coi chúng tương đương ngay cả khi A có lưu lượng lớn gấp 1000 lần.

### Xem xét sự khác biệt về lưu lượng của Chrome
Báo cáo trải nghiệm người dùng được cung cấp vởi các phép đo dựa trên người dùng thực tế được tổng hợp từ người dùng được lựa chọn để đồng bộ lịch sử duyệt web của họ,chưa cài đặt 1 cụm bảo mật Đồng bộ, và đã sử dụng báo cáo thống kê. Lưu lượng có thể không đại diện cho phần lớn người dùng trên những nguồn cụ thể và nhiều nguồn có thể có những lưu lượng khác những cái khác. Vì thế, dữ liệu này không dùng cho những người dùng với trình duyệt khác nhau và sự khác biệt ở thành phần phụ của trình duyệt trên những vùng địa lý khác nhau.

Vì thế, hãy cẩn thận với các loại kết luận khác nhau được vẽ ra khi nhìn vào phần giao nhau giữa các nguồn, và khi so sánh nhưng nguồn riêng biệt: trnah sự dụng các so sánh tuyệt đối và xem xét các đường khía cạnh khác trong phần tren.
