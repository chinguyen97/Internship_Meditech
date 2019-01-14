# File System

Hệ điều hành Linux coi tất cả đều là các tệp tin (file) thậm chí cả các thiết bị cũng như ổ đĩa. Nó quản lý tất cả trên một “hệ thống tệp tin” duy nhất, bắt đầu ở gốc là một thư mục “root” và đây là thư mục ở mức cao nhất, đại diện bằng kí hiệu "/".

**1. / – Root**
Đây là thư mục ở mức cao nhất như đã nói ở trên. Tất cả các tệp tin và thư mục đều nằm trong thư mục này.

**2. /sbin – System Binaries**
Chứa đựng các file thực thi dạng binary (nhị phân) của các chương trình cơ bản giúp hệ thống có thể hoạt động. Các lệnh bên trong /sbin thường được sử dụng dùng cho các mục đích là duy trì quản trị hệ thống. Các lệnh này yêu cầu phải có quyền root.
Một số lệnh trong đây ví dụ: lilo, fdisk, init, ifconfig v.v.. Để liệt kê, bạn dùng lệnh “ls /sbin/”.
Còn một thư mục mà nó chứa các tệp tin thi hành cho hệ thống là /usr/sbin/. Nhưng các chương trình ở đây không được sử dụng để bảo trì hệ thống.

**3. /bin – User Binaries**
Đối lập với /sbin/ thư mục này chứa rất nhiều ứng dụng khác nhau dùng được cả cho việc bảo trì hệ thống của root, cũng như các lệnh cho người dùng thông thường. Thư mục này thông thường chứa hệ vỏ (Shell), cũng như rất nhiều lệnh hữu dụng như cp (sao chép), mv (di chuyển), cat, ls. Cũng giống như sbin, thư mục /usr/bin cũng chứa các tệp tin có chức năng tương tự như /bin.

**4. /boot – Boot Loader Files**
Chứa các tệp tin khởi động và cả nhân kernel là vmlinuz. Trong các bản phân phối gần đây, nó cũng chứa cả dữ liệu cho grub. Phần mềm khởi động Grub (viết tắt của GRand Unified Boot loader) ngày nay được sử dụng khá phổ biến.

**5. /dev – Device Files**
Đây là một thư mục thú vị nhất, nó thể hiện một cách rõ ràng là hệ điều hành Linux coi mọi thứ đều là các tệp tin và thư mục.
Trong thư mục này bạn có thể thấy rất nhiều tệp tin đại diện cho các thiết bị như ổ đĩa SATA, cổng COM v.v.. Liệt kê chúng ra bằng lệnh “ls /dev/”. 
Ví dụ:
/dev/sda : đây là ổ đĩa SATA thứ nhất
/dev/cdrom : ổ CD
/dev/ttyS0 : cổng COM1

**6. /etc – Configuration Files**
Chứa file cấu hình cho các chương trình hoạt động. Chúng thường là các tệp tin dạng text thường. Chức năng của nó gần giống với “Control Panel” trong Windows. Ví dụ:
/etc/resolv.conf (cấu hình dns-server )
/etc/network dùng để quản lý dịch vụ network
Ở /etc có một thư mục quan trọng đó là /etc/rc.d. Nơi đây thường chứa các scripts dùng để start, stop, kiểm tra status cho các chương trình.

**7. /home – Home Directories**
Thư mục Home. Thư mục này chứa thông tin, dữ liệu , cấu hình riêng cho từng user. 

**8. /lib – System Libraries**
Chứa các file library hỗ trợ cho các file thực binary. Tên của các file library thường là ld* or lib*.so.* . Ví dụ như libc.so.* (Thư viện C).

**9. /lost+found**
Vì một lý do bất ngờ nào đó như lỗi phần mềm, mất điện v..v, hệ thống có thể đổ vỡ. Khi khởi động lại, hệ thống sẽ kiểm tra lại hệ thống filesystem bằng lệnh fchk và cố gắng phục hồi lại các lỗi mà nó tìm thấy. Kết quả của việc này sẽ được lưu giữ trong thư mục /lost+found.

**10. /mnt – Mount Directory**
Chứa các thư mục dùng để system admin thực hiện quá trình mount. Như đã nói, hệ điều hành Linux coi tất cả là các file và lưu giữ trên một cây chung. Đây chính nơi tạo ra các thư mục để ‘gắn’ các phân vùng ổ đĩa cứng cũng như các thiết bị khác vào. Sau khi được mount vào đây, các thiết bị hay ổ cứng được truy cập từ đây như là một thư mục. Trong một số hệ điều hành, các ổ đĩa chưa được gắn sẵn vào hệ thống bởi fstab sẽ được gắn ở đây. Về cách gắn và tháo, có lẽ cần một bài viết riêng.

**11. /opt – Optional add-on Applications**
Chứa các phần mềm và phần mở rộng không nằm trong phần cài đặt mặc định, thường là của hãng thứ ba.

**12. /tmp – Temporary Files**
Thư mục này chứa các file được tạo với mục đích dùng tạm thời bởi hệ thống cũng như user. Các file bên dưới thư mục này được xóa đi khi hệ thống reboot hay shutdown.

**13. /usr – User Programs**
Chứa các file binary, library, tài liệu, source-code cho các chương trình

**14. /media – Removable Media Devices**
Chứa thư mục dùng để mount cho các thiết bị removable. Ví dụ như CDROM, Floppy v.v..

**15. /var – Variable Files**
Chứa đựng các file có sự thay đổi trong quá trình hoạt động của hệ điều hành cũng như các ứng dụng. Ví dụ:
+ Nhật ký của hệ thống /var/log
+ database file /var/lib
+ email /var/mail
+ Các hàng đợi in ấn: /var/spool
+ lock file: /var/lock
+ Các file tạm thời cần cho quá trình reboot: /var/tmp
+ Dữ liệu cho trang web: /var/www
Để biết được thư mục đang nằm trên phân vùng nào, sử dụng lệnh df với đối số là dấu chấm (.) biểu diễn thư mục hiện hành.

    $ df -h .

Theo quy tắc chung, mọi thư mục đều nằm dưới thư mục root thì đều nằm trên phân vùng root, trừ phi nó có phân vùng riêng ở một trong số các phân vùng được liệt kê trong lệnh df (hay df -h mà không có tùy chọn khác).