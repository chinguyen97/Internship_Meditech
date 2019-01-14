# Permission

**1. Nhóm quyền**
- Owner: Chỉ cấp quyền cho chủ sở hữu của file.
- Groups: Chỉ cấp quyền cho nhóm sở hữu của file.
- Other: Cấp quyền cho những đối tượng không thuộc hai trường hợp trên.

**2. Nhóm quyền**
Với 1 file, có 3 loại quyền cơ bản sau:

|Tên quyền|Ký hiệu|Dạng sô|Mô tả|
|---------|-------|-------|-----|
|Read|r|4|Quyền đọc file|
|Write|w|2|Quyền ghi file|
|Excute|e|1|Quyền thực thi file|

Ngoài ra, còn có 1 vài quyền đặc biệt sau:

|Tên quyền|Ký hiệu|Dạng số|Mô tả|
|---------|-------|-------|-----|
|Setuid/Setguid|s|1|Nếu file được thự thi, người thực thi sẽ là chủ sở hữu|
|Sticky bit|t|1|Chỉ chủ sở hữu mới được xóa hoặc thay đổi tên file dù khi Other có toàn quyền với file đó|

**3. Cách xem phân quyền của 1 file**
- Sử dụng lệnh `ls -l`, Kết quả sẽ có dạng `-rwxr-x--- 1 user group`
	- Kí tự `-` đầu tiên để chỉ loại file thông thường, `d` với thư mục, `c` với thiết bị, `l` với liên kết (liên kết tới một file khác).
	- 3 kí tự tiếp theo `rwx` là quyền hạn của Owner, ở đây Owner có mọi quyền đối với file.
	- 3 kí tự tiếp `r-x` là quyền hạn của Group, ở đây, Groups có quyền đọc và thực thi đối với file(quyền write bị `-`)
	- 3 kí tự cuối là quyền của Other, ở đây mọi user khác ko có quyền gì đối với file này.
	- Số nguyên đi sau quyền hạn để chỉ số lượng liên kết tới file, ở đây `1` có nghĩa là file này không có liên kết tượng trưng mà chỉ có một liên kết cứng duy nhất trỏ tới chính nó.
	- Cuối cùng là 2 thông tin nói về chủ sở hữu và nhóm sở hữu, ở đây là người dùng `user` và nhóm `group`

**4. Thay đổi quyền và đối tượng sở hữu của file**
- Thay đổi quyền của file:
	- Thay đổi bằng số: `chmod 775 hello.txt`: 
	- Thay đổi bằng kí hiệu: `chmod u+w o-r +e hello.txt`
- Thay đổi đối tượng sở hữu:
	- `chown Nhansu:KeToan folder1` 	 hoặc 	`chown .KeToan folder1`

**5. Umask**
- Khi chúng ta tạo ra file hoặc thư mục, mặc định hệ thống gán cho nó 1 quyền mặc định
File: 666 (rw-rw-rw-) (3)
Folder: 777 (rwxrwxrwx) (4)
Vậy nếu chúng ta muốn thay đổi quyền mặc định của một file, folder khi nó được tạo thì phải làm thế nào. Trong linux điều này khá đơn giản, bởi hệ thống cung cấp cho chúng ta một công cụ đó là umask Khi umask được khởi tạo giá trị thì các quyền mặc định sẽ không còn như (3) và (4) nữa.
Mặc định thì umask = 022. Khi đó các quyền mặc định với file và folder được tính lại như sau:
File:
666: rw- rw- rw-
022: --- -w- -w-
644 rw- r-- r--
Folder:
777: rwx rwx rwx
022: --- -w- -w-
755 rwx r-x r-x
Lưu ý: có một trường hợp ngoại lệ, nếu như umask=123 thì quyền mặc định cho file sẽ là 644 chứ không phải là 543.
- Thay đổi giá trị umask: `umask [value]`


