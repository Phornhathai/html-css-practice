# HTML-CSS-3: 32 - Plans Block
**ไฟล์ต้นฉบับ:** "32- Plans Block.mp4"

---

## ภาพรวมคลิปนี้

คลิปนี้ Mosh สอนการสร้าง **Plans Block** ซึ่งเป็นส่วนแสดงแพ็กเกจราคา (pricing plans) ของหน้า Landing Page "Moshify" โดยมีการ์ดราคา 3 ใบเรียงกัน ได้แก่ Entry, Business (การ์ดตรงกลางที่ถูกเน้นด้วยป้าย "Popular") และ Business Plus แต่ละใบมีชื่อแพ็กเกจ ราคา/เดือน ป้ายส่วนลด รายการฟีเจอร์ที่มีเครื่องหมายถูก และปุ่ม "BUY NOW" โดยใช้ mockup จาก Photoshop (`standard.psd`) เป็นต้นแบบ

![หน้าไตเติลคลิป Plans Block](32-Plans-Block/001-title-slide-plans-block.png)

เนื้อหาหลักที่สอนในคลิปนี้ประกอบด้วย
1. การดูโครงสร้างของดีไซน์ Plans ใน Photoshop
2. การสร้าง section ด้วย Emmet และ HTML ของการ์ดแพ็กเกจ (นำ pattern ของ `badge`, `btn`, `card`, `list` ที่ทำไว้ในคลิปก่อนหน้ามาใช้ซ้ำ)
3. การจัดวางการ์ด 3 ใบด้วย CSS Grid (คลาส `.grid`) และปรับ `gap`
4. การจำกัดความกว้างของการ์ดด้วย `max-width` และจัดกึ่งกลางด้วย `margin: 0 auto`
5. การไฮไลต์แพ็กเกจยอดนิยมด้วย modifier class `.plan--popular` — ขยายขนาดด้วย `transform: scale()`, เพิ่มป้าย "Popular" ด้วย `::before` และรูปภาพ `popular.svg`
6. การใส่ hover effect ให้การ์ดขยายเล็กน้อยเมื่อเอาเมาส์ไปวาง (`:hover { transform: scale() }`)
7. การปรับ typography เฉพาะของ Plans เช่น `.plan__name`, `.plan__price`, `.plan__billing-cycle`, `.plan__description`
8. การทำ Responsive ด้วย `@media` query ปรับขนาดตัวอักษรที่ breakpoint 1024px
9. การทดสอบผลลัพธ์ในเบราว์เซอร์ทั้งมุมมองมือถือ (stacked) และเดสก์ท็อป (3 คอลัมน์)

---

## 1. ดูโครงสร้างดีไซน์ Plans Block ใน Photoshop

Mosh เปิดไฟล์ `standard.psd` ใน Adobe Photoshop เพื่อดูภาพรวมของ Plans Block ก่อนเริ่มเขียนโค้ด โดยดีไซน์ประกอบด้วยการ์ด 3 ใบวางเรียงกัน:

- **Entry** — พื้นหลังสีฟ้า (cyan), ราคา `$14/month`, ป้าย "10% OFF", คำอธิบาย "Easy start on the cloud", ปุ่ม "BUY NOW" แบบ outline (ขอบเส้น ไม่มีพื้นทึบ)
- **Business** (การ์ดตรงกลาง) — พื้นหลังสีน้ำเงิน (blue), ราคา `$24/month`, ป้าย "20% OFF", คำอธิบาย "Optimal Cloud Experience", มีริบบิ้น **"Popular"** อยู่มุมขวาบน, ปุ่ม "BUY NOW" แบบพื้นทึบสีม่วงเข้ม (dark purple/navy)
- **Business plus** — พื้นหลังสีฟ้า (cyan) เหมือน Entry, ราคา `$54/month`, ป้าย "10% OFF", ปุ่ม "BUY NOW" แบบ outline

![ภาพรวม Photoshop mockup การ์ดราคา 3 ใบ](32-Plans-Block/003-photoshop-mockup-overview.png)

![ซูมดูรายละเอียด Photoshop mockup](32-Plans-Block/004-photoshop-mockup-zoom.png)

ทุกการ์ดมีรายการฟีเจอร์เหมือนกัน (มีเครื่องหมายถูกสีเขียวหน้าแต่ละรายการ):
- Unlimited Websites
- Unlimited Bandwidth
- 100 GB SSD Storage
- 3 GB RAM
- 2 CPU Cores

> 💡 **หมายเหตุ:** การ์ด "Popular" (Business) จะถูกทำให้ดูเด่นกว่าการ์ดอื่นด้วยการขยายขนาดใหญ่ขึ้นเล็กน้อย (scale up) และมีริบบิ้นสีเข้มเขียนคำว่า "Popular" พาดอยู่มุมขวาบนของการ์ด

ต่อมา Mosh เปิดไฟล์ Photoshop อีกไฟล์เพื่อดูรายละเอียดของราคาและคำอธิบายในแต่ละแพ็กเกจให้ชัดเจนขึ้น ยืนยันว่า Business มีราคา `$24/month` ส่วนลด `20% OFF` และข้อความ "Optimal Cloud Experience" ส่วน Business plus มีราคา `$54/month`

![Photoshop mockup แสดงราคาของแต่ละแพ็กเกจอย่างชัดเจน](32-Plans-Block/015-photoshop-mockup-business-plans.png)

---

## 2. สร้าง Section ด้วย Emmet และ HTML ของการ์ดแพ็กเกจ

Mosh เริ่มจากไฟล์ `index.html` ที่มี `<body>` ว่างเปล่า

![VS Code แสดง index.html ที่มี body ว่าง](32-Plans-Block/005-vscode-empty-body.png)

จากนั้นพิมพ์ Emmet abbreviation ตามรูปแบบเดียวกับ section ก่อนหน้า (Testimonials, Callout ฯลฯ) คือ:

```
section.block.container.block-plans
```

![พิมพ์ Emmet abbreviation สำหรับ section Plans](32-Plans-Block/006-emmet-section-abbreviation.png)

เมื่อกด Tab จะได้โครงสร้าง HTML เริ่มต้น:

```html
<section class="block container block-plans">

</section>
```

จากนั้น Mosh เปิดไฟล์อ้างอิง `plans.html` (ไฟล์ตัวอย่างโค้ด HTML ของการ์ดแพ็กเกจแรกที่เตรียมไว้ล่วงหน้า) เพื่อคัดลอกโครงสร้าง HTML ของการ์ดแพ็กเกจใบแรก (Entry) มาวางในไฟล์ `index.html` ภายใน `<div class="grid grid--1x3">`

> 📝 **หมายเหตุ:** วิธีนี้เป็นแนวทางเดียวกับที่ Mosh ใช้ในคลิปก่อนหน้า (Testimonials Block) คือแทนที่จะพิมพ์ HTML ที่ซับซ้อนทั้งหมดด้วยมือ เขาคัดลอกโครงสร้างจากไฟล์ตัวอย่างที่เตรียมไว้ แล้วค่อยปรับแต่งรายละเอียด (ราคา, ชื่อแพ็กเกจ, class modifier) ให้ตรงกับแต่ละแพ็กเกจ

โครงสร้าง HTML ของการ์ดแพ็กเกจ 1 ใบ ประกอบด้วย:

```html
<div class="card card--secondary plan">
  <div class="card__header">
    <span class="badge badge--secondary">10% OFF</span>
    <h3 class="plan__name">Entry</h3>
    <p class="plan__price">
      <span class="plan__currency">$</span>14
    </p>
    <p class="plan__billing-cycle">/month</p>
    <p class="plan__description">Easy start on the cloud</p>
  </div>
  <div class="card__body">
    <ul class="list list--tick">
      <li class="list__item">Unlimited Websites</li>
      <li class="list__item">Unlimited Bandwidth</li>
      <li class="list__item">100 GB SSD Storage</li>
      <li class="list__item">3 GB RAM</li>
      <li class="list__item">2 CPU Cores</li>
    </ul>
    <a href="#" class="btn btn--outline btn--block">Buy now!</a>
  </div>
</div>
```

> 🔍 โครงสร้างนี้นำ component ที่มีอยู่แล้วมาใช้ซ้ำทั้งหมด: `.card` (จาก Testimonials Block), `.badge` (จาก Feature Block), `.list--tick` (มีเครื่องหมายถูก, สร้างในคลิปก่อนหน้า) และ `.btn` (ปุ่มมาตรฐานของ Moshify) โดยเพิ่มคลาสใหม่เฉพาะของ Plans คือ `.plan`, `.plan__name`, `.plan__price`, `.plan__currency`, `.plan__billing-cycle`, `.plan__description`

จากนั้น Mosh คัดลอกโค้ดของการ์ดแพ็กเกจใบแรกซ้ำอีก 2 ครั้งเพื่อทำเป็นการ์ดที่ 2 (Business) และการ์ดที่ 3 (Business Plus) แล้วแก้ไขเนื้อหาให้ตรงกับแต่ละแพ็กเกจ

---

## 3. ปรับแต่งการ์ดที่ 2 (Business) ให้เป็นแพ็กเกจ "Popular"

สำหรับการ์ดตรงกลาง (Business) Mosh เปลี่ยน modifier class ของ `.card` และ `.badge` จาก `--secondary` เป็น `--primary` เพื่อให้ได้สีพื้นหลังน้ำเงิน (ตาม design system ที่มีอยู่แล้ว) และเพิ่มคลาส `plan--popular` เข้าไปในการ์ด เพื่อใช้เป็น hook สำหรับ CSS ที่จะทำให้การ์ดนี้ดูเด่นกว่าใบอื่น:

```html
<div class="card card--primary plan plan--popular">
  <div class="card__header">
    <span class="badge badge--primary">20% OFF</span>
    <h3 class="plan__name">Business</h3>
    <p class="plan__price">
      <span class="plan__currency">$</span>24
    </p>
    <p class="plan__billing-cycle">/month</p>
    <p class="plan__description">Optimal Cloud Experience</p>
  </div>
  ...
</div>
```

ปุ่มของแพ็กเกจนี้เปลี่ยนจาก `btn--outline` เป็น `btn--secondary` (หรือปุ่มพื้นทึบสีเข้ม) เพื่อให้ตรงกับ mockup ที่ปุ่มของ Business เป็นแบบพื้นทึบสีม่วงเข้ม ขณะที่การ์ด Entry และ Business Plus ยังคงใช้ปุ่มแบบ outline

![เปิดเบราว์เซอร์ทดสอบผลลัพธ์เบื้องต้นของ 3 การ์ด](32-Plans-Block/016-browser-scale-1-1-popular-card.png)

จากการทดสอบในเบราว์เซอร์ช่วงต้น จะเห็นว่าทั้ง 3 การ์ดมีเนื้อหาเหมือนกันหมด (ราคา $14 เท่ากัน) เนื่องจาก Mosh ยังแก้ตัวเลขราคาไม่ครบทุกใบ แต่จะเห็นความแตกต่างของสี (ฟ้า/น้ำเงิน/ฟ้า) และป้าย "Popular" ที่ปรากฏบนการ์ดตรงกลางแล้ว

---

## 4. จัดวางการ์ดด้วย CSS Grid และกำหนดระยะห่าง (gap)

Mosh เปิดไฟล์ `styles.css` และเพิ่มคอมเมนต์หัวข้อใหม่:

```css
/* Plans Block */
```

จากนั้นเขียนกฎ CSS สำหรับจัดระยะห่างระหว่างการ์ดภายใน grid ของ Plans Block:

```css
.block-plans .grid {
  gap: 4rem;
}
```

![โค้ด CSS .block-plans .grid { gap: 4rem; }](32-Plans-Block/047-css-block-plans-grid-gap.png)

> 📌 คลาส `.grid` และ `grid--1x3` ถูกสร้างไว้แล้วในคลิปก่อนหน้า (Feature Block) โดย `.block-plans .grid` เป็นการเจาะจงใช้ selector ที่จำกัดขอบเขตเฉพาะ grid ที่อยู่ภายใน `.block-plans` เท่านั้น (ไม่กระทบ grid ของ section อื่น) แล้วเพิ่ม `gap: 4rem` เพื่อให้มีช่องว่างระหว่างการ์ดมากขึ้น เนื่องจากค่า default gap เดิมเล็กเกินไปสำหรับการ์ดราคาที่มีขนาดใหญ่

จากนั้น Mosh ทดลองย่อขนาดหน้าต่างเบราว์เซอร์เพื่อดูผลลัพธ์ที่ breakpoint ต่าง ๆ

---

## 5. จำกัดความกว้างของการ์ดด้วย max-width

เนื่องจากการ์ดแต่ละใบมีความกว้างเท่ากับคอลัมน์ของ grid ซึ่งอาจกว้างเกินไปในบางหน้าจอ Mosh จึงเพิ่มกฎ:

```css
.block-plans .card {
  max-width: 500px;
  margin: 0 auto;
}
```

![โค้ด CSS .block-plans .card { max-width: 500px; margin: 0 auto; }](32-Plans-Block/050-css-block-plans-grid-card-max-width.png)

> 🔧 `max-width: 500px` จำกัดไม่ให้การ์ดกว้างเกินไปเมื่อพื้นที่ของคอลัมน์มีขนาดใหญ่ ส่วน `margin: 0 auto` ใช้จัดให้การ์ดอยู่กึ่งกลางของคอลัมน์นั้น ๆ (เนื่องจากการ์ดถูกจำกัดความกว้างแล้ว จึงต้องจัดกึ่งกลางเพื่อไม่ให้เอนไปทางซ้ายของคอลัมน์)

---

## 6. เพิ่มป้าย "Popular" ด้วย ::before Pseudo-element

เพื่อให้การ์ด Business มีริบบิ้นคำว่า "Popular" ปรากฏที่มุมขวาบนตามดีไซน์ Mosh ใช้ pseudo-element `::before` ดึงรูปภาพ SVG มาแสดงผล:

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

![โค้ด CSS .plan--popular .card__header::before ดึงรูป popular.svg](32-Plans-Block/007-css-plan-popular-card-header-before.png)

![โค้ด CSS badge::before พร้อมค่า top: -6px และ right: 5%](32-Plans-Block/017-css-badge-before-position-media-query.png)

> ⚠️ **จุดสำคัญ:** `.card__header` ต้องกำหนด `position: relative;` ก่อน เพื่อให้ `::before` ที่มี `position: absolute` อ้างอิงตำแหน่งจากกรอบของ `.card__header` แทนที่จะลอยไปอ้างอิงตำแหน่งของ body/viewport เนื้อหาของ `content` เป็น `url(../images/popular.svg)` ซึ่งเป็นไฟล์รูปริบบิ้น "Popular" ที่เตรียมไว้ในโฟลเดอร์ `images` แล้ว ค่า `top: -6px` และ `right: 5%` ใช้จัดตำแหน่งริบบิ้นให้เยื้องออกไปด้านบนขวาของกรอบการ์ดเล็กน้อยให้ตรงกับ mockup

---

## 7. ทำให้การ์ด Popular ดูใหญ่ขึ้นด้วย transform: scale()

เพื่อให้การ์ด Business (การ์ดยอดนิยม) โดดเด่นกว่าการ์ดอื่น Mosh เพิ่มกฎขยายขนาดการ์ดนั้นเล็กน้อยด้วย `transform: scale()`:

```css
.plan--popular {
  transform: scale(1.1);
}
```

ระหว่างพิมพ์ VS Code แสดง IntelliSense เสนอ property ที่ขึ้นต้นด้วย "tr" ได้แก่ `transform`, `transition`, `transform-origin` และเมื่อพิมพ์ค่า `scale` ต่อ ระบบก็เสนอฟังก์ชันย่อยเช่น `scale()`, `scale3d()`, `scaleX()`, `scaleY()`, `scaleZ()`

![Autocomplete แสดงตัวเลือก property ที่ขึ้นต้นด้วย tr](32-Plans-Block/011-css-transform-autocomplete.png)

![Autocomplete แสดงฟังก์ชัน scale()](32-Plans-Block/012-css-scale-autocomplete.png)

![กำลังพิมพ์ค่า scale(1.1) ในโค้ด](32-Plans-Block/013-css-scale-1-1-editing.png)

![โค้ด transform: scale(1.1) เสร็จสมบูรณ์](32-Plans-Block/014-css-scale-1-1-committed.png)

เมื่อบันทึกและดูผลในเบราว์เซอร์ จะเห็นว่าการ์ดตรงกลาง (Business) ขยายใหญ่กว่าการ์ดข้างเคียงเล็กน้อย ทำให้ดูโดดเด่นขึ้นตามดีไซน์ พร้อมกับริบบิ้น "Popular" ที่ปรากฏอยู่มุมขวาบน

![ผลลัพธ์ในเบราว์เซอร์ การ์ด Popular ขยายด้วย scale(1.1)](32-Plans-Block/016-browser-scale-1-1-popular-card.png)

> ✅ ค่า `scale(1.1)` หมายถึงขยายขนาดของ element ขึ้น 10% จากขนาดปกติ โดยใช้จุดศูนย์กลาง (center) เป็นจุดอ้างอิงในการขยาย (default `transform-origin: center`) ทำให้การ์ดขยายออกทั้งสี่ด้านเท่า ๆ กัน

---

## 8. ปรับแต่ง Typography เฉพาะของ Plan (ชื่อ, ราคา, รอบบิล, คำอธิบาย)

Mosh เพิ่มกฎ CSS สำหรับจัดสไตล์ข้อความภายในการ์ดให้ตรงกับ mockup:

```css
.plan__name {
  color: #fff;
  margin: 0;
  font-weight: 500;
  font-size: 2.4rem;
}

.plan__price {
  font-size: 6rem;
}
```

![โค้ด .plan__name และ .plan__price](32-Plans-Block/031-css-plan-name-color-margin-font.png)

นอกจากนี้ยังมีกฎเพิ่มเติมสำหรับ:
- `.plan__billing-cycle` — ปรับ `font-size`, `font-weight: 300`, `opacity` ให้ดูจางกว่าตัวราคาหลัก และ `margin-right` เพื่อเว้นระยะจากราคา
- `.plan__description` — ปรับ `font-size`, `font-weight: 300`, `letter-spacing`, `display: block` ให้ข้อความคำอธิบายอยู่ในบรรทัดใหม่และมีสไตล์บาง
- `.plan .list__item` — เพิ่ม `margin-bottom` ให้แต่ละรายการฟีเจอร์มีระยะห่างมากขึ้นอ่านง่ายขึ้น

> 🔍 การตั้งชื่อคลาสตามรูปแบบ BEM (`plan__name`, `plan__price`, `plan__billing-cycle`, `plan__description`) สอดคล้องกับแนวทางที่ Mosh ใช้ตลอดทั้งคอร์ส คือ block คือ `.plan` และแต่ละส่วนย่อยภายในคือ element ที่ต่อด้วย `__`

---

## 9. ทำ Responsive ด้วย Media Query ที่ breakpoint 1024px

เพื่อให้ตัวอักษรไม่ใหญ่เกินไปบนหน้าจอขนาดกลาง (เช่น แท็บเล็ตแนวนอนหรือหน้าจอ desktop ที่ยังไม่กว้างมาก) Mosh เพิ่ม media query:

```css
@media screen and (min-width: 1024px) {
  .plan__name {
    font-size: 1.4rem;
  }

  .plan__price {
    font-size: 5rem;
  }
}
```

![โค้ด media query ปรับ font-size ของ plan__name และ plan__price ที่ 1024px](32-Plans-Block/018-css-media-1024-plan-name-price.png)

> 💡 ค่า `font-size` ของ `.plan__name` และ `.plan__price` ที่กำหนดไว้นอก media query (2.4rem และ 6rem) เป็นค่าที่ใช้ตั้งแต่หน้าจอเล็กสุด (mobile-first) ส่วนภายใน media query `min-width: 1024px` คือค่าที่ปรับให้เล็กลงกว่าที่คิดไว้แรก เนื่องจากเมื่อการ์ด 3 ใบเรียงกันในแนวนอนที่หน้าจอความกว้างระดับนี้ ตัวอักษรขนาดใหญ่เกินไปจะทำให้ข้อความล้นหรือดูไม่สมดุลกับพื้นที่การ์ด

---

## 10. เพิ่ม Hover Effect ให้การ์ดขยายขนาดเมื่อเอาเมาส์ชี้

Mosh ต้องการให้ผู้ใช้รู้สึกถึง interactivity เมื่อเอาเมาส์ไปวางเหนือการ์ดแพ็กเกจ จึงเพิ่ม pseudo-class `:hover`:

```css
.plan:hover {
  transform: scale(1.05);
}
```

ระหว่างพิมพ์ VS Code แสดง suggestion `:hover` และตัวเลือก selector ที่มีอยู่แล้วเช่น `.btn--accent:hover`, `.btn--outline:hover`, `.btn--primary:hover`, `.btn--secondary:hover`, `.link-arrow:hover::after`

![พิมพ์ .plan:hov แล้ว IntelliSense แสดงตัวเลือก :hover](32-Plans-Block/020-css-plan-hover-autocomplete.png)

![โค้ด .plan:hover {} ว่างเปล่าก่อนเติมเนื้อหา](32-Plans-Block/021-css-plan-hover-empty-rule.png)

![Autocomplete แสดง property transform ในกฎ hover](32-Plans-Block/022-css-transform-autocomplete-hover.png)

![Autocomplete แสดงฟังก์ชัน scale() ในกฎ hover](32-Plans-Block/023-css-scale-autocomplete-hover.png)

![โค้ด .plan:hover { transform: scale(1.05); }](32-Plans-Block/024-css-scale-1-05-hover.png)

หลังจากนั้น Mosh ทดสอบในเบราว์เซอร์ โดยเอาเมาส์ไปวางเหนือการ์ด Entry (การ์ดปกติ ไม่ใช่ Popular) จะเห็นว่าการ์ดขยายใหญ่ขึ้นเล็กน้อยตาม `scale(1.05)`

![ผลลัพธ์การ hover การ์ด Entry ขยายเล็กน้อย](32-Plans-Block/026-browser-hover-scale-effect.png)

### เพิ่มกฎเฉพาะสำหรับการ์ด Popular เมื่อ hover

เนื่องจากการ์ด `.plan--popular` มีค่า `transform: scale(1.1)` เป็นค่าเริ่มต้นอยู่แล้ว หากใช้กฎ `.plan:hover { transform: scale(1.05); }` ตรง ๆ จะเกิดปัญหาค่า `transform` ถูก override (การ์ด Popular จะกลับไปเล็กลงเหลือ 1.05 แทนที่จะเป็น 1.1 เมื่อ hover) Mosh จึงเพิ่มกฎเฉพาะสำหรับ `.plan--popular:hover` แยกต่างหาก:

```css
.plan--popular:hover {
  transform: scale(1.05);
}
```

![โค้ดเพิ่มกฎ .plan--popular:hover แยกจาก .plan:hover ปกติ](32-Plans-Block/027-css-plan-popular-hover-added.png)

![Autocomplete ระหว่างพิมพ์ .plan--popular:hover](32-Plans-Block/028-css-plan-popular-hover-autocomplete.png)

> ⚠️ **ข้อควรระวัง:** เมื่อมี selector สอง selector ที่ specificity เท่ากัน (`.plan:hover` และ `.plan--popular:hover`) แต่ประกาศ property เดียวกัน (`transform`) ลำดับการเขียนในไฟล์ CSS (source order) จะเป็นตัวตัดสินว่ากฎไหนชนะ — กฎที่เขียนทีหลังจะ override กฎก่อนหน้า ดังนั้น Mosh จึงต้องเขียน `.plan--popular:hover` ไว้หลัง `.plan:hover` เพื่อให้การ์ด Popular แสดงผลถูกต้องเมื่อ hover

ทดสอบผลลัพธ์ในเบราว์เซอร์อีกครั้งโดย hover เหนือการ์ด Popular พบว่าการ์ดยังคงมีขนาดที่เหมาะสม ไม่กระโดดเล็กลงเมื่อ hover

![ผลลัพธ์การ hover การ์ด Popular](32-Plans-Block/029-browser-hover-popular-card.png)

---

## 11. เพิ่ม Transition ให้การขยายขนาดเปลี่ยนแบบนุ่มนวล

เพื่อให้เอฟเฟกต์การขยายขนาด (scale) เมื่อ hover ไม่กระตุกแบบทันทีทันใด แต่เปลี่ยนแปลงอย่างนุ่มนวล (smooth) Mosh เพิ่ม property `transition` ให้กับคลาสหลัก `.plan`:

```css
.plan {
  transition: transform 0.2s ease-out;
}
```

ระหว่างพิมพ์ VS Code แสดง suggestion property ที่ขึ้นต้นด้วย "tr" (transform, transition, transform-origin) และเมื่อพิมพ์ `transition:` ต่อ ระบบเสนอค่า `cubic-bezier(...)` หลายแบบสำหรับ timing function

![Autocomplete property ขึ้นต้นด้วย tr ในกฎ .plan](32-Plans-Block/032-css-transform-transition-autocomplete.png)

![Autocomplete แสดงตัวเลือก cubic-bezier ต่าง ๆ](32-Plans-Block/033-css-transition-cubic-bezier-autocomplete.png)

![Autocomplete แสดงคำแนะนำ transform / text-transform](32-Plans-Block/034-css-transition-transform-autocomplete.png)

![โค้ด .plan { transition: ... } เสร็จสมบูรณ์](32-Plans-Block/037-css-plan-transition-rule.png)

![Autocomplete เพิ่มเติมสำหรับ transition-transform](32-Plans-Block/038-css-transition-transform-autocomplete2.png)

![รายการ cubic-bezier suggestion อีกครั้ง](32-Plans-Block/039-css-transition-cubic-bezier-list.png)

> 📝 **หมายเหตุ:** `transition` ที่ใส่ไว้บนคลาสฐาน `.plan` (ไม่ใช่บน `:hover`) ทำให้การเปลี่ยนแปลงค่า `transform` ทำงานแบบนุ่มนวลทั้งตอนเมาส์เข้า (hover) และตอนเมาส์ออก (กลับสู่ขนาดปกติ) นี่คือแนวทางมาตรฐานของ CSS transitions คือกำหนด `transition` ไว้ที่ selector ปกติ ไม่ใช่ที่ `:hover`

---

## 12. ทดสอบผลลัพธ์บนเบราว์เซอร์ทั้ง Mobile และ Desktop

Mosh เปิด Live Server ทดสอบหน้าเว็บ (`127.0.0.1:5500/index.html`) และทดลองปรับขนาดหน้าต่างเบราว์เซอร์ให้แคบลงเพื่อดูมุมมองมือถือ พบว่าการ์ดทั้ง 3 ใบเรียงซ้อนกันในแนวตั้ง (stacked) โดยอัตโนมัติตามพฤติกรรม default ของ CSS Grid เมื่อพื้นที่แนวนอนไม่เพียงพอ

![มุมมอง Entry card แบบใกล้ (mobile view)](32-Plans-Block/040-browser-entry-card-closeup.png)

![เลื่อนลงดูปุ่ม BUY NOW บนมือถือ](32-Plans-Block/041-browser-scrolled-buy-now-button.png)

เมื่อเอาเมาส์ไปวางเหนือปุ่ม "BUY NOW" (ปุ่มแบบ outline) จะเห็นว่าปุ่มเปลี่ยนเป็นพื้นทึบสีเข้ม (dark fill) ตาม hover state ของ `.btn--outline:hover` ที่สร้างไว้ในคลิปก่อนหน้า

![ปุ่ม BUY NOW เปลี่ยนเป็นพื้นทึบเมื่อ hover](32-Plans-Block/042-browser-buy-now-hover-dark-fill.png)

![มุมมองมือถือแคบ scrolled ลงมา](32-Plans-Block/043-browser-mobile-narrow-view.png)

![เลื่อนดูการ์ดถัดไปในมุมมองมือถือ](32-Plans-Block/044-browser-mobile-scrolled.png)

![ปุ่ม BUY NOW hover ในมุมมองมือถือ](32-Plans-Block/045-browser-mobile-buy-now-hover.png)

![ปุ่ม BUY NOW พื้นเข้มเมื่อ hover ในมุมมองมือถือ](32-Plans-Block/046-browser-mobile-buy-now-dark.png)

![เลื่อนดูการ์ดที่สองพร้อมริบบิ้น Popular ในมือถือ](32-Plans-Block/048-browser-mobile-scrolled-second-card.png)

![การ์ดเรียงซ้อนกันแนวตั้งในมุมมองมือถือแคบ](32-Plans-Block/049-browser-mobile-stacked-cards.png)

![การ์ดที่สองพร้อม Popular ribbon ในมุมมองมือถือ](32-Plans-Block/051-browser-mobile-second-card-popular.png)

จากนั้น Mosh ขยายหน้าต่างเบราว์เซอร์กลับมาที่ขนาดเดสก์ท็อปเต็มความกว้าง เพื่อดูผลลัพธ์สุดท้ายที่การ์ดทั้ง 3 ใบเรียงกันในแนวนอน (3 คอลัมน์) ตาม design เดิม พร้อมมี gap ระหว่างการ์ด, การ์ด Popular ขยายใหญ่กว่าเล็กน้อย, และริบบิ้น "Popular" ปรากฏถูกตำแหน่งมุมขวาบน

![มุมมองเดสก์ท็อป 3 การ์ดเรียงกันแนวนอน](32-Plans-Block/052-browser-three-cards-wide-view.png)

![ซูมดูปุ่ม BUY NOW ของทั้ง 3 การ์ด](32-Plans-Block/053-browser-three-cards-buy-now-zoom.png)

![มุมมองสุดท้ายของ 3 การ์ด พร้อมปุ่ม BUY NOW](32-Plans-Block/054-browser-three-cards-final-buy-now.png)

![ผลลัพธ์สุดท้าย 3 แพ็กเกจ พร้อมริบบิ้น Popular บนการ์ดตรงกลาง](32-Plans-Block/055-browser-final-three-plans-popular-ribbon.png)

> ✅ ผลลัพธ์สุดท้ายของ Plans Block: การ์ด 3 ใบจัดวางด้วย CSS Grid, มีระยะห่าง (gap) ที่เหมาะสม, การ์ดตรงกลาง (Popular) ถูกขยายขนาดและมีริบบิ้นกำกับ, ทุกการ์ดมี hover effect ขยายขนาดแบบนุ่มนวล, ปุ่ม BUY NOW มี hover state เปลี่ยนสี และ layout ปรับตัวตามขนาดหน้าจอได้ทั้ง mobile (stacked) และ desktop (3 คอลัมน์)

---

## สรุปภาพรวมของคลิปนี้

| หัวข้อ | รายละเอียด |
|---|---|
| HTML Structure | `.card` + `.plan` + `.badge` + `.list--tick` + `.btn` ประกอบกันเป็นการ์ดแพ็กเกจ 3 ใบ คัดลอกจากไฟล์อ้างอิง `plans.html` |
| Layout | ใช้ `.grid` (CSS Grid ที่มีอยู่แล้ว) + `.block-plans .grid { gap: 4rem; }` |
| จำกัดขนาดการ์ด | `.block-plans .card { max-width: 500px; margin: 0 auto; }` |
| ไฮไลต์ Popular | `.plan--popular` + `transform: scale(1.1)` + `::before` แสดงริบบิ้น `popular.svg` |
| Typography | `.plan__name`, `.plan__price`, `.plan__billing-cycle`, `.plan__description` |
| Responsive | `@media screen and (min-width: 1024px)` ปรับ font-size ของชื่อ/ราคาให้เล็กลง |
| Hover Effect | `.plan:hover { transform: scale(1.05); }` และ `.plan--popular:hover { transform: scale(1.05); }` แยกเพื่อไม่ให้ override ผิด |
| Smooth Animation | `.plan { transition: transform 0.2s ease-out; }` |
| ทดสอบ | ตรวจสอบทั้ง mobile (stacked) และ desktop (3 คอลัมน์) รวมถึง hover state ของปุ่ม BUY NOW |

**แนวคิดสำคัญที่ได้จากคลิปนี้**
1. การนำ component ที่สร้างไว้แล้ว (`.card`, `.badge`, `.btn`, `.list--tick`) มาผสมกันเพื่อสร้าง UI ใหม่ที่ซับซ้อนขึ้น (การ์ดแพ็กเกจราคา) แทนที่จะเขียนใหม่ทั้งหมด
2. การใช้ modifier class ตามแนวคิด BEM (`.plan--popular`) เพื่อสร้างความแตกต่างเฉพาะจุดโดยไม่กระทบโครงสร้างหลัก
3. `transform: scale()` เป็นเครื่องมือสำคัญในการทำให้ element หนึ่งดูโดดเด่นกว่า element อื่นในกลุ่มเดียวกัน โดยไม่ต้องเปลี่ยนขนาดจริง (width/height) ของ element
4. เมื่อมีสอง selector ที่มี specificity เท่ากันแต่ประกาศ property เดียวกัน CSS จะใช้กฎ "ลำดับการเขียนทีหลังชนะ" (source order) จึงต้องระวังการจัดลำดับ selector ที่ทับซ้อนกัน เช่น `.plan:hover` กับ `.plan--popular:hover`
5. `::before` และ `::after` เป็นเครื่องมือที่มีประโยชน์มากสำหรับการเพิ่มองค์ประกอบตกแต่ง (เช่น ริบบิ้น, ไอคอน) โดยไม่ต้องเพิ่ม HTML element จริง
6. การใส่ `transition` ไว้ที่ selector ปกติ (ไม่ใช่ที่ `:hover`) ทำให้ animation ทำงานนุ่มนวลทั้งขาเข้าและขาออกของ hover state

---
*สรุปจากคลิปสอนของ Mosh Hamedani (codewithmosh.com) - HTML & CSS Course, คลิปที่ 32: Plans Block*
