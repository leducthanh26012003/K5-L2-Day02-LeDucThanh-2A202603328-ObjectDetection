# Báo cáo cá nhân — Ngày 2 Object Detection

Đổi tên file theo `MSSV_HoTen.md`, ví dụ `20241234_NguyenVanAn.md`. Điền kết quả thật, xóa dòng hướng dẫn khi nộp. Xem [quy định nộp](../../SUBMISSION.md).

## 1. Thông tin học viên

- Họ tên:Lê Đức Thanh
- MSSV:2A202603328
- Email:leducthanh26012003@gmail.com
- Lớp:E403
- Link repo bài làm:`https://github.com/leducthanh26012003/K5-L2-Day02-LeDucThanh-2A202603328-ObjectDetection`
- Link Colab đã chạy:`https://colab.research.google.com/drive/1D2c933yZ7tBugZp9GrMxp6UIhHhkX5w_#scrollTo=3e0508d8`

## 2. Schema và mini guideline

Dẫn tới [GUIDELINE_MINI.md](../../GUIDELINE_MINI.md).
Schema 4 lớp: car=0, truck=1, bus=2, van=3. Phân biệt chính theo kích thước và hình dáng: truck có thùng hàng phía sau; bus là xe hình hộp rất dài, nhiều cửa kính; van là xe hình hộp, đầu xe ngắn hoặc gần như không có mũi; car nhỏ hơn và có mũi xe nhô ra.

Quy tắc box: box ôm sát phần thân xe nhìn thấy; xe bị cắt ở rìa ảnh thì box tới rìa ảnh; không box khi xe bị che hoặc bị cắt quá 60%, hoặc không nhận diện được lớp.

3 ca mơ hồ tiêu biểu:
| `drive_024` | Vật thể bị cắt bởi rìa ảnh|car | phần đuôi xe chéo nên không phải hình hộp|
| `drive_031` | Vật thể bị cắt bời rìa ảnh 'car 483' |car | Phần mũi xe quá dài|
| `drive_041` | Vật thể bị cắt bởi rìa ảnh'car 593' |car | Phần thân xe và 1 phần kính của đầu xe chiếm diện tích quá ít nên kích thước xe nhỏ so với xe van|

## 3. Annotation và self-QC

- Số file nhãn train:50; 704 box
- Kết quả checker và lỗi đã xử lý:`check_yolo_labels.py` báo "ĐẠT cấu trúc: 50/50 file nhãn hợp lệ" cho cả bản khóa và bản rework.
- Danh sách ít nhất 10 ảnh đã rà bằng mắt:drive_001, drive_002, drive_003, drive_004, drive_005, drive_006, drive_007, drive_008, drive_009, drive_010
- Lỗi bỏ sót/box/class phát hiện khi rà và cách sửa: box thiếu cách sửa bổ sung lại
- Commit khóa nhãn ban đầu:`f3984ec`

## 4. Gold QC và rework

| Chỉ số | Trước sửa | Sau sửa nếu có |
|---|---:|---:|
| TP |328|391|
| FP |233|313|
| FN |325|262|
| Precision |0.5847|0.5554|
| Recall |0.5023|0.5988|
| F1 |0.5404|0.5763|
| mean_iou_of_matches |0.872|0.8636|
| passed |false|false|

Dẫn tới `outputs/annotation_evaluation.json` trong repo. Nếu rework, ghi ảnh, lỗi đã kiểm, quyết định sửa/giữ và lý do. Không suy nguyên nhân chỉ từ FP/FN. Không có rework thì ghi rõ.

## 5. Kết quả YOLO

- Runtime, GPU/CPU, phiên bản Ultralytics và Torch:Python 3, GPU T4, 2026.10
- Các tham số thay đổi so với notebook nếu có và lý do:
- Đường dẫn best checkpoint trong phiên chạy:`/content/Day2-Lab/outputs/yolo26_runs/vehicle_annotation/weights/best.pt`

| Chỉ số trên 10 ảnh eval | Giá trị |
|---|---:|
| Precision |0.4091|
| Recall |0.2339|
| mAP50 |0.2707|
| mAP50–95 |0.1996|

Đặt cả 2 folder `assets/eval_predictions/` và `assets/yolo26_runs/` (giải nén từ `day2_colab_outputs.zip`) cạnh báo cáo và dẫn link tương đối. Không chỉ ghi số; chỉ ra ít nhất một ảnh và vật thể cụ thể.

Trả lời bốn câu hỏi cuối notebook:

1. van .drive_053 `bus nhưng lại gán thành van`
2. Xe nhỏ ở xa; xe bị che hoặc bị cắt ở rìa ảnh; mép box trong nhãn train có nhất quán không.
3. van thật bị đoán thành car. “đầu xe ngắn”, “lớn hơn car”
4. Nếu đem chúng vào train, model được chấm trên chính những ảnh nó đã học, nên con số sẽ đẹp giả tạo và không còn phản ánh khả năng trên ảnh mới.

## 6. Khó khăn và cách xử lý

| Bước/thời điểm | Lỗi quan sát | Cách đã thử | Kết quả/còn thiếu |
|---|---|---|---|
| | | | |

## 7. Tự đánh giá theo rubric

Đối chiếu [RUBRIC.md](../../RUBRIC.md): phần nào đã có kết quả, phần nào còn thiếu hoặc chưa kiểm được. Không tự nhận hoàn thành bước chưa chạy.
- bao phủ tốt, box rất sát và class nhất quán

## 8. Công cụ AI và tài liệu tham khảo

Ghi công cụ đã dùng, dùng ở bước nào và phần đã tự kiểm tra; không dùng thì ghi rõ. Liệt kê nguồn ngoài repo được sử dụng. Không ghi mật khẩu/token hoặc đính kèm gold train.
