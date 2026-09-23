# BUỔI 1 – PHẦN 1: CÀI ĐẶT VÀ KHÁM PHÁ HỆ THỐNG

- **Họ tên:** Đặng Hoàng Dương
- **MSSV:** 65130586
- **Lớp:** 65cntt-2

## 1. Môi trường

| Mục                                         | Kết quả            |
| ------------------------------------------- | ------------------ |
| Phiên bản Node.js (`node -v`)               | v24.21.0           |
| Phiên bản npm (`npm -v`)                    | 11.19.0            |
| Phiên bản Git (`git --version`)             | git version 2.50.1 |
| Hệ điều hành                                | macOS              |
| Kết quả `npm run lint` (số error / warning) | 19/3               |

Ảnh chụp màn hình (chèn ảnh hoặc đặt file ảnh trong thư mục `bai-nop/hinh/` rồi dẫn link):

- Trang web MiniShop NTU: bai-nop/hinh/65130586-server.png
- Terminal đang chạy server: bai-nop/hinh/65130586-terminal.png

## 2. Kịch bản 1 – Đăng ký với tuổi 17

| Câu hỏi | Trả lời |
| --- | --- |
| Kết quả thực tế | Hệ thống đăng ký thành công |
| Kết quả mong đợi (theo SRS, ghi rõ mục) | Theo mục FR-01.3 của SRS: "Người dùng phải trên 18 tuổi mới được đăng ký", hệ thống phải từ chối và báo lỗi. |
| Có phải failure không? Vì sao? | Có. Vì hệ thống cho phép người 17 tuổi đăng ký, sai lệch so với đặc tả yêu cầu trong tài liệu SRS. |
| Defect nằm ở đâu (file, số dòng, đoạn mã) | File `src/services/registration.js`, dòng 20: `else if (ageNumber < 17 || ageNumber > 100)` (Điều kiện kiểm tra tuổi chặn `< 17` thay vì `< 18` hoặc `<= 18`). |
| Error nào của con người có thể đã gây ra defect này? | Lập trình viên nhầm lẫn điều kiện biên hoặc toán tử logic. |

## 3. Kịch bản 2 – Đơn hàng 500.000đ, nội thành

| Câu hỏi | Trả lời |
| --- | --- |
| Tạm tính | 500.000đ (Balo 350.000đ + Áo 150.000đ) |
| Phí vận chuyển hệ thống tính | 20.000đ |
| Theo FR-04.2, phí đúng phải là | 20.000đ |
| Theo Phụ lục A, phí đúng phải là | 0đ |
| Hệ thống đúng hay sai? Có kết luận được không? Vì sao? | Không thể kết luận hệ thống đúng hay sai, vì tài liệu SRS tự mâu thuẫn giữa mục FR-04.2 và Phụ lục A |
| Defect (nếu có) nằm ở đâu: mã nguồn hay tài liệu? | Nằm ở Tài liệu yêu cầu (SRS) |

## 4. Kịch bản 3 – Tự khám phá

| Mục | Nội dung |
| --- | --- |
| Chức năng | Đăng nhập sai quá số lần cho phép |
| Các bước thực hiện | 1. Vào màn hình Đăng nhập.<br>2. Nhập email `duong.dh.65cntt@ntu.edu.vn` và gõ sai mật khẩu liên tiếp 3 lần.<br>3. Thử đăng nhập lại lần thứ 4 bằng mật khẩu đúng. |
| Dữ liệu sử dụng | Email: `duong.dh.65cntt@ntu.edu.vn`, Mật khẩu sai: `sai123` (3 lần), Mật khẩu đúng: `Matkhau123`. |
| Kết quả mong đợi (căn cứ: mục nào của SRS) | Theo FR-02.3, sau 3 lần sai tài khoản phải bị khóa. |
| Kết quả thực tế | Hệ thống bị khóa tài khoản ngay sau 3 lần nhập sai. |
| Nhận định (failure? mức độ?) | Failure, mức độ Major (Mâu thuẫn với NFR-03 quy định khóa sau 5 lần sai). |
