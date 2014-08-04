[Ghost] thực ra là một dịch vụ blog. Người dùng đăng ký và sử dụng dịch vụ của nó để làm blog. Nó thu phí người ta trên dịch vụ này. Nhưng platform của nó thì lại hehe miễn phí (chắc do xây dựng từ opensource nên cũng phải opensource theo). [Ghost] chạy trên nodejs như [Hexo].

Nếu nodejs và npm đã chạy ổn thì cài đặt khá nhanh và dễ. [Xem hướng dẫn](http://docs.ghost.org/). Ưu điểm của thằng này là có cơ chế kiểm soát đăng nhập, dùng cơ sở dữ liệu để lưu thông tin, và đặc biệt là không cần phải dùng thêm app nào khác để viết bài. Mọi thứ chỉ cần dùng trình duyệt.

Giao diện viết bài cũng khá thuận tiện. Một bên là ô soạn thảo, bên cạnh là ô preview. Soạn thảo bằng Markdown rất tiện. Post hình chỉ bằng cách kéo thả. Tóm lại là tiện dụng hơn hẳn so với các blog platform khác.

Chạy trên virtual server (ubuntu) cần sửa ip và port trong `config.js` để trình duyệt từ máy ngoài có thể truy cập. Mặc định là 127.0.0.1 (cổng 2368), headless server không có sẵn trình duyệt để browse vào localhost. Điều này đã được nhắc đến trong bài về hexo.

Tôi chỉ không thích thằng này ở chỗ giao diện mặc định của nó dùng font không hỗ trợ tiếng Việt, soạn thảo và xem trang web vẫn hiển thị được nhưng bị lỗi, nhìn hơi khó chịu.



[Hexo]: http://hexo.io/
[Jekyll]: http://jekyllrb.com/
[Ghost]: https://ghost.org/