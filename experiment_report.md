# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-XXXX
**Name:** (Dien ten cua ban)
**Date:** (Dien ngay thuc hien)

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) |Based on my data, the best choice is Laptop at $1200.  |9 |Đúng sản phẩm electronics, giá hợp lý |
| Garbage Data (`garbage_data.csv`) | Based on my data, the best choice is Nuclear Reactor at $999999.|3 |Chọn outlier cực đoan, không phải "best deal" thực sự |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Garbage data chứa nhiều vấn đề nghiêm trọng ảnh hưởng đến kết quả Agent:

1. **Duplicate ID (ID=1 xuất hiện 2 lần)**: Laptop và Banana cùng ID=1, gây nhầm lẫn khi Agent đánh giá.

2. **Wrong Data Type (price='ten dollars')**: Giá trị string thay vì số, nếu không có try-except thì sẽ crash.

3. **Extreme Outlier ($999,999)**: Nuclear Reactor có giá bất thường, Agent không detect được đây là outlier và chọn nó làm "best deal".

4. **Null Values (ID=None, category=None)**: Dòng "Ghost Item" có giá trị NULL, Agent xử lý thiếu chính xác.

Kết luận: Không có Data Validation, Agent vẫn "hoạt động" nhưng đưa ra quyết định SAI.

| Vấn đề | Trong garbage_data.csv | Ảnh hưởng |
|--------|------------------------|-----------|
| Duplicate ID | ID=1 (Laptop + Banana) | Data không unique |
| Wrong Type | `ten dollars` (string) | Crash nếu không có error handling |
| Outlier | $999,999 (Nuclear Reactor) | Agent chọn sai |
| Null | ID=None, category=None | Missing data |

---

## 3. Ket luan

**Quality Data > Quality Prompt?** (Dong y hay khong? Giai thich ngan gon.)

(Viet ket luan cua ban o day)

**Đồng ý.** Dù prompt có tốt đến đâu (cùng một prompt cho cả 2 test), Agent vẫn đưa ra kết quả hoàn toàn khác nhau:
- Với Clean Data → Trả lời đúng (Laptop $1200)
- Với Garbage Data → Trả lời sai (Nuclear Reactor $999,999)

**Kết luận**: "Garbage in, garbage out" — AI Agent chỉ tốt khi dữ liệu đầu vào được validate và làm sạch. Data Quality là nền tảng, Prompt Engineering chỉ là lớp trang trí bên trên.

