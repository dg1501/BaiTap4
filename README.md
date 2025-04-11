# BÀI TẬP 4: (SQL SERVER )
# YÊU CẦU BÀI TOÁN:
## Tạo csdl cho hệ thống TKB (đã nghe giảng, đã xem cách làm)
## Nguồn dữ liệu: TMS.tnut.edu.vn
## Tạo các bảng tuỳ ý (3nf)
## Tạo được query truy vấn ra thông tin gồm 4 cột: họ tên gv, môn dạy, giờ vào lớp, giờ ra.
## trả lời câu hỏi: trong khoảng thời gian từ datetime1 tới datetime2 thì có những gv nào đang bận giảng dạy.

# BÀI LÀM
## Tạo csdl cho hệ thống TKB.
### 1. Tạo New Database
![image](https://github.com/user-attachments/assets/51310771-6945-4301-a2ff-de00087c6187)

- 1.1. Tạo table giáo viên

![image](https://github.com/user-attachments/assets/9c3eb25d-01ed-4c76-91c1-8d61caf2eb7b)

- 1.2. Tạo table môn học

![image](https://github.com/user-attachments/assets/909bdc20-be19-466b-9414-ef17b81c293f)

- 1.3. Tạo table lớp học

![image](https://github.com/user-attachments/assets/e94ae9d2-2515-4918-abcd-517c5c502389)

- 1.4. Tạo bảng tkb

![image](https://github.com/user-attachments/assets/5833c3d7-a60a-4ddb-b686-0afd0bda3db1)

### 2. Thiết lập khoá ngoại 
![image](https://github.com/user-attachments/assets/5fea9801-c0be-4926-8490-b75743a3bb89)

- Tại bảng lớp học, thiết lập khoá ngoại (FK)
+ Thiết lập khoá ngoại giữa bảng (**LopHoc*) và bảng (**GiaoVien*) thông qua **MaGV**
+ Thiết lập khoá ngoại giữa bảng (**LopHoc*) và bảng (**MonHoc*) thông qua **MaMH**
+ Thiết lập khoá ngoại giữa bảng (**LopHoc*) và bảng (**TKB*) thông qua **MaLop**

### 3. Thêm thông tin demo cho bảng **GiaoVien**
- Bước 1: Truy cập Link nguồn dữ liệu **TMS.tnut.edu.vn*
![image](https://github.com/user-attachments/assets/fa059624-4b66-40a1-aadd-0c6025fbd6f9)

- Bước 2: Tiến hành copy dữ liệu cần thiết
- Bước 3: Paste vào phần mềm Excel để tiến hành chỉnh sửa
![image](https://github.com/user-attachments/assets/b4420119-4b35-42bc-a3ba-655e25231276)

- Bước 4: Vì chưa có thông tin của trường MaGV nên ta tiến hành thêm cột **MaGV** và thêm thông tin demo cho cột

+ Thêm cột MaGV

  ![image](https://github.com/user-attachments/assets/594ff72b-9608-4d7e-bf7a-cd4527961dfa)

++ Chọn vào cột **MaGV* và viết câu lệnh sau vào thanh công thức **( =VLOOKUP(B2, Sheet2!$A$2:$B$100, 2, FALSE )**

+++ B2: là ô chứa tên GV cần tra.

+++ Sheet2!$A$2:$B$100: là vùng dữ liệu chứa danh sách mã GV (bạn chỉnh lại theo bảng thật của bạn).

+++ 2: nghĩa là lấy giá trị ở cột thứ 2 trong vùng tra.

+++ FALSE: tra chính xác tuyệt đối.

![Untitled](https://github.com/user-attachments/assets/c7a72701-1b13-480a-8e31-00d71339e93a)

