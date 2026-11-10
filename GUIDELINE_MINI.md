# Mini guideline — bài làm cá nhân

> Điền nội dung này trước khi bắt đầu gán nhãn. Giữ lại các quyết định sau khi self-QC.

## Định nghĩa lớp

| Lớp | Định nghĩa của bạn | Ví dụ/điểm phân biệt |
| --- | --- | --- |
| `car` |Phương tiện giao thông cơ giới 4 bánh, chủ yếu dùng để chở người, có kích thước nhỏ hoặc trung bình. |Sedan, SUV, hatchback. Phân biệt với `van` và `truck` dựa vào thiết kế, kích thước và mục đích sử dụng. |
| `truck` |Phương tiện cơ giới có kích thước lớn, được thiết kế chủ yếu để vận chuyển hàng hóa. |Xe tải thùng, xe ben, xe đầu kéo. Thường có khoang chở hàng riêng biệt. |
| `bus` |Phương tiện giao thông kích thước lớn để vận chuyển nhiều hành khách cùng lúc. |Xe buýt công cộng, xe khách, xe buýt trường học. Có khoang hành khách lớn với nhiều hàng ghế. |
| `van` |Phương tiện cơ giới có khoang thân xe kín, thường dùng để chở hàng hóa hoặc một nhóm hành khách, kích thước thường nhỏ hơn xe tải lớn. |Minivan, cargo van, passenger van. Thường có thân xe liền khối và khoang chứa hàng hoặc hành khách phía sau. |

## Quy tắc chung

- Box bám sát vật thể nghĩa là: Bounding Box phải bao quanh toàn bộ phần vật thể nhìn thấy được, sát với đường biên bên ngoài của vật thể, hạn chế lấy thừa vùng nền xung quanh. Không cần bao gồm phần bị che khuất hoặc không xuất hiện trong ảnh
- Vật thể bị che khuất: Chỉ vẽ Bounding Box dựa trên phần vật thể còn quan sát được. Nếu vẫn nhận diện được vật thể và xác định được lớp, tiến hành gán nhãn bình thường.
- Vật thể bị cắt bởi rìa ảnh: Vẫn gán nhãn nếu vật thể đủ đặc điểm để nhận diện. Bounding Box kéo dài đến rìa ảnh, không tự suy đoán hoặc vẽ thêm phần nằm ngoài khung hình.
- Vật thể rất nhỏ/mơ hồ: Chỉ gán nhãn khi có đủ thông tin hình ảnh để xác định vật thể và phân loại chính xác. Nếu quá nhỏ, mờ hoặc không thể phân biệt giữa các lớp thì không tự ý đoán nhãn; xử lý theo quy định của dataset (ví dụ: bỏ qua hoặc đánh dấu cần review).

## Ghi lại quyết định cho ít nhất ba ca mơ hồ

| Ảnh | Tình huống | Quyết định cuối | Lý do theo schema |
| --- | --- | --- | --- |
| `drive_56` |1 chiếc xe ở phía mép trên ở ảnh chỉ thấy phần đuôi xe, khó phân biệt giữa `car` và `van`|Không gán nhãn, chuyển sang review nếu schema hỗ trợ. |Không đủ bằng chứng hình ảnh để xác định class một cách đáng tin cậy. |
| `drive_56` |Một chiếc car bị xe khác che khuất phần đầu xe. |Gán nhãn `car`, Bounding Box bao quanh phần nhìn thấy được. |Vẫn nhận diện được đặc điểm của xe con và xác định được class. |
| `drive_56` |Một chiếc truck bị cắt mất phần đầu do nằm sát rìa ảnh. |Gán nhãn `truck`, Bounding Box kết thúc tại rìa ảnh. |Phần thùng xe và cấu trúc phương tiện vẫn đủ để xác định class. |
