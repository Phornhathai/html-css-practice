# HTML-CSS-3: 24 - Testimonials

**ไฟล์ต้นฉบับ:** 24- Testimonials.mp4

▶️ [ดูวิดีโอ](../../HTML-CSS-3/24-%20Testimonials.mp4)

---

## ภาพรวมคลิปนี้

![Title slide](24-Testimonials/001-title-slide.png)

ในคลิปนี้ Mosh สอนการสร้าง **Testimonials component** (กล่องคำรับรอง/รีวิวจากลูกค้า) โดยใช้ความรู้ที่เรียนมาแล้วทั้งหมด: CSS Grid (จากคลิป Grids), Icon Container แบบ position absolute (จากคลิป Media Objects), และโครงสร้าง Quote/Blockquote (จากคลิป Quotes) มาผสมกันเป็น component ใหม่ พร้อมทั้งสอนพฤติกรรมสำคัญของ CSS Grid ที่ยังไม่เคยพูดถึงมาก่อน คือ **`align-items: stretch`** ที่เป็นค่า default ของ grid item

> 💡 Mosh เปิด Photoshop เพื่อ recap ดีไซน์สุดท้ายของ testimonial card อีกครั้ง เพื่อให้เห็นภาพรวมก่อนเริ่มเขียนโค้ด — เป็นการ์ดสีขาว มีรูปลูกค้าทางซ้าย มีไอคอนเครื่องหมายคำพูด (quote icon) วงกลมสีแดงวางซ้อนที่มุมขวาบนของรูป และข้อความคำรับรองพร้อมชื่อ-ตำแหน่งทางขวา

![Photoshop final mockup recap](24-Testimonials/002-photoshop-final-mockup-recap.png)

---

## 1. เริ่มต้นด้วย Grid 1x2 และรูปภาพลูกค้า

Mosh เปิด `index.html` ที่ว่างเปล่า (ลบโค้ดจากคลิปก่อนหน้าออกหมดแล้ว) แล้วสร้างโครงสร้างการ์ดใหม่ทั้งหมด โดยเริ่มจาก `<div class="card">` ครอบไว้ก่อน

```html
<div class="card">

</div>
```

จากนั้นใช้ Emmet พิมพ์ `div.grid.grid--1x2` เพื่อสร้าง grid สองคอลัมน์ (คลาสนี้เคยสร้างไว้แล้วในคลิป Grids)

![index.html div.card created](24-Testimonials/003-index-html-div-card-created.png)

```html
<div class="card">
  <div class="grid grid--1x2">

  </div>
</div>
```

> 📝 สังเกตว่า Mosh ใช้ class ที่มีอยู่แล้วจาก component อื่น (`grid--1x2`) มาสร้าง layout ใหม่ทันที นี่คือประโยชน์ของการทำ CSS แบบ reusable/utility class — ไม่ต้องเขียน CSS ใหม่สำหรับทุก component

จากนั้น Mosh เปิด Finder ไปที่โฟลเดอร์ `Downloads/images` เพื่อดูรูปภาพที่จะใช้เป็นรูปลูกค้า พบไฟล์ `testimonial.jpg` (ผู้ชายใส่เสื้อเชิ้ตยีนส์ กอดอก ยิ้ม)

![Finder testimonial.jpg selected](24-Testimonials/004-finder-testimonial-jpg-selected.png)

Mosh ดับเบิลคลิกเปิดดูตัวอย่างรูปใน VS Code เพื่อยืนยันว่าเป็นรูปที่ถูกต้องก่อนใช้งาน

![testimonial.jpg preview](24-Testimonials/005-testimonial-jpg-preview.png)

กลับมาที่ `index.html` แล้วพิมพ์ Emmet `img` ในบรรทัดว่างภายใน `.grid--1x2` เพื่อสร้างแท็ก `<img src="" alt="">` ที่ยังว่างเปล่า

![img src alt empty emmet](24-Testimonials/006-img-src-alt-empty-emmet.png)

จากนั้นพิมพ์ `src="images/testimonial.jpg"` (VS Code แสดง path suggestion จากไฟล์ในโฟลเดอร์ images ให้อัตโนมัติ) และเริ่มพิมพ์ `alt="A happy, smiling custom...`

![img src testimonial.jpg alt typed](24-Testimonials/007-img-src-testimonial-jpg-alt-typed.png)

พิมพ์ alt text จนจบเป็น **"A happy, smiling customer"**

![img alt text happy smiling customer](24-Testimonials/008-img-alt-text-happy-smiling-customer.png)

```html
<div class="card">
  <div class="grid grid--1x2">
    <img src="images/testimonial.jpg" alt="A happy, smiling customer" />
  </div>
</div>
```

---

## 2. สาธิตพฤติกรรม CSS Grid: `align-items: stretch` (default)

ก่อนจะไปต่อ Mosh ต้องการสาธิตพฤติกรรมสำคัญของ CSS Grid ที่นักเรียนควรรู้ นั่นคือ grid item ที่ "ว่างเปล่า" (ไม่มีเนื้อหา) จะ **ยืดความสูงเท่ากับ sibling ที่สูงที่สุดโดยอัตโนมัติ** เพราะค่า default ของ `align-items` ใน CSS Grid คือ `stretch`

Mosh สร้าง `<div>` ที่สองต่อจาก `<img>` โดยใช้ Emmet พิมพ์ `div` แล้วเติม `style` attribute

![second div style emmet suggestions](24-Testimonials/009-second-div-style-emmet-suggestions.png)

พิมพ์ inline style ทีละ property จนได้:

```html
<div style="height: 100px; background: gold"></div>
```

![second div height 100px background gold](24-Testimonials/010-second-div-height-100px-background-gold.png)

```html
<body style="padding: 5rem">
  <div class="card">
    <div class="grid grid--1x2">
      <img src="images/testimonial.jpg" alt="A happy, smiling customer" />
      <div style="height: 100px; background: gold"></div>
    </div>
  </div>
</body>
```

เมื่อเปิดดูใน browser (localhost:5500 ผ่าน Live Server) จะเห็นว่ากล่องสีทอง (gold) แม้จะกำหนด `height: 100px` ไว้ แต่กลับ **ยืดความสูงเต็มเท่ากับความสูงของรูปภาพ** ทางซ้ายโดยอัตโนมัติ

![browser grid stretch image and gold box](24-Testimonials/011-browser-grid-stretch-image-and-gold-box.png)

> 🔍 **หลักการสำคัญ:** ใน Flexbox และ Grid ค่า default ของ `align-items` คือ `stretch` เสมอ ต่างจาก block/inline layout ปกติที่แต่ละ element จะสูงเท่ากับเนื้อหาของตัวเองเท่านั้น นี่คือเหตุผลที่ Mosh มักใช้ Grid/Flexbox แม้กับ layout ง่าย ๆ เพราะพฤติกรรมการยืด (stretch) นี้ทำให้ design ดูสม่ำเสมอโดยไม่ต้องกำหนด height เอง
>
> ⚠️ กล่องสีทองนี้เป็นแค่ตัวอย่างสาธิต (placeholder) เท่านั้น ภายหลัง Mosh จะลบทิ้งแล้วแทนที่ด้วยเนื้อหาคำรับรองจริง

---

## 3. Refactor: ห่อรูปภาพด้วย wrapper div (testimonial__image)

หลังจากสาธิตพฤติกรรม stretch จบแล้ว Mosh กลับมาปรับโครงสร้าง โดยห่อ `<img>` ด้วย `<div class="testimonial__image">` แทนที่จะใส่ class ลงบน `<img>` ตรง ๆ

![testimonial image wrapper div created](24-Testimonials/012-testimonial-image-wrapper-div-created.png)

```html
<div class="testimonial__image">
  <img src="images/testimonial.jpg" alt="A happy, smiling customer" />
</div>
```

![testimonial image img nested in wrapper](24-Testimonials/013-testimonial-image-img-nested-in-wrapper.png)

> 📌 **ทำไมต้องห่อด้วย div แทนที่จะใส่ class บน img ตรง ๆ?** เพราะภายหลัง Mosh จะต้องวางไอคอน quote (position: absolute) ซ้อนทับบนรูปภาพ ซึ่งต้องมี **positioning context** (`position: relative`) การมี wrapper div แยกต่างหากทำให้ควบคุม positioning ของทั้งรูปภาพและไอคอนได้ง่ายกว่า และยังใช้ BEM naming (`testimonial__image`) ตั้งชื่อ element ย่อยของ component `testimonial` ได้ชัดเจนตามหลักการที่เรียนมาในคลิปก่อน ๆ

จากนั้นไปที่ `styles.css` เพื่อเขียน selector แบบ **child combinator** (`>`) กำหนดให้เฉพาะ `<img>` ที่อยู่ตรงภายใน `.testimonial__image` เท่านั้นที่ได้รับสไตล์นี้

![css testimonial image child combinator selector](24-Testimonials/014-css-testimonial-image-child-combinator-selector.png)

```css
.testimonial__image > img {
  width: 100%;
}
```

![css img width 100 percent rule](24-Testimonials/015-css-img-width-100-percent-rule.png)

> 🔧 **Child combinator (`>`)** ต่างจาก descendant selector (space) ตรงที่จะเลือกเฉพาะ **ลูกโดยตรง** (direct child) เท่านั้น ไม่ใช่ลูกหลานทุกระดับ ในที่นี้ใช้เพื่อป้องกันไม่ให้กฎ `width: 100%` ไปกระทบ `<img>` ตัวอื่นที่อาจซ้อนอยู่ลึกกว่านั้นในอนาคต — เป็น pattern เดียวกับที่เคยสอนไว้ในคลิป Media Objects

Mosh ทดสอบปรับขนาดหน้าต่าง browser หลายระดับความกว้างเพื่อยืนยันว่ารูปภาพ scale ตามคอลัมน์อย่างถูกต้อง:

![browser resize 922px image scaled](24-Testimonials/016-browser-resize-922px-image-scaled.png)

![browser resize 785px image scaled](24-Testimonials/017-browser-resize-785px-image-scaled.png)

![browser resize 856px image scaled](24-Testimonials/018-browser-resize-856px-image-scaled.png)

Mosh สลับไปดู `styles.css` เพื่อยืนยันกฎ CSS ที่เขียนไว้ทั้งหมด ณ จุดนี้

![vscode styles.css final testimonial rules](24-Testimonials/019-vscode-styles-css-final-testimonial-rules.png)

```css
.testimonial {
  padding: 3rem;
}
.testimonial__image > img {
  width: 100%;
}
```

![testimonial image img width 100 confirmed](24-Testimonials/020-testimonial-image-img-width-100-confirmed.png)

![styles.css open confirming rules](24-Testimonials/021-styles-css-open-confirming-rules.png)

---

## 4. นำ Icon Container กลับมาใช้ซ้ำ (Reuse จาก Media Objects)

ขั้นตอนถัดไป Mosh ต้องการวางไอคอนเครื่องหมายคำพูด (quote icon) วงกลมซ้อนทับที่มุมขวาบนของรูปภาพ แทนที่จะเขียน HTML/CSS ใหม่ทั้งหมด เขาเปิด `icons.html` ในโฟลเดอร์ `components` ขึ้นมาดูเป็นตัวอย่างอ้างอิง (reference) เพราะมี pattern `<span class="icon-container">` พร้อม SVG `<use>` อยู่แล้วจากคลิปก่อน ๆ

![icons.html icon-container svg reference](24-Testimonials/022-icons-html-icon-container-svg-reference.png)

กลับมาที่ `styles.css` Mosh พิมพ์ `.testi` เพื่อดู Emmet/VS Code autocomplete แสดง selector ที่มีอยู่แล้วในไฟล์ (`.testimonial`, `.testimonial__image`)

![testi class emmet autocomplete suggestions](24-Testimonials/023-testi-class-emmet-autocomplete-suggestions.png)

จากนั้นกลับไปที่ `index.html` แล้ว **copy** โครงสร้าง `<span class="icon-container">...</span>` จาก `icons.html` มา **paste** ไว้ข้างใน `<div class="testimonial__image">` ต่อจาก `<img>`

![icon-container span pasted into testimonial image](24-Testimonials/024-icon-container-span-pasted-into-testimonial-image.png)

```html
<div class="testimonial__image">
  <img src="images/testimonial.jpg" alt="A happy, smiling customer" />
  <span class="icon-container">
    <svg class="icon icon--primary">
      <use xlink:href="images/sprite.svg#wordpress"></use>
    </svg>
  </span>
</div>
```

> 💡 ตอนนี้ไอคอนที่ copy มายังเป็นไอคอน **WordPress** (ไอคอนตัวอย่างเดิมจาก `icons.html`) — Mosh จะเปลี่ยนเป็นไอคอน quote (เครื่องหมายคำพูด) ในขั้นตอนถัดไป นี่เป็นเทคนิคการทำงานจริงที่ Mosh ใช้บ่อย: copy โครงสร้างที่ใช้งานได้แล้วมาก่อน แล้วค่อยแก้ไขรายละเอียดทีหลัง แทนที่จะพิมพ์ใหม่ทั้งหมด

---

## 5. Position Absolute: วางไอคอนซ้อนทับมุมขวาบนของรูป

ไปที่ `styles.css` เขียน selector ใหม่ด้วย child combinator เช่นกัน

![icon-container position absolute typed](24-Testimonials/025-icon-container-position-absolute-typed.png)

```css
.testimonial__image > .icon-container {
  position: absolute;
}
```

จากนั้นเติมค่า `top` และ `right` เพื่อกำหนดตำแหน่ง

![icon-container top right values typed](24-Testimonials/026-icon-container-top-right-values-typed.png)

ค่าเริ่มต้นที่ลองคือ `top: 3rem; right: 0;` ทดสอบดูใน browser พบว่าไอคอน (ตอนนี้ยังเป็น WordPress icon) ลอยซ้อนทับขอบขวาบนของรูปพอดี

![browser wordpress icon circle overlay](24-Testimonials/027-browser-wordpress-icon-circle-overlay.png)

Mosh เปิด Photoshop มาเทียบกับดีไซน์ต้นแบบอีกครั้งเพื่อดูตำแหน่งไอคอน quote ที่ถูกต้อง (วงกลมสีแดงอยู่คร่อมขอบรูปภาพเล็กน้อย ไม่ใช่อยู่ในขอบเป๊ะ)

![photoshop mockup quote icon reference](24-Testimonials/028-photoshop-mockup-quote-icon-reference.png)

> 📌 เพื่อให้ตำแหน่งตรงกับดีไซน์ ไอคอนต้อง "ล้น" ออกไปนอกขอบรูปภาพทางขวาเล็กน้อย ซึ่งทำได้โดยกำหนดค่า `right` เป็น**ค่าลบ** — Mosh ปรับค่าจาก `right: 0` ไปเรื่อย ๆ

Mosh ปรับค่า `right` จาก `0` เป็นค่าอื่น ๆ เพื่อทดสอบตำแหน่ง

![icon-container right value adjustment](24-Testimonials/029-icon-container-right-value-adjustment.png)

![browser icon position adjusted](24-Testimonials/030-browser-icon-position-adjusted.png)

> ⚠️ **สำคัญ (แก้ไขจากที่เข้าใจผิดตอนดูรอบแรก):** ค่าสุดท้ายที่ Mosh ใช้จริง ๆ คือ **`right: -32px;`** (ค่าติดลบ) ไม่ใช่ค่าบวก — ค่าลบทำให้ไอคอนเลื่อนออกไป**นอก**ขอบขวาของ `.testimonial__image` ทำให้เกิดเอฟเฟกต์ไอคอนวงกลม "ลอยคร่อม" ขอบรูปภาพพอดีตามดีไซน์ต้นแบบ

```css
.testimonial__image > .icon-container {
  position: absolute;
  top: 3rem;
  right: -32px;
}
```

---

## 6. สี Accent และเปลี่ยนไอคอนเป็น Quote พร้อมปรับขนาดเล็กลง

Mosh สร้าง modifier class ใหม่ชื่อ `.icon-container--accent` (ว่างเปล่าก่อน)

![icon-container accent class created empty](24-Testimonials/031-icon-container-accent-class-created-empty.png)

```css
.icon-container--accent {
}
```

แล้วเติมกฎเปลี่ยนสีพื้นหลังเป็นสี accent (แดง) โดยใช้ CSS variable ที่มีอยู่แล้ว

![icon-container accent background color var](24-Testimonials/032-icon-container-accent-background-color-var.png)

```css
.icon-container--accent {
  background: var(--color-accent);
}
```

นำ class ไปใส่เพิ่มบน `<span>` ใน HTML (`class="icon-container icon-container--accent"`) แล้วดูผลใน browser เห็นวงกลมพื้นหลังเปลี่ยนเป็นสีแดงตามดีไซน์

![browser red circle accent background](24-Testimonials/033-browser-red-circle-accent-background.png)

Mosh เปิดดูกฎ `.icon--primary` ที่มีอยู่แล้ว (ใช้ CSS variable สีน้ำเงิน primary) เป็นตัวอย่างอ้างอิงก่อนสร้าง modifier สีขาวใหม่

![icon-primary existing rule reference](24-Testimonials/034-icon-primary-existing-rule-reference.png)

```css
.icon--primary {
  fill: var(--color-primary);
}
```

จากนั้นพิมพ์ selector ใหม่ `.icon--white` โดย VS Code แสดง autocomplete ของ class ที่มีอยู่แล้วทั้งหมด (`.icon--primary`, `.icon-container`, `.icon-container--accent`)

![icon-white class emmet suggestions](24-Testimonials/035-icon-white-class-emmet-suggestions.png)

```css
.icon--white {
  fill: #fff;
}
```

![icon-white fill white rule](24-Testimonials/036-icon-white-fill-white-rule.png)

กลับมาที่ HTML เปลี่ยน class บน `<svg>` จาก `icon icon--primary` เป็น `icon icon--white` และเปลี่ยน `xlink:href` จาก `#wordpress` เป็น **`#quotes`** เพื่อเปลี่ยนรูปไอคอนจาก WordPress logo เป็นเครื่องหมายคำพูดจริง

![html svg class icon-white quotes href](24-Testimonials/037-html-svg-class-icon-white-quotes-href.png)

```html
<span class="icon-container icon-container--accent">
  <svg class="icon icon--white">
    <use xlink:href="images/sprite.svg#quotes"></use>
  </svg>
</span>
```

ดูผลใน browser: วงกลมแดง + ไอคอนเครื่องหมายคำพูดสีขาวซ้อนทับมุมขวาบนของรูปภาพลูกค้าพอดีตามดีไซน์

![browser white quote icon on red circle](24-Testimonials/038-browser-white-quote-icon-on-red-circle.png)

> ⚠️ ไอคอนตอนนี้ยังมีขนาด**ใหญ่เกินไป**เมื่อเทียบกับดีไซน์ต้นแบบ (ที่ใช้ขนาด default `.icon { width: 40px; height: 40px; }`) ขั้นตอนต่อไป Mosh จึงสร้าง modifier ลดขนาดไอคอนโดยเฉพาะ

---

## 7. Modifier ขนาดไอคอน: `.icon--small`

Mosh สร้าง selector ว่างชื่อ `.icon--small` (VS Code แสดงกฎ `.icon` เดิม `{ width: 40px; height: 40px; }` อยู่ด้านบนเป็นตัวอ้างอิง)

![icon base class width height 40px](24-Testimonials/039-icon-base-class-width-height-40px.png)

![icon-small class created empty](24-Testimonials/040-icon-small-class-created-empty.png)

พิมพ์ `width: 30px;`

![icon-small width 30px typed](24-Testimonials/041-icon-small-width-30px-typed.png)

แล้วพิมพ์ `height: 30px;` ต่อ

![icon-small height 30px typed](24-Testimonials/042-icon-small-height-30px-typed.png)

```css
.icon--small {
  width: 30px;
  height: 30px;
}
```

นำ class `icon--small` ไปเพิ่มบน `<svg>` ต่อจาก `icon icon--white` กลายเป็น `class="icon icon--white icon--small"`

![html svg class icon-white-small quotes](24-Testimonials/043-html-svg-class-icon-white-small-quotes.png)

```html
<svg class="icon icon--white icon--small">
  <use xlink:href="images/sprite.svg#quotes"></use>
</svg>
```

ผลลัพธ์สุดท้ายใน browser: ไอคอน quote สีขาวขนาดเล็กลงพอดีกับวงกลมสีแดง ตรงตามดีไซน์ Photoshop ทุกประการ

![browser final quote icon small size](24-Testimonials/044-browser-final-quote-icon-small-size.png)

> 🔍 **BEM Modifier แบบผสมหลายคลาส:** จุดนี้แสดงให้เห็นพลังของ BEM — element เดียว (`<svg class="icon">`) สามารถผสม modifier ได้หลายตัวพร้อมกัน (`icon--white` ควบคุมสี, `icon--small` ควบคุมขนาด) โดยไม่ต้องสร้าง class ผสมแบบ `icon--white-small` ทำให้ CSS reusable และยืดหยุ่นมากขึ้น

---

## 8. แทนที่ Placeholder ด้วยคำรับรองจริง (Blockquote)

Mosh ลบ `<div style="height: 100px; background: gold"></div>` (placeholder เดิม) ออก เหลือเป็น div ว่างเปล่าชั่วคราว

![placeholder gold div deleted empty](24-Testimonials/045-placeholder-gold-div-deleted-empty.png)

จากนั้นใช้ Quick Open (Cmd+P) พิมพ์ `quo` เพื่อค้นหาไฟล์ที่เกี่ยวกับ quote พบทั้ง `quotes.svg` และ `quotes.html`

![quick open search quotes files](24-Testimonials/046-quick-open-search-quotes-files.png)

เปิด `quotes.html` (component จากคลิป Quotes ก่อนหน้า) ขึ้นมาดูโครงสร้าง `<blockquote>` เพื่อใช้เป็นตัวอย่างอ้างอิงสำหรับเขียนคำรับรอง

![quotes.html reference component code](24-Testimonials/047-quotes-html-reference-component-code.png)

```html
<div class="media__image">
  <svg class="icon icon--primary quote__line">
    <use xlink:href="images/sprite.svg#line"></use>
  </svg>
</div>
<div class="media__body">
  <h3 class="media__title quote__author">John Smith</h3>
  <p class="quote__organization">ABC Company</p>
</div>
```

Mosh นำแนวคิดโครงสร้างนี้มาปรับใช้ ใส่เนื้อหาจริงแทนที่ placeholder เดิมในการ์ด testimonial ด้วยข้อความ Lorem Ipsum จำลองเป็นคำพูดลูกค้า พร้อมชื่อ **"John Smith"** และองค์กร **"ABC Company"**

![browser lorem ipsum real quote text](24-Testimonials/048-browser-lorem-ipsum-real-quote-text.png)

Mosh ทดสอบปรับขนาดหน้าต่าง browser หลายระดับเพื่อดูว่าข้อความคำรับรองตัดบรรทัด (wrap) อย่างเหมาะสมหรือไม่ เมื่อความกว้างเปลี่ยนไป

![browser resize 919px quote text](24-Testimonials/049-browser-resize-919px-quote-text.png)

![browser full quote author organization](24-Testimonials/050-browser-full-quote-author-organization.png)

ผลลัพธ์สุดท้ายแสดงข้อความคำรับรองแบบเต็ม พร้อมเส้นคั่นสั้น ๆ (accent line) เหนือชื่อ "John Smith" และ "ABC Company" อยู่ใต้ลงมา ตรงกับ pattern ของ component `quote` เดิม

---

## 9. เริ่มต้น Responsive: `@media` สำหรับ Testimonials

Mosh ยืนยันกฎ CSS สุดท้ายของ `.testimonial__image > .icon-container` อีกครั้งก่อนเริ่มทำ responsive

```css
.testimonial__image > .icon-container {
  position: absolute;
  top: 3rem;
  right: -32px;
}
```

![css testimonial image icon-container final right negative 32px](24-Testimonials/051-css-testimonial-image-icon-container-final-right-negative-32px.png)

จากนั้นเริ่มพิมพ์ `@media` ด้านล่างไฟล์ styles.css โดย VS Code แสดง autocomplete รายการ at-rules ทั้งหมด (`@-moz-document`, `@-moz-keyframes`, `@charset` ฯลฯ) ก่อนเลือก `@media`

![media emmet suggestion responsive start](24-Testimonials/052-media-emmet-suggestion-responsive-start.png)

```css
@media
```

> 📌 คลิปจบลงตรงจุดเริ่มต้นของการเขียน media query สำหรับปรับ typography ของ testimonial ให้ตอบสนอง (responsive) ตามขนาดหน้าจอ ซึ่งเป็นแนวทางเดียวกับที่ Mosh ใช้มาตลอดทั้งคอร์ส คือ**เขียนแบบ mobile-first ก่อน แล้วค่อยเพิ่ม breakpoint สำหรับจอใหญ่ทีหลัง**

---

## สรุปภาพรวมของคลิปนี้

| หัวข้อ | รายละเอียดสำคัญ |
|---|---|
| CSS Grid stretch | `align-items: stretch` เป็นค่า default ทำให้ grid item ว่างเปล่ายืดสูงเท่า sibling อัตโนมัติ |
| Wrapper div pattern | ห่อ `<img>` ด้วย `<div class="testimonial__image">` เพื่อเตรียม positioning context สำหรับไอคอนซ้อนทับ |
| Child combinator | ใช้ `.testimonial__image > img` และ `.testimonial__image > .icon-container` เพื่อเจาะจงเฉพาะลูกโดยตรง |
| Reuse component | Copy โครงสร้าง icon-container จาก `icons.html` และโครงสร้าง blockquote จาก `quotes.html` มาปรับใช้ซ้ำ |
| Position absolute | `top: 3rem; right: -32px;` ทำให้ไอคอนวงกลมลอยคร่อมขอบรูปภาพตามดีไซน์ |
| BEM modifier ผสม | `icon-container--accent` (สีพื้นหลัง) + `icon--white` (สีไอคอน) + `icon--small` (ขนาด) ใช้ร่วมกันได้ |
| Responsive | เริ่มต้น `@media` สำหรับปรับ typography ของ testimonial (ส่วนที่เหลือจะสอนต่อในคลิปถัดไป) |

### แนวคิดสำคัญที่ได้จากคลิปนี้

1. **CSS Grid/Flexbox มี `align-items: stretch` เป็นค่า default** — grid item ที่ไม่ได้กำหนดความสูงจะยืดเท่ากับ sibling ที่สูงที่สุดโดยอัตโนมัติ ต่างจาก block layout ปกติ
2. **Wrapper div ช่วยสร้าง positioning context** — เมื่อจะวาง element ซ้อนทับด้วย `position: absolute` ควรห่อ element เป้าหมายด้วย wrapper ที่มี `position: relative` แยกต่างหาก
3. **Reuse component เดิมเสมอ** — แทนที่จะเขียนใหม่ทุกครั้ง ให้ copy โครงสร้างที่ทำงานได้แล้ว (icon-container, blockquote) มาปรับแก้รายละเอียด (เปลี่ยน icon, เปลี่ยนสี, เปลี่ยนขนาด) ประหยัดเวลาและคงความสม่ำเสมอของโค้ด
4. **BEM modifier หลายตัวผสมกันได้ในคลาสเดียว** — เช่น `icon icon--white icon--small` แต่ละ modifier ควบคุมคุณสมบัติคนละด้าน (สี, ขนาด) ทำให้ CSS ยืดหยุ่นและ reusable สูง
5. **ค่าลบ (negative value) ใน positioning มีประโยชน์มาก** — `right: -32px` ทำให้ element "ล้น" ออกนอกกรอบของ parent ได้ตามต้องการ ซึ่งเป็นเทคนิคที่ใช้บ่อยมากในการทำ overlay icon/badge
6. **Child combinator (`>`) ป้องกัน CSS รั่วไหล (leak)** — เจาะจงเฉพาะลูกโดยตรงของ selector ทำให้กฎ CSS ไม่กระทบ element อื่นที่อาจซ้อนลึกกว่าโดยไม่ตั้งใจ

---

*สรุปจากคลิปที่ 24 ของคอร์ส "Building a Web Site" โดย Mosh Hamedani (codewithmosh.com)*
