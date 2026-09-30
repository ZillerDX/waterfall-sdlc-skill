# Thai & Multilingual Typography Hygiene

Guidelines for handling Thai typography, line metrics, and button layout with precision.

## 1. Font Stack & Language Tag
- Always set `<html lang="th">` on the root container.
- Use a Latin-first font stack paired with high-legibility Thai body fonts:
  ```css
  font-family: 'Inter', 'Prompt', 'Sarabun', 'Noto Sans Thai', system-ui, -apple-system, sans-serif;
  ```
- Use `Prompt` for contemporary geometric interfaces, or `Sarabun` for formal, document-heavy or editorial interfaces.

## 2. Line-Height & Vertical Clearance (Zero Clipped Tone Marks)
- **Line-height Guard**: Absolute ban on `leading-none` or `leading-tight` (line-height < 1.4) on Thai text.
- Thai vowels (สระบน/ล่าง: ิ, ี, ุ, ู) and tone marks (วรรณยุกต์: ่, ้, ๊, ๋) require vertical clearance.
- Always use `leading-normal` (1.5) or `leading-relaxed` (1.625).
- Ensure overflow containers (`overflow-hidden`) provide adequate vertical padding (`py-1` or `py-1.5`) so tall tone marks do not get cut off by bounding boxes.

## 3. Letter-Spacing & Tracking (Zero Baseline Collisions)
- **Tracking Guard**: Absolute ban on negative tracking (`tracking-tight`, `tracking-tighter`, `letter-spacing: -0.025em`) on Thai strings.
- Negative tracking causes Thai vowels and tone marks to collide and shift baselines awkwardly. Always use `tracking-normal`.
- Negative tracking may only be applied to standalone Latin display headlines.

## 4. Button & Control Layout
- **No Awkward Syllable Breaks**: Add `whitespace-nowrap` on short controls, buttons, and tab pills so labels never break into single-syllable wraps.
- **Uniform Height**: Buttons in a single row/toolbar must share an explicit height (`h-9` or `h-10`) and align vertically via `inline-flex items-center justify-center gap-2`.
- **No Parenthetical English**: Strictly avoid appending English translations in parentheses to Thai buttons (e.g. use `เริ่มการเทรน` over `เริ่มการเทรน (Train)`, `จำลองจุดรบกวน` over `จำลองจุดรบกวน (Inject Outliers)`).

## 5. UI Vocabulary & Tone
- Use natural, standard action verbs: บันทึก (Save), ยกเลิก (Cancel), ลบ (Delete), แก้ไข (Edit), ส่ง (Submit), ดาวน์โหลด (Download), ค้นหา (Search).
- Keep standard loanwords where recognized: อีเมล, ล็อกอิน, แดชบอร์ด.
- Avoid bureaucratic fluff or generic AI slogans: ยกระดับ..., ปลดล็อก..., ครบจบในที่เดียว.
