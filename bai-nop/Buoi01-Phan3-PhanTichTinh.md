# BUỔI 1 – PHẦN 3: PHÂN TÍCH TĨNH VỚI ESLINT

- **Họ tên:** Đặng Hoàng Dương
- **MSSV:**
  65130586

## 1. Kết quả chạy công cụ

Lệnh: `npm run lint:lab`

| Tổng số problem | Số error | Số warning |
| --------------- | -------- | ---------- |
| 19              | 16       | 3          |

Ảnh chụp kết quả:
bai-nop/hinh/chaycongcu-terminal.png

## 2. Bảng phân tích

Phân loại: **DEFECT** (chắc chắn gây sai/dừng chương trình) · **SMELL** (khó bảo trì, tiềm ẩn rủi ro) · **CHẤP NHẬN** (không cần sửa, giải thích lý do)

| STT | Dòng | Rule                  | Vấn đề (giải thích bằng lời của bạn)                                                           | Hậu quả nếu chạy chương trình                                                                                       | Phân loại | Cách sửa                                                                        |
| --- | ---- | --------------------- | ---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | --------- | ------------------------------------------------------------------------------- |
| 1   | 9    | no-unused-vars        | Khai báo biến fs nhưng không bao giờ sử dụng.                                                  | Tốn tài nguyên nạp thư viện rác, làm rối mã nguồn.                                                                  | SMELL     | Xóa dòng 9 (const fs = require('fs');).                                         |
| 2   | 14   | no-dupe-keys          | Trùng khóa noiThanh trong đối tượng SHIPPING_CONFIG (dòng 12 là 20000, dòng 14 lại gán 25000). | Giá trị khai báo sau (25000) đè lên giá trị trước (20000), khiến phí nội thành bị tính sai 25.000đ thay vì 20.000đ. | DEFECT    | Xóa dòng 14 (noiThanh: 25000,).                                                 |
| 3   | 21   | no-unused-vars        | Biến total được tính tích lũy trong vòng lặp nhưng không được sử dụng ở lệnh return.           | Kết quả tính tổng giỏ hàng không được trả về.                                                                       | DEFECT    | Sửa dòng 23 thành return total;.                                                |
| 4   | 23   | no-undef              | Trả về biến totl chưa từng được định nghĩa (gõ sai chính tả của total).                        | Chương trình tung ngoại lệ ReferenceError: totl is not defined và bị crash dừng đột ngột.                           | DEFECT    | Sửa totl thành total.                                                           |
| 5   | 28   | eqeqeq                | Sử dụng phép so sánh lỏng lẻo == thay vì ===.                                                  | Dễ bị ép kiểu ngầm định ('0' == 0), dẫn đến kết quả so sánh không chính xác ngoài mong đợi.                         | SMELL     | Thay == thành ===.                                                              |
| 6   | 31   | no-cond-assign        | Dùng phép gán = thay cho phép so sánh === trong biểu thức điều kiện if (qty = 100).            | Biến qty bị gán lại thành 100, biểu thức luôn trả về 100 (truthy), khiến hàm luôn trả về false.                     | DEFECT    | Thay = bằng === hoặc >= 100.                                                    |
| 7   | 31   | no-constant-condition | Biểu thức điều kiện if (qty = 100) luôn có giá trị hằng số 100 (luôn true).                    | Cùng nguyên nhân với dòng 31 trên; khối if luôn được thực hiện.                                                     | DEFECT    | Cùng nguyên nhân dòng 31: chuyển phép gán thành so sánh đúng.                   |
| 8   | 39   | valid-typeof          | So sánh kết quả typeof price với chuỗi sai chính tả 'numbr' (đúng phải là 'number').           | Biểu thức typeof price === 'numbr' luôn trả về false, bỏ sót việc kiểm tra sai kiểu dữ liệu.                        | DEFECT    | Thay 'numbr' thành 'number'.                                                    |
| 9   | 42   | use-isnan             | So sánh trực tiếp price === NaN.                                                               | Trong JS, NaN === NaN luôn trả về false, khiến việc kiểm tra NaN bị vô hiệu hóa hoàn toàn.                          | DEFECT    | Thay bằng Number.isNaN(price).                                                  |
| 10  | 54   | no-fallthrough        | case 'noi-thanh' thiếu câu lệnh break, dẫn đến trôi xuống (fallthrough) case 'ngoai-thanh'.    | Phí nội thành bị gán 20.000đ rồi lập tức bị đè thành 35.000đ (ngoại thành). Phí nội thành luôn bị tính sai.         | DEFECT    | Thêm break; vào cuối case 'noi-thanh'.                                          |
| 11  | 68   | no-dupe-else-if       | Nhánh else if lặp lại đúng điều kiện customer.type === 'VIP' của nhánh if trước đó.            | Nhánh else if không bao giờ chạy tới (dead code), làm mất mức giảm giá 10% (hoặc mức giảm giá khác).                | DEFECT    | Sửa lại điều kiện nhánh if/else if (ví dụ: VIP giảm 10%, THUONG giảm 0%).       |
| 12  | 72   | no-unreachable        | Câu lệnh console.log(...) nằm ngay sau lệnh return 0;.                                         | Đoạn code log không bao giờ được thực thi (unreachable code).                                                       | DEFECT    | Xóa câu lệnh console.log hoặc đưa lên trước lệnh return.                        |
| 13  | 72   | no-console            | Sử dụng câu lệnh console.log trong mã nguồn nghiệp vụ.                                         | Gây bẩn log hệ thống môi trường production.                                                                         | SMELL     | Xóa câu lệnh console.log.                                                       |
| 14  | 77   | no-unsafe-negation    | Phủ định sai vị trí trong biểu thức !productId in cart (JS hiểu là (!productId) in cart).      | Phép phủ định !productId thực hiện trước trả về boolean, dẫn tới logic kiểm tra bị sai hoàn toàn.                   | DEFECT    | Thay bằng !(productId in cart) hoặc !cart.hasOwnProperty(productId).            |
| 15  | 87   | no-unused-vars        | Biến e trong catch (e) được khai báo nhưng không dùng.                                         | Khai báo biến thừa không sử dụng.                                                                                   | SMELL     | Dùng cú pháp catch {} (ES2019) hoặc bỏ tên biến nếu không dùng.                 |
| 16  | 87   | no-empty              | Khối catch (e) {} để rỗng không xử lý ngoại lệ.                                                | Âm thầm nuốt lỗi (swallow exception) khi JSON bị sai định dạng mà không có phản hồi/xử lý.                          | DEFECT    | Trả về null trong khối catch: catch { return null; }.                           |
| 17  | 92   | complexity            | Hàm xepHangKhachHang có độ phức tạp xyclomatic = 9 (vượt mức tối đa 5 cho phép).               | Hàm chứa quá nhiều nhánh rẽ lồng nhau, khó đọc, khó viết unit test đầy đủ, dễ phát sinh lỗi khi bảo trì.            | DEFECT    | Tách nhỏ hàm hoặc giữ nguyên nếu giải thích logic phân hạng cần nhiều nhánh.    |
| 18  | 116  | no-console            | Sử dụng console.log trong hàm tinhTongDon.                                                     | In log thừa khi tính tổng đơn hàng.                                                                                 | SMELL     | Xóa dòng console.log.                                                           |
| 19  | 121  | no-unused-vars        | Tham số kyHieu khai báo nhưng không được sử dụng trong hàm dinhDangTien.                       | Khai báo tham số thừa, làm hàm bị fix cứng ký hiệu tiền 'đ'.                                                        | SMELL     | Dùng kyHieu trong chuỗi trả về: amount.toLocaleString('vi-VN') + (kyHieu 'đ');. |

## 3. Sau khi sửa

Kết quả `npm run lint:lab` sau khi sửa (ảnh chụp hoặc dán kết quả):

```
bai-nop/hinh/ketquachay-terminal.png
```

## 4. Lỗi logic ESLint không phát hiện được

| STT | Hàm         | Mô tả lỗi                                                                                                                      | Căn cứ (chú thích hàm / mục SRS)                                                               | Vì sao ESLint không phát hiện được?                                                                                 |
| --- | ----------- | ------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| 1   | tinhTongDon | Công thức tính tổng tiền bị viết sai phép tính: return tamTinh - giamGia - phi; (đang trừ cả phí vận chuyển thay vì cộng phí). | Chú thích dòng 111 & SRS FR-05.2: "Tổng tiền phải trả = Tạm tính − Giảm giá + Phí vận chuyển". | ESLint chỉ phân tích cú pháp tĩnh, không hiểu được ý nghĩa toán học hay logic nghiệp vụ của các phép tính cộng/trừ. |
| 2   | tinhGiamGia | Logic tính giảm giá cho VIP sai tỉ lệ: đang tính subtotal \* 0.05 (5%), trong khi VIP đúng phải được giảm 10%.                 | SRS FR-05.3 & Phụ lục A: Thành viên VIP được hưởng ưu đãi giảm giá cao hơn (10%).              | ESLint không thể kiểm tra giá trị hằng số kinh doanh (0.05 hay 0.1) có đúng với yêu cầu nghiệp vụ hay không.        |
|     |

## 5. (Không bắt buộc) Nhận xét về phân tích tĩnh trong trình soạn thảo
