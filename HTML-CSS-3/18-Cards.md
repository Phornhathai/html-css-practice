# HTML-CSS-3: 18 - Cards

**ไฟล์ต้นทอง:** 18-Cards.mp4

▶️ [ดูวิดีโอ](../../HTML-CSS-3/18-Cards.mp4)

---

## ภาพรวมคลิปนี้

![Title Slide](18-Cards/001-title-slide-cards.png)

คลิปนี้เป็นการเริ่มสร้าง component ใหม่ที่สำคัญมากคือ **Card** ซึ่งจะถูกนำไปใช้เป็นโครงสร้างหลักของการ์ดราคาแพ็กเกจ (Pricing Plans) ในคลิปถัดไป เนื้อหาครอบคลุมการสร้างโครงสร้าง BEM แบบ Block-Element-Modifier ที่สมบูรณ์เป็นครั้งแรกในคอร์ส (`.card`, `.card__header`, `.card__body`, `.card--primary`, `.card--secondary`) การใช้ `box-shadow` เพื่อสร้างเงา การแก้ปัญหามุมโค้งที่ถูกเนื้อหาด้านในบังด้วย `overflow: hidden` และเทคนิค Emmet ใหม่ๆ เช่น `lorem1` และ "Wrap with Abbreviation"

> 💡 **บริบท:** Card component นี้จะถูกใช้เป็นแม่แบบสำหรับการ์ดแพ็กเกจราคา (Entry, Business, Business Plus) ในคลิปถัดไป ("Plans") ซึ่งมีหัวการ์ดสีต่างกันตามแต่ละแพ็กเกจ

---

## 1. ทบทวนดีไซน์ใน Photoshop

![Photoshop Entry Card](18-Cards/002-photoshop-entry-card-design-standard-mobile.png)
![Photoshop Entry Card Scroll](18-Cards/003-photoshop-entry-card-design-scroll.png)

Mosh เปิด Photoshop (`standard.psd` และ `mobile.psd`) ดูดีไซน์การ์ดแพ็กเกจ "Entry" ที่มีหัวการ์ดสีฟ้าอมเขียว (cyan) แสดงราคา `$14/month`, ป้าย `10% OFF`, ข้อความ "Easy start on the cloud" ตามด้วยรายการฟีเจอร์ (checkmark) และปุ่ม BUY NOW ด้านล่าง

---

## 2. สร้างโครงสร้าง HTML ของ Card ด้วย BEM

![VSCode Empty Body](18-Cards/004-vscode-index-html-empty-body-recap.png)
![VSCode Body Cursor](18-Cards/005-vscode-html-body-cursor-ready.png)

เริ่มต้นด้วย `<body>` ว่างเปล่า (ไฟล์ index.html ถูกเคลียร์เพื่อทดลอง component ใหม่แยกต่างหาก)

![Emmet Div Card](18-Cards/006-vscode-emmet-div-card-typed.png)
![Div Card Created](18-Cards/007-vscode-html-div-card-created.png)

พิมพ์ Emmet abbreviation `.card` แล้วกด Tab เพื่อสร้าง:

```html
<div class="card"></div>
```

![Header Tag Typed](18-Cards/008-vscode-html-header-tag-typed.png)
![Header Class Card Typing](18-Cards/009-vscode-html-header-class-card-typing.png)
![Header Class Card Header BEM](18-Cards/010-vscode-html-header-class-card-header-bem-element.png)

พิมพ์ `<header>` เพิ่มเข้าไปข้างใน แล้วใส่ class ตามแบบแผน **BEM (Block Element Modifier)**:

```html
<div class="card">
  <header class="card__header"></header>
</div>
```

> 🧩 **แนวคิด BEM:** `.card` คือ **Block** (ส่วนประกอบหลัก) ส่วน `.card__header` คือ **Element** (ส่วนย่อยภายใน Block นั้น) เขียนด้วยรูปแบบ `block__element` (ขีดล่างคู่) ซึ่งเป็นรูปแบบเดียวกับที่เคยใช้กับ `.list__item` ในคลิป 13

![Photoshop Recap 2](18-Cards/011-photoshop-entry-card-recap-2.png)

![Card Title Text Added](18-Cards/012-vscode-html-header-card-title-text-added.png)

เพิ่มข้อความ "Card Title" ลงใน header เพื่อทดสอบ (placeholder ชั่วคราว):

```html
<header class="card__header">Card Title</header>
```

![Card Body Div Typing](18-Cards/013-vscode-html-card-body-div-typing.png)
![Div Card Body Created](18-Cards/014-vscode-html-div-card-body-created.png)

สร้าง Element ที่สองสำหรับส่วนเนื้อหา:

```html
<div class="card">
  <header class="card__header">Card Title</header>
  <div class="card__body"></div>
</div>
```

### สร้างข้อความจำลองด้วย Emmet `lorem`

![Lorem1 Emmet Typed](18-Cards/015-vscode-html-lorem1-emmet-typed.png)
![Lorem Ipsum Generated](18-Cards/016-vscode-html-lorem-ipsum-text-generated.png)

พิมพ์ `lorem1` แล้วกด Tab — Emmet สร้างข้อความ "Lorem Ipsum" จำลองให้อัตโนมัติ:

```html
<div class="card__body">
  Lorem ipsum dolor sit amet consectetur, adipisicing elit. Eum, assumenda?
</div>
```

> ⚡ **เทคนิค Emmet lorem:** พิมพ์ `lorem` ตามด้วยตัวเลข (เช่น `lorem1`, `lorem20`) แล้วกด Tab จะได้ข้อความ "Lorem Ipsum" แบบสุ่มความยาวตามจำนวนคำที่ระบุ มีประโยชน์มากเวลาต้องการเนื้อหาจำลองไว้ทดสอบ layout อย่างรวดเร็วโดยไม่ต้องพิมพ์เอง หรือคัดลอกจากที่อื่น

---

## 3. จัดสไตล์พื้นฐานให้ `.card`

![Switch to Styles CSS Empty](18-Cards/017-vscode-switch-to-styles-css-empty.png)
![Cards Comment Card Selector](18-Cards/018-vscode-styles-css-cards-comment-card-selector.png)

สลับไปที่ `styles.css` เพิ่ม comment section ใหม่:

```css
/* Cards */
.card {
}
```

![Border Property Autocomplete](18-Cards/019-vscode-styles-css-card-border-property-autocomplete.png)
![Border Radius 7px](18-Cards/020-vscode-styles-css-card-border-radius-7px.png)

```css
.card {
  border-radius: 7px;
}
```

### เพิ่ม `box-shadow` เพื่อสร้างเงา

![Box Shadow Intellisense](18-Cards/021-vscode-styles-css-card-box-shadow-property-intellisense.png)
![Box Shadow Values Typing](18-Cards/022-vscode-styles-css-card-box-shadow-values-typing.png)
![Box Shadow Color Autocomplete](18-Cards/023-vscode-styles-css-card-box-shadow-color-autocomplete.png)
![Box Shadow F3F3F3 Typed](18-Cards/024-vscode-styles-css-card-box-shadow-f3f3f3-typed.png)
![Box Shadow Complete](18-Cards/025-vscode-styles-css-card-box-shadow-complete.png)

```css
.card {
  border-radius: 7px;
  box-shadow: 0 0 20px 10px #f3f3f3;
}
```

> 🌟 **แนวคิดสำคัญ (box-shadow):** ค่าของ `box-shadow` เรียงตามลำดับ `offset-x offset-y blur-radius spread-radius color` ในที่นี้ `0 0 20px 10px #f3f3f3` หมายถึง ไม่มีการเลื่อนเงาในแนวนอน/แนวตั้ง (`0 0`) เบลอเงา 20px กระจายเงาออกอีก 10px ด้วยสีเทาอ่อนมาก (`#f3f3f3`) ทำให้การ์ดดูมีความ "ลอย" ขึ้นมาจากพื้นหลัง (elevation effect) ซึ่งเป็นเทคนิคการออกแบบที่ใช้กันทั่วไปใน Material Design และ UI สมัยใหม่

![Browser Card No Style](18-Cards/026-browser-card-title-lorem-ipsum-no-style.png)

ทดสอบในเบราว์เซอร์ — เนื่องจากยังไม่ได้จัดสไตล์ให้ `.card__header`/`.card__body` จึงยังเห็นแค่ข้อความธรรมดา มองไม่เห็นเงาหรือขอบโค้งชัดเจน (เพราะการ์ดยังไม่มีพื้นหลัง/ขนาดที่ชัดเจน)

---

## 4. ทดลองความกว้างด้วย Emmet "Wrap with Abbreviation"

![HTML Recap Full Structure](18-Cards/027-vscode-html-recap-full-card-structure.png)
![Select Lines Recap](18-Cards/028-vscode-html-select-lines-recap.png)

Mosh เลือกทั้งบล็อก `<div class="card">...</div>` แล้วเปิด Command Palette

![Emmet Wrap With Abbreviation](18-Cards/029-vscode-command-palette-emmet-wrap-with-abbreviation.png)

เลือกคำสั่ง **"Emmet: Wrap with Abbreviation"** แล้วพิมพ์ `div` เพื่อห่อ card เดิมด้วย `<div>` ใหม่อีกชั้น:

![Wrapped in Outer Div](18-Cards/030-vscode-html-wrapped-in-outer-div.png)

```html
<div>
  <div class="card">
    <header class="card__header">Card Title</header>
    <div class="card__body">Lorem ipsum...</div>
  </div>
</div>
```

> ⚡ **เทคนิค Emmet "Wrap with Abbreviation":** คำสั่งนี้ (เรียกผ่าน Command Palette หรือคีย์ลัด) ให้เลือกโค้ด HTML ที่มีอยู่แล้วแล้วห่อด้วย tag ใหม่ได้ทันที โดยไม่ต้องพิมพ์ tag เปิด-ปิดเองทีละตัว สะดวกมากเมื่อต้องการเพิ่ม wrapper element ให้กับโค้ดที่เขียนไว้แล้ว

![Outer Div Style Width Empty](18-Cards/031-vscode-html-outer-div-style-width-empty.png)
![Outer Div Style Width 30 Percent](18-Cards/032-vscode-html-outer-div-style-width-30-percent.png)

เพิ่ม inline style ชั่วคราวให้ div ครอบนอกเพื่อจำกัดความกว้างไว้ทดสอบการแสดงผล (ยังไม่ใช่ CSS ถาวรในไฟล์):

```html
<div style="width: 30%">
```

![Browser Card 30 Percent No CSS](18-Cards/033-browser-card-width-30-percent-no-padding-css.png)

ทดสอบผลลัพธ์ในเบราว์เซอร์ — การ์ดถูกจำกัดความกว้างไว้ที่ 30% ของหน้าจอแล้ว แต่ยังไม่มี padding ภายใน

---

## 5. จัดสไตล์ `.card__header` และ `.card__body` ด้วย Grouped Selector

![Card and Header Selectors Recap](18-Cards/034-vscode-styles-css-card-and-header-selectors-recap.png)
![Padding Property Autocomplete](18-Cards/035-vscode-styles-css-padding-property-autocomplete.png)
![Card Header Padding 2rem](18-Cards/036-vscode-styles-css-card-header-padding-2rem.png)

Mosh เริ่มพิมพ์ `padding: 2rem` ให้ `.card__header` ก่อน

![Grouped Selector Header Body Typing](18-Cards/037-vscode-styles-css-grouped-selector-card-header-body-typing.png)
![Grouped Selector Card Body Typing](18-Cards/038-vscode-styles-css-grouped-selector-card-body-typing.png)
![Grouped Selector Complete](18-Cards/039-vscode-styles-css-grouped-selector-complete.png)

จากนั้นสังเกตว่า `.card__body` ก็ต้องการ padding แบบเดียวกัน จึงใช้ **grouped selector** (คั่นด้วยคอมม่า) เพื่อกำหนดสไตล์เดียวกันให้ทั้งสอง selector พร้อมกัน:

```css
.card__header,
.card__body {
  padding: 2rem 3rem;
}
```

> 🔗 **แนวคิดสำคัญ (Grouped Selector):** การใช้เครื่องหมายคอมม่า (`,`) คั่นระหว่าง selector หลายตัว ทำให้ทุก selector ที่ระบุได้รับกฎ CSS ชุดเดียวกัน เป็นวิธีลดความซ้ำซ้อนของโค้ดเมื่อหลาย element ต้องการสไตล์เหมือนกันทุกประการ

![Browser Card Styled](18-Cards/040-browser-card-with-padding-and-shadow-styled.png)

ทดสอบผลลัพธ์ในเบราว์เซอร์ — ตอนนี้เห็นการ์ดที่มีทั้งขอบโค้งมน เงา (box-shadow) และ padding ภายในครบถ้วนแล้ว

---

## 6. สร้าง BEM Modifier: `.card--primary`

![HTML Div Card Class Recap](18-Cards/041-vscode-html-div-card-class-recap.png)
![Card Modifier Class Typing](18-Cards/042-vscode-html-card-modifier-class-typing-autocomplete.png)
![Card Modifier Dash Typing](18-Cards/043-vscode-html-card-card-modifier-dash-typing.png)

กลับไปที่ `index.html` เพิ่ม class ที่สองให้กับ `<div class="card">`:

```html
<div class="card card--primary">
```

![Grouped Selector Recap Full](18-Cards/044-vscode-styles-css-grouped-selector-recap-full.png)
![New Modifier Selector Typing](18-Cards/045-vscode-styles-css-new-modifier-selector-typing.png)
![Card Primary Modifier Typed](18-Cards/046-vscode-styles-css-card-primary-modifier-typed.png)
![Descendant Selector Autocomplete](18-Cards/047-vscode-styles-css-card-primary-descendant-selector-autocomplete.png)
![Compound Selector](18-Cards/048-vscode-styles-css-card-primary-card-header-compound-selector.png)

ใน `styles.css` สร้าง selector ที่รวม Modifier กับ Element เข้าด้วยกันแบบ descendant selector:

```css
.card--primary .card__header {
}
```

![Background Var Autocomplete](18-Cards/049-vscode-styles-css-card-primary-header-background-var-autocomplete.png)
![Background Var Color Primary](18-Cards/050-vscode-styles-css-card-primary-header-background-var-color-primary.png)
![Color Property Intellisense](18-Cards/051-vscode-styles-css-card-primary-header-color-property-intellisense.png)
![Color FFF Complete](18-Cards/052-vscode-styles-css-card-primary-header-color-fff-complete.png)

```css
.card--primary .card__header {
  background: var(--color-primary);
  color: #fff;
}
```

> 🎨 **แนวคิดสำคัญ (BEM Modifier + Descendant Selector):** `.card--primary` คือ **Modifier** (ตัวแปรของ Block เดิม เขียนด้วยขีดกลางคู่ `--`) เมื่อรวมกับ descendant selector `.card--primary .card__header` จะหมายถึง "จัดสไตล์ `.card__header` เฉพาะเมื่อมันอยู่ภายในการ์ดที่มี Modifier `--primary`" ทำให้สามารถสร้างการ์ดหลายสีสันได้โดยแค่เปลี่ยน Modifier class บน HTML โดยไม่ต้องเขียน HTML โครงสร้างใหม่

![Browser Card Primary Blue](18-Cards/053-browser-card-primary-blue-header-bem-modifier-applied.png)

ทดสอบผลลัพธ์ในเบราว์เซอร์ — หัวการ์ดเปลี่ยนเป็นพื้นหลังสีน้ำเงิน (`--color-primary`) ตัวอักษรสีขาวแล้ว

---

## 7. แก้ปัญหามุมโค้งถูกบดบัง (Overflow Issue)

![Card Card Primary Recap](18-Cards/054-vscode-html-card-card-primary-modifier-class-recap.png)
![Outer Div Padding Typing](18-Cards/055-vscode-html-outer-div-padding-typing-autocomplete.png)
![Outer Div Padding 4rem](18-Cards/056-vscode-html-outer-div-padding-4rem-added.png)

เพิ่ม inline style ชั่วคราวอีกครั้งเพื่อดูระยะห่างรอบการ์ดในเบราว์เซอร์ให้ชัดเจนขึ้น: `style="width: 30%; padding: 4rem"`

![Browser Card Primary Padding Test](18-Cards/057-browser-card-primary-with-outer-padding-test.png)

เมื่อซูมดูใกล้ๆ จะสังเกตเห็นปัญหา: **มุมบนของหัวการ์ดสีน้ำเงินเป็นมุมฉาก ไม่โค้งมนตามที่ตั้งค่า `border-radius: 7px` ไว้ใน `.card`**

![Card Recap Before Overflow](18-Cards/058-vscode-styles-css-card-recap-before-overflow.png)
![Overflow Property Typing](18-Cards/059-vscode-styles-css-card-overflow-property-typing.png)
![Overflow Hidden Added](18-Cards/060-vscode-styles-css-card-overflow-hidden-added.png)

แก้ไขโดยเพิ่ม property ใหม่ให้ `.card`:

```css
.card {
  border-radius: 7px;
  box-shadow: 0 0 20px 10px #f3f3f3;
  overflow: hidden;
}
```

![Browser Rounded Corners Fixed](18-Cards/061-browser-card-primary-overflow-hidden-rounded-corners-fixed.png)

ทดสอบอีกครั้ง — ตอนนี้มุมบนของหัวการ์ดโค้งมนตามขอบของ `.card` แล้ว

> ✂️ **แนวคิดสำคัญ (ทำไมต้อง `overflow: hidden`):** `border-radius` ทำให้ตัว **container** (`.card`) มีขอบโค้งมน แต่ไม่ได้บังคับให้ **เนื้อหาภายใน** (เช่น `.card__header` ที่มีพื้นหลังสีของตัวเอง) โค้งมนตามไปด้วยโดยอัตโนมัติ ค่าเริ่มต้นของเบราว์เซอร์คือปล่อยให้เนื้อหาล้นออกมาทับมุมโค้งได้ (เป็นมุมฉากทับซ้อน) การกำหนด `overflow: hidden` ให้กับ container สั่งให้เบราว์เซอร์ "ตัด" ส่วนใดๆ ของเนื้อหาภายในที่ล้นออกนอกขอบเขตของ container ทิ้งไป ทำให้เนื้อหาภายในถูกครอบตามรูปทรงโค้งมนของ container ไปด้วย เป็นเทคนิคที่ต้องใช้คู่กับ `border-radius` แทบทุกครั้งเมื่อ container มีเนื้อหาสีพื้นหลังของตัวเอง

---

## 8. สร้าง Modifier ที่สอง: `.card--secondary`

![Duplicate Card Primary Rule](18-Cards/062-vscode-styles-css-duplicate-card-primary-rule.png)
![Card Primary Rule Duplicated Recap](18-Cards/063-vscode-styles-css-card-primary-rule-duplicated-recap.png)

Mosh คัดลอก (duplicate) กฎ `.card--primary .card__header { ... }` ทั้งชุดมาวางต่อท้าย

![Card Secondary Selector Renamed](18-Cards/064-vscode-styles-css-card-secondary-selector-renamed.png)
![Card Secondary Var Autocomplete](18-Cards/065-vscode-styles-css-card-secondary-var-color-secondary-autocomplete.png)
![Card Secondary Var Applied](18-Cards/066-vscode-styles-css-card-secondary-var-color-secondary-applied.png)

แก้ไขชื่อ selector และค่าตัวแปรสีให้เป็นชุดที่สอง:

```css
.card--secondary .card__header {
  background: var(--color-secondary);
  color: #fff;
}
```

![Swap to Card Secondary](18-Cards/067-vscode-html-card-swap-to-card-secondary-modifier-class.png)
![Card Secondary Class Recap](18-Cards/068-vscode-html-card-secondary-class-recap.png)

กลับไปแก้ไข class ใน `index.html` จาก `card--primary` เป็น `card--secondary` เพื่อทดสอบ:

```html
<div class="card card--secondary">
```

![Browser Card Secondary Cyan](18-Cards/069-browser-card-secondary-cyan-header-applied.png)

ทดสอบผลลัพธ์ในเบราว์เซอร์ — หัวการ์ดเปลี่ยนเป็นสีฟ้าอมเขียว (cyan, `--color-secondary`) ตามที่ตั้งค่าไว้ พิสูจน์ว่าระบบ Modifier ทำงานถูกต้อง สามารถสลับสีของการ์ดได้ง่ายๆ เพียงเปลี่ยน class เดียว

---

## 9. ทบทวนดีไซน์เต็มรูปแบบก่อนจบคลิป

![Photoshop Final Full Recap](18-Cards/070-photoshop-entry-card-final-full-recap.png)

Mosh ปิดท้ายด้วยการเปิด Photoshop ทบทวนดีไซน์การ์ด "Entry" แบบเต็มอีกครั้ง เพื่อเตรียมพร้อมสำหรับคลิปถัดไป ("Plans") ที่จะนำ Card component นี้ไปประกอบเป็นการ์ดราคาแพ็กเกจจริงพร้อมรายการฟีเจอร์และปุ่ม BUY NOW ครบถ้วน

---

## สรุปภาพรวมของคลิปนี้

| หัวข้อ | รายละเอียด |
|---|---|
| BEM Block | `.card` |
| BEM Elements | `.card__header`, `.card__body` |
| BEM Modifiers | `.card--primary`, `.card--secondary` |
| CSS Properties/แนวคิดใหม่ | `box-shadow`, `overflow: hidden`, grouped selector (`,`), compound descendant selector (Modifier + Element) |
| เครื่องมือ | VS Code (Emmet `lorem`, "Wrap with Abbreviation"), Photoshop |

## แนวคิดสำคัญที่ได้จากคลิปนี้

1. โครงสร้าง BEM ที่สมบูรณ์: **Block** (`.card`) → **Element** (`.card__header`, ขีดล่างคู่ `__`) → **Modifier** (`.card--primary`, ขีดกลางคู่ `--`) ใช้ร่วมกันเพื่อสร้าง component ที่ปรับแต่งได้หลากหลายโดยไม่ต้องเขียน CSS ซ้ำซ้อน
2. `box-shadow: offset-x offset-y blur-radius spread-radius color` สร้างเงาให้ element ดูมีมิติ ลอยขึ้นจากพื้นหลัง
3. **Grouped selector** (คอมม่าคั่น) ใช้กำหนดสไตล์เดียวกันให้หลาย selector พร้อมกัน ลดความซ้ำซ้อนของโค้ด
4. `overflow: hidden` จำเป็นเมื่อต้องการให้เนื้อหาภายในถูก "ตัด" ให้โค้งมนตามขอบของ container ที่มี `border-radius` โดยเฉพาะเมื่อเนื้อหาภายในมีพื้นหลังสีของตัวเอง
5. **Compound descendant selector** ที่รวม Modifier กับ Element (เช่น `.card--primary .card__header`) เป็นรูปแบบมาตรฐานของ BEM สำหรับปรับสไตล์ Element ตามบริบทของ Modifier ที่ครอบอยู่
6. Emmet `lorem` + ตัวเลข สร้างข้อความจำลองอย่างรวดเร็ว และ "Wrap with Abbreviation" ห่อโค้ดที่เลือกไว้ด้วย tag ใหม่ได้ทันทีโดยไม่ต้องพิมพ์เอง

---

*สรุปจากคลิปที่ 18 ของคอร์ส "Building a Web Site" (Moshify Project) สอนโดย Mosh Hamedani — codewithmosh.com*
