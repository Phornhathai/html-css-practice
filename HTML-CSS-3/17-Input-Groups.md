# HTML-CSS-3: 17 - Input Groups

**ไฟล์ต้นทอง:** 17-Input-Groups.mp4

▶️ [ดูวิดีโอ](../../HTML-CSS-3/17-Input-Groups.mp4)

---

## ภาพรวมคลิปนี้

![Title Slide](17-Input-Groups/001-title-slide-input-groups.png)
![Title Slide 2](17-Input-Groups/002-title-slide-input-groups-2.png)

คลิปนี้ต่อยอดจากคลิป 16 (Inputs) โดยนำ `<input>` และ `<button>` มารวมกันเป็นกลุ่มเดียว (**Input Group**) ให้ดูเป็น "ช่องค้นหา + ปุ่ม" ที่ติดกันแบบไร้รอยต่อ (seamless) เนื้อหาครอบคลุมตั้งแต่การห่อ element ด้วย `<div class="input-group">` การรีแฟคเตอร์ CSS ให้เป็น DRY มากขึ้นด้วย **CSS Custom Properties** ใหม่ (`--color-border`, `--border-radius`) การใช้ **Flexbox** (`display: flex`, `flex-grow`) เพื่อให้ input ขยายเต็มพื้นที่ที่เหลือ การแก้ปัญหา double border ด้วย descendant selector และปิดท้ายด้วยแนวคิดสำคัญเรื่องปรัชญาการสร้าง UI แบบ **"Bottom Up" (Components First)**

> 💡 **บริบท:** input-group นี้คือส่วนเดียวกับ input และปุ่ม SEARCH ที่สร้างไว้ในคลิปก่อนหน้า เพียงแต่ตอนนี้ทำให้มันแสดงผลรวมกันเป็นกล่องเดียว (ไม่มีช่องว่างระหว่าง input กับปุ่ม)

---

## 1. ทบทวนดีไซน์และโครงสร้าง HTML เดิม

![Photoshop Design](17-Input-Groups/003-photoshop-input-group-design.png)
![Photoshop Design 2](17-Input-Groups/004-photoshop-input-group-design-2.png)

Mosh เปิด Photoshop ทบทวนดีไซน์ของส่วน input + ปุ่มค้นหาที่ต้องรวมกันเป็นกลุ่มเดียว

![VSCode Recap](17-Input-Groups/005-vscode-index-html-recap-existing-input.png)

กลับมาที่ `index.html` ซึ่งมี `<input>` ที่สร้างไว้จากคลิปก่อนอยู่แล้ว

---

## 2. สร้างปุ่ม SEARCH ด้วย Emmet Abbreviation

![Emmet Typed](17-Input-Groups/006-vscode-emmet-button-btn-btn-accent-typed.png)

Mosh พิมพ์ Emmet abbreviation อย่างรวดเร็วเพื่อสร้างปุ่มที่มี class ครบตามที่เคยสร้างไว้ในคลิป 15 (Buttons):

```
button.btn.btn--accent
```

![Emmet Expanded](17-Input-Groups/007-vscode-emmet-button-expanded.png)

กด Tab แล้ว Emmet ขยายเป็น:

```html
<button class="btn btn--accent"></button>
```

จากนั้นพิมพ์ข้อความ "Search" ลงในปุ่ม

> ⚡ **เทคนิค Emmet:** การพิมพ์ `tagname.class1.class2` แล้วกด Tab เป็นวิธีที่เร็วกว่าการพิมพ์ HTML เต็มรูปแบบมาก โดยเฉพาะเมื่อต้องใช้ class ที่ซับซ้อนหลายตัวซ้ำๆ กันในหลายจุดของโปรเจกต์

![HTML Auto Format](17-Input-Groups/008-vscode-html-auto-format-multiline-attributes.png)

VS Code จัดรูปแบบ (auto-format) attribute ของ input ให้ขึ้นบรรทัดใหม่แยกกันอัตโนมัติเมื่อมี attribute เยอะ

---

## 3. ห่อ Input และ Button ด้วย `<div class="input-group">`

![Div Input Group Wrap](17-Input-Groups/009-vscode-html-div-input-group-wrap-added.png)

Mosh เลือกทั้ง `<input>` และ `<button>` แล้วห่อด้วย `<div class="input-group">` ครอบทั้งคู่:

```html
<div class="input-group">
  <input type="text" class="input" placeholder="Enter domain name here..." />
  <button class="btn btn--accent">Search</button>
</div>
```

![Switch to Styles CSS](17-Input-Groups/010-vscode-switch-to-styles-css.png)

สลับไปที่ `styles.css` เพื่อเริ่มจัดสไตล์ให้กับกลุ่มนี้

---

## 4. สร้าง `.input-group` Selector

![Input Group Selector Created](17-Input-Groups/011-vscode-styles-css-input-group-selector-created.png)
![Border Property Typed](17-Input-Groups/012-vscode-styles-css-input-group-border-property-typed.png)
![Border CCC Value](17-Input-Groups/013-vscode-styles-css-input-group-border-ccc-value.png)

```css
.input-group {
  border: 1px solid #ccc;
}
```

---

## 5. รีแฟคเตอร์ #1: สร้าง Custom Property `--color-border`

Mosh สังเกตว่าค่าสี `#ccc` ถูกใช้ซ้ำในหลายจุด (ทั้งใน `.input` จากคลิปก่อน และ `.input-group` ใหม่) จึงตัดสินใจแยกเป็น CSS Custom Property เพื่อความเป็น DRY (Don't Repeat Yourself)

![Root Color Property Intellisense](17-Input-Groups/014-vscode-root-color-property-name-intellisense.png)
![Root Color Border Added](17-Input-Groups/015-vscode-root-color-border-hash-ccc-added.png)

ใน `:root` เพิ่มตัวแปรใหม่:

```css
:root {
  --color-primary: #2584ff;
  --color-secondary: #00d9ff;
  --color-accent: #ff3400;
  --color-headings: #1b0760;
  --color-body: #918ca4;
  --color-border: #ccc;
}
```

![Recap 1](17-Input-Groups/016-vscode-styles-css-recap-after-color-border.png)
![Recap 2](17-Input-Groups/017-vscode-styles-css-recap-2.png)
![Recap 3](17-Input-Groups/018-vscode-styles-css-recap-3.png)
![Recap 4](17-Input-Groups/019-vscode-styles-css-recap-4.png)
![Root Intellisense Noise](17-Input-Groups/020-vscode-root-color-border-intellisense-moz-noise.png)
![Root Empty Value](17-Input-Groups/021-vscode-root-color-border-value-empty.png)

### ใช้ VS Code Find (Cmd+F) หาทุกจุดที่ใช้ `#ccc`

![Input Border CCC Cursor](17-Input-Groups/022-vscode-input-class-border-ccc-cursor.png)

กลับไปที่ `.input` (จากคลิป 16) วาง cursor ไว้ที่ `#ccc`

![Var Dropdown](17-Input-Groups/023-vscode-input-class-var-dropdown-color-border.png)

พิมพ์ `color-` แล้ว IntelliSense แสดงตัวแปรทั้งหมดที่มีใน `:root` ให้เลือก รวมถึง `--color-border` ตัวใหม่

![Border Var Applied](17-Input-Groups/024-vscode-input-class-border-var-color-border-applied.png)

```css
.input {
  border: 1px solid var(--color-border);
}
```

![Find Widget Search CCC](17-Input-Groups/025-vscode-find-widget-search-ccc-2-of-2.png)

Mosh เปิด **Find widget** (Cmd+F) พิมพ์ `ccc` เพื่อค้นหาว่ายังมีจุดไหนในไฟล์ที่ใช้ `#ccc` แบบ hardcode อยู่อีกหรือไม่ — ผลลัพธ์แสดง **"2 of 2"** หมายถึงพบ 2 จุด (จุดหนึ่งคือ `.input-group` ที่เพิ่งสร้าง)

> 🔍 **เทคนิคสำคัญ:** การใช้ Find (Cmd+F) เพื่อค้นหาค่าที่ hardcode ไว้ทั้งไฟล์ เป็นวิธีตรวจสอบที่รวดเร็วก่อนจะรีแฟคเตอร์เป็น CSS Variable ให้ครบทุกจุด ป้องกันไม่ให้มีจุดใดตกหล่น

![Input Group Second Match](17-Input-Groups/026-vscode-input-group-border-ccc-second-match.png)

พบ match ที่สองใน `.input-group`

![Border Var Applied 2](17-Input-Groups/027-vscode-input-group-border-var-color-border-applied.png)

```css
.input-group {
  border: 1px solid var(--color-border);
}
```

---

## 6. รีแฟคเตอร์ #2: สร้าง Custom Property `--border-radius`

![Border Radius Typing](17-Input-Groups/028-vscode-input-group-border-radius-typing-autocomplete.png)
![Border Radius 30px Added](17-Input-Groups/029-vscode-input-group-border-radius-30px-added.png)

```css
.input-group {
  border: 1px solid var(--color-border);
  border-radius: 30px;
}
```

![Input Full Properties Recap](17-Input-Groups/030-vscode-input-class-full-properties-recap.png)

Mosh สังเกตว่า `border-radius: 30px` ก็ถูกใช้ซ้ำใน `.input` ด้วย (จากคลิป 16) จึงรีแฟคเตอร์อีกรอบ

![Root Border Radius Typing](17-Input-Groups/031-vscode-root-border-radius-property-name-typing.png)
![Root Border Radius Added](17-Input-Groups/032-vscode-root-border-radius-30px-variable-added.png)
![Root Full Recap](17-Input-Groups/033-vscode-root-full-variables-recap.png)

```css
:root {
  --color-primary: #2584ff;
  --color-secondary: #00d9ff;
  --color-accent: #ff3400;
  --color-headings: #1b0760;
  --color-body: #918ca4;
  --color-border: #ccc;
  --border-radius: 30px;
}
```

![Input Border Radius Var Typing](17-Input-Groups/034-vscode-input-border-radius-var-border-radius-typing.png)
![Input Border Radius Var Applied](17-Input-Groups/035-vscode-input-border-radius-var-border-radius-applied.png)

```css
.input {
  border-radius: var(--border-radius);
  border: 1px solid var(--color-border);
  color: var(--color-headings);
  font-size: 2rem;
  outline: 0;
  padding: 1.5rem 3.5rem;
}
```

![Input Group Before Refactor](17-Input-Groups/036-vscode-input-group-border-radius-30px-before-refactor.png)

### สำรวจ Hover Documentation ใน VS Code

![MDN Hover Tooltip](17-Input-Groups/037-vscode-input-group-border-radius-mdn-hover-tooltip.png)

เมื่อวางเมาส์ไว้ที่ property `border-radius` VS Code แสดง tooltip เอกสารอ้างอิงจาก MDN ทันที: *"Defines the radii of the outer border edge. Syntax: `<length-percentage>{1,4} [/ <length-percentage>{1,4}]?` — MDN Reference"*

> 📖 **เทคนิค VS Code:** การ hover เมาส์ไว้ที่ CSS property ใดๆ จะแสดงคำอธิบายและ syntax reference จาก MDN แบบ inline ทันที ไม่ต้องเปิดเบราว์เซอร์ค้นหาเอง ช่วยประหยัดเวลาในการเรียนรู้ property ใหม่ๆ

![Input Group Var Applied](17-Input-Groups/038-vscode-input-group-border-radius-var-border-radius-applied.png)

```css
.input-group {
  border: 1px solid var(--color-border);
  border-radius: var(--border-radius);
}
```

---

## 7. ใช้ Flexbox จัดเรียง Input และ Button ในแนวนอน

![Display Flex Typing](17-Input-Groups/039-vscode-input-group-display-flex-typing.png)
![Display Flex Autocomplete](17-Input-Groups/040-vscode-input-group-display-flex-autocomplete.png)
![Display Flex Added](17-Input-Groups/041-vscode-input-group-display-flex-added.png)

```css
.input-group {
  border: 1px solid var(--color-border);
  border-radius: var(--border-radius);
  display: flex;
}
```

![Browser Pill Shape Recap](17-Input-Groups/042-browser-input-group-pill-shape-recap.png)

ทดสอบในเบราว์เซอร์ — เห็น input และปุ่มอยู่ในกรอบเดียวกันแล้ว แต่ยังมีปัญหาเรื่องเส้นขอบซ้อนกัน (double border) ระหว่าง `.input` เดิมกับ `.input-group` ใหม่

---

## 8. แก้ปัญหา Double Border ด้วย Descendant Selector

![Input Group Recap](17-Input-Groups/043-vscode-input-group-recap-after-flex.png)
![Input Selector Typing](17-Input-Groups/044-vscode-input-group-input-selector-typing.png)
![Border 0 Selector Created](17-Input-Groups/045-vscode-input-group-input-border-0-selector-created.png)

Mosh สร้าง selector ใหม่แบบ **descendant combinator** (เว้นวรรคระหว่าง 2 selector) เพื่อ target เฉพาะ `.input` ที่อยู่ **ภายใน** `.input-group` เท่านั้น:

```css
.input-group .input {
  border: 0;
}
```

![Browser No Double Border](17-Input-Groups/046-browser-input-group-no-double-border.png)

ทดสอบในเบราว์เซอร์ — เส้นขอบซ้อนกันหายไปแล้ว เหลือแค่กรอบเดียวรอบกลุ่มทั้งหมด

> 🎯 **แนวคิดสำคัญ (Descendant Selector):** `.input-group .input { }` (มีช่องว่างคั่นระหว่าง selector ทั้งสอง) หมายถึง "เลือก element ที่มี class `.input` ที่อยู่เป็นลูกหลาน (descendant) ของ element ที่มี class `.input-group`" ซึ่งต่างจาก `.input-group.input` (ไม่มีช่องว่าง) ที่หมายถึง "element เดียวที่มีทั้งสอง class พร้อมกัน" เทคนิคนี้ทำให้ปรับสไตล์ของ `.input` เฉพาะเมื่ออยู่ในบริบทของ input-group โดยไม่กระทบ `.input` ที่ใช้เดี่ยวๆ ที่อื่น

---

## 9. Bug: Flexbox ไม่ขยาย Input ให้เต็มพื้นที่

![Browser Flex Bug](17-Input-Groups/047-browser-input-group-flex-bug-button-pushed-right.png)

เมื่อขยายหน้าต่างเบราว์เซอร์ให้กว้างขึ้น พบปัญหา: input ยังคงมีความกว้างเท่าเดิม (ตามขนาดเนื้อหา) ในขณะที่ปุ่ม SEARCH ถูกดันไปอยู่ชิดขวาสุดของกล่อง โดยมีพื้นที่ว่างเปล่าตรงกลาง

![DevTools Button Inspect](17-Input-Groups/048-devtools-button-box-model-inspect.png)
![DevTools Button Margin](17-Input-Groups/049-devtools-button-box-model-margin-10.png)

Mosh เปิด Chrome DevTools ตรวจสอบ box model ของปุ่ม (`<button class="btn btn--accent">`) ผ่าน Computed panel พบว่าปุ่มมี `margin: 10px` มาจาก **user-agent stylesheet** (ค่า default ของเบราว์เซอร์สำหรับ `<button>`)

---

## 10. แก้ไขด้วย `flex-grow`

![Flex Grow Added](17-Input-Groups/050-vscode-input-group-input-flex-grow-1-added.png)

```css
.input-group .input {
  border: 0;
  flex-grow: 1;
}
```

![Flex Grow Recap](17-Input-Groups/051-vscode-input-group-input-flex-grow-recap.png)
![Media Query Recap](17-Input-Groups/052-vscode-media-query-recap-after-flex-grow.png)

> 🔑 **แนวคิดสำคัญ (Flexbox `flex-grow`):** เมื่อ container มี `display: flex` ลูกๆ (flex items) จะเรียงตัวในแนวนอนตามค่าเริ่มต้น แต่จะไม่ขยายเพื่อเติมเต็มพื้นที่ว่างเอง เว้นแต่จะกำหนด `flex-grow` ให้มีค่ามากกว่า 0 การตั้งค่า `flex-grow: 1` ให้กับ `.input` ทำให้มันดึงพื้นที่ว่างทั้งหมดที่เหลือมาเป็นของตัวเอง ในขณะที่ปุ่มยังคงมีขนาดตามเนื้อหา (content-based width) เหมือนเดิม

### เพิ่ม margin เล็กน้อยให้ปุ่มดูมีระยะห่างจากขอบ

![Button Margin Typing](17-Input-Groups/053-vscode-input-group-btn-margin-typing.png)

```css
.input-group .btn {
  margin: 4px;
}
```

![DevTools Margin 4 Inspect](17-Input-Groups/054-devtools-button-box-model-margin-4-inspect.png)
![DevTools Sources Margin 4](17-Input-Groups/055-devtools-sources-panel-button-margin-4.png)

ตรวจสอบผ่าน DevTools อีกครั้ง ยืนยันว่าปุ่มตอนนี้มี margin เพียง 4px รอบด้าน ทำให้เห็นเป็นช่องว่างเล็กๆ ระหว่างปุ่มกับกรอบของ input-group (ดูเป็นปุ่มลอยอยู่ในกล่องแบบมีระยะห่างสวยงาม)

![Browser Long Text Test](17-Input-Groups/056-browser-input-group-long-text-overflow-test.png)

ทดสอบพิมพ์ข้อความยาวๆ ลงในช่อง input เพื่อยืนยันว่า `flex-grow: 1` ทำงานถูกต้อง — input ขยายเต็มพื้นที่ที่เหลือทั้งหมดโดยไม่ดันปุ่มออกนอกกรอบ

---

## 11. ทดลอง: สลับลำดับ HTML ระหว่าง Input กับ Button

![HTML Recap Order](17-Input-Groups/057-vscode-html-recap-input-group-order.png)
![HTML Swap Order](17-Input-Groups/058-vscode-html-swap-button-before-input.png)
![HTML Order Swapped](17-Input-Groups/059-vscode-html-button-input-order-swapped.png)

Mosh ทดลองสลับตำแหน่งของ `<button>` ให้มาอยู่ **ก่อน** `<input>` ในโค้ด HTML:

```html
<div class="input-group">
  <button class="btn btn--accent">Search</button>
  <input type="text" class="input" placeholder="Enter domain name here..." />
</div>
```

![Browser Button Left](17-Input-Groups/060-browser-input-group-button-left-input-right.png)

ผลลัพธ์ในเบราว์เซอร์: ปุ่ม SEARCH ย้ายไปอยู่ด้านซ้าย ส่วน input (ที่ยังคงมี `flex-grow: 1`) ขยายเต็มพื้นที่ด้านขวาแทน

![DevTools Computed Recap](17-Input-Groups/061-devtools-input-group-button-computed-box-model.png)
![HTML Recap Detail](17-Input-Groups/062-vscode-html-recap-order-swap-detail.png)
![HTML Detail 2](17-Input-Groups/063-vscode-html-order-swap-detail-2.png)
![DevTools Recap](17-Input-Groups/064-devtools-input-group-recap-computed.png)

> 🔀 **แนวคิดสำคัญ (Flexbox ตามลำดับ DOM):** ค่า default ของ Flexbox คือแสดงผล flex items **ตามลำดับที่ปรากฏใน HTML** (source order) การจะเปลี่ยนตำแหน่งการแสดงผลที่ง่ายที่สุดคือการสลับลำดับ element ใน HTML โดยตรง (ซึ่ง Flexbox ก็มี property `order` ที่สามารถเปลี่ยนลำดับการแสดงผลได้โดยไม่ต้องแก้ HTML แต่ Mosh ยังไม่ได้สอน property นี้ในคลิปนี้)

---

## 12. เปลี่ยนปุ่มเป็นไอคอนเพื่อทดสอบความยืดหยุ่น

![Quick Open Icons](17-Input-Groups/065-vscode-quick-open-file-switcher-icons-html.png)

Mosh ใช้ Quick Open (Cmd+P) เพื่อเปิดไฟล์ `components/icons.html` ซึ่งเป็นไฟล์ตัวอย่างไอคอนต่างๆ ที่เก็บไว้แยกต่างหาก (Component Library pattern ที่ใช้มาตลอดคอร์ส)

![Icons HTML Markup](17-Input-Groups/066-vscode-icons-html-wordpress-svg-sprite-markup.png)

ดูโครงสร้าง markup ของไอคอน:

```html
<span class="icon-container">
  <svg class="icon icon--primary">
    <use xlink:href="images/sprite.svg#wordpress"></use>
  </svg>
</span>
```

![Index HTML Swap Icon](17-Input-Groups/067-vscode-index-html-input-group-swap-in-icon-span.png)

คัดลอกโค้ดนี้มาใส่แทนที่ `<button>` ใน `index.html` ชั่วคราวเพื่อทดสอบว่า `.input-group` (ที่ใช้ Flexbox) รองรับเนื้อหาประเภทอื่นนอกจาก `<button>` ได้หรือไม่

![Browser WordPress Icon](17-Input-Groups/068-browser-input-group-wordpress-icon-instead-of-button.png)

ผลลัพธ์ในเบราว์เซอร์: ไอคอน WordPress แสดงแทนที่ปุ่ม โดยยังคงอยู่ในกรอบ pill shape เดียวกัน แสดงให้เห็นว่าโครงสร้าง Flexbox ที่วางไว้มีความยืดหยุ่น รองรับเนื้อหาประเภทใดก็ได้

![Browser Garbage Text Test](17-Input-Groups/069-browser-input-group-garbage-text-overflow-test.png)

ทดสอบพิมพ์ข้อความยาวมากๆ อีกครั้งเพื่อยืนยันว่า layout ยังคงทำงานถูกต้องแม้เปลี่ยนเนื้อหาฝั่งขวาเป็นไอคอนแล้ว

---

## 13. แนวคิดสำคัญ: Bottom Up vs Top Down

![Concept Slide Bottom Up](17-Input-Groups/070-concept-slide-bottom-up-components-first.png)
![Concept Slide Comparison](17-Input-Groups/071-concept-slide-bottom-up-vs-top-down.png)

Mosh หยุดพักเพื่ออธิบายแนวคิดเชิงปรัชญาของการสร้าง UI ที่ใช้มาตลอดคอร์สนี้ ผ่านสไลด์เปรียบเทียบ 2 แนวทาง:

- **BOTTOM UP (Components First)** — แนวทางที่คอร์สนี้ใช้: เริ่มจากสร้าง**ส่วนประกอบย่อยๆ** ก่อน (list, button, input, input-group ฯลฯ) แต่ละชิ้นแยกทดสอบในไฟล์ component ของตัวเอง (เช่น `components/lists.html`, `components/buttons.html`) จนกว่าจะสมบูรณ์ แล้วค่อยประกอบร่างรวมเป็นหน้าเว็บทั้งหน้าในภายหลัง
- **TOP DOWN** — แนวทางตรงข้าม: เริ่มจากออกแบบ/สร้างหน้าเว็บทั้งหน้าก่อน แล้วค่อยแตกย่อยลงมาเป็นส่วนประกอบย่อยทีหลัง

> 🏗️ **แนวคิดสำคัญ (Bottom Up Development):** การสร้างส่วนประกอบ UI แบบแยกส่วน (isolated component) ก่อนแล้วค่อยประกอบรวมมีข้อดีคือ ทดสอบและปรับแต่งแต่ละชิ้นได้ง่ายโดยไม่ต้องพะวงกับบริบทของทั้งหน้า ส่วนประกอบที่ได้ยังนำกลับมาใช้ซ้ำ (reusable) ได้ในหลายที่ของโปรเจกต์ ซึ่งเป็นเหตุผลที่ตลอดคอร์สนี้ Mosh สร้างไฟล์แยกในโฟลเดอร์ `components/` สำหรับแต่ละ UI element ก่อนจะนำไปประกอบใน `index.html` จริง

---

## 14. เจาะลึกต่อด้วย DevTools

![Browser Icon Recap](17-Input-Groups/072-browser-input-group-icon-recap.png)
![Browser Typed Mosh](17-Input-Groups/073-browser-input-typed-mosh-context-menu.png)
![DevTools Shadow Root Mosh](17-Input-Groups/074-devtools-input-shadow-root-mosh-text-inspected.png)

Mosh พิมพ์คำว่า "Mosh" ลงในช่อง input แล้วเปิด DevTools ตรวจสอบโครงสร้างภายในอีกครั้ง (ต่อเนื่องจากการอธิบาย shadow DOM ในคลิป 16) คราวนี้แสดงให้เห็นทั้ง placeholder div (ที่ซ่อนอยู่เพราะมีข้อความแล้ว) และ text node ที่ผู้ใช้พิมพ์เข้าไปจริง

![DevTools Computed Icon Variant](17-Input-Groups/075-devtools-input-computed-box-model-icon-variant.png)
![DevTools Computed Icon Variant 2](17-Input-Groups/076-devtools-input-computed-box-model-icon-variant-2.png)
![DevTools Computed Highlighted](17-Input-Groups/077-devtools-input-computed-box-model-icon-variant-highlighted.png)

ตรวจสอบ Computed panel ของ `.input` เพื่อดู box model ที่แท้จริง (margin, border, padding, ขนาดเนื้อหา) เมื่อมีไอคอนอยู่ข้างๆ แทนปุ่ม

---

## 15. ปรับแต่ง Padding เพิ่มเติม

![Padding Property Added](17-Input-Groups/078-vscode-input-group-input-padding-property-added.png)
![Padding Value Typing](17-Input-Groups/079-vscode-input-group-input-padding-value-typing.png)

กลับไปที่ `styles.css` เพิ่ม property `padding` ให้กับ `.input-group .input` เพื่อปรับระยะห่างภายในให้เหมาะสมยิ่งขึ้นเมื่ออยู่ในบริบทของ input-group

![Browser Final Recap](17-Input-Groups/080-browser-input-group-icon-final-recap.png)
![HTML Final Recap](17-Input-Groups/081-vscode-html-final-recap-icon-container-span.png)

ทดสอบผลลัพธ์สุดท้ายในเบราว์เซอร์และทบทวนโครงสร้าง HTML ทั้งหมดอีกครั้งก่อนจบคลิป

---

## สรุปภาพรวมของคลิปนี้

| หัวข้อ | รายละเอียด |
|---|---|
| Element หลัก | `<div class="input-group">` ห่อ `<input class="input">` + `<button class="btn btn--accent">` |
| CSS Properties/แนวคิดใหม่ | `display: flex`, `flex-grow`, descendant selector (`.input-group .input`) |
| CSS Variables ใหม่ | `--color-border: #ccc`, `--border-radius: 30px` |
| BEM | ไม่มี Element/Modifier ใหม่ในคลิปนี้ ใช้ class เดี่ยว `.input-group` ร่วมกับ descendant selector |
| เครื่องมือ | VS Code (Find widget, Quick Open, hover MDN docs), Chrome DevTools (Computed panel), Photoshop |

## แนวคิดสำคัญที่ได้จากคลิปนี้

1. **Descendant selector** (`.input-group .input`) ใช้เลือก element ที่อยู่ *ภายใน* element อื่น แตกต่างจาก selector ที่ติดกัน (`.a.b`) ซึ่งหมายถึง element เดียวที่มีทั้งสอง class
2. การรีแฟคเตอร์ค่าที่ซ้ำกันในหลายจุด (เช่น `#ccc`, `30px`) ให้เป็น **CSS Custom Property** ทำให้โค้ดเป็น DRY มากขึ้น และแก้ทีเดียวมีผลทุกจุด
3. VS Code **Find widget** (Cmd+F) ช่วยตรวจสอบว่ายังมีค่า hardcode หลงเหลืออยู่ในไฟล์หรือไม่ ก่อนรีแฟคเตอร์เป็นตัวแปร
4. **Flexbox**: `display: flex` ทำให้ลูกเรียงตัวแนวนอน แต่ต้องใช้ `flex-grow` เพื่อให้ลูกตัวใดตัวหนึ่งขยายเต็มพื้นที่ว่างที่เหลือ
5. Flexbox แสดงผลตามลำดับ **DOM/HTML source order** เป็นค่าเริ่มต้น การสลับตำแหน่งการแสดงผลที่ง่ายที่สุดคือสลับลำดับ element ใน HTML
6. แนวคิด **Bottom Up (Components First)**: สร้างส่วนประกอบ UI แยกทีละชิ้นในไฟล์ของตัวเองก่อน แล้วค่อยประกอบรวมเป็นหน้าเว็บทั้งหน้า ตรงข้ามกับแนวทาง Top Down
7. VS Code แสดง **MDN documentation แบบ hover** เมื่อวางเมาส์บน CSS property ช่วยเรียนรู้ syntax ได้ทันทีโดยไม่ต้องออกจาก editor

---

*สรุปจากคลิปที่ 17 ของคอร์ส "Building a Web Site" (Moshify Project) สอนโดย Mosh Hamedani — codewithmosh.com*
