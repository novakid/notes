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

Lục lọi các file trong `core` để thay thế `Iconsolata` (ghost dùng font này cho hiển thị code) bằng `Cousine`.

Thực ra làm đến bước này mới chỉ giải quyết được phần hiển thị tiếng Việt. Quậy nữa cũng được nhưng về sau nâng cấp lại phải làm lại hơi rắc rối. Dùng tạm vậy!

##interesting link:
- http://mhurwi.com/show-text-with-ghost-and-angular/

##quậy tiếp slg...
- vấn đề font chữ đã nói ở trên
- cấu trúc của Ghost có hai phần đáng chú ý ở trang `default.hbs`, là `{{ghost_head}}` trong header và {{ghost_foot}} ở cuối trang (trước khi đóng `</body>`). Mặc định là Ghost sẽ lấy đoạn code được viết trong `core/server/helpers/index.hbs` để chèn vào các vị trí này. 
    - `{{ghost_head}}` lấy đoạn từ dòng 636 đến 460.
    - `{{ghost_foot}}` lấy từ 461 đến 475.
    - Nội dung của nó là những gì mới chỉ hiểu sơ sơ. Không thích cách này lắm vì thằng nào muốn mod theme sâu hơn một tí sẽ phải *hard coding* trong này. Nếu Ghost có API hay plugin gì gì đó để làm việc này thì hay hơn. Hy vọng nó sẽ sớm ra trong những phiên bản tiếp theo.
    - Lưu ý là `{{ghost_foot}}` sẽ chèn jquery.js vào đấy. Mà cái `jquery` này lại nằm trong `core/built/public` Phiên bản nó đang dùng là 1.11.0. <span style="color:red;">đã thay bằng 1.11.1</span>
- đang định dùng [backstretch](http://srobbin.com/jquery-plugins/backstretch/) để làm theme vì dễ dùng. Làm slideshow chạy dưới nền cũng hay. Khi dùng chỉ cần lấy cái `backstretch.js` về thôi. Jquery đã include sẵn rồi. ~~Một cái khác cũng rất hay là [anystretch](https://github.com/danmillar/jquery-anystretch) hình như cũng folk từ backstretch về modify thì phải. Có vẻ hay hơn nhưng chưa thử.~~ <span style="color:red;">Sorry, anystretch chỉ dùng được với 1 hình ảnh, không làm slideshow được.</span>
- thư viện javascript để làm gallery hình ảnh: [baguettebox](https://github.com/feimosi/baguetteBox.js). Thấy cũng khá đơn giản. Sẽ dùng thử vào một lúc nào đó.

##ghost on openshift

Đăng nhập vào cài qua web không được, đành dùng `rhc`. Server cần có sẵn `ruby` và `git`. Lệnh cài đặt:

    sudo gem install rhc

Đợi cài xong, chạy

    rhc setup

Ngoài việc phải nhập username & password, chỉ cần trả lời yes với tất cả các yêu cầu của nó. Lưu ý một chút chỗ này là server cũng cần có sẵn Openssh và đã genrate các key cần thiết.

Cài đặt ghost, lưu ý tôi lấy appname = ghost, anh chị có thể dùng tên khác thoải mái.

    rhc app create ghost nodejs-0.10 --env NODE_ENV=production --from-code https://github.com/openshift-quickstart/openshift-ghost-quickstart.git

Đợi nó cài đặt xong cũng khá lâu. Có thể quá trình cài đặt sẽ tự clone một bản về server. Nếu báo lỗi hoặc bị ngắt giữa chừng (như tôi gặp phải ngày hôm qua) thì chạy tại server: `rhc git-clone ghost` (ghost là appname tôi đã đặt, anh chị có thể dùng tên khác).

Xong phần thiết lập. Với server khác thì sao? Chỉ cần cài `rhc` (như trên). Sau đó `rhc git-clone ghost`.

Làm việc với nó như một git repository bình thường.

Tôi đã thử clone một bản về server, rồi loay hoay thử các kiểu mất nguyên một buổi mà không thể chạy được. Đành để đấy coi như một bản sao lưu. Làm theme cho thằng này cũng đơn giản, nó dùng [handlebar](), cấu trúc cũng khá giống với Liquid của Jekyll.

Làm xong dùng wincsp copy vào thư mục đã clone về. Dùng git push sau khi đã add & commit như thường. Máy ảo openshift sau khi nhận được file sẽ tắt và khởi động lại. Toàn bộ quá trình mất khoảng 3 đến 5 phút (hơi lâu quá đấy!)

Dùng online khá nhanh. Tôi làm ra để viết cho mình nên vẫn cứ dùng hình nền cỡ lớn (khá nặng). Lúc đầu load cũng phải mất đến hơn chục giây mới hiển thị được toàn bộ.

---

Đã làm xong theme và deploy (git push). Có gì lăn tăn về giao diện sẽ gom lại để làm một thể. Làm với Openshift không thể cứ sửa vài chữ rồi lại push lên vô tội vạ. Lâu bỏ mẹ.

Dùng ghost tiện ở chỗ không cần app nào khác tham gia vào quá trình viết bài. Bản thân nó cũng đã có trình soạn thảo hỗ trợ markdown khá tốt.

Điểm trừ của thằng này là nó không hỗ trợ .svg (hơi lạ)

[Hexo]: http://hexo.io/
[Jekyll]: http://jekyllrb.com/
[Ghost]: https://ghost.org/
