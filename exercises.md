# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> *Câu trả lời của bạn*
> Khi temperature thấp thì phản hồi ổn định và trực tiếp hơn. Khi tăng lên 0.5 và 1.0, câu trả lời đa dạng hơn về cách diễn đạt. Còn đối với mức 1.5, phản hồi cực kì sáng tạo nhưng dễ lan man, dễ lạc đề hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> *Câu trả lời của bạn*
> Tôi sẽ đặt khoảng 0.2 đến 0.4 để chatbot trả lời nhất quán, đúng chính sách và giảm rủi ro bịa đặt thông tin. Ở mức này, tôi thấy câu trả lời của chatbot vẫn rất linh hoạt, tự nhiên, nhưng không quá sáng tạo, bịa đặt.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> *Câu trả lời của bạn*
> Như ở trong file template.py, giá của gpt-4o cho 1000 token là $0.01, còn của gpt-4o-mini là $0.0006. Lượng workload là như nhau cho cả 2 model. Vì vậy, GPT-4o đắt hơn $0.010 / $0.0006 = 16.67 lần. 

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> *Câu trả lời của bạn*
> GPT-4o xứng đáng khi bài toán cần độ chính xác và suy luận cao, ví dụ như khi hỗ trợ phân tích hợp đồng hoặc tư vấn nghiệp vụ quan trọng. GPT-4o-mini phù hợp cho tác vụ khối lượng lớn, yêu cầu phản hồi nhanh và chi phí thấp hơn như FAQ nội bộ, phân loại ticket cơ bản hoặc tóm tắt ngắn.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> *Câu trả lời của bạn*
> Streaming quan trọng nhất khi người dùng cần cảm giác phản hồi tức thì và câu trả lời có thể dài, ví dụ chatbot tư vấn, coding assistant hoặc hỗ trợ chăm sóc khách hàng theo thời gian thực, vì nó giảm cảm giác chờ đợi và tăng mức độ tin cậy. Ngược lại, non-streaming phù hợp hơn khi ứng dụng cần xử lý trọn vẹn kết quả trước khi hiển thị, ví dụ như việc kiểm duyệt nội dung hay pipeline cần kết quả đầy đủ để lưu log. Với những việc này, 1 output đầy đủ quan trọng hơnviệc hiển thị từng phần.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
