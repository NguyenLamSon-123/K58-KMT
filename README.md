# k58_kmt
bài tập số 3 mssv k225480106076 - NGUYỄN LAM SƠN- hệ quản trị cơ sở dữ liệu
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
## yêu cầu bài 3: 
. Sửa bảng DKMH và bảng Điểm từ bài tập 2 để có các bảng như yêu cầu.
2. Nhập dữ liệu demo cho các bảng (nhập có kiểm soát từ tính năng Edit trên UI của mssm)
3. Viết lệnh truy vấn để: Tính được điểm thành phần của 1 sinh viên đang học tại 1 lớp học phần.

hình ảnh paste
![image](https://github.com/user-attachments/assets/f0932f55-f00e-4c02-a030-361a1967b751)
![image](https://github.com/user-attachments/assets/2670329f-58f4-458a-af8b-3f6ee4ba4408)
![image](https://github.com/user-attachments/assets/7bca9e52-3c65-4e69-8e60-a241db7732c8)
![image](https://github.com/user-attachments/assets/624ba2c1-186c-4867-a2d6-4a688912a055)
![image](https://github.com/user-attachments/assets/0caceb16-c505-48ad-b9d6-ff85914476a1)
![image](https://github.com/user-attachments/assets/5dace23d-87cb-4234-b0bf-8d31f2c2e3d9)
![image](https://github.com/user-attachments/assets/1c972484-3754-45a6-a103-267c878d27b9)

## câu lệnh truy vấn
SELECT 
    SV.MASINHVIEN,
    SV.HOTEN AS TEN_SINH_VIEN,
    LHP.MALOPHOCPHAN,
    LHP.TENLOPHOCPHAN,
    MH.TENMON AS TEN_MON_HOC,
    GVCN_GV.HOTEN AS TEN_GV_CHU_NHIEM,  
    GV.HOTEN AS TEN_GV_DAY,
    D.DIEMTHANHPHAN,
    D.DIEMTHI,
    D.DIEMTONGKET
FROM DIEM D
JOIN SINHVIEN SV ON D.MASINHVIEN = SV.MASINHVIEN
JOIN LOPHOCPHAN LHP ON D.MALOPHOCPHAN = LHP.MALOPHOCPHAN
JOIN MONHOC MH ON LHP.MAMON = MH.MAMON
JOIN GIAOVIEN GV ON LHP.MAGIAOVIEN = GV.MAGIAOVIEN
JOIN DANGKIMONHOC DK ON D.MALOPHOCPHAN = DK.MALOPHOCPHAN AND D.MASINHVIEN = DK.MASINHVIEN
JOIN LOPSINHVIEN LSV ON SV.MASINHVIEN = LSV.MASINHVIEN
JOIN GIAOVIENCHUNHIEM GVCN ON LSV.MALOP = GVCN.MALOP
JOIN GIAOVIEN GVCN_GV ON GVCN.MAGIAOVIEN = GVCN_GV.MAGIAOVIEN  
WHERE SV.MASINHVIEN = 'K225480106092' 
AND LHP.MALOPHOCPHAN = 'K58';
## tạo bảng 
USE QLSV;
go
DROP TABLE IF EXISTS DIEM, DANGKIMONHOC, GIAOVIENCHUNHIEM, LOPSINHVIEN, SINHVIEN, LOPHOCPHAN, LOP, MONHOC, GIAOVIEN, BOMON, KHOA;
GO
-- Tạo bảng khoa
CREATE TABLE KHOA(
  MAKHOA NVARCHAR(10) PRIMARY KEY,
  TENKHOA NVARCHAR(50) NOT NULL
);
GO

-- Tạo bảng bộ môn
CREATE TABLE BOMON (
  MABOMON NVARCHAR(10) PRIMARY KEY,
  TENBOMON NVARCHAR(100) NOT NULL,
  MAKHOA NVARCHAR(10) FOREIGN KEY REFERENCES KHOA(MAKHOA)
);
GO

-- Tạo bảng giáo viên
CREATE TABLE GIAOVIEN (
  MAGIAOVIEN NVARCHAR(10) PRIMARY KEY,
  HOTEN NVARCHAR(100) NOT NULL,
  NGAYSINH DATE NOT NULL,
  MABOMON NVARCHAR(10) FOREIGN KEY REFERENCES BOMON(MABOMON)
);
GO

-- Tạo bảng môn học
CREATE TABLE MONHOC(
  MAMON NVARCHAR(10) PRIMARY KEY,
  TENMON NVARCHAR(100) NOT NULL,
  SOTINCHI INT NOT NULL
);
GO

-- Tạo bảng lớp
CREATE TABLE LOP(
  MALOP NVARCHAR(10) PRIMARY KEY,
  TENLOP NVARCHAR(100) NOT NULL
);
GO

-- Tạo bảng lớp học phần 
CREATE TABLE LOPHOCPHAN(
  MALOPHOCPHAN NVARCHAR(10) PRIMARY KEY,
  TENLOPHOCPHAN NVARCHAR(100) NOT NULL,
  HOCKI INT NOT NULL,
  MAMON NVARCHAR(10) FOREIGN KEY REFERENCES MONHOC(MAMON),
  MAGIAOVIEN NVARCHAR(10) FOREIGN KEY REFERENCES GIAOVIEN(MAGIAOVIEN)
);
GO

-- Tạo bảng sinh viên
CREATE TABLE SINHVIEN(
  MASINHVIEN NVARCHAR(13) PRIMARY KEY,
  HOTEN NVARCHAR(100) NOT NULL,
  NGAYSINH DATE NOT NULL
);
GO

-- Tạo bảng lớp sinh viên
CREATE TABLE LOPSINHVIEN(
  MALOP NVARCHAR(10),
  MASINHVIEN NVARCHAR(13),
  CHUCVU NVARCHAR(50),
  PRIMARY KEY (MALOP, MASINHVIEN),
  FOREIGN KEY (MALOP) REFERENCES LOP(MALOP),
  FOREIGN KEY (MASINHVIEN) REFERENCES SINHVIEN(MASINHVIEN)
);
GO

-- Tạo bảng giáo viên chủ nhiệm
CREATE TABLE GIAOVIENCHUNHIEM(
  MALOP NVARCHAR(10),
  MAGIAOVIEN NVARCHAR(10),
  HOCKI INT,
  PRIMARY KEY (MALOP, MAGIAOVIEN, HOCKI),
  FOREIGN KEY (MALOP) REFERENCES LOP(MALOP),
  FOREIGN KEY (MAGIAOVIEN) REFERENCES GIAOVIEN(MAGIAOVIEN)
);
GO

-- Tạo bảng đăng kí môn học 
CREATE TABLE DANGKIMONHOC(
  MALOPHOCPHAN NVARCHAR(10),
  MASINHVIEN NVARCHAR(13),
  PRIMARY KEY (MALOPHOCPHAN, MASINHVIEN),
  FOREIGN KEY (MALOPHOCPHAN) REFERENCES LOPHOCPHAN(MALOPHOCPHAN),
  FOREIGN KEY (MASINHVIEN) REFERENCES SINHVIEN(MASINHVIEN)
);
GO

-- Tạo bảng điểm
CREATE TABLE DIEM(
  MALOPHOCPHAN NVARCHAR(10),
  MASINHVIEN NVARCHAR(13),
  DIEMTHANHPHAN FLOAT CHECK (DIEMTHANHPHAN BETWEEN 0 AND 10),
  DIEMTHI FLOAT CHECK (DIEMTHI BETWEEN 0 AND 10),
  PHANTRAMTHI FLOAT CHECK (PHANTRAMTHI BETWEEN 0 AND 100),
  DIEMTONGKET AS (DIEMTHANHPHAN * 0.4 + DIEMTHI * 0.6),
  PRIMARY KEY (MALOPHOCPHAN, MASINHVIEN),
  FOREIGN KEY (MALOPHOCPHAN, MASINHVIEN) REFERENCES DANGKIMONHOC(MALOPHOCPHAN, MASINHVIEN)
);
GO






