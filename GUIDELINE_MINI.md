# Mini guideline — bài làm cá nhân

> Điền nội dung này trước khi bắt đầu gán nhãn. Giữ lại các quyết định sau khi self-QC.

## Định nghĩa lớp

| Lớp | Định nghĩa của bạn | Ví dụ/điểm phân biệt |
| --- | --- | --- |
| `car` | Là phương tiện giao thông 4 bánh khác với 3 loại truck, van, bus|Các loại car thường có kích thước nhỏ hơn 3 loại xe còn lại|
| `truck` | Là Phương tiện giao thông 4 bánh ở phía sau xe có thùng xe| Có thùng xe ở phía sau xe|
| `bus` | là xe liền khối hình hộp chữ nhật nhưng lớn hơn rất nhiều so với xe van| Xe kích thước lớn, có nhiều kính xe|
| `van` | Là xe liền khối hình hộp phần đầu mũi xe ngắn cụt hoặc gần như không có| Có kích thước lớn hơn car nhưng phần đầu xe không nhô ra quá nhiều như car|

## Quy tắc chung

- Box bám sát vật thể nghĩa là: Phần box ôm sát phần thân xe nhìn thấy
- Vật thể bị che khuất: Nếu vật thể bị che quá 60% cơ thể hoặc không thể nhận diện chính xác loại vật thể thì không box
- Vật thể bị cắt bởi rìa ảnh: Nếu vật thể bị mất quá 60% cơ thể hoặc không thể nhận diện chính xác loại vật thể thì không box. Nếu box thì box phần vật thể đến rìa ảnh
- Vật thể rất nhỏ/mơ hồ: Nếu không thể nhận diện không box

## Ghi lại quyết định cho ít nhất ba ca mơ hồ

| Ảnh | Tình huống | Quyết định cuối | Lý do theo schema |
| --- | --- | --- | --- |
| `drive_238` | Vật thể mơ hồ| van| chiều cao lớn hơn so với CAR 239|
| `drive_272` |Vật thể bị cắt bởi rìa ảnh | car | kích thước phần đầu xe bằng với "car" khác và nhỏ hơn van |
| `drive_281` | Vật thể bị che khuất|car | Chiều cao phần đầu xe nhỏ hơn xe van|
| `drive_300` | Vật thể bị cắt bởi rìa ảnh|car | phần đuôi xe chéo nên không phải hình hộp|
| `drive_306` | Vật thể mơ hồ|van | Chiều cao của xe lớn hơn "car"|
| `drive_357` | Vật thể bị che khuất |van | Chiều dài của xe lớn hơn "car"|
| `drive_374` | Vật thể mơ hồ |car | Phần mũi xe quá dài|
| `drive_492` | Vật thể bị cắt bởi rìa ảnh |car | Phần thân xe và 1 phần kính của đầu xe chiếm diện tích quá ít nên kích thước xe nhỏ so với xe van|
| `drive_512` | Vật thể mơ hồ |car | Kích thước xe nhỏ so với xe van|