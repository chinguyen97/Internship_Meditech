# Linux Basic Commandline 
**1. man**
- Tìm kiếm thông tin command. vd: `man cd` , `man pwd`
**2. pwd**
- Hiển thị đường dẫn tuyệt đối của thư mục hiện tại đang đứng.
**3. ls**
- Hiển thị danh sách các thư mục con hoặc file của thư mục hiện tại.
- Có thể kèm một số tham số:
		-a	 Liệt kê tất cả file và thư mục (ẩn).
		-l	 Liệt kê theo dạng bảng.
		-t	 Liệt kê kèm theo giá trị thời gian.
**4. cd**
- Thay đổi đường dẫn thư mục hiện tại. vd: `cd /etc/sysconfig/network-scripts/`  `cd ..`
**5. mkdir, touch**
- `mkdir + [Tên thư mục]`: Tạo mới 1 thư mục trong thư mục hiện tại.
- `touch + [Tên file]`: Tạo mới 1 file trong thư mục hiện tại.
**6. rm**
- `rm + [Tên file(tên thư mục)]`: Xóa file (thư mục)
- Một số tham số đi cùng:
			-r	   Xóa thư mục
			-rf	   Xóa không cần hỏi(thận trọng)
**7. mv**
- `mv + [đường dẫn file(thư mục cũ)] [đường dẫn file(thư mục mới)]`: Di chuyển file(thư mục)
- `mv + [Tên file(thư mục) cũ] [Tên file(thư mục) mới]`: Đổi tên file(thư mục)
**8. cp**
- `cp + [đường dẫn file(thư mục cũ)] [đường dẫn file(thư mục mới)]`: copy file(thư mục)
			cp -r 	copy tất cả các file, subfolder
**9. cat**
- `cat hello.txt`: Đọc file hello.txt(show toàn bộ ra màn hình, nếu file lớn, chỉ hiển thị những dòng cuối cùng). Lệnh `cat` thường dùng để đọc những file nhỏ.
**10. less**
- `less hello.txt`: Đọc file hello.txt(hiển thị từng trang một)
- Lệnh `more` tương tự
**11. head**
- `head hello.txt`: Hiển thị 10 dòng đầu tiên của file hello.txt
**12. tail**
- `tail hello.txt`: Hiển thị 10 dòng cuối cùng của file hello.txt
**13. grep**
- `grep [word] [file]`: Tìm kiếm và lọc `[word]` trong `[file]`
			-i	    Tìm kiếm không phân biệt hoa thường
			-r	    Tìm tất cả file ở tất cả các thư mục con
			-v	    Tìm kiếm ngược
**14. stdin, stdout,stderr, pipe**
- `<` hay stdin: Nơi dữ liệu được nhập vào 
- `>` hay stdout: Nơi chương trình xuất dữ liệu ra (`>>`: append)
- `2>` hay stderr: Để đưa nội dung thông báo lỗi ra file thay vì màn hình hiển thị.
- `|`: Chuyển hướng dữ liệu: Đầu ra của cmd này là đầu và của cmd khác. Vd: cat /etc/sysconfig/network-scrpits | less

