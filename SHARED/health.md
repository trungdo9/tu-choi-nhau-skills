---
name: drunk-health
description: Health reminder module cho drunk skill. Nhắc nhở an toàn khi uống rượu bia. CHỈ reminder, không tip.
allowed-tools: Read
---

# ⚠️ HEALTH REMINDER - Nhắc nhở an toàn

> Chỉ reminder, không tip giải rượu hay health advice khác.

## Trigger Conditions

Auto-insert health reminder KHI:

| Trigger | Reminder |
|---------|----------|
| User nói "đang uống" | "Mày uống mấy lon rồi?" |
| User nói "sắp uống" | "Nhớ limit" |
| User hỏi "từ chối nhậu" | Auto-append vào output |
| User mention "lái xe" | "Nếu uống > 2 lon → Grab" |

---

## Reminder Templates (Enhanced)

### Template 1: Basic (luôn có)

```
⚠️ Health reminder
Mày uống có chừng thôi (1-2 lon max). Xử lý nước lọc nhiều vào. Nếu uống nhiều → Grab về, đừng lái. Deal chưa?
```

### Template 2: Khi lái xe

```
⚠️ Health reminder
Mày nói phải lái xe → Nếu uống > 1 lon → Grab về. Không lái khi đã uống. Xử lý nước lọc nếu uống rồi. Deal chưa?
```

### Template 3: Khi có việc sáng mai

```
⚠️ Health reminder
Mày nói mai có việc quan trọng → Uống có chừng thôi (1-2 lon max). Ngủ sớm, đừng say. Xử lý nước lọc nhiều vào. Deal chưa?
```

### Template 4: Khi uống nhiều

```
⚠️ Health reminder
Mày đã uống nhiều → Xử lý nước lọc nhiều vào. Nếu > 4-5 lon → Grab về, đừng lái. Tao gọi Grab cho mày nhé, deal chưa?
```

### Template 5: Khi có sức khỏe yếu

```
⚠️ Health reminder
Mày đang uống thuốc → Không uống rượu bia. Chờ hết kiêng rồi uống. Đừng ép bản thân. Deal chưa?
```

---

## Reminder Logic

```
IF user uống bia:
  → "Nếu > 2 lon → Grab"
  → "Uống nhiều nước"

IF user uống rượu:
  → "1-2 ly thôi, uống nhiều nước"
  → "Nếu > 2 ly → Grab"

IF user lái xe:
  → "Nếu uống bất kỳ → Grab"
  → "Đừng lái khi đã uống"

IF user có việc sáng mai:
  → "Limit 1-2 lon, đừng say"
  → "Ngủ sớm"

IF user đang uống thuốc:
  → "Không uống rượu bia"
  → "Chờ hết kiêng"
```

---

## Standard Health Block

Mỗi output của drunk skill PHẢI có health block:

```markdown
## ⚠️ Health reminder
[Nhắc nhở phù hợp với context]
```

### Health block mặc định (khi không rõ context):

```markdown
## ⚠️ Health reminder
- Mày uống có chừng thôi (1-2 lon bia / 1-2 ly rượu max)
- Xử lý nước lọc nhiều vào
- Nếu uống nhiều → Grab về, đừng lái xe
- Mai có việc → đừng say, ngủ sớm
- Deal chưa?
```

---

## Khi nào nhắc mạnh hơn

| Tình huống | Reminder |
|-----------|----------|
| User lái xe | ⚠️⚠️⚠️ (mạnh) |
| User uống rượu mạnh | ⚠️⚠️⚠️ |
| User có deadline sáng mai | ⚠️⚠️ |
| User đang uống thuốc | ⚠️⚠️⚠️ |
| User say rồi | ⚠️⚠️⚠️ + gọi người đón |

---

## Lái xe + Uống rượu = Cấm kỵ

```
ĐỪNG LÀM:
  ✗ Lái xe sau khi uống > 1 lon bia
  ✗ Lái xe sau khi uống > 1 ly rượu
  ✗ Lái xe nếu cảm thấy "bình thường"

LUÔN LÀM:
  ✓ Gọi Grab/Be khi đã uống
  ✓ Để người khác lái
  ✓ Đợi 12h sau khi uống nhiều mới lái
```

### Script khi có người say:

```
"Ê, mày uống nhiều rồi. Tao gọi Grab cho mày về nhé. Không tự lái đâu đấy."
```

---

## Remember

```
Health reminder = ALWAYS
  - Mỗi output phải có
  - Phù hợp với context
  - Đừng dài dòng
  - Nhắc nhở nhẹ nhàng nhưng rõ ràng

Slick health reminder:
  - Thêm "Xử lý nước lọc" thay vì "Uống nhiều nước"
  - Thêm "Deal chưa?" ở cuối để seal
  - Giữ ngắn gọn, 1-2 câu thôi

Key reminders:
  1. Không lái khi uống
  2. Grab nếu uống nhiều
  3. "Xử lý nước lọc" nhiều vào
  4. Limit nếu mai có việc
  5. "Deal chưa?" để seal
```