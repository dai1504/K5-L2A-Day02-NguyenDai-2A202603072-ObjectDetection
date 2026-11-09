# Mini guideline — bài làm cá nhân

> Điền nội dung này trước khi bắt đầu gán nhãn. Giữ lại các quyết định sau khi self-QC.

## Định nghĩa lớp

| Lớp | Định nghĩa của bạn | Ví dụ/điểm phân biệt |
| --- | --- | --- |
| `car` | Phương tiện giao thông thuộc nhóm xe con, dùng để chở người hoặc có kiểu dáng xe con. Bao gồm sedan, SUV, taxi và xe bán tải.| Xe bán tải được gán car, không gán truck. Không bao gồm xe buýt, xe tải chở hàng hoặc mô tô.|
| `truck` | Phương tiện chuyên dùng để vận chuyển hàng hóa, có dạng xe tải hoặc xe đầu kéo.| Xe tải chở hàng, xe đầu kéo. Không gán các loại xe bán tải thuộc nhóm car.|
| `bus` | Phương tiện chuyên chở hành khách với kiểu dáng xe buýt, bao gồm xe buýt lớn và minibus chở khách. | Xe buýt công cộng, minibus chở khách. Không gán van/minivan thông thường thuộc nhóm van.|
| `van` | Phương tiện có kiểu dáng van hoặc minivan, được sử dụng để chở hàng hoặc chở người.| Xe van giao hàng, minivan. Không gán xe buýt lớn thuộc bus hoặc xe con thông thường thuộc car.|

## Quy tắc chung

- Box bám sát vật thể nghĩa là: Bounding box bao quanh sát các cạnh của phương tiện nhìn thấy trong ảnh, hạn chế khoảng trống không thuộc đối tượng. Box sử dụng hình chữ nhật và không bao gồm các đối tượng xung quanh.
- Vật thể bị che khuất: Nếu phương tiện bị che khuất một phần nhưng vẫn đủ thông tin để xác định class, tiếp tục gán nhãn. Bounding box bao quanh phần đối tượng có thể nhìn thấy. Không bỏ sót phương tiện chỉ vì bị che khuất.
- Vật thể bị cắt bởi rìa ảnh: Nếu phương tiện bị cắt bởi mép ảnh nhưng phần còn lại vẫn đủ để xác định class, vẫn gán nhãn. Box chỉ bao quanh phần phương tiện nằm trong ảnh, không mở rộng ra ngoài phạm vi ảnh.
- Vật thể rất nhỏ/mơ hồ: Nếu phương tiện quá nhỏ hoặc không đủ thông tin để xác định class một cách đáng tin cậy, không tự suy đoán. Ghi nhận trường hợp mơ hồ và hỏi Lab Coach hoặc giảng viên để được làm rõ.

## Ghi lại quyết định cho ít nhất ba ca mơ hồ

| Ảnh | Tình huống | Quyết định cuối | Lý do theo schema |
| --- | --- | --- | --- |
| `drive_007` |Xe bán tải (Pickup truck) có thùng chở hàng phía sau nhưng cấu hình thân xe giống xe con. | Gán nhãn| Theo định nghĩa lớp, xe bán tải thuộc nhóm xe con (car), không phân loại vào nhóm xe tải nặng (truck).|
| `drive_018` | Xe minibus cỡ nhỏ (khoảng 16 chỗ) có thiết kế lai giữa xe van lớn và xe buýt thu nhỏ.|Gán nhãn bus | Mặc dù kích thước nhỏ, phương tiện này chuyên dùng chở hành khách theo tuyến/dịch vụ dạng xe buýt, thuộc nhóm bus theo schema phân loại.|
| `drive_025` | Một chiếc ô tô bị che khuất phần đầu xe bởi cột đèn giao thông, chỉ nhìn thấy khoảng 40% thân và đuôi xe.|Vẫn gán nhãn (car), vẽ box ôm sát phần hiển thị | Theo quy tắc vật thể bị che khuất, miễn là còn đủ đặc điểm nhận diện kiểu dáng xe con thì vẫn gán nhãn và chỉ vẽ bounding box bao quanh phần nhìn thấy.|
