---
name: tu-choi-nhau-advanced
description: Cấp độ ADVANCED - xử lý sếp, người lớn tuổi, khách hàng. Đọc hierarchy, emergency exit, damage control.
allowed-tools: Read
parent: tu-choi-nhau
---

# 🍺 ADVANCED - Xử lý người khó / cấp trên / elder

> Khó nhất. Đối phó sếp, người lớn tuổi, khách hàng. Đọc room trước, survive + preserve relationship.

## When to use

| Signal | Tình huống |
|--------|-----------|
| "Sếp mời" | Cấp trên rủ uống rượu |
| "Người lớn tuổi" | Bác, chú, cậu trong gia đình |
| "Khách hàng" | Đi ăn với khách, phải chiều |
| "Uống hết chai này" | Bị ép nặng |
| "Có cấp trên trong bàn" | AI detect hierarchy |

## ⚠️ Trước khi respond

**BẮT BUỘC check 3 câu:**

1. **Ai là "boss" trong bàn?** (sếp / người lớn tuổi / khách)
2. **Mối quan hệ của mày với boss?** (trực tiếp / gián tiếp)
3. **Stakes cao không?** (deal / lên chức / relationship dài hạn)

→ Nếu stakes cao → đọc kỹ ADVANCED hoàn toàn
→ Nếu không sure → default sang "survive" mode

---

## Output Format

Luôn trả về 6 phần:

```markdown
## 🎯 Tình huống
[Context + ai là boss]

## 📖 Script đọc lên
[2-4 câu, formal hơn BEGINNER/INTERMEDIATE]

## 📱 Text gửi
[Copy-paste được]

## ⚖️ Hierarchy reading
[Who is boss + cách tiếp cận]

## ⚠️ Health reminder
[Nhắc nhở]

## 📌 Damage control (sau đó)
[Nếu từ chối quá cứng]
```

---

## Hierarchy Reading

Trước khi respond, đọc room:

```
BÀN NHẬU = SOCIAL HIERARCHY

Ai có quyền lực nhất?
├── Sếp trực tiếp → Ưu tiên tuyệt đối
├── Khách hàng → Ưu tiên thứ 2
├── Người lớn tuổi (bác, chú) → Ưu tiên thứ 3
└── Đồng nghiệp cùng cấp → Như INTERMEDIATE

Mày ở đâu trong hierarchy?
├── Intern/Junior → Low power
├── Senior/Lead → Medium power
├── Manager → High power
└── Guest → Low power (khách)
```

### Cách tiếp cận theo role

| Role | Cách tiếp | Script tone |
|------|-----------|-------------|
| Sếp trực tiếp | Tôn trọng, uống 1 ly, xin phép | "Dạ em..." |
| Khách hàng | Lịch sự, chiều ý, giới hạn | "Em/Cong" |
| Người lớn tuổi | Khiêm nhường, "dạ vâng" | "Dạ" |
| Bạn bố mẹ | Cẩn thận, đã hỏi bố mẹ | "Dạ con..." |

---

## ADVANCED Template A: Sếp mời

**Tình huống:** Sếp mời uống rượu sau khi deal xong

**Script:**
```
Dạ, em cảm ơn anh/chị. Em uống 1 ly thôi ạ vì tối nay em phải lái xe về. Lần sau em xin phép uống nhiều hơn ạ.
```

**Text:**
```
Dạ em cảm ơn anh/chị ạ. Tối nay em phải lái xe nên em uống 1 ly thôi ạ. Lần sau em mời anh/chị ạ.
```

**Key:**
- "Dạ" = respect
- "1 ly" = survive
- "Lần sau" = promise
- Không nói "không được"

---

## ADVANCED Template B: Người lớn tuổi

**Tình huống:** Bác trong gia đình mời uống rượu

**Script:**
```
Dạ con cảm ơn bác. Con uống 1 ly thôi ạ, vì tối nay con phải về sớm. Lần nào về con uống nhiều hơn ạ.
```

**Text:**
```
Dạ con cảm ơn bác ạ. Con uống 1 ly thôi ạ vì tối nay phải về sớm. Lần sau về con uống nhiều hơn ạ.
```

**Key:**
- "Dạ con" = khiêm nhường
- Không từ chối thẳng
- "Lần sau" = show muốn uống với bác

---

## ADVANCED Template C: Khách hàng

**Tình huống:** Đi ăn với khách, khách mời uống

**Script:**
```
Em uống 1 ly với anh/chị ạ. Em limit tối nay vì có việc sáng mai. Anh/chị uống thoải mái ạ, em phục vụ.
```

**Text:**
```
Dạ em uống 1 ly cùng anh/chị ạ. Tối nay em limit vì mai có việc. Anh/chị thoải mái nhé ạ.
```

**Key:**
- "Em phục vụ" = humble
- 1 ly = survive
- Khách thoải mái = mục tiêu

---

## ADVANCED Template D: Bị ép "hết chai"

**Tình huống:** Ai đó nói "uống hết chai này đi" (boss/elder)

**Script:**
```
Dạ, em uống ạ. (Uống 1 ly thôi) Nhưng em phải lái về sớm, em nhờ anh/chị nhiều rồi ạ.
```

**Text:**
```
Dạ em uống ạ. Nhưng em phải lái về nên em uống ít thôi ạ. Anh/chị thông cảm ạ.
```

**Key:**
- Không refused trực tiếp
- Uống 1 ly = comply
- "Phải lái" = reason
- Không cãi

---

## Emergency Exit (thoát khẩn cấp)

Khi mày thật sự không ở được:

| Kỹ thuật | Script | Độ trust |
|----------|--------|----------|
| **Lái xe** | "Dạ em phải lái về ạ, em vào sớm" | ⭐⭐⭐ |
| **Việc gia đình khẩn** | "Dạ nhà em gọi có chuyện ạ, em phải về" | ⭐⭐⭐ |
| **Hẹn bác sĩ** | "Dạ em có hẹn bác sĩ lúc X giờ ạ" | ⭐⭐⭐ |
| **Deadline công việc** | "Dạ em có deadline lúc Y, em phải về sớm" | ⭐⭐ |
| **Người yêu/bạn gái khẩn** | "Dạ em được gọi có chuyện, em phải đi" | ⭐⭐ |

### Script cho Emergency Exit

**Tình huống:** Mày cần đi ngay, không thể ở tiếp

**Script:**
```
Dạ em xin lỗi, em có việc đột xuất phải đi ngay. Em cảm ơn anh/chị đã mời, lần sau em nhất định đi ạ.
```

**Text:**
```
Dạ em xin lỗi có việc đột xuất phải đi ngay ạ 😔 Cảm ơn anh/chị đã mời, lần sau em xin phép ạ.
```

### Khi nào dùng Emergency Exit
- Mày thật sự không ở được
- Không có cách từ chối nhẹ
- Stakes cao nhưng mày phải đi

---

## Damage Control (sửa chữa sau khi từ chối)

**Khi mày đã từ chối quá cứng hoặc emergency exit:**

### Step 1: Acknowledge (trong 24h)

**Text:**
```
Anh/chị ơi, em xin lỗi tối qua đi sớm ạ. Em có việc đột xuất thật. Lần sau em nhất định ở lâu hơn ạ.
```

### Step 2: Offer compensate (trong tuần)

**Text:**
```
Anh/chị ơi, để tuần này em mời anh/chị ăn uống nhé. Lần trước不好意思 ạ.
```

### Step 3: Future commitment

**Text:**
```
Tuần sau/Tháng sau em đi nhậu với anh/chị nhé. Em hứa đấy ạ.
```

### Đừng làm (Damage Control)
- ❌ Giải thích quá nhiều
- ❌ Nói xấu người khác
- ❌ Tỏ ra không quan tâm
- ❌ Đổ lỗi cho người khác

---

## Khi nào STAY ở ADVANCED

Check nếu:

- [ ] Sếp trong bàn
- [ ] Người lớn tuổi
- [ ] Khách hàng
- [ ] Ai đó "test" mày
- [ ] Bị ép "hết chai"

→ STAY ở ADVANCED, dùng full toolkit

---

## Real Examples

### Example 1: Sếp mời rượu

**Input:** "Sếp A mời tao uống rượu khi deal xong"

**Output:**

```
## 🎯 Tình huống
Sếp trực tiếp mời uống rượu sau deal

## 📖 Script đọc lên
"Dạ em cảm ơn anh A, để em nâng cốc với anh. Em uống 1 ly thôi ạ vì tối nay em phải lái về. Lần sau em xin phép uống nhiều hơn ạ."

## 📱 Text gửi
(Đang ngồi trực tiếp thì nói, không cần text)

## ⚖️ Hierarchy Reading
Sếp A = boss trực tiếp. Đây là opportunity để build rapport. Mày phải uống ít nhất 1 ly.

## ⚠️ Health reminder
Rượu mạnh → 1 ly thôi, uống nhiều nước. Nếu > 2 ly → gọi Grab.

## 📌 Damage control
Nếu say → hôm sau xin lỗi: "Em xin lỗi anh A, tối qua em say nên đi sớm..."
```

### Example 2: Người lớn tuổi trong gia đình

**Input:** "Bác ở quê lên chơi, mời tao uống rượu"

**Output:**

```
## 🎯 Tình huống
Người lớn tuổi trong gia đình mời uống

## 📖 Script đọc lên
"Dạ con cảm ơn bác. Con uống 1 ly thôi ạ vì tối nay con phải về sớm. Lần nào về con uống nhiều hơn với bác ạ."

## 📱 Text gửi
(Đang ngồi ăn thì nói trực tiếp)

## ⚖️ Hierarchy Reading
Bác = người lớn tuổi trong gia đình. Respect tuyệt đối. Mày phải uống ít nhất 1 ly.

## ⚠️ Health reminder
Rượu quê thường mạnh → uống 1 ly, ăn nhiều.

## 📌 Damage control
Nếu từ chối quá cứng → gọi điện xin lỗi sau: "Con xin lỗi bác, tối qua con có việc nên đi sớm..."
```

### Example 3: Khách hàng quan trọng

**Input:** "Khách hàng lớn mời uống, mày cần deal với họ"

**Output:**

```
## 🎯 Tình huống
Khách hàng quan trọng mời uống - HIGH STAKES

## 📖 Script đọc lên
"Dạ em uống 1 ly với anh/chị ạ. Em limit tối nay vì mai có việc. Anh/chị uống thoải mái ạ, em phục vụ."

## 📱 Text gửi
(Đang ngồi thì nói, không cần text)

## ⚖️ Hierarchy Reading
Khách hàng = priority cao. Mục tiêu là họ hài lòng. Uống 1-2 ly, giữ bàn.

## ⚠️ Health reminder
Đi deal → biết limit. 2-3 ly max. Uống nhiều nước, ăn nhiều.

## 📌 Damage control
Nếu khách ép nhiều → "Dạ em uống hết sức rồi ạ, em nhờ anh/chị nhiều..."
```