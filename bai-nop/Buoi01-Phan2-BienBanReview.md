# BIÊN BẢN REVIEW TÀI LIỆU YÊU CẦU

## Thông tin chung

| Mục                                 | Nội dung                                             |
| ----------------------------------- | ---------------------------------------------------- |
| Họ tên                              | Đặng Hoàng Dương                                     |
| MSSV                                | 65130586                                             |
| Tài liệu được review                | MSN-SRS – Đặc tả yêu cầu MiniShop NTU, phiên bản 1.0 |
| Loại review                         | Review theo checklist (cá nhân)                      |
| Ngày                                |                                                      |
| Bước 1 – Khởi động                  | từ …0.4… đến …0.45…                                  |
| Bước 2 – Đọc lần 1 (theo trình tự)  | từ …0.45… đến …1.15…                                 |
| Bước 3 – Đọc lần 2 (đối chiếu chéo) | từ …1.15… đến …1.35…                                 |
| Bước 4 – Hoàn thiện biên bản        | từ …1.35… đến …1.55…                                 |

## Danh sách lỗi

Loại lỗi: MƠ HỒ · MÂU THUẪN · THIẾU · KHÔNG KIỂM THỬ ĐƯỢC · KHÔNG KHẢ THI · THUẬT NGỮ · SAI SỐ LIỆU
Mức độ: Major · Minor

| STT | Vị trí (mã yêu cầu / mục)     | Mô tả lỗi                                                                                                                                                                             | Mã checklist | Loại lỗi            | Mức độ | Tìm thấy ở lần đọc (1/2) | Đề xuất sửa                                                                                                                               |
| --- | ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | ------------------- | ------ | ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | Mục 2.2 & FR-01.3             | Mâu thuẫn điều kiện tuổi: Mục 2.2 quy định "từ 18 tuổi trở lên" (≥18), nhưng FR-01.3 ghi "phải trên 18 tuổi" (>18). Người đủ 18 tuổi không rõ có được đăng ký không.                  | CL-02        | MÂU THUẪN           | Major  | 2                        | Thống nhất quy định: "Người dùng từ 18 tuổi trở lên (≥18) được đăng ký tài khoản."                                                        |
| 2   | FR-01.4                       | Mơ hồ độ mạnh mật khẩu: Sử dụng cụm từ cảm tính "phải đủ mạnh để đảm bảo an toàn", không thể kiểm thử chính xác.                                                                      | CL-01        | MƠ HỒ               | Major  | 1                        | Sửa thành: "Mật khẩu có độ dài từ 8 đến 20 ký tự, phải chứa ít nhất 1 chữ hoa, 1 chữ thường, 1 chữ số và 1 ký tự đặc biệt."               |
| 3   | FR-02.3 & NFR-03              | Mâu thuẫn số lần khóa tài khoản: FR-02.3 ghi bị khóa sau "3 lần đăng nhập sai", nhưng NFR-03 lại ghi "5 lần đăng nhập sai".                                                           | CL-02        | MÂU THUẪN           | Major  | 2                        | Thống nhất ở cả 2 mục thành cùng 1 số lần (ví dụ: 5 lần đăng nhập sai liên tiếp).                                                         |
| 4   | FR-02.3                       | Thiếu xử lý ngoại lệ khi khóa: Không nêu rõ tài khoản bị khóa trong bao lâu, có tự mở khóa hay cần quy trình khôi phục/email/quản trị viên.                                           | CL-03        | THIẾU               | Major  | 1                        | Bổ sung: "Tài khoản bị khóa tạm thời trong 30 phút, hoặc người dùng có thể thực hiện quy trình 'Quên mật khẩu' để mở khóa qua email."     |
| 5   | FR-03.4                       | Mơ hồ giới hạn giỏ hàng: Dùng từ cảm tính "số lượng sản phẩm hợp lý", không rõ số lượng tối đa là bao nhiêu.                                                                          | CL-01        | MƠ HỒ               | Major  | 1                        | Sửa thành: "Giỏ hàng chứa tối đa 50 loại sản phẩm khác nhau và tổng số lượng sản phẩm không quá 200."                                     |
| 6   | FR-04.1 & Phụ lục A (dòng #2) | Sai phí vận chuyển ngoại thành: FR-04.1 quy định ngoại thành là 35.000đ, nhưng Phụ lục A dòng #2 (Thường, Ngoại thành, Tạm tính 200.000đ) lại tính 30.000đ.                           | CL-07        | SAI SỐ LIỆU         | Major  | 2                        | Sửa Phụ lục A dòng #2 cột Phí vận chuyển từ 30.000đ thành 35.000đ                                                                         |
| 7   | FR-04.2 & Phụ lục A (dòng#3)  | Mâu thuẫn điều kiện miễn phí vận chuyển: FR-04.2 ghi tạm tính "trên 500.000đ" (>500k), nhưng Phụ lục A dòng #3 mức tạm tính 500.000đ lại tính 0đ (miễn phí).                          | CL-09        | MÂU THUẪN           | Major  | 2                        | Sửa FR-04.2 thành: "Đơn hàng có tạm tính từ 500.000đ trở lên (≥500k) được miễn phí vận chuyển."                                           |
| 8   | FR-05.3                       | Sử dụng thuật ngữ chưa định nghĩa: Thuật ngữ "Khách hàng thân thiết" không có trong bảng Thuật ngữ (1.3) hay Nhóm người dùng (2.1) (chỉ có Khách, Thành viên, Thành viên VIP).        | CL-06        | THUẬT NGỮ           | Major  | 2                        | Đổi tên thành "Thành viên VIP" hoặc thêm khái niệm "Khách hàng thân thiết" vào mục 1.3 và 2.1 với tiêu chí định nghĩa rõ ràng.            |
| 9   | UC-03 (Bước 3) & FR-05        | Thiếu FR về Mã giảm giá: UC-03 Bước 3 có thao tác "Nhập mã giảm giá", nhưng không có yêu cầu chức năng FR nào quy định về Mã giảm giá (điều kiện áp dụng, kiểm tra hợp lệ, mức giảm). | CL-08        | THIẾU               | Major  | 2                        | Bổ sung FR-05.6: "Hệ thống cho phép thành viên nhập Mã giảm giá hợp lệ tại màn hình đặt hàng để giảm trừ trực tiếp vào tổng tiền."        |
| 10  | FR-05.5                       | Thiếu quy tắc và trạng thái hủy đơn: Không quy định đơn hàng ở trạng thái nào được phép hủy (chỉ "Chờ xác nhận" hay đang giao cũng được hủy?), kết quả sau khi hủy ra sao.            | CL-03        | THIẾU               | Major  | 2                        | Sửa thành: "Thành viên chỉ được hủy đơn hàng khi đơn ở trạng thái 'Chờ xác nhận'. Khi hủy thành công, trạng thái đơn đổi thành 'Đã hủy'." |
| 11  | NFR-01                        | Không kiểm thử được hiệu năng: Cụm từ "phản hồi nhanh" là cảm tính, thiếu chỉ số đo lường định lượng cụ thể.                                                                          | CL-04        | KHÔNG KIỂM THỬ ĐƯỢC | Minor  | 1                        | Sửa thành: "Thời gian phản hồi của hệ thống với các thao tác không vượt quá 2 giây đối với 95% số request."                               |
| 12  | NFR-02                        | Yêu cầu không khả thi: "Hoạt động 100% thời gian và không bao giờ xảy ra lỗi" là phi thực tế và vi phạm nguyên lý kiểm thử phần mềm.                                                  |              | KHÔNG KHẢ THI       | Minor  | 1                        | Sửa thành: "Hệ thống đạt độ sẵn sàng (Availability) tối thiểu 99.5% thời gian trong tháng."                                               |

(Thêm dòng nếu cần.)

## Thống kê

| Loại lỗi               | Số lượng |
| ---------------------- | -------- |
| MƠ HỒ                  | 2        |
| MÂU THUẪN              | 3        |
| THIẾU                  | 3        |
| KHÔNG KIỂM THỬ ĐƯỢC    | 1        |
| KHÔNG KHẢ THI          | 1        |
| THUẬT NGỮ              | 1        |
| SAI SỐ LIỆU            | 1        |
| **Tổng**               | 12       |
| Trong đó Major / Minor | 10/2     |

## Các điểm cần hỏi lại BA (em chưa chắc ý đồ tác giả)

1."Khách hàng thân thiết" trong FR-05.3 có phải chính là "Thành viên VIP" không, hay là một phân hạng người dùng mới sẽ được phát triển ở phiên bản sau? 2.
Mốc miễn phí vận chuyển là từ 500.000đ trở lên (
≥
500.000
đ
≥500.000đ) hay bắt buộc phải lớn hơn 500.000đ (>500.000đ)?

## Kết luận review

Đánh dấu một lựa chọn:

- [ ] **Chấp nhận** – tài liệu dùng được ngay
- [ ] **Chấp nhận có điều kiện** – dùng được sau khi sửa các lỗi đã nêu, không cần review lại
- [x] **Review lại** – phải sửa và tổ chức review lần 2

Lý do:Lý do: Tài liệu SRS v1.0 tồn tại tới 13 lỗi, trong đó có 10 lỗi mức độ Major gây mâu thuẫn trực tiếp giữa các yêu cầu chức năng (tuổi đăng ký, số lần khóa tài khoản, phí vận chuyển), thiếu yêu cầu chức năng quan trọng (mã giảm giá, quy định hủy đơn, xử lý mở khóa tài khoản) và số liệu ví dụ minh họa bị sai.

## Tự đánh giá (3–5 câu)

1. Lần đọc thứ hai (đối chiếu chéo) giúp em tìm thêm được bao nhiêu lỗi? Đó là những loại lỗi nào? -> Lần đọc thứ hai (đối chiếu chéo) giúp em tìm thêm được 5 lỗi quan trọng (Mâu thuẫn tuổi Mục 2.2 ↔ FR-01.3; Mâu thuẫn số lần khóa FR-02.3 ↔ NFR-03; Sai số liệu & mâu thuẫn Phụ lục A ↔ FR-04.1/04.2; Thuật ngữ FR-05.3 ↔ 1.3/2.1; Thiếu FR cho UC-03 bước 3). Đó chủ yếu là các loại lỗi MÂU THUẪN, SAI SỐ LIỆU, THUẬT NGỮ và THIẾU.
2. Nếu tổ chức review theo nhóm (có Moderator, Author, nhiều Reviewer), em nghĩ những lỗi nào sẽ dễ được phát hiện hơn? Vì sao? -> Nếu tổ chức review theo nhóm (có Moderator, Author, nhiều Reviewer), các lỗi về MƠ HỒ (từ ngữ cảm tính như "đủ mạnh", "hợp lý"), lỗi KHÔNG KHẢ THI (NFR-02), và lỗi THUẬT NGỮ sẽ dễ phát hiện hơn. Lý do là vì mỗi thành viên có góc nhìn kỹ thuật khác nhau, qua thảo luận và phản biện sẽ nhanh chóng nhận ra các điểm thiếu thực tế hoặc đa nghĩa mà một cá nhân tự review dễ bỏ qua.
3. Lần sau review tài liệu, em sẽ làm khác đi điều gì? -> Lần sau review tài liệu, em sẽ chủ động lập bảng ma trận đối chiếu chéo (Cross-reference table) trước giữa các phần (FR ↔ NFR, FR ↔ UC, Quy tắc ↔ Phụ lục/Ví dụ) để việc phát hiện mâu thuẫn diễn ra nhanh chóng và toàn diện hơn.
