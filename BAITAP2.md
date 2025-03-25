# K58-KMT
Bài tập số 2 của sinh viên : K225480106076 - Nguyễn Lam Sơn - Hệ quản trị cơ sở dữ liệu
## DEADLINE: 23H59 NGÀY 25/03/2025

## ĐIỀU KIỆN: (ĐÃ LÀM XONG BÀI 1)
1. Đã cài đặt SQL Server 2022 Dev.
2. Đã cài đặt SQL Managerment Studio bản mới nhất.
3. Đã kết nối từ SQL Managerment Studio vào SQL Server.
4. Đã có tài khoản github, biết cách tạo repository(kho lưu trữ) cho phép truy cập public.

## BÀI TOÁN:
- Tạo csdl quan hệ với tên QLSV gồm các bảng sau:
  + SinhVien(#masv,hoten,NgaySinh)
  + Lop(#maLop,tenLop)
  + GVCN(#@maLop,#@magv,#HK)
  + LopSV(#@maLop,#@maSV,ChucVu)
  + GiaoVien(#magv,hoten,NgaySinh,@maBM)
  + BoMon(#MaBM,tenBM,@maKhoa)
  + Khoa(#maKhoa,tenKhoa)
  + MonHoc(#mamon,Tenmon,STC)
  + LopHP(#maLopHP,TenLopHP,HK,@maMon,@maGV)
  + DKMH(#@maLopHP,#@maSV,DiemTP,DiemThi,PhanTramThi)

## YÊU CẦU:
1. Thực hiện các hành động sau trên giao diện đồ hoạ để tạo cơ sở dữ liệu cho bài toán:
  + Tạo database mới, mô tả các tham số(nếu có) trong quá trình.
  + Tạo các bảng dữ liệu với các trường như mô tả, chọn kiểu dữ liệu phù hợp với thực tế (tự tìm hiểu)
  + Mỗi bảng cần thiết lập PK, FK(s) và CK(s) nếu cần thiết. (chú ý dấu # và @: # là chỉ PK, @ chỉ FK)
2. Chuyển các thao tác đồ hoạ trên thành lệnh SQL tương đương. lưu tất cả các lệnh SQL trong file: Script_DML.sql
## HINH ANH PASTE
![image](https://github.com/user-attachments/assets/e42f6a0c-b6e3-4e7a-9ab4-68f86cfe8049)
![image](https://github.com/user-attachments/assets/1e334ad5-1e78-4df0-ba93-2e8ac06570cb)
![image](https://github.com/user-attachments/assets/55f70d62-57ff-4aa9-b944-9c9ef45d61f2)
![image](https://github.com/user-attachments/assets/3140d25f-73d4-49c3-9555-8fc0ff3b42d9)
![image](https://github.com/user-attachments/assets/ef763403-e102-430e-96f0-163c2f4d37c4)
![image](https://github.com/user-attachments/assets/ef2f1831-a494-47a0-ab2d-80dc3058df20)
![image](https://github.com/user-attachments/assets/4102a7f8-f96f-4823-8f40-b52c836eda4e)
![image](https://github.com/user-attachments/assets/04aea1d5-0eb7-4fdc-bc96-ab9dd300691e)
![image](https://github.com/user-attachments/assets/41c5111c-d702-45f8-8bbc-53cfd46f7e98)
![image](https://github.com/user-attachments/assets/0a352d93-5662-4964-a3a1-09e1fa6c2d4c)
![image](https://github.com/user-attachments/assets/287d0c82-4331-434e-93ae-2bae83ddb789)
![image](https://github.com/user-attachments/assets/0536e3c6-c37e-47f5-8108-0b0921b9b8d4)

![image](https://github.com/user-attachments/assets/6bb97670-5715-4db0-8546-f9185e7a4ded)

![image](https://github.com/user-attachments/assets/fa1fb847-f2c9-4903-aa1c-f182422fe011)

![image](https://github.com/user-attachments/assets/8b803180-9803-4c33-9212-e29f6f6c248f)

![image](https://github.com/user-attachments/assets/dbfb7cca-6ae4-4996-b714-945628f184e8)

![image](https://github.com/user-attachments/assets/e0fb6b0f-182d-4463-a5a7-79310325b1ac)

![image](https://github.com/user-attachments/assets/ecb9ecc1-200f-416e-a481-2dcd27239a2f)

![image](https://github.com/user-attachments/assets/0df15d7b-229f-4d1c-ab46-0a3dad72c2bd)

![image](https://github.com/user-attachments/assets/e87bb2f2-a9c1-4d4a-9a6e-0574f494067a)

![image](https://github.com/user-attachments/assets/6528c28a-b032-4a26-a2dd-69a71ab9a98d)

![image](https://github.com/user-attachments/assets/f977172f-9887-4004-b6c7-17d58aaf1e3f)

























