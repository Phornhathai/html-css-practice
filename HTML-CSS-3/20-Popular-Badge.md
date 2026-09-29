# HTML-CSS-3: 20 - Popular Badge

**ไฟล์ต้นฉบับ:** 20-Popular-Badge.mp4

▶️ [ดูวิดีโอ](../../HTML-CSS-3/20-Popular-Badge.mp4)

---

## ภาพรวมคลิปนี้

![Title Slide](20-Popular-Badge/001-title-slide-popular-badge.png)

คลิปนี้เป็นคลิปที่ **สั้นและเจาะจง** (53 เฟรมสำคัญ) สอนเทคนิคการเพิ่ม **ริบบิ้น "Popular" (ป้ายยอดนิยม)** ที่มุมขวาบนของการ์ดแพลนราคา ซึ่งเป็นเทคนิคที่ใช้กันทั่วไปเพื่อดึงดูดความสนใจไปยังแพลนที่ผู้ขายต้องการให้ลูกค้าเลือกมากที่สุด (มักเป็นแพลนราคากลาง)

> 🎯 หัวข้อหลักที่สอนในคลิปนี้:
> 1. การใช้ SVG เป็นภาพกราฟิกตกแต่ง
> 2. การเปรียบเทียบวิธี `<img>` ใน HTML กับวิธี `::before` pseudo-element ใน CSS
> 3. การใช้ `position: absolute` ร่วมกับ `position: relative` เพื่อจัดวางองค์ประกอบให้ลอยอยู่ที่มุมของ Container

![Photoshop Business Card Recap](20-Popular-Badge/002-photoshop-business-card-popular-ribbon-recap.png)

ภาพจาก Photoshop แสดงดีไซน์เป้าหมาย: การ์ด "Business" ($24/month, 20% OFF, "Optimal Cloud Experience") ที่มีริบบิ้นสีกรมท่าเข้มเขียนคำว่า "Popular" พาดอยู่ที่มุมขวาบนของการ์ด

---

## 1. สำรวจไฟล์ SVG ที่มีอยู่แล้วในโปรเจกต์

![Explorer Images Folder](20-Popular-Badge/003-vscode-explorer-images-folder-css-components.png)

Mosh เปิด Explorer panel ของ VS Code แสดงโครงสร้างโปรเจกต์ Moshify: โฟลเดอร์ `components/`, `css/`, `images/` (มีไฟล์ `sprite.svg`, `tick.svg`) และ `index.html`

![Popular SVG File Markup](20-Popular-Badge/004-vscode-popular-svg-file-markup.png)

Mosh เปิดไฟล์ **`images/popular.svg`** ที่มีอยู่แล้วในโปรเจกต์ (เตรียมไว้ล่วงหน้าโดยผู้สอน) ซึ่งมีโค้ด SVG ของริบบิ้น:

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="...">
  <path fill="#1e0f6d" d="M0 4.7h35L30.3 0H5..." />
  <g data-name="Layer 1">
    <path fill="#1b0760" d="M5.3.2v87l11.9-1..." />
    <text transform="rotate(90 1.05 12.25)">
      <tspan letter-spacing="-.01em">Popular</tspan>
    </text>
  </g>
</svg>
```

> 📄 นี่คือไฟล์ Vector Graphic (SVG) ของริบบิ้นที่วาดไว้ล่วงหน้าแล้ว มีรูปทรงธงพร้อมข้อความ "Popular" หมุน 90 องศาให้อ่านจากล่างขึ้นบน (แนวตั้ง) ซึ่งเหมาะสำหรับใช้เป็นริบบิ้นที่พาดมุมการ์ด

![Explorer Popular SVG Selected](20-Popular-Badge/005-vscode-explorer-popular-svg-selected.png)

---

## 2. วิธีที่ 1: ลองใส่ด้วย `<img>` Tag ก่อน (แล้วจะพบปัญหา)

![Quick Open Index Search](20-Popular-Badge/006-vscode-quick-open-index-search.png)

Mosh ใช้ Quick Open (Cmd+P) เพื่อกลับไปที่ไฟล์ `index.html`

![Index HTML Recap](20-Popular-Badge/007-vscode-index-html-plan-card-secondary-breadcrumb-recap.png)

เริ่มต้นจากโครงสร้างการ์ดแพลน "Entry" ที่สร้างไว้ในคลิปก่อนหน้า (Plans)

### เพิ่ม `<img>` เข้าไปในหัวการ์ด

![Img Emmet Abbreviation Typing](20-Popular-Badge/008-vscode-html-img-emmet-abbreviation-typing.png)

Mosh พิมพ์ `img` แล้ว Emmet แนะนำ Abbreviation

![Img Src Alt Attributes Added](20-Popular-Badge/009-vscode-html-img-src-alt-attributes-added.png)

```html
<img src="" alt="" />
```

![Img Src Images Popular SVG Typed](20-Popular-Badge/010-vscode-html-img-src-images-popular-svg-typed.png)

```html
<img src="images/popular.svg" alt="" />
```

ตำแหน่งของ `<img>` ถูกวางไว้เป็นตัวแรกใน `card__header` ก่อนหน้า `<h3 class="plan__name">`:

```html
<header class="card__header">
  <img src="images/popular.svg" alt="" />
  <h3 class="plan__name">Entry</h3>
  ...
</header>
```

![Browser Popular SVG Huge Unstyled](20-Popular-Badge/011-browser-popular-svg-huge-unstyled-recap.png)

**🐛 ปัญหาที่พบ:** เมื่อดูผลลัพธ์ในบราวเซอร์ พบว่าภาพ SVG ริบบิ้น "Popular" แสดงผลใหญ่มากจนเต็มความกว้างของการ์ด และล้นเลยขอบเขตปกติของหัวการ์ดไปอย่างมาก (เพราะ SVG ไม่มีขนาดกำหนดไว้ ค่า default จะยึดตาม `viewBox` ซึ่งมีสัดส่วนที่ค่อนข้างใหญ่)

![Browser Popular SVG Huge Scrolled](20-Popular-Badge/012-browser-popular-svg-huge-scrolled-recap.png)

เมื่อเลื่อนดูเพิ่มเติมจะเห็นข้อความ "Popular" หมุนแนวตั้งเต็มพื้นที่ ซึ่งไม่ตรงกับดีไซน์ที่ต้องการ (ริบบิ้นเล็กๆ ที่มุมการ์ด)

![Img Self Closing Slash Recap](20-Popular-Badge/013-vscode-html-img-self-closing-slash-recap.png)

### ลองเพิ่ม class ให้ img แต่ยังไม่แก้ปัญหาขนาด

![Img Class Attribute Autocomplete](20-Popular-Badge/014-vscode-html-img-class-attribute-autocomplete-badge-options.png)

Mosh ลองพิมพ์ attribute `class` ใน `<img>` แล้ว VS Code แสดง Autocomplete รายการ class ที่มีในโปรเจกต์: `badge`, `badge--primary`, `badge--secondary`, `badge--small`, `btn`, `btn--accent`

![Img Class Empty Src Popular SVG Recap](20-Popular-Badge/015-vscode-html-img-class-empty-src-popular-svg-recap.png)
![Img Full Recap Before Removal](20-Popular-Badge/016-vscode-html-img-full-recap-before-removal.png)

> ⚠️ **ทำไม Mosh เปลี่ยนใจไม่ใช้ `<img>`:** หลังจากทดลองแล้วพบว่าการใช้ `<img>` มีข้อเสีย 2 อย่างในกรณีนี้ - (1) ต้องเขียน CSS จำกัดขนาดเพิ่มเติมทุกครั้งที่ใช้ และ (2) ที่สำคัญกว่านั้นคือ **ริบบิ้น "Popular" ไม่ใช่เนื้อหา (Content) ที่มีความหมายทางความหมาย (Semantic)** แต่เป็นเพียง**องค์ประกอบตกแต่ง (Decorative)** ที่ไม่ควรอยู่ใน HTML - ดังนั้น Mosh จึงตัดสินใจลบ `<img>` ออกทั้งหมด แล้วเปลี่ยนไปใช้เทคนิค CSS `::before` แทน

---

## 3. วิธีที่ 2 (วิธีที่ถูกต้อง): ใช้ CSS `::before` Pseudo-element

![Img Cursor Positioned Before H3](20-Popular-Badge/017-vscode-html-img-cursor-positioned-before-h3.png)

Mosh ลบ `<img>` ออกจาก HTML ทั้งหมด แล้วกลับไปที่ `<div class="plan">` เพื่อเพิ่ม Modifier Class ใหม่

### เพิ่ม Modifier Class `.plan--popular`

![Plan Class Typing Modifier](20-Popular-Badge/018-vscode-html-plan-class-typing-modifier.png)

```html
<div class="plan plan">
```

![Plan Class Autocomplete Suggestions](20-Popular-Badge/019-vscode-html-plan-class-autocomplete-suggestions.png)

VS Code แสดง Autocomplete: `plan`, `plan__billing-cycle`, `plan__description`, `plan__name`, `plan__price`

![Plan Popular Modifier Class Added](20-Popular-Badge/020-vscode-html-plan-plan-popular-modifier-class-added.png)

```html
<div class="plan plan--popular">
```

> 🧬 **แนวคิด BEM Modifier:** `.plan--popular` คือ Modifier ที่จะใช้ทำเครื่องหมายว่าแพลนไหนควรมีริบบิ้น "Popular" แสดงอยู่ - เมื่อไม่มี class นี้ ริบบิ้นจะไม่ปรากฏ ซึ่งเป็นวิธีที่ยืดหยุ่นกว่าการเขียน `<img>` แยกในทุกการ์ด เพราะ Developer แค่เพิ่มหรือลบ class เดียวก็ควบคุมการแสดงผลได้

---

## 4. เขียน CSS Rule สำหรับริบบิ้น

![Media Query Recap](20-Popular-Badge/021-vscode-styles-css-media-query-plan-name-price-recap.png)

Mosh สลับไปที่ไฟล์ `styles.css` ทวนโค้ด Media Query ของ `.plan__name` และ `.plan__price` ที่เขียนไว้ในคลิปก่อน

![Plan Selector Autocomplete Typing](20-Popular-Badge/022-vscode-styles-css-plan-selector-autocomplete-typing.png)

VS Code แสดง Autocomplete เมื่อพิมพ์ `.plan`

![Plan Popular Selector Created](20-Popular-Badge/023-vscode-styles-css-plan-popular-selector-created.png)

```css
.plan--popular {
}
```

![Plan Popular Empty Rule Recap](20-Popular-Badge/024-vscode-styles-css-plan-popular-empty-rule-recap.png)

> 🤔 Mosh พิจารณาเลือก Selector ที่เหมาะสม สุดท้ายตัดสินใจว่าควรเขียนกฎที่เจาะจงเข้าไปถึง `card__header::before` แทนที่จะเขียนบน `.plan--popular` โดยตรง เพราะริบบิ้นควรจะแสดงอยู่ในตำแหน่งของหัวการ์ด

---

## 5. สร้าง Pseudo-element `::before` เพื่อแทรกไอคอนตกแต่ง

![Plan Popular Card Header Selector Typing](20-Popular-Badge/025-vscode-styles-css-plan-popular-card-header-selector-typing.png)

```css
.plan--popular .card__header:
```

![Plan Popular Card Header Before Pseudo Element](20-Popular-Badge/026-vscode-styles-css-plan-popular-card-header-before-pseudo-element.png)

```css
.plan--popular .card__header::before {
}
```

![Before Empty Braces Recap](20-Popular-Badge/027-vscode-styles-css-before-empty-braces-recap.png)

> ✨ **แนวคิดสำคัญ: `::before` Pseudo-element** คือองค์ประกอบเสมือนที่ CSS สร้างขึ้นมาแทรกไว้ **ก่อน** เนื้อหาจริงภายใน Element ที่เลือก (ในที่นี้คือก่อนเนื้อหาทั้งหมดใน `.card__header`) โดยไม่ต้องเพิ่ม Tag ใหม่ใน HTML เลย ข้อดีคือ:
> - ไม่ทำให้ HTML รกไปด้วย Element ที่ไม่มีความหมายเชิงเนื้อหา (Non-semantic)
> - ควบคุมการแสดงผลได้เต็มที่ผ่าน CSS เพียงจุดเดียว
> - เปิด/ปิดการแสดงผลได้ง่ายด้วยการเพิ่ม/ลบ Class (`plan--popular`) โดยไม่ต้องแก้ HTML

### เพิ่มเนื้อหาด้วย `content: url(...)`

![Content URL Popular SVG Added](20-Popular-Badge/028-vscode-styles-css-content-url-popular-svg-added.png)

```css
.plan--popular .card__header::before {
  content: url(../images/popular.svg);
}
```

> 📌 **หมายเหตุเรื่อง Path:** สังเกตว่า Path ในไฟล์ CSS ใช้ `../images/popular.svg` (มี `../` นำหน้า) ต่างจาก Path ใน HTML ที่ใช้ `images/popular.svg` เพราะไฟล์ `styles.css` อยู่ในโฟลเดอร์ `css/` ซึ่งเป็นคนละระดับกับไฟล์ `index.html` ดังนั้น Path ที่อ้างอิงจากไฟล์ CSS จึงต้องถอยกลับ 1 ระดับ (`../`) ก่อนเข้าไปในโฟลเดอร์ `images/`
>
> 🔑 **`::before` ต้องมี `content` เสมอ:** Pseudo-element `::before` (และ `::after`) จะไม่แสดงผลอะไรเลยถ้าไม่มีการกำหนดค่า `content` แม้จะเป็นค่าว่าง (`content: "";`) ก็ตาม การกำหนด `content: url(...)` เป็นวิธีแทรกรูปภาพ (รวมถึง SVG) เข้าไปโดยไม่ต้องใช้ `<img>` เลย

![Browser Popular SVG Huge After Before](20-Popular-Badge/029-browser-popular-svg-huge-recap-after-before-pseudo.png)

ผลลัพธ์เบื้องต้น: ริบบิ้นปรากฏแล้วแต่ยังคงมีขนาดใหญ่เกินไปเหมือนตอนใช้ `<img>` (ปัญหาเดิมยังคงอยู่ เพราะ SVG ไม่มีขนาดกำหนด)

![Before Content URL Recap](20-Popular-Badge/030-vscode-styles-css-before-content-url-recap.png)

---

## 6. จำกัดขนาดและจัดวางริบบิ้น

### เพิ่ม width เพื่อจำกัดขนาด

![Width 40px Typing](20-Popular-Badge/031-vscode-styles-css-width-40px-typing.png)

```css
.plan--popular .card__header::before {
  content: url(../images/popular.svg);
  width: 40px;
}
```

### เปลี่ยน display เป็น inline-block

![Display Emmet Abbreviation Typing](20-Popular-Badge/032-vscode-styles-css-display-emmet-abbreviation-typing.png)

Mosh พิมพ์ `ds` แล้ว Emmet แนะนำ `display: subgrid;` และตัวเลือกอื่น

![Display Inline Autocomplete Options](20-Popular-Badge/033-vscode-styles-css-display-inline-autocomplete-options.png)

VS Code แสดงตัวเลือก: `inline`, `inline-block`, `inline-flex`, `inline-flexbox`, `inline-table`

![Display Inline Block Added](20-Popular-Badge/034-vscode-styles-css-display-inline-block-added.png)

```css
.plan--popular .card__header::before {
  content: url(../images/popular.svg);
  width: 40px;
  display: inline-block;
}
```

> 🔧 **ทำไมต้องเป็น `inline-block` ไม่ใช่ `block`:** ค่า Default ของ Pseudo-element ที่มี `content` เป็นรูปภาพจะเป็น `inline` ซึ่งไม่รองรับการกำหนด `width` โดยตรง (คล้ายกับปัญหาที่เจอกับ `<span>` ในคลิปก่อนหน้า) การเปลี่ยนเป็น `inline-block` ทำให้สามารถกำหนดความกว้างได้ ในขณะที่ยังคงพฤติกรรมคล้าย Inline (ไม่ขึ้นบรรทัดใหม่)

![Browser Popular Ribbon Sized Correctly](20-Popular-Badge/035-browser-popular-ribbon-sized-correctly-top-left-recap.png)

ผลลัพธ์: ริบบิ้นมีขนาดเล็กลงเหมาะสมแล้ว (40px) แต่ยังคงอยู่ที่ตำแหน่งซ้ายบนของหัวการ์ด (ตำแหน่งปกติของ Pseudo-element ในลำดับ Content) ยังไม่ได้ลอยไปที่มุมขวาบนตามดีไซน์

---

## 7. ใช้ Position Absolute ย้ายริบบิ้นไปมุมขวาบน

![Position Emmet Abbreviation Typing](20-Popular-Badge/036-vscode-styles-css-position-emmet-abbreviation-typing.png)

Mosh พิมพ์ `pos` แล้ว Emmet แนะนำ `position: relative;`

![Position Absolute Added](20-Popular-Badge/037-vscode-styles-css-position-absolute-added.png)

```css
.plan--popular .card__header::before {
  content: url(../images/popular.svg);
  width: 40px;
  display: inline-block;
  position: absolute;
}
```

![Recap Full Before Rule](20-Popular-Badge/038-vscode-styles-css-recap-full-before-rule.png)

### สร้าง Positioning Context ด้วย `position: relative` บน Card Header

![Plan Popular Card Header Selector Typing 2](20-Popular-Badge/039-vscode-styles-css-plan-popular-card-header-selector-typing-2.png)

```css
.plan--popular .card
```

![Card Autocomplete Suggestions](20-Popular-Badge/040-vscode-styles-css-card-autocomplete-suggestions.png)

VS Code แสดง Autocomplete: `.card`, `.card--primary`

![Plan Popular Card Header Empty Rule Created](20-Popular-Badge/041-vscode-styles-css-plan-popular-card-header-empty-rule-created.png)

```css
.plan--popular .card__header {
}
```

![Position Emmet Typing 2](20-Popular-Badge/042-vscode-styles-css-position-emmet-typing-2.png)

![Position Relative Added Card Header](20-Popular-Badge/043-vscode-styles-css-position-relative-added-card-header.png)

```css
.plan--popular .card__header {
  position: relative;
}
```

> 🧭 **แนวคิดสำคัญ: Positioning Context (`position: relative` + `position: absolute`)** นี่คือรูปแบบมาตรฐานที่ใช้บ่อยที่สุดใน CSS สำหรับการวางองค์ประกอบลอยอยู่ในตำแหน่งที่ต้องการภายใน Container หนึ่งๆ:
> - เมื่อ Parent Element (`.card__header`) มี `position: relative` จะทำให้มันกลายเป็น **"Containing Block"** (จุดอ้างอิงตำแหน่ง) สำหรับลูกหลานที่มี `position: absolute`
> - เมื่อ Child Element (`::before`) มี `position: absolute` มันจะหลุดออกจาก Flow ปกติของเอกสาร (Document Flow) และสามารถกำหนดตำแหน่งได้อย่างอิสระโดยอ้างอิงจาก Parent ที่ใกล้ที่สุดที่มี `position: relative` (หรือค่าอื่นที่ไม่ใช่ `static`)
> - หากไม่มี `position: relative` บน Parent เลย Browser จะอ้างอิงตำแหน่งจาก `<body>` หรือ Viewport ทั้งหน้าแทน ซึ่งจะทำให้ริบบิ้นหลุดไปอยู่ผิดที่ผิดทางอย่างมาก

![Recap Position Relative Before Rule](20-Popular-Badge/044-vscode-styles-css-recap-position-relative-before-rule.png)

---

## 8. กำหนดพิกัดที่แน่นอน (top, right)

![Before Top 0 Added](20-Popular-Badge/045-vscode-styles-css-before-top-0-added.png)

```css
.plan--popular .card__header::before {
  content: url(../images/popular.svg);
  width: 40px;
  display: inline-block;
  position: absolute;
  top: 0;
}
```

![Before Right Property Typing](20-Popular-Badge/046-vscode-styles-css-before-right-property-typing.png)

```css
  right: ;
```

![Browser Popular Ribbon Positioned Top Right](20-Popular-Badge/047-browser-popular-ribbon-positioned-top-right-corner-recap.png)

ผลลัพธ์เบื้องต้น: ริบบิ้นเริ่มลอยไปที่มุมขวาบนของหัวการ์ดตามที่ต้องการแล้ว

![Before Right 5 Percent Added](20-Popular-Badge/048-vscode-styles-css-before-right-5-percent-added.png)

```css
.plan--popular .card__header::before {
  content: url(../images/popular.svg);
  width: 40px;
  display: inline-block;
  position: absolute;
  top: 0;
  right: 5%;
}
```

### ปรับ top ให้ริบบิ้นดูเหมือน "เสียบ" จากขอบบนสุดของการ์ด

![Before Top Negative 6px Typing](20-Popular-Badge/049-vscode-styles-css-before-top-negative-6px-typing.png)

```css
.plan--popular .card__header::before {
  content: url(../images/popular.svg);
  width: 40px;
  display: inline-block;
  position: absolute;
  top: -6px;
  right: 5%;
}
```

> 🎯 **การใช้ค่าลบ (Negative Value) ใน top:** ค่า `top: -6px;` (แทนที่จะเป็น `top: 0;`) ทำให้ริบบิ้นเลื่อนขึ้นไปเหนือขอบบนของ `.card__header` เล็กน้อย (6 พิกเซล) เพื่อให้ดูเหมือนริบบิ้นถูกปักหรือเสียบทะลุออกมาจากขอบบนสุดของการ์ดจริงๆ (มองเห็นปลายแหลมด้านบนของริบบิ้นเต็มรูปแบบ ไม่ถูกตัดโดยขอบการ์ด) ซึ่งเป็นการปรับแต่งรายละเอียดเล็กน้อย (Fine-tuning) ให้ตรงกับดีไซน์ต้นฉบับมากที่สุด

![Browser Popular Ribbon Final Position Recap](20-Popular-Badge/050-browser-popular-ribbon-final-position-recap.png)

---

## 9. รีแคปผลลัพธ์สุดท้าย

![Browser Final Recap Chrome Full Width](20-Popular-Badge/051-browser-popular-ribbon-final-recap-chrome-full-width.png)

![Browser Final Recap Narrower Window](20-Popular-Badge/052-browser-popular-ribbon-final-recap-narrower-window.png)

![Browser Final Recap Numbers App Visible](20-Popular-Badge/053-browser-popular-ribbon-final-recap-numbers-app-visible.png)

ริบบิ้น "Popular" เสร็จสมบูรณ์แล้ว: ขนาดเล็กพอดี (40px) ลอยอยู่ที่มุมขวาบนของหัวการ์ด และดูเหมือนปักทะลุออกมาจากขอบบนของการ์ดตามดีไซน์ต้นฉบับใน Photoshop ทุกประการ

---

## สรุปภาพรวมของคลิปนี้

**CSS ทั้งหมดที่เขียนในคลิปนี้:**

```css
.plan--popular .card__header {
  position: relative;
}

.plan--popular .card__header::before {
  content: url(../images/popular.svg);
  width: 40px;
  display: inline-block;
  position: absolute;
  top: -6px;
  right: 5%;
}
```

**HTML ที่เปลี่ยนแปลง (เพิ่ม Modifier Class เพียงตัวเดียว ไม่มี `<img>` เพิ่ม):**

```html
<div class="plan plan--popular">
  <div class="card card--secondary">
    <header class="card__header">
      <h3 class="plan__name">Entry</h3>
      ...
```

| CSS Selector | คุณสมบัติ | ค่า |
|---|---|---|
| `.plan--popular .card__header` | positioning context | `position: relative;` |
| `.plan--popular .card__header::before` | เนื้อหาไอคอน | `content: url(../images/popular.svg);` |
| `.plan--popular .card__header::before` | ขนาดและการแสดงผล | `width: 40px; display: inline-block;` |
| `.plan--popular .card__header::before` | ตำแหน่งลอย | `position: absolute; top: -6px; right: 5%;` |

### แนวคิดสำคัญที่ได้จากคลิปนี้

1. **`<img>` vs `::before` สำหรับองค์ประกอบตกแต่ง** - เมื่อกราฟิกไม่ใช่เนื้อหาที่มีความหมาย (Non-semantic/Decorative) ควรใส่ผ่าน CSS (`::before`/`content: url()`) แทนที่จะเพิ่ม `<img>` ใน HTML เพราะช่วยแยก Presentation ออกจาก Content และควบคุมการเปิด/ปิดด้วย Class เดียวได้
2. **`::before` ต้องมี `content` เสมอ** ไม่งั้นจะไม่แสดงผลอะไรเลย และสามารถใช้ `content: url(...)` เพื่อแทรกรูปภาพ/SVG ได้โดยตรง
3. **Positioning Context Pattern** - `position: relative` บน Parent + `position: absolute` บน Child คือรูปแบบมาตรฐานสำหรับวางองค์ประกอบลอยในตำแหน่งที่ต้องการภายใน Container
4. **`display: inline-block`** จำเป็นเมื่อต้องการกำหนด `width`/`height` ให้กับ Element ที่มีค่า default เป็น `inline` (รวมถึง Pseudo-element ที่มี content เป็นรูปภาพ)
5. **ค่าลบ (Negative Value) ใน CSS Position** สามารถใช้เพื่อขยับองค์ประกอบให้ล้นออกไปนอกขอบเขตปกติของ Parent ได้ ซึ่งเป็นเทคนิคที่ใช้บ่อยสำหรับสร้างเอฟเฟกต์ "ป้าย" หรือ "ริบบิ้น" ที่ดูเหมือนติดอยู่บนขอบขององค์ประกอบอื่น
6. **BEM Modifier ควบคุมการแสดงผล** - `.plan--popular` เป็นตัวอย่างที่ดีของการใช้ Modifier Class เพื่อเปิด/ปิดฟีเจอร์การแสดงผล (แสดงหรือไม่แสดงริบบิ้น) โดยไม่ต้องแก้โครงสร้าง HTML

---

*สรุปจากคลิปที่ 20 (Popular Badge) คอร์ส HTML & CSS โดย Mosh Hamedani จาก codewithmosh.com*
