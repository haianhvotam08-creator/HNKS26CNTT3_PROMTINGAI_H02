# BÀI LÀM PHA 2 – HACKATHON 02

- **Mã đề:** 08
- **Họ tên:** Nguyễn Hải Anh
- **Lớp:** CNTT3
- **Link repository Pha2:** https://github.com/haianhvotam08-creator/HNKS26CNTT3_PROMTINGAI_H02
- **Công cụ AI đã dùng (ChatGPT/Claude/Gemini):** Gemini

> Pha 2 (20 phút cuối). Mỗi mục: mở cuộc trò chuyện mới, gửi nguyên văn prompt đã viết trong bai_lam_pha1.md, dán câu trả lời và link chia sẻ vào đây. Xong, kéo thả file này vào repository Pha2.

## 4.2. Trích xuất tin nhắn đặt lịch khám ra JSON

**KET QUA AI**

```text
[
{
"ma_dich_vu": "TRAM",
"ngay_hen": "2026-12-17",
"nguoi_lon": 2,
"tre_em": 1,
"khung_gio": "chieu",
"ghi_chu": null
},
{
"ma_dich_vu": "CAOVOI",
"ngay_hen": "2027-01-06",
"nguoi_lon": 3,
"tre_em": 0,
"khung_gio": null,
"ghi_chu": "1 người bị tiểu đường"
},
{
"ma_dich_vu": "TAYTRANG",
"ngay_hen": null,
"nguoi_lon": 4,
"tre_em": 0,
"khung_gio": "sang",
"ghi_chu": "1 người dị ứng thuốc tê"
}
]
```

**Link trò chuyện:**https://share.gemini.google/0OoaRbn1Y2lY

## 4.3. Báo giá bằng Chain-of-Thought

**KET QUA AI**

```text
Chào bạn, tôi sẽ lập bảng tính chi tiết cho yêu cầu báo giá dịch vụ **CAOVOI** (Khám và cạo vôi răng, đơn giá người lớn: 350.000 đồng) theo đúng từng bước:

* **Tiền người lớn:** Có 6 người lớn làm dịch vụ CAOVOI.

$$6 \times 350.000 = 2.100.000 \text{ đồng}$$


* **Tiền trẻ em:** Có 2 trẻ trong độ tuổi từ 6 đến 12 (7 tuổi và 11 tuổi) tính 80% giá người lớn, và 1 bé 4 tuổi (dưới 6 tuổi) được miễn phí.

$$2 \times (350.000 \times 80\%) + 1 \times 0 = 2 \times 280.000 + 0 = 560.000 \text{ đồng}$$


* **Tiền dịch vụ:** Cộng tiền người lớn và tiền trẻ em.

$$2.100.000 + 560.000 = 2.660.000 \text{ đồng}$$


* **Giảm giá nhóm:** Nhóm có 6 người lớn (từ 5 người lớn trở lên) nên được giảm 10% trên tiền dịch vụ.

$$2.660.000 \times 10\% = 266.000 \text{ đồng}$$



*(Tiền dịch vụ sau giảm: $2.660.000 - 266.000 = 2.394.000 \text{ đồng}$)*
* **Phí X-quang:** 3 người chụp X-quang, mỗi người 1 phim (tổng 3 phim), đơn giá 150.000 đồng/phim, không giảm giá.

$$3 \times 150.000 = 450.000 \text{ đồng}$$


* **Tổng tiền:** Tiền dịch vụ sau giảm cộng phí chụp X-quang.

$$2.394.000 + 450.000 = 2.844.000 \text{ đồng}$$



[RESULT: 2.844.000 đồng]
```

**Link trò chuyện:**https://share.gemini.google/CMtMJp5mcWFT

### b) Kiểm tra kết quả AI

ĐÚNG

## 4.4. Dây chuyền xử lý khiếu nại – kết quả Trạm 1

**KET QUA AI**

```text
```json
{
  "loai_su_co": "tre_hen",
  "so_khach": 3,
  "so_lan_hen_bi_tre": 2,
  "tom_tat": "Gia đình 3 người bị trễ hẹn 2 lần quá 1 tiếng tại phòng khám."
}

```
```

**Link trò chuyện:**https://share.gemini.google/0aL0jTNvxu7o

## 4.5. Prompt chấm bài theo Rubric

**KET QUA AI**

```text
| Tiêu chí | Điểm | Minh chứng | Đề xuất sửa |
| --- | --- | --- | --- |
| Đúng thông tin (50%) | 0/5 | Không có thông tin chuẩn để đối chiếu chính xác giá và chính sách bảo hành; ngoài ra nội dung cam kết miệng ("Bong sau 8 tháng thì em làm lại free cho anh nha") thiếu cơ sở quy định rõ ràng. | Đối chiếu với bảng giá và chính sách bảo hành chính thức của phòng khám; nêu rõ điều kiện áp dụng bảo hành thay vì hứa miệng chung chung. |
| Đầy đủ (30%) | 0/3 | Chưa trả lời đủ cả hai câu hỏi của khách hàng (do thiếu dữ liệu câu hỏi gốc) và chưa mời khách cung cấp ngày hẹn, khung giờ để đặt lịch. | Bổ sung đầy đủ câu trả lời cho từng câu hỏi của khách và thêm lời mời: "Anh/chị vui lòng cho biết ngày và khung giờ mong muốn để bên em hỗ trợ đặt lịch hẹn ạ." |
| Giọng điệu (20%) | 0.5/2 | Câu bị lỗi: *"Trám răng bên em 450k/răng thôi, đẹp như răng thật luôn. Bong sau 8 tháng thì em làm lại free cho anh nha. Cần gì cứ inbox em ạ!"*<br>

<br>Lý do sai: Dùng nhiều từ ngữ suồng sã, thiếu tính chuyên nghiệp trong tư vấn dịch vụ ("bên em", "450k", "luôn", "free", "nha", "inbox").<br>

<br>Câu sửa đề xuất: *"Chi phí trám răng tại phòng khám là 450.000 VNĐ/răng, đảm bảo tính thẩm mỹ tự nhiên và được bảo hành 8 tháng theo quy định. Nếu anh/chị cần hỗ trợ thêm hoặc muốn đặt lịch, vui lòng nhắn tin để đội ngũ tư vấn hỗ trợ."* | *"Dạ chào anh/chị! Chi phí trám răng tại phòng khám là 450.000 VNĐ/răng, đảm bảo thẩm mỹ tự nhiên và áp dụng chính sách bảo hành 8 tháng theo quy định. Anh/chị cho em xin ngày và khung giờ thuận tiện để đặt lịch nhé. Nếu cần thêm thông tin, anh/chị cứ nhắn cho bên em ạ."* |
| **Tổng điểm** | **0.5 / 10** | — | — |
```

**Link trò chuyện:**https://share.gemini.google/lHvMy8WSAumU
