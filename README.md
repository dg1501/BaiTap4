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

- 1.1. Tạo bảng giáo viên
![Screenshot (461)](https://github.com/user-attachments/assets/1264688c-f58d-4444-99c8-e81a221f0bd1)

- 1.2. Tạo bảng môn học
![Screenshot (465)](https://github.com/user-attachments/assets/e0fa0da6-9252-4f0d-9728-ae1c38c5d7c9)

- 1.3. Tạo bảng lớp học
![Screenshot (463)](https://github.com/user-attachments/assets/6917f385-13ab-4cd5-b847-69adb044f157)

- 1.4. Tạo bảng tkb
![Screenshot (464)](https://github.com/user-attachments/assets/550b99fa-c4e4-4c33-be05-83fb2a461deb)

### 2. Thiết lập khoá ngoại 
![image](https://github.com/user-attachments/assets/5fea9801-c0be-4926-8490-b75743a3bb89)

- Tại bảng lớp học, thiết lập khoá ngoại (FK)
+ Thiết lập khoá ngoại giữa bảng (*LopHoc*) và bảng (*GiaoVien*) thông qua **MaGV**
+ Thiết lập khoá ngoại giữa bảng (*LopHoc*) và bảng (*MonHoc*) thông qua **MaMH**
+ Thiết lập khoá ngoại giữa bảng (*LopHoc*) và bảng (*TKB*) thông qua **MaLop**

### 3. Thêm thông tin demo cho bảng GIÁO VIÊN
- Bước 1: Truy cập Link nguồn dữ liệu *TMS.tnut.edu.vn*
![image](https://github.com/user-attachments/assets/fa059624-4b66-40a1-aadd-0c6025fbd6f9)

- Bước 2: Tiến hành copy dữ liệu cần thiết
- Bước 3: Paste vào phần mềm Excel để tiến hành chỉnh sửa
![image](https://github.com/user-attachments/assets/b4420119-4b35-42bc-a3ba-655e25231276)

- Bước 4: Vì chưa có thông tin của trường MaGV nên ta tiến hành thêm cột **MaGV** và thêm thông tin demo cho cột

+ Thêm cột MaGV
![image](https://github.com/user-attachments/assets/594ff72b-9608-4d7e-bf7a-cd4527961dfa)

- Vì cột Tên Giáo viên đang có nhiều giá trị bị trùng lặp, nên ta tiến hành bước sau để xử lý chúng
+ Bước 1: Chọn cột Tên Giáo Viên
+ Bước 2: Chọn *Data* trên thanh công cụ
+ Bước 3: Chọn *Remove Duplicates*
![Untitled](https://github.com/user-attachments/assets/230e5f0d-3dfb-4525-ac14-35af541d80c6)

+ Bước 4: Chọn Continue With.... Selection ( Vì chúng ta chỉ cần loại bỏ các thông tin trùng lặp ở cột Tên Giáo Viên nên ta chọn Continue....selection )
![Untitled](https://github.com/user-attachments/assets/57e9d2ee-9a3e-4532-b89e-20b64790ffd2)

- Tiếp theo ta chọn dòng đầu tiên của cột MaGV và gõ câu lệnh sau vào thanh công thức ( =TEXT(ROW()-1;"000")

- **Giải thích lệnh**
+ Hàm ROW():
Trả về số dòng hiện tại của ô đang viết công thức.
Ví dụ: nếu bạn viết công thức ở dòng 2 thì ROW() sẽ cho ra số 2.

+ ROW() - 1:
Vì ROW() ở dòng 2 trả về 2, nên ta trừ đi 1 để bắt đầu từ số 1.
Tức là, kết quả sẽ là 1, 2, 3, ... tùy theo bạn đặt công thức ở dòng nào.

+ Hàm TEXT(...;"000"):
Dùng để định dạng số thành chuỗi văn bản có đủ 3 chữ số.

- Khi đã được dòng dầu tiên, ta di chuột vào ô đó và kéo xuống các ô còn lại để hoàn thành công việc
![Untitled](https://github.com/user-attachments/assets/c71c578f-fb39-4943-b879-c5409a47774b)

![Untitled](https://github.com/user-attachments/assets/25a71860-a198-447e-a810-a0e705b3297c)

- Sau đó ta tiến hành copy dữ liệu đầy đủ vào SQL
![image](https://github.com/user-attachments/assets/51f68307-e9d4-4464-aa1f-ff9d15669564)

### 4. Tương tự, ta thêm thông tin demo cho bảng MÔN HỌC, LỚP HỌC VÀ TKB
- MÔN HỌC
![Untitled](https://github.com/user-attachments/assets/50268b4f-6855-49aa-9922-1ee096207a1a)

- LỚP HỌC
![Screenshot (477)](https://github.com/user-attachments/assets/dacb5fc3-0202-4b47-bdb1-4cc294e150f4)

- TKB
