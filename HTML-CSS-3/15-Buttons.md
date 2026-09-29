# HTML-CSS-3: 15 - Buttons (Buttons)

**ไฟล์ต้นทาง:** 15-Buttons.mp4

▶️ [ดูวิดีโอ](../../HTML-CSS-3/15-Buttons.mp4)

---

## ภาพรวมคลิปนี้

![สไลด์ชื่อคลิป Buttons](15-Buttons/001-title-slide-buttons.png)

คลิปนี้เป็นคลิปที่ยาวและมีเนื้อหาเยอะที่สุดคลิปหนึ่งในซีรีส์ Mosh สอนเรื่อง **Buttons (ปุ่ม)** ซึ่งเป็น component ที่สำคัญมากในทุกเว็บไซต์ โดยเริ่มจากการดูดีไซน์ใน Photoshop ที่มีปุ่มหลายรูปแบบ ทั้งปุ่ม "GET STARTED" สีแดง/ส้ม บนพื้นหลังสีดำ

![ดีไซน์ Photoshop: ปุ่ม GET STARTED สีแดงบนพื้นดำ](15-Buttons/002-photoshop-get-started-button-design-cloud-hosting.png)

ปุ่ม "BUY NOW" หลายแบบ (สีขาว มีขอบ, สีกรมท่า)

![ดีไซน์ Photoshop: ปุ่ม BUY NOW](15-Buttons/003-photoshop-buy-now-button-design-recap.png)

ปุ่ม "SEARCH" สีแดงคู่กับช่องค้นหาชื่อโดเมน

![ดีไซน์ Photoshop: ปุ่ม SEARCH คู่กับช่องค้นหาโดเมน](15-Buttons/004-photoshop-search-button-design-domain-pricing.png)

และปุ่ม "BUY NOW" สีกรมท่าเข้มในส่วนของ pricing plan

![ดีไซน์ Photoshop: ปุ่ม BUY NOW สีกรมท่าใน pricing plan](15-Buttons/005-photoshop-dark-navy-buy-now-button-pricing-plan.png)

![ดีไซน์ Photoshop: ทบทวนปุ่ม GET STARTED สีฟ้า](15-Buttons/006-photoshop-cyan-get-started-button-recap.png)

![ดีไซน์ Photoshop: ภาพรวมปุ่มหลากสี](15-Buttons/007-photoshop-buttons-various-colors-overview.png)

![ดีไซน์ Photoshop: ภาพรวมปุ่มหลากสี เพิ่มเติม](15-Buttons/008-photoshop-buttons-various-colors-overview-2.png)

เป้าหมายของคลิปนี้คือสร้าง CSS component `.btn` แบบ BEM ที่มี Modifier หลายแบบ (`--primary`, `--secondary`, `--accent`, `--block`, `--outline`) รวมถึงสอนเรื่อง **`:hover` pseudo-class**, การใช้ทั้ง `<button>` และ `<a>` เป็นปุ่มได้เหมือนกัน, และแนะนำ **CSS Reset ระดับ Global** ด้วย `box-sizing: border-box` เป็นครั้งแรกในซีรีส์

---

## 1. สร้าง Block พื้นฐาน `.btn`

Mosh เริ่มต้นด้วยการสร้าง markup ใน `index.html`

```html
<button class="btn btn--primary">Buy Now</button>
```

![HTML: button class btn btn--primary ถูกสร้างขึ้น](15-Buttons/009-vscode-index-html-button-class-btn-btn-primary-created.png)

จากนั้นสลับไปที่ `styles.css` เพิ่ม comment `/* Buttons */` แล้วเริ่มพิมพ์ selector `.btn`

![พิมพ์ comment Buttons และ selector .btn](15-Buttons/010-vscode-styles-css-buttons-comment-btn-selector-typing.png)

ภายในบล็อกนี้เริ่มด้วย:

```css
.btn {
  font-size: 1.8rem;
  font-weight: 600;
}
```

![font-size 1.8rem, font-weight 600](15-Buttons/011-vscode-btn-font-size-1-8rem-font-weight-600.png)

จากนั้นพิมพ์ `text-transform`

![พิมพ์ text-transform](15-Buttons/012-vscode-btn-text-transform-typing.png)

โดย IntelliSense แนะนำค่า `uppercase`

![IntelliSense แนะนำ text-transform: uppercase](15-Buttons/013-vscode-btn-text-transform-uppercase-suggestion.png)

จากนั้นเพิ่ม `padding: 2rem 3rem;`

![พิมพ์ padding: 2rem 3rem](15-Buttons/014-vscode-btn-padding-2rem-3rem-typing.png)

ทดสอบผลลัพธ์ในเบราว์เซอร์ — ปุ่มมีขนาดใหญ่ขึ้นและมีมุมโค้งเล็กน้อย (เพราะเบราว์เซอร์ให้ `<button>` มี border เริ่มต้นที่ทำให้มุมโค้งนิดหน่อยโดยอัตโนมัติ)

![เบราว์เซอร์: ปุ่ม Buy Now ก่อนใส่ border-radius](15-Buttons/015-browser-buy-now-button-rounded-corners-before-border-radius.png)

> **คำอธิบาย property เบื้องต้น:**
> - `font-size: 1.8rem;` และ `font-weight: 600;` — กำหนดขนาดและความหนาตัวอักษรให้ปุ่มดูเด่นชัด
> - `text-transform: uppercase;` — แปลงข้อความให้เป็นตัวพิมพ์ใหญ่ทั้งหมดโดยอัตโนมัติ (ไม่ต้องพิมพ์ตัวพิมพ์ใหญ่ใน HTML เอง) ตรงกับดีไซน์ที่ใช้ตัวพิมพ์ใหญ่ทุกปุ่ม
> - `padding: 2rem 3rem;` — ค่าที่สองในรูปแบบ shorthand หมายถึง padding บน-ล่าง 2rem และซ้าย-ขวา 3rem ทำให้ปุ่มมีพื้นที่ภายในกว้างพอสมควร

---

## 2. เพิ่ม `border-radius` และล้าง `border`

Mosh พิมพ์ property ใหม่

![พิมพ์ border-radius](15-Buttons/016-vscode-btn-border-radius-property-typing.png)

ตั้งค่าเป็น `40px`

```css
border-radius: 40px;
```

![border-radius: 40px](15-Buttons/017-vscode-btn-border-radius-40px-value.png)

จากนั้นเพิ่ม `border: 0;` เพื่อล้าง border เริ่มต้นของเบราว์เซอร์ที่ `<button>` มีอยู่แล้ว (เพราะ `<button>` เป็น form element ที่เบราว์เซอร์ใส่ style พิเศษให้)

![พิมพ์ border: 0](15-Buttons/018-vscode-btn-border-0-typing.png)

ทดสอบผลลัพธ์ในเบราว์เซอร์ — ปุ่มกลายเป็นรูปทรงแคปซูล (pill shape) โค้งมนเต็มที่ตามดีไซน์

![เบราว์เซอร์: ปุ่ม Buy Now เป็นรูปทรงแคปซูลโค้งมน](15-Buttons/019-browser-buy-now-button-pill-shape-rounded-fully.png)

โค้ด `.btn` สมบูรณ์ในขั้นตอนนี้:

```css
.btn {
  border-radius: 40px;
  border: 0;
  font-size: 1.8rem;
  font-weight: 600;
  padding: 2rem 3rem;
  text-transform: uppercase;
}
```

![บล็อก .btn ครบทุก property พื้นฐาน](15-Buttons/020-vscode-btn-block-complete-all-base-properties.png)

> **คำอธิบาย:**
> - `border-radius: 40px;` — ค่าความโค้งของมุม เมื่อค่านี้มากกว่าครึ่งหนึ่งของความสูงปุ่ม จะทำให้ขอบซ้าย-ขวากลายเป็นครึ่งวงกลมสมบูรณ์ (capsule/pill shape) ซึ่งเป็นทรงปุ่มยอดนิยมในดีไซน์เว็บสมัยใหม่
> - `border: 0;` — เอา border เริ่มต้นของ `<button>` (ซึ่งบางเบราว์เซอร์แสดงเป็นเส้นกรอบบางๆ) ออกไปทั้งหมด

---

## 3. สร้าง BEM Modifier ทั้ง 3 สี: `--primary`, `--secondary`, `--accent`

### Modifier 1: `.btn--primary`

พิมพ์ selector ใหม่

![พิมพ์ selector .btn--primary](15-Buttons/021-vscode-btn-primary-selector-typing-modifier.png)

พิมพ์ `background: var(--color-primary);`

![พิมพ์ background var color-primary](15-Buttons/022-vscode-btn-primary-background-var-color-primary-typing.png)

พิมพ์ `color: #fff;`

![พิมพ์ color fff](15-Buttons/023-vscode-btn-primary-color-fff-typing.png)

โค้ดสมบูรณ์:

```css
.btn--primary {
  background: var(--color-primary);
  color: #fff;
}
```

![บล็อก .btn--primary สมบูรณ์](15-Buttons/024-vscode-btn-primary-block-complete.png)

ทดสอบในเบราว์เซอร์ — ปุ่มเปลี่ยนเป็นสีน้ำเงิน (primary)

![เบราว์เซอร์: ปุ่ม Buy Now สีน้ำเงิน primary](15-Buttons/025-browser-buy-now-button-blue-primary-color-applied.png)

### Modifier 2: `.btn--secondary`

พิมพ์ selector

![พิมพ์ selector .btn--secondary](15-Buttons/026-vscode-btn-secondary-selector-typing.png)

พิมพ์ `background: var(--color-secondary);`

![พิมพ์ background var color-secondary](15-Buttons/027-vscode-btn-secondary-background-var-color-secondary-typing.png)

พิมพ์ `color: #fff;`

![พิมพ์ color fff สำหรับ secondary](15-Buttons/028-vscode-btn-secondary-color-fff-typing.png)

โค้ดสมบูรณ์:

```css
.btn--secondary {
  background: var(--color-secondary);
  color: #fff;
}
```

![บล็อก .btn--secondary สมบูรณ์](15-Buttons/029-vscode-btn-secondary-block-complete.png)

กลับไปที่ `index.html` เปลี่ยน class ของปุ่มทดสอบเป็น `btn--secondary`

![HTML: เปลี่ยน class เป็น btn btn--secondary](15-Buttons/030-vscode-index-html-class-btn-btn-secondary-typing.png)

ทดสอบในเบราว์เซอร์ — ปุ่มเปลี่ยนเป็นสีฟ้าอมเขียว (cyan/secondary)

![เบราว์เซอร์: ปุ่ม Buy Now สีฟ้า secondary](15-Buttons/031-browser-buy-now-button-cyan-secondary-color-applied.png)

### Modifier 3: `.btn--accent`

พิมพ์ selector

![พิมพ์ selector .btn--accent](15-Buttons/032-vscode-btn-accent-selector-typing.png)

พิมพ์ `background: var(--color-accent);`

![พิมพ์ background var color-accent](15-Buttons/033-vscode-btn-accent-background-var-color-accent-typing.png)

เพิ่ม `color: #fff;` ให้ครบ

![color fff สำหรับ accent เสร็จสมบูรณ์](15-Buttons/034-vscode-btn-accent-color-fff-complete.png)

เปลี่ยน class ใน HTML เป็น `btn--accent` เพื่อทดสอบ

![HTML: เปลี่ยน class เป็น btn btn--accent](15-Buttons/035-vscode-index-html-class-btn-btn-accent-typing.png)

ทดสอบในเบราว์เซอร์ — ปุ่มเปลี่ยนเป็นสีแดง/ส้ม (accent)

![เบราว์เซอร์: ปุ่ม Buy Now สีแดง accent](15-Buttons/036-browser-buy-now-button-red-accent-color-applied.png)

ทบทวนโค้ดทั้ง 3 Modifier พร้อมกัน:

```css
.btn--primary {
  background: var(--color-primary);
  color: #fff;
}

.btn--secondary {
  background: var(--color-secondary);
  color: #fff;
}

.btn--accent {
  background: var(--color-accent);
  color: #fff;
}
```

![ทบทวนทั้ง 3 modifier primary secondary accent](15-Buttons/037-vscode-three-btn-modifiers-primary-secondary-accent-recap.png)

นำทั้ง 3 ปุ่มมาวางเทียบกันในเบราว์เซอร์ — เห็นสีน้ำเงิน ฟ้า และแดง เรียงกัน

![เบราว์เซอร์: ปุ่มทั้ง 3 สีเรียงกัน](15-Buttons/038-browser-three-buy-now-buttons-blue-cyan-red-side-by-side.png)

---

## 4. ใช้ `.btn` กับทั้ง `<button>` และ `<a>` ได้เหมือนกัน

Mosh อธิบายว่า class `.btn` (พร้อม Modifier) ไม่ได้ผูกติดกับ tag `<button>` เท่านั้น แต่สามารถใช้กับ `<a>` (ลิงก์) ได้เช่นกัน เพราะ CSS เพียงแค่มองหา class ไม่ได้สนใจว่า tag คืออะไร เขาพิมพ์ tag ใหม่

![พิมพ์ a tag พร้อม class btn--accent](15-Buttons/039-vscode-index-html-a-tag-btn-accent-typing.png)

```html
<a href="#" class="btn btn--accent">Buy Now</a>
```

![HTML: a href hash class btn btn--accent](15-Buttons/040-vscode-index-html-a-href-hash-class-btn-btn-accent.png)

วางไว้คู่กับ `<button>` เดิมที่มี class เดียวกัน

![HTML: button และ a tag ทั้งคู่มี class btn btn--accent](15-Buttons/041-vscode-index-html-button-and-a-tag-both-btn-accent.png)

ทดสอบในเบราว์เซอร์ — ทั้ง `<button>` และ `<a>` แสดงผลเหมือนกันทุกประการ (สีแดง, รูปทรงแคปซูล, ข้อความตัวพิมพ์ใหญ่)

![เบราว์เซอร์: button และ anchor tag แสดงผลเป็นปุ่มเหมือนกัน](15-Buttons/042-browser-button-and-anchor-tag-both-styled-as-buy-now.png)

> **ทำไมเรื่องนี้ถึงสำคัญ:** ในเว็บจริง บางครั้งเราต้องการปุ่มที่ "คลิกแล้วส่ง form" (ใช้ `<button type="submit">`) และบางครั้งต้องการปุ่มที่ "คลิกแล้วพาไปหน้าอื่น" (ใช้ `<a href="...">`) การออกแบบ class `.btn` ให้ไม่ผูกกับ tag ใดๆ ทำให้นำ style เดียวกันไปใช้ได้กับทั้งสองสถานการณ์ นี่คือหลักการออกแบบ CSS ที่ดี คือแยก "หน้าตา" (style) ออกจาก "พฤติกรรม" (HTML element type)

จากนั้นเพิ่ม `cursor: pointer;` ให้กับ `.btn` เพื่อให้แน่ใจว่าเมื่อเอาเมาส์ไปชี้ที่ปุ่ม (ไม่ว่าจะเป็น `<button>` หรือ `<a>`) จะแสดงเป็นรูปมือชี้ (pointer) เสมอ

![พิมพ์ cursor: pointer](15-Buttons/043-vscode-btn-cursor-pointer-property-typing.png)

![cursor: pointer เสร็จสมบูรณ์](15-Buttons/044-vscode-btn-cursor-pointer-complete.png)

ทดสอบในเบราว์เซอร์โดยเอาเมาส์ไปชี้ที่ปุ่มทั้งสองแบบ

![เบราว์เซอร์: ทดสอบ cursor pointer บนปุ่มทั้งสองแบบ](15-Buttons/045-browser-buy-now-buttons-cursor-pointer-hover-test.png)

> **หมายเหตุ:** โดยปกติ `<a>` จะแสดง cursor pointer อยู่แล้วโดยอัตโนมัติ แต่ `<button>` ในบางเบราว์เซอร์ (โดยเฉพาะ Safari) จะไม่แสดง cursor pointer โดย default ดังนั้นการเขียน `cursor: pointer;` ให้กับ `.btn` อย่างชัดเจนจึงเป็นแนวทางที่ปลอดภัยกว่า เพื่อให้ผลลัพธ์เหมือนกันในทุกเบราว์เซอร์

---

## 5. ป้องกันข้อความตัดบรรทัดด้วย `white-space: nowrap`

Mosh เพิ่ม property สุดท้ายให้กับ `.btn`

![พิมพ์ white-space: nowrap](15-Buttons/046-vscode-btn-white-space-nowrap-typing.png)

```css
white-space: nowrap;
```

> **คำอธิบาย:** `white-space: nowrap;` ป้องกันไม่ให้ข้อความภายในปุ่ม (เช่น "BUY NOW") ตัดขึ้นบรรทัดใหม่โดยไม่ได้ตั้งใจ ถ้าปุ่มมีความกว้างจำกัดหรือใช้ในพื้นที่แคบ ข้อความจะยังคงอยู่ในบรรทัดเดียวเสมอ ทำให้ปุ่มดูเป็นระเบียบไม่ว่าจะอยู่ในบริบทไหน

---

## 6. จัดเรียง CSS Properties ด้วย Command Palette

เช่นเดียวกับที่ทำในคลิป Badges ก่อนหน้า Mosh ใช้ VS Code Command Palette เพื่อจัดเรียง property ใน `.btn` ให้เป็นระเบียบตามตัวอักษร

![เปิด Command Palette พิมพ์ค้นหา Sort Lines](15-Buttons/047-vscode-command-palette-sort-lines-search.png)

ผลลัพธ์: properties ทั้งหมดถูกจัดเรียงตามตัวอักษร (a-z)

```css
.btn {
  border-radius: 40px;
  border: 0;
  cursor: pointer;
  font-size: 1.8rem;
  font-weight: 600;
  padding: 2rem 3rem;
  text-transform: uppercase;
  white-space: nowrap;
}
```

![บล็อก .btn properties ถูกจัดเรียงตามตัวอักษรแล้ว](15-Buttons/048-vscode-btn-properties-sorted-alphabetically.png)

![ทบทวนบล็อก .btn ฉบับสมบูรณ์ที่จัดเรียงแล้ว](15-Buttons/049-vscode-btn-block-final-sorted-recap.png)

ทดสอบผลลัพธ์สุดท้ายของทั้ง 3 สีในเบราว์เซอร์อีกครั้ง

![เบราว์เซอร์: ปุ่มทั้ง 3 สีผลลัพธ์สุดท้าย](15-Buttons/050-browser-buy-now-buttons-final-recap-three-colors.png)

---

## 7. เพิ่มเอฟเฟกต์ `:hover` ให้ปุ่ม (Pseudo-class)

นี่คือหัวข้อใหม่ที่สำคัญมากของคลิปนี้ — การเพิ่มการเปลี่ยนสีเมื่อเอาเมาส์ไปวางบนปุ่ม (hover)

Mosh พิมพ์ selector ใหม่

![พิมพ์ selector .btn--primary:hover](15-Buttons/051-vscode-btn-primary-hover-selector-typing.png)

ในตอนแรก เขาลองพิมพ์ค่าโดยใช้ฟังก์ชัน `lighten()`

![พิมพ์ background: lighten() ใน .btn--primary:hover](15-Buttons/052-vscode-btn-primary-hover-background-lighten-function-typing.png)

พยายามพิมพ์ `lighten(prim...)` เพื่ออ้างอิงตัวแปรสี primary

![พิมพ์ lighten(prim...) พร้อม autocomplete](15-Buttons/053-vscode-btn-primary-hover-lighten-prim-autocomplete.png)

> **ข้อควรระวังสำคัญ: `lighten()` ไม่ใช่ฟังก์ชันของ CSS มาตรฐาน!**
> ฟังก์ชัน `lighten()` (และ `darken()`) เป็นฟังก์ชันที่มีอยู่ใน **Sass/SCSS** (CSS preprocessor) เท่านั้น ไม่ใช่ฟังก์ชันของ CSS ธรรมดาที่เบราว์เซอร์เข้าใจโดยตรง เนื่องจากโปรเจกต์นี้เขียนด้วย CSS ธรรมดา (ไม่ได้ใช้ Sass) การพิมพ์ `lighten()` แบบนี้จะไม่ทำงานจริงในเบราว์เซอร์ — เป็นตัวอย่างที่ดีของความสับสนระหว่างฟีเจอร์ของ CSS กับฟีเจอร์ของ preprocessor ที่นักพัฒนาหลายคนพบเจอบ่อย

เมื่อทดสอบไม่ได้ผล Mosh จึงเปลี่ยนวิธีไปใช้ **Photoshop's Eyedropper Tool** เพื่อสุ่มตัวอย่างสี (sample color) จากดีไซน์จริง โดยเลือกสีที่ "อ่อนกว่า" สีปุ่มปกติเล็กน้อยด้วยตาเปล่า

![Photoshop: ใช้ eyedropper สุ่มสีปุ่ม GET STARTED สีแดง](15-Buttons/057-photoshop-eyedropper-tool-sampling-get-started-red-color.png)

![Photoshop Color Picker แสดงค่าสี fc3e0d](15-Buttons/061-photoshop-color-picker-foreground-color-fc3e0d-red.png)

จากนั้นกลับไปที่ VS Code พิมพ์ค่าสีที่เลือกไว้ (hex code) ลงไปตรงๆ แทนฟังก์ชัน `lighten()`

![พิมพ์ค่าสีที่เลือกจาก Photoshop ลงใน background](15-Buttons/058-vscode-btn-primary-hover-background-value-typing.png)

โค้ดสุดท้ายของ `.btn--primary:hover`:

```css
.btn--primary:hover {
  background: #3a8ffd;
}
```

![btn--primary:hover background 3a8ffd สมบูรณ์](15-Buttons/082-vscode-btn-primary-hover-fd4516-hex-secondary-block-recap.png)

> **บทเรียนสำคัญจากจุดนี้:** เมื่อ CSS ธรรมดาไม่มีฟังก์ชันปรับความสว่าง/มืดของสีในตัว (ต่างจาก Sass) วิธีแก้ปัญหาที่ Mosh ใช้คือการ **สุ่มตัวอย่างสี (sample) จากดีไซน์ต้นแบบด้วยเครื่องมือ Eyedropper ใน Photoshop โดยตรง** แล้วนำค่า hex ที่ได้มาใส่ใน CSS ตรงๆ นี่คือแนวทางปฏิบัติจริงในการทำงานร่วมกันระหว่างนักออกแบบ (designer) กับนักพัฒนา (developer) — เมื่อดีไซน์มีสี hover ที่กำหนดไว้แล้ว นักพัฒนาก็แค่สุ่มตัวอย่างสีนั้นมาใช้ ไม่จำเป็นต้องคำนวณเอง (ในโปรเจกต์ที่ใช้ Sass จริง อาจใช้ `darken(map-get($colors, "primary"), 10%)` แทนได้ แต่นั่นไม่ใช่ขอบเขตของคลิปนี้)

---

## 8. เพิ่ม `:hover` ให้ Modifier ที่เหลือ (Secondary, Accent)

ทำแบบเดียวกันกับ `.btn--secondary` — พิมพ์ selector ใหม่

![พิมพ์ selector .btn--secondary:hover](15-Buttons/067-vscode-btn-secondary-hover-selector-typing.png)

ใส่ค่าสีที่สุ่มมาจากดีไซน์:

```css
.btn--secondary:hover {
  background: #00c8eb;
}
```

![background 00c8eb hex ใน btn--secondary hover](15-Buttons/068-vscode-btn-secondary-hover-background-00c8eb-hex-value.png)

> **ข้อควรระวัง: การพิมพ์ selector ผิดพลาด (`.btn-secondary` แทน `.btn--secondary`)**
> ระหว่างขั้นตอนนี้ เกิดจุดที่น่าสังเกต — selector บางจุดในไฟล์ปรากฏเป็น `.btn-secondary:hover` (มีขีดกลางแค่ตัวเดียว) แทนที่จะเป็น `.btn--secondary:hover` (สองขีดกลางตามหลัก BEM Modifier) ซึ่งหากเกิดขึ้นจริงจะทำให้ selector นี้ **ไม่ตรงกับ class ใดๆ ในหน้าเว็บเลย** (เพราะ HTML ใช้ class `btn--secondary` มีสองขีด) ทำให้กฎ CSS นั้นกลายเป็น "โค้ดที่ตายแล้ว" (dead code) ไม่มีผลอะไรกับหน้าเว็บ

![selector .btn-secondary:hover ขีดกลางเดียว (จุดที่ต้องระวัง)](15-Buttons/073-vscode-btn-secondary-single-dash-typo-hover-selector.png)

> นี่คือตัวอย่างที่ดีมากว่าทำไมการตั้งชื่อ class ตามหลัก BEM ต้องระมัดระวังเรื่องจำนวนขีด (`-` เดี่ยว vs `--` คู่) ให้ถูกต้องเป๊ะทุกครั้ง เพราะ CSS จะไม่ error หรือเตือนอะไรเลยถ้า selector สะกดผิดแบบนี้ — มันแค่จะไม่ทำงานเงียบๆ เท่านั้นเอง ผู้เรียนควรฝึกตรวจสอบ selector ของตัวเองอย่างละเอียดเสมอ โดยเฉพาะกับ BEM ที่ใช้สัญลักษณ์ขีดกลางซ้ำกันหลายแบบ (`__` สำหรับ Element, `--` สำหรับ Modifier)

ต่อด้วย `.btn--accent:hover`

![พิมพ์ selector .btn--accent:hover](15-Buttons/074-vscode-btn-accent-hover-selector-typing.png)

![IntelliSense แนะนำ property background](15-Buttons/075-vscode-background-property-suggestions-list.png)

พิมพ์ค่าสี

![พิมพ์ค่าสี ec3 กำลังพิมพ์](15-Buttons/076-vscode-btn-accent-hover-background-ec3-hex-typing.png)

โค้ดสมบูรณ์:

```css
.btn--accent:hover {
  background: #ec3000;
}
```

![background ec3000 สมบูรณ์](15-Buttons/080-vscode-btn-accent-hover-background-ec3000-complete.png)

ทดสอบผลลัพธ์ในเบราว์เซอร์ — เอาเมาส์ไปวางบนปุ่มแต่ละสี สีจะเปลี่ยนเป็นเฉดที่อ่อน/เข้มกว่าเดิมเล็กน้อย

![เบราว์เซอร์: ทดสอบ hover ปุ่มสีแดงและฟ้า](15-Buttons/081-browser-two-buy-now-buttons-red-cyan-hover-recap.png)

ทบทวนโค้ดทั้งหมดของ hover ทุก Modifier:

```css
.btn--primary:hover {
  background: #3a8ffd;
}

.btn--secondary:hover {
  background: #00c8eb;
}

.btn--accent:hover {
  background: #ec3000;
}
```

![ทบทวนโค้ด hover ของ primary secondary accent ทั้งหมด](15-Buttons/083-vscode-btn-primary-hover-3a8ffd-secondary-hover-00c8eb-recap.png)

> **คำอธิบายหลักการ `:hover` pseudo-class:**
> `:hover` เป็น pseudo-class ที่ CSS จะนำกฎมาใช้ก็ต่อเมื่อผู้ใช้เอาเมาส์ไปวางอยู่เหนือ element นั้น เขียนต่อท้าย selector ด้วยเครื่องหมาย colon (`:`) เช่น `.btn--primary:hover` หมายถึง "เมื่อเมาส์อยู่เหนือ element ที่มี class `btn--primary`" เป็นเทคนิคพื้นฐานที่ทำให้เว็บไซต์มี **interactivity** (การตอบสนองต่อผู้ใช้) แม้จะไม่มี JavaScript เลยก็ตาม — ใช้ได้แค่ CSS ล้วนๆ

---

## 9. เพิ่ม Modifier `.btn--block` (ปุ่มเต็มความกว้าง)

Mosh สร้าง Modifier ใหม่สำหรับปุ่มที่ต้องการให้กว้างเต็มพื้นที่ (full width)

![พิมพ์ selector .btn--block](15-Buttons/054-vscode-btn-secondary-block-recap-before-accent.png)

ภายในบล็อกนี้พิมพ์ `width: 100%;` แล้วเริ่มพิมพ์ `display:` โดย IntelliSense แนะนำค่าต่างๆ เช่น `inline-block`, `inline-table`, `inline-flexbox`

![IntelliSense แนะนำ display inline-block](15-Buttons/089-vscode-selector-autocomplete-btn-accent-block-primary-secondary.png)

โค้ดสมบูรณ์:

```css
.btn--block {
  width: 100%;
  display: inline-block;
}
```

![บล็อก .btn--block สมบูรณ์](15-Buttons/091-vscode-index-html-button-btn-btn-primary-btn-block-complete.png)

นำ class `btn--block` ไปเพิ่มในปุ่มที่มี `btn--primary` เพื่อทดสอบ

```html
<button class="btn btn--primary btn--block">Buy Now</button>
<a href="#" class="btn btn--secondary">Buy Now</a>
```

ทดสอบในเบราว์เซอร์ — ปุ่มแรกยืดเต็มความกว้างของหน้าจอ ในขณะที่ปุ่มที่สองยังคงขนาดปกติ

![เบราว์เซอร์: ปุ่มแรกเต็มความกว้าง ปุ่มที่สองปกติ](15-Buttons/092-browser-buy-now-button-full-width-block-blue-cyan.png)

เพิ่ม class `btn--block` ให้ปุ่มที่สองด้วยเพื่อทดสอบทั้งคู่

![HTML: เพิ่ม a href class btn btn--secondary](15-Buttons/093-vscode-index-html-a-href-hash-class-btn-btn-secondary-typing.png)

ผลลัพธ์: ทั้งสองปุ่มเต็มความกว้างและเรียงต่อกันในแนวตั้ง

![เบราว์เซอร์: ปุ่มทั้งสองเต็มความกว้างเรียงต่อกัน](15-Buttons/095-browser-buy-now-buttons-full-width-blue-cyan-stacked.png)

![เบราว์เซอร์: ผลลัพธ์สุดท้ายปุ่มเต็มความกว้างทั้งคู่](15-Buttons/096-browser-buy-now-buttons-full-width-both-blue-cyan-final.png)

> **อธิบายทำไมต้องมีทั้ง `width: 100%` และ `display: inline-block`:**
> - `<button>` โดย default เป็น `inline-block` อยู่แล้ว แต่ `<a>` โดย default เป็น `inline` ซึ่ง**ไม่รองรับการตั้งค่า `width` โดยตรง** (element แบบ inline จะไม่ยอมรับ `width`/`height` ที่กำหนดเอง)
> - การเขียน `display: inline-block;` จึงจำเป็นเพื่อบังคับให้ `<a>` (และ element อื่นๆ ที่อาจมี class นี้) กลายเป็น inline-block ก่อน แล้วค่อยกำหนด `width: 100%;` ถึงจะมีผลจริง — นี่เป็นเทคนิคสำคัญที่ทำให้ Modifier `.btn--block` ใช้ได้กับทั้ง `<button>` และ `<a>` อย่างสม่ำเสมอ

จากนั้นเพิ่ม `text-align: center;` ให้กับ `.btn` (Block หลัก ไม่ใช่ Modifier) เพื่อให้ข้อความอยู่กึ่งกลางเสมอเมื่อปุ่มถูกขยายให้กว้างเต็มที่

![พิมพ์ text-align property suggestions](15-Buttons/099-vscode-btn-text-align-property-suggestions.png)

ทดสอบก่อนเพิ่ม text-align — ข้อความอาจจะไม่อยู่กึ่งกลางพอดี

![เบราว์เซอร์: ทดสอบก่อนใส่ text-align center](15-Buttons/100-browser-buy-now-buttons-text-align-center-test.png)

โค้ดสมบูรณ์:

```css
.btn {
  ...
  text-align: center;
  ...
}
```

![text-align center เสร็จสมบูรณ์](15-Buttons/101-vscode-btn-text-align-center-complete.png)

---

## 10. CSS Reset ระดับ Global: `box-sizing: border-box`

หัวข้อนี้เป็นแนวคิดใหม่ที่สำคัญมากในคลิปนี้ Mosh ทบทวนตัวแปรสีใน `:root` อีกครั้ง

```css
:root {
  --color-primary: #2584ff;
  --color-secondary: #00d9ff;
  --color-accent: #ff3400;
  --color-headings: #1b0760;
  --color-body: #918ca4;
}
```

![ทบทวน :root variables ทั้งหมด](15-Buttons/102-vscode-root-color-variables-recap-primary-secondary-accent.png)

จากนั้นเลื่อนขึ้นไปบนสุดของไฟล์ CSS แล้วสร้าง selector ใหม่ที่ไม่เคยเห็นมาก่อนในซีรีส์นี้ — **Universal Selector** (`*`) ผสมกับ pseudo-elements

![พิมพ์ *, *::after, *::before](15-Buttons/103-vscode-universal-selector-star-after-before-typing.png)

```css
*,
*::after,
*::before {

}
```

ภายในบล็อกนี้พิมพ์ `box-sizing:`

![พิมพ์ box-sizing property](15-Buttons/104-vscode-universal-selector-box-sizing-property-typing.png)

![พิมพ์ค่า box-sizing](15-Buttons/105-vscode-universal-selector-box-sizing-value-typing.png)

ตั้งค่าเป็น `border-box`:

```css
*,
*::after,
*::before {
  box-sizing: border-box;
}
```

![box-sizing: border-box เสร็จสมบูรณ์](15-Buttons/106-vscode-universal-selector-box-sizing-border-box-complete.png)

ทดสอบผลลัพธ์ในเบราว์เซอร์ — ปุ่มยังคงแสดงผลถูกต้องเหมือนเดิม (เพราะในกรณีนี้ยังไม่มีปัญหาเรื่องขนาดเกิน แต่การเพิ่ม reset นี้จะป้องกันปัญหาที่อาจเกิดในอนาคต)

![เบราว์เซอร์: ทดสอบหลังเพิ่ม box-sizing border-box](15-Buttons/107-browser-buy-now-buttons-box-sizing-border-box-test.png)

> **อธิบายแนวคิด `box-sizing: border-box` แบบละเอียด:**
>
> โดย default (ค่าเริ่มต้นของเบราว์เซอร์) ทุก element ใช้ `box-sizing: content-box;` ซึ่งหมายความว่าเมื่อกำหนด `width` และ `height` ให้กับ element นั้น ค่า `padding` และ `border` **จะถูกบวกเพิ่มเข้าไป** นอกเหนือจากค่า width/height ที่ตั้งไว้ ทำให้ขนาดจริงของ element ใหญ่กว่าที่ตั้งใจไว้เสมอ — นี่คือสาเหตุของปัญหา layout ที่นักพัฒนาหน้าใหม่มักงงบ่อยๆ ("ทำไม div ของฉันถึงกว้างเกินกว่าที่ตั้งไว้")
>
> เมื่อเปลี่ยนเป็น `box-sizing: border-box;` ค่า `padding` และ `border` **จะถูกรวมอยู่ภายในค่า `width`/`height` ที่ตั้งไว้แทน** ทำให้ขนาดของ element เป็นไปตามที่กำหนดไว้เป๊ะ ไม่ว่าจะมี padding หรือ border เท่าไหร่ก็ตาม
>
> การเขียน selector แบบ `*, *::after, *::before { box-sizing: border-box; }` คือการ**ใช้กฎนี้กับทุก element ในทั้งหน้าเว็บ** (รวมถึง pseudo-element `::before` และ `::after` ด้วย) นี่คือ pattern มาตรฐานระดับอุตสาหกรรมที่โปรเจกต์ CSS แทบทุกโปรเจกต์ในปัจจุบันใช้กันเป็นประจำ ถือเป็นหนึ่งใน "CSS Reset" ที่สำคัญที่สุดที่ควรใส่ไว้บนสุดของไฟล์ CSS เสมอ
>
> **Universal Selector (`*`)** หมายถึง "เลือกทุก element ในหน้าเว็บ" ส่วน `*::after` และ `*::before` หมายถึง pseudo-element ทั้งหมดที่ element ต่างๆ อาจสร้างขึ้น (เช่นเดียวกับที่เคยเห็นใน `.link-arrow::after` จากคลิป Links) การรวม 3 selector นี้เข้าด้วยกันด้วยเครื่องหมายจุลภาค (`,`) ทำให้กฎ `box-sizing: border-box;` มีผลครอบคลุมทุกอย่างในหน้าเว็บอย่างสมบูรณ์

---

## 11. Media Query สำหรับหน้าจอขนาดใหญ่

ก่อนเข้าสู่หัวข้อ media query Mosh กลับไปดูดีไซน์ Photoshop เพื่อตรวจสอบขนาดตัวอักษรจริงของปุ่มบนหน้าจอ desktop โดยใช้เครื่องมือ Text Tool คลิกที่ข้อความ "GET STARTED" เพื่อดูค่า font size

![Photoshop: ตรวจสอบขนาดตัวอักษร GET STARTED = 15px](15-Buttons/114-photoshop-get-started-button-text-15px-font-size-check.png)

![Photoshop: เลื่อนดู standard.psd ส่วนหัวข้อ webhosting](15-Buttons/115-photoshop-standard-psd-webhosting-title-scroll.png)

![Photoshop: เลื่อนดู standard.psd ส่วนค้นหาโดเมนและราคา](15-Buttons/117-photoshop-standard-psd-search-domain-pricing-scroll.png)

![Photoshop: ดูส่วน mobile.psd pricing plan tick list และปุ่ม Buy Now](15-Buttons/118-photoshop-mobile-psd-pricing-plan-tick-list-buy-now-compare.png)

จากนั้นกลับไปที่ `styles.css` สร้าง media query ใหม่

![พิมพ์ @media screen](15-Buttons/111-vscode-media-query-atmedia-screen-typing.png)

ภายในเขียน selector `.btn` แล้วพิมพ์ `font-size`

![IntelliSense แนะนำ font-size ใน media query](15-Buttons/112-vscode-media-query-btn-font-size-suggestions.png)

โดยมีตัวเลือกค่าต่างๆ ปรากฏขึ้น เช่น `large`, `medium`, `small`, `x-large` ฯลฯ (ค่าคำศัพท์ absolute size ของ CSS แบบเก่า ซึ่งไม่ค่อยได้ใช้ในโปรเจกต์นี้)

![รายการค่า font-size แบบคำศัพท์ (large medium small)](15-Buttons/113-vscode-media-query-font-size-value-suggestions-list.png)

พิมพ์ค่าที่ต้องการจริง

![พิมพ์ font-size 1.5](15-Buttons/116-vscode-media-query-btn-font-size-1-5-typing.png)

โค้ดสมบูรณ์:

```css
@media screen and (min-width: 1024px) {
  .btn {
    font-size: 1.5rem;
  }
}
```

![media query .btn font-size 1.5rem สมบูรณ์](15-Buttons/119-vscode-media-query-btn-font-size-1-5rem-complete.png)

ทดสอบผลลัพธ์บนหน้าจอกว้าง (desktop) — ปุ่มเต็มความกว้างแสดงผลถูกต้องพร้อมขนาดตัวอักษรที่เล็กลงเล็กน้อยตามที่ตั้งใจไว้สำหรับจอใหญ่

![เบราว์เซอร์: ปุ่มเต็มความกว้างบนจอ desktop](15-Buttons/120-browser-buy-now-buttons-full-width-desktop-width-test.png)

---

## 12. Modifier สุดท้าย: `.btn--outline` (ปุ่มแบบมีแค่กรอบ)

Modifier สุดท้ายของคลิปนี้คือปุ่มแบบ "outline" หรือ "ghost button" — ปุ่มที่มีพื้นหลังโปร่ง/ขาว มีแค่เส้นขอบ ใช้สำหรับกรณีที่ไม่ต้องการให้ปุ่มดูเด่นเกินไป (secondary action)

ทดสอบผลลัพธ์เริ่มต้นในเบราว์เซอร์ — ปุ่มพื้นขาว มีเส้นขอบสีกรมท่า ตัวอักษรสีกรมท่า

![เบราว์เซอร์: ปุ่ม outline พื้นขาวขอบกรมท่า](15-Buttons/121-browser-buy-now-button-outline-white-navy-border-test.png)

โค้ด CSS สมบูรณ์:

```css
.btn--outline {
  background: #fff;
  color: var(--color-headings);
  border: 2px solid var(--color-headings);
}

.btn--outline:hover {
  background: var(--color-headings);
  color: #fff;
}
```

![บล็อก .btn--outline และ .btn--outline:hover สมบูรณ์](15-Buttons/122-vscode-btn-outline-block-background-color-border-complete.png)

> **คำอธิบาย `.btn--outline`:**
> - `background: #fff;` — พื้นหลังสีขาว (ตรงข้ามกับปุ่มสีทึบแบบ primary/secondary/accent)
> - `color: var(--color-headings);` — ใช้สีของ heading (สีกรมท่าเข้ม) เป็นสีตัวอักษร ให้ดูเข้ากับธีมโดยรวม
> - `border: 2px solid var(--color-headings);` — เส้นขอบหนา 2 พิกเซล แบบทึบ (solid) ใช้สีเดียวกับตัวอักษรเพื่อความสอดคล้อง
>
> **คำอธิบาย `.btn--outline:hover`:**
> - เมื่อเอาเมาส์ไปวาง สีจะ**สลับกัน** — พื้นหลังกลายเป็นสีกรมท่าเข้ม (เดิมเป็นสี border) และตัวอักษรกลายเป็นสีขาว (เดิมเป็นสีตัวอักษร) เทคนิคการ "สลับสี" (invert) แบบนี้เป็นรูปแบบที่นิยมมากสำหรับปุ่มแบบ outline เพราะทำให้ผู้ใช้เห็นชัดเจนว่าปุ่มกำลังถูกโต้ตอบ (interactive feedback) โดยไม่ต้องเปลี่ยนสีที่ซับซ้อน

---

## สรุปภาพรวมของคลิปนี้

| หัวข้อ | รายละเอียด |
|---|---|
| Block หลัก | `.btn` — border-radius 40px, border 0, cursor pointer, font-size 1.8rem, font-weight 600, padding 2rem 3rem, text-align center, text-transform uppercase, white-space nowrap |
| Modifier สี | `.btn--primary`, `.btn--secondary`, `.btn--accent` — พร้อม `:hover` state แต่ละสี (ค่าสีสุ่มจาก Photoshop eyedropper) |
| Modifier รูปทรง | `.btn--block` (เต็มความกว้าง, ใช้ `display: inline-block` + `width: 100%`), `.btn--outline` (พื้นขาว/ขอบ พร้อม hover สลับสี) |
| ใช้ได้ทั้ง `<button>` และ `<a>` | class `.btn` ไม่ผูกกับ tag ใดๆ ทำให้ปุ่มและลิงก์แสดงผลเหมือนกันทุกประการ |
| CSS Reset ใหม่ | `*, *::after, *::before { box-sizing: border-box; }` — ป้องกันปัญหา padding/border บวกเพิ่มเข้าไปในขนาดจริง |
| Media Query | `@media screen and (min-width: 1024px) { .btn { font-size: 1.5rem; } }` |
| ข้อผิดพลาดที่พบ | `lighten()` ไม่ใช่ฟังก์ชัน CSS มาตรฐาน (เป็นของ Sass เท่านั้น) ต้องแก้ด้วยการสุ่มสีจาก Photoshop แทน; selector พิมพ์ผิดเป็น `.btn-secondary:hover` (ขีดเดียว) แทน `.btn--secondary:hover` (สองขีด) ทำให้กลายเป็น dead code |

### แนวคิดสำคัญที่ได้จากคลิปนี้

1. **BEM Modifier หลายตัวพร้อมกัน** — component เดียว (`.btn`) สามารถมี Modifier ได้หลายแบบและใช้ร่วมกันได้ (เช่น `btn btn--primary btn--block`) ทำให้ CSS ยืดหยุ่นและนำกลับมาใช้ซ้ำได้มาก
2. **`:hover` pseudo-class** — เทคนิคพื้นฐานที่สำคัญที่สุดอย่างหนึ่งในการทำให้เว็บไซต์มี interactivity โดยไม่ต้องพึ่ง JavaScript
3. **Class ไม่ผูกกับ HTML tag** — การออกแบบ CSS ที่ดีควรแยก "หน้าตา" ออกจาก "ชนิดของ element" ทำให้ class เดียวใช้ได้กับทั้ง `<button>` และ `<a>`
4. **ข้อจำกัดของ CSS ธรรมดาเทียบกับ Sass** — ฟังก์ชันอย่าง `lighten()`/`darken()` ไม่มีอยู่ใน CSS มาตรฐาน ต้องหาสีเองด้วยเครื่องมืออย่าง Photoshop Eyedropper หรือเขียนค่า hex ตรงๆ
5. **`box-sizing: border-box` แบบ Global Reset** — เป็นหนึ่งใน CSS Reset ที่สำคัญที่สุดที่ควรใส่ในทุกโปรเจกต์ เพื่อป้องกันปัญหา padding/border บวกเพิ่มเข้าไปในขนาดจริงของ element
6. **`display: inline-block` จำเป็นสำหรับ `<a>` ที่ต้องการกำหนด `width`** — เพราะ `<a>` เป็น inline element โดย default ซึ่งไม่รองรับการตั้งค่าความกว้าง/สูงโดยตรง
7. **ความระมัดระวังเรื่องขีดกลางใน BEM** — การสะกดผิดระหว่างขีดเดียว (`-`) กับสองขีด (`--`) ทำให้ CSS กลายเป็น dead code แบบเงียบๆ โดยไม่มี error ใดๆ แจ้งเตือน ต้องตรวจทานอย่างละเอียดเสมอ

---

*สรุปจากคลิปที่ 15 (Buttons) ของคอร์ส "Building a Web Site" (โปรเจกต์ Moshify) สอนโดย Mosh Hamedani จาก codewithmosh.com*
