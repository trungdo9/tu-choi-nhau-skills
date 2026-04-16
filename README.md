# tu-choi-nhau

> AI coach từ chối nhậu khéo léo cho người trẻ Việt Nam

## Tại sao?

Người trẻ Việt Nam 22-30 tuổi ở thành phố thường gặp tình huống:
- Bạn bè rủ nhậu liên tục
- Sếp mời rượu sau deal
- Bị ép uống thêm dù đã từ chối
- Không biết cách từ chối mà không mất tình bạn

Skill này giúp từ chối khéo léo, giữ mặt mũi, không say.

## Cách dùng

Khi cần từ chối lời mời nhậu:
```
User: "Mấy đứa rủ tao đi nhậu tối nay"
→ Skill tự detect tier + đưa ra script & text phù hợp
```

## Tier System

| Tier | Độ khó | Khi nào |
|------|--------|---------|
| **BEGINNER** | ⭐ | Từ chối lần đầu, bạn thường rủ, không ép |
| **INTERMEDIATE** | ⭐⭐ | Bị pressure thêm, "uống thêm đi" |
| **ADVANCED** | ⭐⭐⭐ | Sếp mời, người lớn tuổi, khách hàng |

## Tone

- Xưng **tao/mày** (gen-Z casual)
- **Slick language**: deal, xử lý, sắp xếp, đặt trước
- **Formula**: EXCUSE + WANT-TO-GO + COUNTER-OFFER

### Slick Example

❌ Before:
```
"Không đi được, lần sau nhé"
```

✅ After:
```
"Mày ơi, tối nay tao có việc bận thật, không đi được. Để lần sau tao đặt trước cho mày nha, deal không?"
```

## Output Format

Mỗi response đều có:

1. **Tình huống** - Context ngắn
2. **Script** - Câu nói đọc lên khi gặp trực tiếp
3. **Text** - Tin nhắn copy-paste gửi ngay
4. **Health reminder** - Nhắc nhở uống có chừng
5. **Khi nào nên đi?** - Flip perspective

## Quick Start

```markdown
## 🎯 Tình huống
Bạn thường trong công ty rủ nhậu

## 📖 Script đọc lên
"Mày ơi, tối nay tao bận thật, tập gym xong rồi mà còn phải xử lý đống việc. Để lần sau tao đặt trước cho mày nha, deal không?"

## 📱 Text gửi
"Mấy ơi tối nay tao bận thật, đang xử lý deadline 😰 Để tuần sau tao đặt bàn trước cho mấy người nhé! Deal chưa?"

## ⚠️ Health reminder
Mày uống có chừng thôi (1-2 lon max). Xử lý nước lọc nhiều vào. Nếu uống nhiều → Grab về, đừng lái. Deal chưa?

## 💡 Khi nào nên đi?
Team có chuyện vui (lên chức, deal xong) → đi cho vui. Đây là opportunity, đừng miss.
```

## Examples

### BEGINNER
```
User: "Bọn tao đi uống bia cuối tuần, đi không?"
→ Script: "Tuần này tao bận thật, đang xử lý mấy deal cuối tháng. Để tuần sau tao đặt bàn trước cho mày nha, mày chọn quán đi, deal chưa?"
```

### INTERMEDIATE
```
User: "Tao từ chối rồi nhưng thằng A cứ nói 'đi 1 lon thôi mà'"
→ Script: "Thật tối nay tao không uống được. Mày uống đi, tao ngồi chơi với, tiền tao chia."
```

### ADVANCED
```
User: "Sếp A mời tao uống rượu khi deal xong"
→ Script: "Dạ em cảm ơn anh A, để em nâng cốc với anh. Em uống 1 ly thôi ạ vì tối nay em phải lái về. Lần sau em xin phép uống nhiều hơn ạ."
```

## File Structure

```
tu-choi-nhau/
├── SKILL.md                    # Main entry point
├── TIER.md                     # Tier overview + detection
├── CLAUDE.md                   # Developer docs
├── README.md                  # This file
├── BEGINNER/
│   ├── SKILL.md               # Từ chối lần đầu
│   ├── templates.md           # Template A-F
│   └── excuses.md             # Kho excuse
├── INTERMEDIATE/
│   ├── SKILL.md               # Bị ép thêm
│   ├── pressure-handling.md   # L1-L5 responses
│   └── scenarios.md          # Real scenarios
├── ADVANCED/
│   ├── SKILL.md               # Sếp/người lớn/khách
│   ├── hierarchy-reading.md  # Đọc bàn nhậu
│   ├── emergency-exit.md     # Thoát khẩn cấp
│   └── damage-control.md     # Sửa chữa sau từ chối
└── SHARED/
    ├── health.md              # Health templates
    ├── when-to-say-yes.md     # Khi nào nên đi
    └── culture-notes.md       # Background văn hóa nhậu
```

## Tech Stack

- Claude Code skill format
- Pure markdown, no dependencies
- Tier-based routing

## License

MIT - Dùng tự do, modify tùy ý.
