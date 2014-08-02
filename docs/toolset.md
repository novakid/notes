##Lựa chọn công cụ:
Mục tiêu triển khai website của doanh nghiệp, nội dung là giới thiệu về công ty và trình bày hình ảnh sản phẩm thực tế. 

Cơ sở dữ liệu không nhiều, không cần cập nhật thường xuyên. Các yếu tố tương tác trực tiếp trên website không có. Do đó không cần sử dụng phần mềm database. Một số bảng dữ liệu đơn giản có thể dùng Google Spreadsheet để tất cả mọi người có thể dùng được.

Cần quy trình xây dựng đơn giản, dễ cập nhật. Không cần phần mềm chuyên dụng. Sử dụng Opensource để tránh các vấn đề bản quyền.

Linh hoạt trong việc sử dụng các thư viện Javascript và CSS có sẵn. Không dùng Flash.

**Responsive layout** là bắt buộc trong thiết kế. Website cần chạy tốt trên các thiết bị di động với layout hợp lý.

##Phương án lựa chọn:
Đã dùng thử và cân nhắc giữa khá nhiều phương án (kể cả các CMS lớn như Drupal, Joomla, Wordpress...). Cuối cùng chọn sử dụng bộ công cụ Jekyll + Github để xây dựng và chạy thử. Các CMS quá cồng kềnh đối với các yêu cầu đã nêu. 

Mặt khác với yêu cầu hiển thị dữ liệu đặc thù của c.ty (tích hợp với google maps), các CMS nêu trên cần có plugin để thực hiện. Quá phức tạp cho việc code và bảo trì.

##Tại sao không phải là các CMS khác?
1. Không nắm rõ cách sử dụng -> khó triển khai, khó bảo trì & cập nhật.
2. Github tích hợp Jekyll --> dễ xem, dễ sửa, dễ quản lý code.
3. Static web, sử dụng opensource --> không lo vấn đề bảo mật & bản quyền.

##Quy trình làm việc như thế nào?
Việc lựa chọn phương án thiết kế phù hợp mất khá nhiều thời gian. Quá trình thiết kế luôn phải cân nhắc để xác định kích cỡ các thành phần hiển thị sao cho website không bị vỡ layout khi hiển thị trên nhiều loại màn hình khác nhau.

Sau khi phác thảo phần cấu trúc, việc thiết kế các thành phần đồ hoạ được làm chủ yếu bằng Photoshop và Illustrator. Dựa trên layout này, coder thực hiện chuyển thành html & css để dựng website.

Vấn đề cơ sở dữ liệu sản phẩm cũng được giải quyết trong lúc này. Điều kiện cty không thể phân riêng một người chuyên trách, do đó cơ sở dữ liệu cần đơn giản và dễ cập nhật. Yêu cầu là một người có kiến thức thông thường về phần mềm văn phòng có thể cập nhật được mà không cần học thêm kiến thức mới.

Lựa chọn cuối cùng là sử dụng Google Spreadsheet làm backend database. Bất kỳ ai dùng được excel cũng có thể xem và sửa bảng dữ liệu này. 