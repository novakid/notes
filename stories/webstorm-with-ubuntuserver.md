<strong style="color:red;">update:</strong> Dùng hay nhưng nặng nề quá. Công việc thường này cứ ST và N+ dùng vẫn là hay nhất.

##dùng làm gì?
- Webstorm (WS) có cả bộ dùng cho PC, MAC & Linux. Tính năng như nhau, nhưng công cụ tích hợp trong App có vẻ hợp với Linux & Mac hơn (nodejs, bower, grunt, git...).
- luộc lại từ torrentz.eu như vẫn... :)
- Cài đặt bình thường. Key của bản trên PC có thể dùng cho bản trên Mac.

##webstorm
- create new project from existing files
- chọn: web server is on remote host, files are accessible via FTP/SFTP/FTPS.
- khai báo các thông số như tên, địa chỉ thư mục web v..v.. 
- khai báo các thông số server (sftp, port 22, username, password...)
- lưu ý khai báo đường dẫn tới thư mục web trong server
- chọn don't check http connect to server
- finish

##test
- tạo file index.html trong thư mục web (trên pc tất nhiên), nội dung tùy thích
- webstorm menu, tools > deployment > browse remote host (cho dễ nhìn)
- webstorm menu, tools > deployment > upload to <server_name>(ubuntu)
- file index.html vừa tạo sẽ được upload lên server
- ubuntu server, vào thư mục web (`cd /path/to/www`)
- tạo http server: `python -m SimpleHTTPServer 8000`
- mở trình duyệt trên pc, nhập địa chỉ server & cổng đã chỉ định (`http://192.168.0.113:8000`). Nếu thấy nội dung file index.html đã tạo thì ok.
- Nếu không thấy? Tự tìm cách mà sửa tôi cũng đéo biết hehe...