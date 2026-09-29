# HTML-CSS-3: 33 - Features Block
**ไฟล์ต้นฉบับ:** "33- Features Block.mp4"

---

## ภาพรวมคลิปนี้

คลิปนี้ Mosh สอนการสร้าง **Features Block** ของหน้า Landing Page "Moshify" ซึ่งเป็นส่วนที่โชว์จุดเด่นของผลิตภัณฑ์ 2 หัวข้อ ได้แก่ "Super Easy to Use" และ "Simply fast websites" โดยแต่ละหัวข้อมีไอคอน หัวข้อย่อย คำอธิบาย ลิงก์ "Learn More" และรูปภาพประกอบ จัดวางแบบ 2 คอลัมน์ (ข้อความ-รูปภาพ) และสลับด้านกันในแต่ละหัวข้อ (ซ้าย-ขวา สลับกับ ขวา-ซ้าย) เพื่อความสวยงามไม่ซ้ำซาก คลิปนี้ยังนำเทคนิคการ optimize รูปภาพด้วย `<picture>`/`<source>`/`srcset` ที่สอนไว้ในคลิป 30 (Optimizing Images) มาใช้ซ้ำกับรูปภาพประกอบของแต่ละ feature ด้วย

![หน้าไตเติล Photoshop mockup ของ Features Block](33-Features-Block/001-photoshop-standard-psd-host-on-cloud-mockup.png)

เนื้อหาหลักที่สอนในคลิปนี้ประกอบด้วย
1. การดูโครงสร้างดีไซน์ของ Features Block ใน Photoshop (มี 2 features เรียงต่อกันในแนวตั้ง)
2. การสร้าง `<section class="block container">` พร้อม `<header class="block__header">` (หัวข้อใหญ่ + คำอธิบาย) เหมือนรูปแบบที่ใช้ในบล็อกก่อนหน้า
3. การสร้างแต่ละ feature ด้วย `<article class="grid grid--1x2 feature">` ที่แบ่งเป็น `.feature__content` (ไอคอน + หัวข้อ + คำอธิบาย + ลิงก์) กับรูปภาพ
4. การนำ SVG sprite icon (`images/sprite.svg#easy`, `#fast`) มาใช้ผ่าน `<use xlink:href="...">`
5. การนำเทคนิค responsive image (`<picture>`, `<source type="image/webp">`, `<source type="image/jpg">`, `srcset` แบบ 1x/2x) มาใช้กับรูปภาพของแต่ละ feature
6. การจัดระยะห่างด้วย `.feature { gap: 4rem 2rem; margin: 12rem 0; }` และปรับ margin พิเศษให้ feature แรกด้วย `.feature:first-of-type`
7. การทำ Responsive ด้วย `@media` query ที่ breakpoint 768px เพื่อสลับตำแหน่งรูปภาพ (ซ้าย/ขวา) ของ feature คู่ (even) ด้วย `:nth-of-type(even)`
8. การทดสอบผลลัพธ์ในเบราว์เซอร์ทั้งมุมมองมือถือและเดสก์ท็อป

---

## 1. ดูโครงสร้างดีไซน์ Features Block ใน Photoshop

Mosh เปิดไฟล์ `standard.psd` เพื่อดูภาพรวมของส่วน Features ซึ่งอยู่ถัดจาก Plans Block ที่ทำไปในคลิปก่อนหน้า ดีไซน์ประกอบด้วยหัวข้อใหญ่ "Host On The Cloud to Keep Growing" พร้อมคำอธิบายสั้นๆ ตามด้วย feature แรก "Super Easy to Use" ที่มีไอคอนวงกลม หัวข้อ คำอธิบาย ลิงก์ "LEARN MORE" อยู่ด้านซ้าย และภาพหน้าจอแดชบอร์ด (การ์ด "Easy to use" กับกราฟ "Balance") อยู่ด้านขวา

![Photoshop mobile.psd ซูมดู Super Easy to Use](33-Features-Block/002-photoshop-mobile-psd-super-easy-to-use-zoom.png)

> 💡 **หมายเหตุ:** ดีไซน์นี้มี feature ที่สองต่อท้ายคือ "Simply fast websites" ซึ่งมีโครงสร้างเหมือนกันทุกอย่าง แต่ **สลับตำแหน่ง** รูปภาพกับข้อความ (รูปภาพอยู่ซ้าย ข้อความอยู่ขวา) เพื่อสร้างจังหวะการอ่านที่ไม่น่าเบื่อ ซึ่งจะใช้ CSS `:nth-of-type(even)` มาจัดการเรื่องนี้ในภายหลัง

![Photoshop แสดงพาเนล Super Easy to Use แบบเต็ม](33-Features-Block/004-photoshop-super-easy-to-use-panel.png)

## 2. สร้าง Section, Header และโครงสร้าง Article

Mosh เริ่มจาก `index.html` ที่มี `<body>` ว่างเปล่า แล้วใช้ Emmet เหมือนรูปแบบที่ทำมาตลอดในคลิปก่อนหน้า (Testimonials, Plans, Domain) คือ

```
section.block.container
```

จากนั้นภายใน section เพิ่ม `<header class="block__header">` ที่มี `<h2>` เป็นหัวข้อใหญ่ "Host On The Cloud to Keep Growing" และ `<p>` เป็นคำอธิบายสั้นๆ ตามด้วยแต่ละ feature ที่ใช้ Emmet

```
article.grid.grid--1x2.feature
```

ได้โครงสร้างเริ่มต้น

```html
<section class="block container">
  <header class="block__header">
    <h2>Host On The Cloud to Keep Growing</h2>
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Sed, voluptatem.</p>
  </header>
  <article class="grid grid--1x2 feature">

  </article>
</section>
```

> 📝 **หมายเหตุ:** โครงสร้างนี้เหมือนกับ Domain Block และ Plans Block ที่ทำมาก่อนหน้า คือใช้ `.block.container` ครอบทั้ง section แล้วใช้ `.grid.grid--1x2` (CSS Grid 2 คอลัมน์ที่มีอยู่แล้วในโปรเจกต์) มาจัดวางเนื้อหาแต่ละ feature เป็น 2 คอลัมน์ (ข้อความ + รูปภาพ)

## 3. สร้างเนื้อหาฝั่งข้อความของ Feature แรก (ไอคอน, หัวข้อ, คำอธิบาย, ลิงก์)

ภายใน `<article class="grid grid--1x2 feature">` Mosh สร้าง `<div class="feature__content">` ครอบกลุ่มข้อความทั้งหมดของ feature ประกอบด้วย

```html
<div class="feature__content">
  <span class="icon-container">
    <svg class="icon icon--primary">
      <use xlink:href="images/sprite.svg#easy"></use>
    </svg>
  </span>
  <h3 class="feature__heading">Super Easy to Use</h3>
  <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Quis ipsum suspendisse ultrices gravida. Risus commodo viverra maecenas accumsan lacus vel facilisis.</p>
  <a href="#" class="link-arrow">Learn More</a>
</div>
```

![โครงสร้าง HTML เต็มของ feature ที่มองผ่าน breadcrumb ใน VS Code](33-Features-Block/036-vscode-full-html-structure-breadcrumb-feature-heading.png)

> 🔧 **จุดสำคัญ:** ไอคอนไม่ได้เป็นไฟล์รูปภาพแยก แต่ใช้ SVG sprite (`images/sprite.svg`) ที่มีไอคอนหลายแบบรวมกันไว้ในไฟล์เดียว แล้วอ้างอิงไอคอนที่ต้องการด้วย `<use xlink:href="images/sprite.svg#easy">` — เทคนิคนี้ช่วยลดจำนวน HTTP request เพราะโหลดไฟล์ SVG เดียวแต่ใช้ไอคอนได้หลายแบบ คลาส `.link-arrow` ก็เป็น component ที่มีอยู่แล้วในโปรเจกต์ (ลิงก์ที่มีลูกศรต่อท้าย) ซึ่งเคยเห็นในคลิปก่อนๆ

## 4. เพิ่มรูปภาพประกอบด้วยเทคนิค Responsive Image (`<picture>`)

ต่อจาก `.feature__content` Mosh พิมพ์ Emmet `picture` เพื่อสร้างโครงสร้าง `<picture><img /></picture>` แล้วขยายต่อด้วย `source` เพื่อสร้าง `<source>` ที่มี `type` และ `srcset`

![พิมพ์ Emmet abbreviation "picture" ใน Command Palette](33-Features-Block/009-vscode-emmet-command-palette.png)

![โครงสร้าง picture/img ที่ขยายจาก Emmet](33-Features-Block/011-vscode-picture-img-expanded.png)

จากนั้นพิมพ์ Emmet `source` ต่อภายใน `<picture>`

![พิมพ์ Emmet abbreviation "source"](33-Features-Block/012-vscode-emmet-source-typing.png)

แล้วเติม attribute `type="image/webp"` และ `srcset="images/easy.webp 1x, images/easy@2x.webp 2x"` เหมือนรูปแบบที่สอนในคลิป Optimizing Images

![source type image/webp เริ่มพิมพ์](33-Features-Block/014-vscode-source-type-image-webp.png)

![srcset ของ webp กำลังพิมพ์](33-Features-Block/015-vscode-source-srcset-easy-webp-1x.png)

![srcset webp 1x กำลังพิมพ์ชื่อไฟล์](33-Features-Block/016-vscode-srcset-easy-webp-1x-typing.png)

![srcset webp 1x, 2x ใกล้เสร็จสมบูรณ์](33-Features-Block/017-vscode-srcset-1x-2x-webp.png)

![source webp เสร็จสมบูรณ์](33-Features-Block/018-vscode-srcset-easy-2x-webp-complete.png)

จากนั้นคัดลอก `<source>` ตัวแรกมาวางอีกชุดเพื่อสร้าง fallback สำหรับ browser ที่ไม่รองรับ WebP โดยเปลี่ยน `type` เป็น `image/jpg` และ `srcset` เป็นไฟล์ `.jpg`

![สำเนา source ตัวที่สองถูกสร้าง](33-Features-Block/019-vscode-second-source-duplicated.png)

![source ตัวที่สอง type=image/jpg](33-Features-Block/020-vscode-second-source-jpg-type.png)

สุดท้ายเติม `<img>` เป็น fallback สุดท้ายที่ทุก browser อ่านได้ พร้อมเพิ่ม `class="feature__image"`

```html
<picture>
  <source type="image/webp" srcset="images/easy.webp 1x, images/easy@2x.webp 2x" />
  <source type="image/jpg" srcset="images/easy.jpg 1x, images/easy@2x.jpg 2x" />
  <img class="feature__image" src="images/easy@2x.jpg" alt="" />
</picture>
```

![img src=images/easy@2x.jpg fallback สุดท้าย](33-Features-Block/021-vscode-img-src-easy-2x-jpg-fallback.png)

![picture element เสร็จสมบูรณ์ทั้ง webp และ jpg fallback](33-Features-Block/022-vscode-picture-complete-webp-jpg-fallback.png)

> 📌 **หมายเหตุสำคัญ:** นี่คือการนำเทคนิคเดียวกับคลิป 30 (Optimizing Images) มาใช้ซ้ำ — ให้ browser เลือกไฟล์ WebP (เล็กกว่า) ก่อน ถ้าไม่รองรับก็ fallback ไปที่ JPG และเลือกความละเอียด 1x หรือ 2x ตาม pixel density ของหน้าจอผู้ใช้ ก่อนหน้านี้ Mosh ต้องเตรียมไฟล์รูปภาพ `easy.jpg`, `easy@2x.jpg`, `easy.webp`, `easy@2x.webp` ไว้ในโฟลเดอร์ `images/resized` ด้วย Photoshop และ CloudConvert เหมือนขั้นตอนในคลิป 30

## 5. ตรวจสอบไฟล์รูปภาพที่เตรียมไว้ใน Finder

Mosh เปิด Finder เพื่อดูไฟล์รูปภาพต้นฉบับ (`easy.jpg`, `fast.jpg`, `banner.png` ฯลฯ) และโฟลเดอร์ `resized` ที่มีไฟล์ที่ผ่านการปรับขนาดและแปลงเป็น WebP แล้ว

![Finder แสดงโฟลเดอร์ images พร้อมไฟล์ easy.jpg, fast.jpg](33-Features-Block/003-finder-images-folder-listing.png)

![Finder โฟลเดอร์ resized แสดง easy.jpg, easy.webp, easy@2x.jpg, easy@2x.webp](33-Features-Block/005-finder-resized-folder-easy-webp-files.png)

![เลือกไฟล์ทั้ง 4 ในโฟลเดอร์ resized เพื่อคัดลอกไปยังโปรเจกต์](33-Features-Block/007-finder-resized-folder-selected-files.png)

![VS Code Explorer แสดงไฟล์ svg และรูปภาพที่อยู่ในโฟลเดอร์ images ของโปรเจกต์](33-Features-Block/006-vscode-explorer-images-folder-svg-files.png)

> 🔍 ในแผง Explorer จะเห็นไฟล์ `logo.svg`, `popular.svg`, `sprite.svg`, `tick.svg` ซึ่งเป็น SVG sprite/icon ที่ใช้ทั่วทั้งโปรเจกต์ รวมถึงไฟล์รูปภาพ `banner.png/webp` ที่ทำไว้ในคลิป Optimizing Images

## 6. ทดสอบผลลัพธ์ Feature แรกในเบราว์เซอร์

หลังจากเขียน HTML เสร็จ Mosh สลับไปที่ Chrome เพื่อดูผลลัพธ์ของ Feature แรก "Super Easy to Use" ที่แสดงไอคอน หัวข้อ คำอธิบาย ลิงก์ Learn More และภาพหน้าจอ dashboard ประกอบ

![เบราว์เซอร์แสดง Super Easy to Use พร้อมภาพ dashboard](33-Features-Block/024-browser-super-easy-to-use-section-preview.png)

## 7. สร้าง Feature ที่สอง "Simply fast websites"

Mosh ทำซ้ำขั้นตอนเดียวกันเพื่อสร้าง `<article class="grid grid--1x2 feature">` ตัวที่สอง โดยเปลี่ยนไอคอนเป็น `#fast` เปลี่ยนหัวข้อเป็น "Simply fast websites" และเปลี่ยนรูปภาพเป็น `fast.jpg`/`fast.webp` (พร้อม 2x) ตามภาพ mockup ที่แสดงกราฟ "Server Request"

![Photoshop mockup ของ Simply fast websites พร้อมกราฟ Server Request](33-Features-Block/027-photoshop-server-request-simply-fast-websites-section.png)

![picture element ของ feature ที่สองด้วยไฟล์ fast](33-Features-Block/025-vscode-picture-jpg-source-img-class-feature-image.png)

![โครงสร้าง article ของ feature ที่สองใน VS Code](33-Features-Block/037-vscode-second-feature-article-structure.png)

เมื่อเลื่อนดูในเบราว์เซอร์จะเห็นทั้งสอง feature เรียงต่อกัน

![เบราว์เซอร์เลื่อนลงเห็น Server Request และ Simply fast websites](33-Features-Block/026-browser-scrolled-server-request-simply-fast-websites.png)

## 8. เขียน CSS จัดระยะห่างของ Features Block

Mosh สลับไปที่ `styles.css` และเริ่มเขียน comment `/* Features */` ตามด้วย selector `.feature` เพื่อกำหนดระยะห่างระหว่าง feature แต่ละอัน

```css
/* Features */
.feature {
  gap: 4rem 2rem;
  margin: 12rem 0;
}

.feature__heading {
  margin: 1rem 0;
}

.feature__image {
  width: 100%;
}
```

![CSS comment Features, .feature gap, .feature__heading margin](33-Features-Block/023-css-features-comment-feature-gap-heading-margin.png)

![.feature__image width: 100% เสร็จสมบูรณ์](33-Features-Block/031-css-feature-image-width-100-percent.png)

> ⚠️ **หมายเหตุ:** `gap: 4rem 2rem;` เป็นการกำหนดระยะห่าง 2 ค่า คือ row-gap 4rem และ column-gap 2rem (ค่าที่ 1 = แนวตั้ง, ค่าที่ 2 = แนวนอน) ส่วน `margin: 12rem 0;` ทำให้แต่ละ feature มีระยะห่างจากกันเยอะพอสมควรในแนวตั้ง (เพราะ layout เดิมเป็นแบบ stack บนมือถือ) และ `.feature__image { width: 100%; }` ทำให้รูปภาพขยายเต็มความกว้างของคอลัมน์เสมอ ไม่ล้นหรือแคบเกินไป

## 9. ปรับ margin พิเศษให้ Feature แรกด้วย `:first-of-type`

เนื่องจาก `margin: 12rem 0;` ทำให้ feature แรกมีช่องว่างด้านบนเยอะเกินไป (เพราะติดกับ header ของ section อยู่แล้ว) Mosh จึงเพิ่ม selector พิเศษเพื่อ override ค่านี้เฉพาะ feature แรก

```css
.feature:first-of-type {
  margin-top: 6rem;
}
```

![autocomplete :first-of-type กำลังพิมพ์](33-Features-Block/041-css-feature-first-of-type-autocomplete.png)

![margin-top: 6rem ของ .feature:first-of-type](33-Features-Block/042-css-feature-first-of-type-margin-top.png)

> ✅ นี่คือตัวอย่างการใช้ pseudo-class `:first-of-type` เพื่อ "แต่งเป็นพิเศษ" ให้ element ตัวแรกในกลุ่มที่มี class เดียวกัน โดยไม่ต้องเพิ่ม class พิเศษใน HTML

## 10. ทำ Responsive: สลับตำแหน่งรูปภาพของ Feature คู่ (even) บนหน้าจอกว้าง

จุดเด่นของคลิปนี้คือการทำให้ feature ที่สอง (และคู่ที่ 4, 6 ถ้ามี) แสดงรูปภาพสลับด้านกับข้อความบนหน้าจอเดสก์ท็อป Mosh ใช้ pseudo-class `:nth-of-type(even)` ร่วมกับ media query

```css
@media screen and (min-width: 768px) {
  .feature:nth-of-type(even) .feature__image {
    order: -1;
  }
}
```

![พิมพ์ .feature:nth-of-type(even) พร้อม autocomplete](33-Features-Block/029-css-feature-nth-of-type-even-autocomplete.png)

![.feature:nth-of-type(even) .feature__heading/.feature__image autocomplete](33-Features-Block/030-css-feature-nth-of-type-even-feature-heading-image.png)

![pseudo-class :first-of-type / nth-of-type(even) เสร็จสมบูรณ์](33-Features-Block/032-vscode-feature-nth-of-type-even-pseudoclass-completion.png)

![media query min-width 768px ครอบ .feature:nth-of-type(even)](33-Features-Block/033-css-media-768px-feature-nth-of-type-even-order.png)

> 🔧 **หลักการสำคัญ:** เนื่องจาก `.feature` เป็น `.grid.grid--1x2` (CSS Grid/Flex) การใช้ CSS property `order` กับลูกของ grid สามารถเปลี่ยนลำดับการแสดงผล "ทางสายตา" ได้โดยไม่ต้องแก้ไขลำดับ element ใน HTML เลย เมื่อกำหนด `order: -1` ให้ `.feature__image` ของ feature คู่ (even) รูปภาพจะถูกดันไปแสดงก่อนข้อความ (อยู่ซ้ายในกรณีนี้) ทำให้เกิด layout สลับฟันปลาสวยงามระหว่าง feature คี่และคู่ — เงื่อนไขนี้ใช้เฉพาะบนหน้าจอกว้างตั้งแต่ 768px ขึ้นไป เพราะบนมือถือทุก feature จะเรียง stack กันตามลำดับ HTML ปกติอยู่แล้ว

## 11. ตรวจสอบผลลัพธ์สุดท้ายในเบราว์เซอร์

Mosh ทดสอบผลลัพธ์ทั้งสอง feature ทั้งบนมุมมองปกติและมุมมองที่เลื่อนดู เพื่อยืนยันว่าเลย์เอาต์ ระยะห่าง และการสลับตำแหน่งรูปภาพทำงานถูกต้อง

![Photoshop เปรียบเทียบทั้งสอง feature เต็มหน้า](33-Features-Block/034-photoshop-full-page-both-features-overview.png)

![เบราว์เซอร์แสดง Super Easy to Use แบบเต็มความกว้าง](33-Features-Block/035-browser-super-easy-to-use-full-view.png)

![เบราว์เซอร์มุมมองกว้างของ Super Easy to Use](33-Features-Block/038-browser-super-easy-to-use-wide-view.png)

![เบราว์เซอร์เลื่อนดูภาพรวมทั้งสอง feature](33-Features-Block/039-browser-scrolled-full-features-view.png)

![CSS สุดท้ายของ .feature gap และ margin](33-Features-Block/040-css-feature-gap-margin-final.png)

![ผลลัพธ์สุดท้าย: หัวข้อ Host on the Cloud พร้อม Features Block](33-Features-Block/043-browser-final-result-host-cloud-heading-features.png)

> ✅ ผลลัพธ์สุดท้ายของ Features Block: หัวข้อใหญ่ "Host On The Cloud to Keep Growing" ตามด้วย 2 feature ที่มีไอคอน หัวข้อ คำอธิบาย ลิงก์ Learn More และรูปภาพ optimize ด้วย `<picture>`/`srcset` โดย feature คู่ (Simply fast websites) สลับตำแหน่งรูปภาพไปอยู่ด้านซ้ายบนหน้าจอกว้าง ระยะห่างระหว่าง feature เหมาะสม และรองรับทั้งมือถือและเดสก์ท็อป

---

## สรุปภาพรวมของคลิปนี้

| หัวข้อ | รายละเอียด |
|---|---|
| HTML Structure | `.block__header` (h2+p) ตามด้วยหลาย `.grid.grid--1x2.feature` แต่ละอันมี `.feature__content` + `<picture>` |
| Icon | SVG sprite ผ่าน `<use xlink:href="images/sprite.svg#easy">` / `#fast` |
| Responsive Image | `<picture>` + `<source type="image/webp">` + `<source type="image/jpg">` + `srcset` 1x/2x (เทคนิคเดียวกับคลิป 30) |
| ระยะห่าง | `.feature { gap: 4rem 2rem; margin: 12rem 0; }` |
| แก้ margin พิเศษ | `.feature:first-of-type { margin-top: 6rem; }` |
| สลับตำแหน่งรูปภาพ | `@media (min-width: 768px) { .feature:nth-of-type(even) .feature__image { order: -1; } }` |
| ทดสอบ | ตรวจสอบทั้งมือถือ (stack) และเดสก์ท็อป (สลับตำแหน่งรูปภาพของ feature คู่) |

**แนวคิดสำคัญที่ได้จากคลิปนี้**
1. การนำเทคนิคที่เคยสอนไปแล้ว (responsive image ด้วย `<picture>`/`srcset` จากคลิป Optimizing Images) มาใช้ซ้ำในบริบทใหม่ แสดงให้เห็นว่าเทคนิค CSS/HTML ที่ดีสามารถนำไปประยุกต์ใช้ได้หลายที่ในโปรเจกต์เดียวกัน
2. SVG sprite (`<use xlink:href="...">`) เป็นวิธีจัดการไอคอนหลายแบบในไฟล์เดียว ลดจำนวน HTTP request และทำให้ดูแลง่ายกว่าไฟล์ภาพแยก
3. Pseudo-class `:first-of-type` และ `:nth-of-type(even)` ช่วยเลือก element เฉพาะตำแหน่งโดยไม่ต้องเพิ่ม class พิเศษใน HTML ทำให้ HTML สะอาดและ CSS ยืดหยุ่น
4. CSS property `order` เป็นเครื่องมือทรงพลังในการเปลี่ยนลำดับการแสดงผลของ Grid/Flex item โดยไม่ต้องแก้ไขลำดับจริงใน HTML — มีประโยชน์มากสำหรับสร้าง layout สลับฟันปลา (zig-zag)
5. การใช้ media query ควบคู่กับ pseudo-class ทำให้ปรับพฤติกรรม layout ได้ต่างกันระหว่างมือถือ (เรียง stack ปกติ) กับเดสก์ท็อป (สลับตำแหน่ง) โดยไม่ต้องเขียน HTML แยกกัน
6. การกำหนด `margin`/`gap` แบบ 2 ค่า (`row-gap column-gap` หรือ `margin-vertical margin-horizontal`) ช่วยควบคุมระยะห่างในแต่ละทิศทางได้ละเอียดกว่าการกำหนดค่าเดียว

---

*สรุปจากคลิปสอนของ Mosh Hamedani (codewithmosh.com) - HTML & CSS Course, คลิปที่ 33: Features Block*
