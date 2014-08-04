[Ghost] thực ra là một dịch vụ blog. Người dùng đăng ký và sử dụng dịch vụ của nó để làm blog. Nó thu phí người ta trên dịch vụ này. Nhưng platform của nó thì lại hehe miễn phí (chắc do xây dựng từ opensource nên cũng phải opensource theo). [Ghost] chạy trên nodejs như [Hexo].

Nếu nodejs và npm đã chạy ổn thì cài đặt khá nhanh và dễ. [Xem hướng dẫn](http://docs.ghost.org/). Ưu điểm của thằng này là có cơ chế kiểm soát đăng nhập, dùng cơ sở dữ liệu để lưu thông tin, và đặc biệt là không cần phải dùng thêm app nào khác để viết bài. Mọi thứ chỉ cần dùng trình duyệt.

Giao diện viết bài cũng khá thuận tiện. Một bên là ô soạn thảo, bên cạnh là ô preview. Soạn thảo bằng Markdown rất tiện. Post hình chỉ bằng cách kéo thả. Tóm lại là tiện dụng hơn hẳn so với các blog platform khác.

Chạy trên virtual server (ubuntu) cần sửa ip và port trong `config.js` để trình duyệt từ máy ngoài có thể truy cập. Mặc định là 127.0.0.1 (cổng 2368), headless server không có sẵn trình duyệt để browse vào localhost. Điều này đã được nhắc đến trong bài về hexo.

Tôi chỉ không thích thằng này ở chỗ giao diện mặc định của nó dùng font không hỗ trợ tiếng Việt, soạn thảo và xem trang web vẫn hiển thị được nhưng bị lỗi, nhìn hơi khó chịu.

##Themming Ghost
- http://docs.ghost.org/themes/
- http://webdesign.tutsplus.com/series/building-a-ghost-theme-from-scratch--webdesign-16179
- http://www.allaboutghost.com/the-best-free-ghost-themes-february-2014/

##Font Problem (Admin interface)
Font Open Sans dùng trong giao diện điều khiển của Ghost có thể hiển thị tiếng Việt ở tất cả các kiểu chữ. Tất nhiên bọn làm ra sẽ không include cả tiếng Việt vào đấy trừ khi trong số bọn chúng có thằng là người Việt.

File `ghostblog/core/server/views/default.hbs`, dòng 32, thay

    <link href='http://fonts.googleapis.com/css?family=Open+Sans:400,300,300italic,400italic,600,600italic,700,700italic,800,800italic&subset=latin,vietnamese' rel='stylesheet' type='text/css'>

Bổ sung thêm nếu dùng font monospace của Google font:

    <link href='http://fonts.googleapis.com/css?family=Cousine:400,400italic,700,700italic&subset=latin,vietnamese' rel='stylesheet' type='text/css'>

File `ghostblog/core/server/views/editor.hbs`, dòng 7, thêm `Cousine` vào `font-family`

Làm theo 2 bước trên mới chỉ giải quyết được vấn đề hiển thị tiếng Việt với font thường (Open Sans), font trong editor vẫn là Courier như mặc định. Có thể còn cái css style nào đó tham gia điều khiển font ở chỗ này. Chưa tìm ra.


[Hexo]: http://hexo.io/
[Jekyll]: http://jekyllrb.com/
[Ghost]: https://ghost.org/