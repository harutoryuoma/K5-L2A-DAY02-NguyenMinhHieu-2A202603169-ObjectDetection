# Báo cáo cá nhân — Ngày 2 Object Detection

Đổi tên file theo `MSSV_HoTen.md`, ví dụ `20241234_NguyenVanAn.md`. Điền kết quả thật, xóa dòng hướng dẫn khi nộp. Xem [quy định nộp](../../SUBMISSION.md).

## 1. Thông tin học viên

- Họ tên:Nguyễn Minh Hiếu   
- MSSV: AI202603169
- Email:harutoryuoma@gmail.com
- Lớp:2A
- Link repo bài làm: https://github.com/harutoryuoma/K5-L2A-DAY02-NguyenMinhHieu-2A202603169-ObjectDetection.git
- Link Colab đã chạy: https://colab.research.google.com/github/harutoryuoma/K5-L2B-DAY02-NguyenMinhHieu-2A202603169-ObjectDetection/blob/main/notebooks/day2_annotation_to_yolo.ipynb
## 2. Schema và mini guideline

Dẫn tới [GUIDELINE_MINI.md](../../GUIDELINE_MINI.md). Tóm tắt ba ca mơ hồ đã quyết định, cách áp dụng schema và phần cần giảng viên làm rõ.

## 3. Annotation và self-QC

- Số file nhãn train: 50
- Kết quả checker và lỗi đã xử lý: 
- Danh sách ít nhất 10 ảnh đã rà bằng mắt: từ ảnh 1 đến 50
- Lỗi bỏ sót/box/class phát hiện khi rà và cách sửa: 
- Commit khóa nhãn ban đầu:

## 4. Gold QC và rework

| Chỉ số | Trước sửa | Sau sửa nếu có |
|---|---:|---:|
| TP |420 | |
| FP | 559| |
| FN | 233| |
| Precision |0.4290 | |
| Recall |0.6432 | |
| F1 | 0.5147| |
| mean_iou_of_matches | 0.8186| |
| passed | false| |

Dẫn tới `outputs/annotation_evaluation.json` trong repo. Nếu rework, ghi ảnh, lỗi đã kiểm, quyết định sửa/giữ và lý do. Không suy nguyên nhân chỉ từ FP/FN. Không có rework thì ghi rõ.

## 5. Kết quả YOLO

- Runtime, GPU/CPU, phiên bản Ultralytics và Torch:
- Các tham số thay đổi so với notebook nếu có và lý do:
- Đường dẫn best checkpoint trong phiên chạy: runs/detect/train/weights/best.pt

| Chỉ số trên 10 ảnh eval | Giá trị |
|---|---:|
| Precision |0.2195 (21.95%) |
| Recall |0.3856 (38.56%) |
| mAP50 |0.3611 (36.11%) |
| mAP50–95 |0.2156 (21.56%) |

Đặt cả 2 folder `assets/eval_predictions/` và `assets/yolo26_runs/` (giải nén từ `day2_colab_outputs.zip`) cạnh báo cáo và dẫn link tương đối. Không chỉ ghi số; chỉ ra ít nhất một ảnh và vật thể cụ thể.

Trả lời bốn câu hỏi cuối notebook:

1. Lớp nào recall thấp nhất? Ảnh nào minh họa?

Lớp bus recall thấp nhất
Ảnh ở địa chỉ này minh họa điều đó K5-L2B-DAY02-NguyenMinhHieu-2A202603169-ObjectDetection\report\individual\assets\eval_predictions\visuals\drive_58

2. Nếu mAP50 cao nhưng mAP50–95 thấp, cần kiểm điều gì trên box?

Điều này thường cho thấy model phát hiện đúng đối tượng nhưng độ chính xác định vị Bounding Box chưa tốt.

Một số vấn đề có thể gặp:
- Box quá rộng, chứa nhiều nền xung quanh.
- Box chưa ôm sát biên xe.
- Box bị lệch so với vị trí thực tế.
- Box không tuân thủ quy tắc chỉ bao phần vật thể nhìn thấy.

Kết luận: Model nhận diện được xe nhưng khả năng định vị chính xác Bounding Box còn hạn chế.

3. Lỗi class nào có thể liên quan guideline? Dữ kiện nào hỗ trợ nhận xét?
- Chủ yếu là gán nhầm 2 class van và car do hình dáng đôi khi giống nhau hoặc ảnh bị khuất, mờ,không rõ
- Bounding Box không ôm sát phần xe nhìn thấy

4. Vì sao không dùng 10 ảnh eval để train? Vai trò validation của chúng trong notebook là gì?

- Nếu đưa 10 ảnh eval vào train, model đã được học từ những ảnh dùng để đánh giá. Kết quả đánh giá không còn phản ánh chính xác khả năng phát hiện trên dữ liệu chưa từng gặp.
- Mục tiêu là kiểm tra xem model có nhận diện tốt những chiếc xe trong ảnh mới hay không, thay vì chỉ ghi nhớ những ảnh đã học.
- Giữ nguyên 10 ảnh eval giúp so sánh các phiên bản model một cách công bằng.
## 6. Khó khăn và cách xử lý

| Bước/thời điểm | Lỗi quan sát | Cách đã thử | Kết quả/còn thiếu |
|---|---|---|---|
| | | | |

## 7. Tự đánh giá theo rubric

Đối chiếu [RUBRIC.md](../../RUBRIC.md): phần nào đã có kết quả, phần nào còn thiếu hoặc chưa kiểm được. Không tự nhận hoàn thành bước chưa chạy.
Chưa tổng hợp khó khăn và cách xử lý

## 8. Công cụ AI và tài liệu tham khảo

Ghi công cụ đã dùng, dùng ở bước nào và phần đã tự kiểm tra; không dùng thì ghi rõ. Liệt kê nguồn ngoài repo được sử dụng. Không ghi mật khẩu/token hoặc đính kèm gold train.
SỬ dụng chatgpt cho GUIDELINE_MINI.md và report cuối cùng