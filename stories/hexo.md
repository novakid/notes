Mới biết đến [Hexo], đọc qua documentation của nó thấy rất hay. Có nhiều thứ còn hơn cả [Jekyll], có lẽ do ra đời sau và định hướng tập trung vào làm blog chăng? Cứ cài đặt vào server ít nữa rảnh rỗi nghiên cứu sau. Về cơ chế hoạt động thì nó giống [Jekyll] đến 80% nên có lẽ cũng không quá khó nhằn.

Cài đặt cũng dễ và nhanh nếu như `nodejs` và `npm` đã chạy ổn.

Có một lưu ý nhỏ là để npm chạy được mà không cần `sudo` thì phải đổi chủ sở hũu của một số thư mục trong hệ thống, thông thường là từ `root` sang `username`. Nếu chạy `npm install -g ...` mà thấy báo lỗi thì cứ xem trong thông báo, thấy đường dẫn tới thư mục nào thì đổi chủ cho thư mục ấy là ok.

**Tip:** lệnh `npm -g bin` sẽ in ra đường dẫn tới thư mục nó dùng để cài đặt. 

Ở server ubuntu của tôi dùng thế này:

    sudo chown -R xabeng:xabeng `npm -g bin`
    //lưu ý là không phải dấu nháy đơn '' nhé. Dùng cái dấu ` dưới phím Esc ý.

Xử lý xong đám lỗi `npm install` thì mọi việc đều suôn sẻ.

---

Cài đặt xong chạy `hexo server` nhưng không xem được từ browser. Headless server lấy đéo đâu ra trình duyệt để browse vào `localhost` cơ chứ!. 

**Tip**: Chạy `hexo server -i 192.168.0.113` (ip của server) thì ổn.


[Hexo]: http://hexo.io/
[Jekyll]: http://jekyllrb.com/