---
name: tu-choi-nhau-tiers
description: 3 tier system cho tu-choi-nhau skill - Beginner/Intermediate/Advanced. Hướng dẫn cách detect và route user vào tier phù hợp.
allowed-tools: Read, Glob, Grep
---

# 📊 TIER SYSTEM - 3 Cấp độ từ chối nhậu

## Tier Overview

| Tier | Độ khó | Trigger | Độ dài response | Khi nào dùng |
|------|--------|---------|-----------------|--------------|
| **BEGINNER** | ⭐ | Từ chối lần đầu | 2-4 câu | Bạn thường rủ, không ép |
| **INTERMEDIATE** | ⭐⭐ | Bị pressure thêm | 4-6 câu | "Uống thêm đi", "1 chai nữa thôi" |
| **ADVANCED** | ⭐⭐⭐ | Elder / Boss / Khó trả | 6-8 câu | Sếp mời, người lớn tuổi, event lớn |

---

## Tier Detection Algorithm

```
INPUT: user_message
OUTPUT: tier + response

1. Check for TIER KEYWORDS
   ├── "mới", "lần đầu", "beginner" → BEGINNER
   ├── "khó", "boss", "sếp", "elder", "advanced" → ADVANCED
   └── Default → INTERMEDIATE

2. Check RELATIONSHIP
   ├── Bạn thân thường xuyên → BEGINNER
   ├── Đồng nghiệp thân → INTERMEDIATE
   ├── Sếp / người lớn / event lớn → ADVANCED

3. Check PRESSURE LEVEL
   ├── "đi một lúc thôi" → BEGINNER
   ├── "không say không về" → INTERMEDIATE
   ├── "uống hết chai này đi" → ADVANCED

4. FINAL: User có thể override
   "Cho tao beginner" → BEGINNER
   "Advanced đi" → ADVANCED
```

---

## BEGINNER (⭐)

### Đặc điểm
- Từ chối đơn giản, 1 lần
- Lý do nhẹ nhàng
- Không cần giải thích dài
- Phù hợp: bạn thân rủ, không có áp lực

### Response template

```markdown
## 🎯 Tình huống
[Bạn thường trong công ty rủ nhậu]

## 📖 Script đọc lên
"Mày ơi, tối nay tao bận thật, tập gym xong rồi mà còn phải xử lý đống việc. Để lần sau tao đặt trước cho mày nha, deal không?"

## 📱 Text gửi
"Mấy ơi tối nay tao bận thật, đang xử lý deadline 😰 Để tuần sau tao đặt bàn trước cho mấy người nhé! Deal chưa?"

## ⚠️ Health reminder
Mày uống có chừng thôi (1-2 lon max). Xử lý nước lọc nhiều vào. Nếu uống nhiều → Grab về, đừng lái. Deal chưa?

## 💡 Khi nào nên đi?
Team có chuyện vui (lên chức, deal xong) → đi cho vui.
```

### Kho lý do BEGINNER

| Excuse | Detail-Rich Version | Dùng khi |
|--------|---------------------|----------|
| "Tối nay có việc bận" | "Tao đang xử lý deadline cuối tháng" |通用 |
| "Hôm nay mệt" | "Tao tập gym xong mệt quá" | Không muốn giải thích |
| "Tao vừa uống thuốc" | "Tao đang kiêng rượu theo lời bác sĩ" | Y tế |
| "Tối nay có hẹn rồi" | "Tao có hẹn với thằng A lâu rồi, không cancel được" | Đã có kế hoạch |
| "Có việc gia đình" | "Nhà tao có việc gấp, bố mẹ cần tao về" | Nghiêm túc |

### Đừng làm
- ❌ "Tao lười" → quá thật, không maintain được
- ❌ "Không thích uống" → defensive
- ❌ "Bọn mày uống đi" → cold

---

## INTERMEDIATE (⭐⭐)

### Đặc điểm
- Bị pressure thêm 1-2 lần sau khi từ chối lần đầu
- Cần giữ chân được 1 phần
- Không để "sẹo" với group
- Phù hợp: đồng nghiệp thân, bạn bè hay ép

### Response template

```markdown
## 🎯 Tình huống
"Bọn tao đang ngồi ăn, mày từ chối rồi nhưng thằng A nói 'đi 1 lon thôi'"

## 📖 Script đọc lên
"Thật là tối nay tao không được thật. Để lần sau tao xử lý 1 chai full với mày nha, deal chưa? Mày uống đi, tao ngồi chơi với, tiền tao chia."

## 📱 Text gửi
"Thật ra tối nay tao không uống được thật, nhưng tao ngồi chơi với mấy người. Lần sau tao đặt bàn trước cho mày nhé, deal chưa?"

## ⚠️ Health reminder
Mày uống có chừng thôi (1-2 lon max). Xử lý nước lọc nhiều vào. Nếu > 2 lon → Grab về, đừng lái. Deal chưa?

## 💡 Khi nào nên đi?
Deal lớn xong → celebrate với team. Đây là opportunity, đừng miss.
```

### Pressure Handling Script

| Pressure | Enhanced Response |
|----------|-------------------|
| "Đi 1 lon thôi mà" | "Tao thật sự không uống được thật. Để lần sau tao xử lý 1 chai full với mày nha, deal chưa? Mày uống đi, tao ngồi chơi với." |
| "Không say không về" | "Tao có deal sáng mai, không say được thật. Để tuần này tao sắp xếp rồi nhậu max với bọn mày. Lần này mày say đi, tao ngồi cạn chai với." |
| "Mày sợ gì vậy" | "Không phải sợ gì đâu mày ơi! Tao thật sự bận thật, đang xử lý deadline. Tao muốn đi lắm nhưng hôm nay không kịp. Tin tao đi, tuần này tao deal với mày, deal chưa?" |
| "Nể mày lắm mới mời" | "Tao biết mày nể tao, cảm ơn nhiều nha! Tao rất muốn đi lắm, nhưng hôm nay xử lý không kịp thật. Để tuần này tao đặt trước cho mày nha, mày chọn quán, deal chưa?" |

### Đừng làm
- ❌ Cãi nhau với thằng ép
- ❌ Tỏ thái độ "tao giỏi hơn"
- ❌ Imply "bọn mày làm quá"

---

## ADVANCED (⭐⭐⭐)

### Đặc điểm
- Đối phó người khó tính, cấp trên, elder
- Đọc được hierarchy trong bàn nhậu
- Emergency exit khi cần thiết
- Preserve quan hệ với người quan trọng

### Response template

```markdown
## 🎯 Tình huống
[Sếp mời uống rượu khi deal xong]

## 📖 Script đọc lên
"Tao cảm ơn mày, để tao nâng cốc với mày. Tao uống 1 ly thôi vì tối nay tao phải lái về. Lần sau tao xin phép đặt trước 1 chai riêng với mày nha."

## 📱 Text gửi
"Mày ơi tao không uống được nhiều vì tối nay phải lái xe. Để lần nào tao mời mày 1 chai riêng nha, deal chưa? Cảm ơn mày nhiều!"

## ⚠️ Health reminder
Mày uống có chừng thôi (1-2 ly max). Xử lý nước lọc nhiều vào. Nếu > 2 ly → Grab về, đừng lái. Deal chưa?

## 💡 Khi nào nên đi?
Sếp mời deal xong → đi. Đây là opportunity để build rapport với sếp.
```

### Hierarchy Reading

| Role | Cách tiếp cận |
|------|---------------|
| Sếp trực tiếp | Tôn trọng, uống 1 ly rồi xin phép về sớm |
| Khách hàng | Lịch sự, chiều ý nhưng giới hạn bản thân |
| Người lớn tuổi | Khiêm nhường, uống 1 ly, xin phép về |
| Bạn của bố mẹ | Cẩn thận, nói đã hỏi bố mẹ |

### Emergency Exit Techniques

| Kỹ thuật | Khi nào |
|----------|---------|
| **Lái xe** | "Tao phải lái về" → giải thích được |
| **Việc gia đình khẩn** | "Nhà tao gọi có việc gấp" → đi ngay |
| **Hẹn bác sĩ** | "Tao có hẹn bác sĩ lúc X giờ" → y tế |
| **Deadline công việc** | "Tao đang xử lý deadline gấp" → work |
| **Sickness** | "Tao đang chờ kết quả xét nghiệm" → nghiêm trọng |

### Damage Control

**Khi đã từ chối quá cứng:**
1. Hôm sau xin lỗi nhẹ: "Tối qua xin lỗi mày, tao có việc đột xuất thật. Để tuần này tao đặt trước cho mày nhé, deal chưa?"
2. Offer compensate: "Để tuần này tao mời mày"
3. Future commitment: "Lần sau tao nhất định ở lâu hơn"

**Khi bị elders khó tính:**
1. Acknowledgement: "Tao hiểu, tao biết ơn mày"
2. Explanation: ngắn gọn, đừng dài dòng
3. Future commitment: "Để tao sắp xếp lại rồi đi với mày"

---

## Tier Escalation

```
BEGINNER
  │
  ├─ User bị ép lần 2 → tự động upgrade INTERMEDIATE
  │
  └─ User mention "sếp", "elder" → tự động ADVANCED

INTERMEDIATE
  │
  ├─ Pressure tăng → cung cấp stronger responses
  │
  └─ User mention "boss", "khách" → upgrade ADVANCED

ADVANCED
  │
  └─ Cung cấp full toolkit: hierarchy + exit + damage control
```

---

## Remember

| Tier | Goal | Key |
|------|------|-----|
| BEGINNER | Từ chối nhẹ nhàng | Đừng làm mất mặt |
| INTERMEDIATE | Giữ chân được 1 phần | Đừng để "sẹo" |
| ADVANCED | Tôn trọng + survive | Đọc room trước |

**Cuối cùng:** Mục tiêu là mày có mặt mũi, không say, và vẫn giữ được quan hệ.