# HTML-CSS-3: 26 - Collapsibles

**ไฟล์ต้นฉบับ:** 26- Collapsibles.mp4

▶️ [ดูวิดีโอ](../../HTML-CSS-3/26-%20Collapsibles.mp4)

---

## ภาพรวมคลิปนี้

![ภาพรวมคลิปนี้](26-Collapsibles/001-title-slide.png)

คลิปนี้ Mosh สอนการสร้าง **Collapsible component** (เรียกอีกชื่อว่า Accordion) ซึ่งเป็นกล่องที่คลิกที่หัวข้อแล้วสามารถ **ขยาย/ย่อ** เนื้อหาข้างในได้ — pattern นี้มักใช้ใน footer ของเว็บไซต์ (คอลัมน์ PRODUCTS, COMPANY, SUPPORT บนมือถือ) โดยคลิปนี้ครอบคลุมทั้ง CSS (โครงสร้าง, ไอคอนลูกศร, การซ่อน/แสดงเนื้อหา) และ **JavaScript พื้นฐาน** (การ toggle class ด้วย `classList.toggle`) รวมถึงเทคนิคการทำ **CSS transition แบบ smooth animation** สำหรับการขยาย/ย่อ ซึ่งเป็นเรื่องที่ซับซ้อนกว่าที่คิด เพราะ `display` และค่าความสูงแบบ `auto` ไม่สามารถ animate ได้ตรงๆ

![Browser: ตัวอย่าง footer accordion บนมือถือ](26-Collapsibles/002-browser-footer-collapsible-accordion-preview.png)

> 💡 Mosh อธิบายว่า pattern นี้พบได้ทั่วไปในเว็บไซต์จริง เช่น footer ของเว็บไซต์ที่มือถือจะยุบคอลัมน์เมนูเป็นแถบที่กดขยายได้ เพื่อประหยัดพื้นที่หน้าจอ

---

## 1. เขียนโครงสร้าง HTML ของ Collapsible

เริ่มต้นด้วย `<div class="collapsible">` เป็น container หลัก

![เริ่มเขียน div collapsible](26-Collapsibles/003-html-collapsible-div-start.png)

ภายในใส่ `<header class="collapsible__header">` สำหรับส่วนหัวที่คลิกได้

![header class collapsible__header](26-Collapsibles/004-html-header-class-collapsible-header.png)

ภายใน header ใส่ `<h2 class="collapsible__heading">Item 1</h2>`

![h2 collapsible__heading พร้อมข้อความ Item 1](26-Collapsibles/005-html-h2-collapsible-heading-item1.png)

ตามด้วยไอคอนลูกศร (chevron) โดยใช้ `<svg class="icon">` แบบเดียวกับที่เคยใช้ในบทเรียนก่อนหน้า (Media Objects, Testimonials)

![เริ่มเขียน svg icon chevron](26-Collapsibles/006-html-svg-icon-chevron-start.png)

ภายใน svg ใส่ `<use xlink:href="images/sprite.svg#chevron"></use>` เพื่อดึงรูปลูกศรจาก sprite sheet ที่มีอยู่แล้วในโปรเจกต์

![use xlink href sprite svg chevron](26-Collapsibles/007-html-svg-xlink-href-sprite-chevron.png)

ปิด `</header>` แล้วตามด้วย `<div class="collapsible__content">` ที่มีพารากราฟ Lorem Ipsum อยู่ข้างใน (เนื้อหาที่จะถูกซ่อน/แสดง)

![collapsible__content div พร้อมพารากราฟ](26-Collapsibles/008-html-collapsible-content-div-paragraph.png)

โค้ด HTML ทั้งหมด:

```html
<div class="collapsible">
  <header class="collapsible__header">
    <h2 class="collapsible__heading">Item 1</h2>
    <svg class="icon collapsible__chevron">
      <use xlink:href="images/sprite.svg#chevron"></use>
    </svg>
  </header>
  <div class="collapsible__content">
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolorum, accusamus.
  </div>
</div>
```

ผลลัพธ์ในเบราว์เซอร์ก่อนใส่ CSS: เห็นหัวข้อ ไอคอน และเนื้อหาเรียงต่อกันแบบไม่มีสไตล์ใดๆ

![Browser: preview ก่อนใส่ CSS](26-Collapsibles/009-browser-unstyled-collapsible-preview.png)

---

## 2. จัดวาง Header ด้วย Flexbox

เขียน selector `.collapsible__header`

![เริ่ม selector .collapsible__header](26-Collapsibles/010-css-collapsible-header-selector.png)

ใส่ `display: flex;` เพื่อให้หัวข้อกับไอคอนอยู่ในแนวเดียวกัน (แนวนอน)

![collapsible__header display flex](26-Collapsibles/011-css-collapsible-header-display-flex.png)

ตามด้วย `justify-content: space-between;` เพื่อดันไอคอนไปชิดขวาสุด ในขณะที่หัวข้อชิดซ้าย

![justify-content space-between](26-Collapsibles/012-css-collapsible-header-justify-content-space-between.png)

```css
.collapsible__header {
  display: flex;
  justify-content: space-between;
}
```

จากนั้นเขียน selector `.collapsible__heading` ใส่ `margin-top: 0;` เพื่อลบ margin บนของ h2 ให้ชิดขอบบน

![collapsible__heading margin-top 0](26-Collapsibles/013-css-collapsible-heading-margin-top-0.png)

ผลลัพธ์ในเบราว์เซอร์: หัวข้อกับไอคอนอยู่คนละฝั่งของแถวแล้ว

![Browser: header แสดงผลแบบ flex](26-Collapsibles/014-browser-header-flex-icon-right-aligned.png)

---

## 3. ขยายขนาดตัวอักษรหัวข้อ

เพิ่ม `font-size: 3rem;` ให้กับ `.collapsible__heading` เพื่อให้ดูโดดเด่นเหมือนหัวข้อจริง

![collapsible__heading font-size 3rem](26-Collapsibles/015-css-collapsible-heading-font-size-3rem.png)

```css
.collapsible__heading {
  margin-top: 0;
  font-size: 3rem;
}
```

ผลลัพธ์ในเบราว์เซอร์: หัวข้อมีขนาดใหญ่ขึ้นชัดเจน

![Browser: หัวข้อขนาดใหญ่](26-Collapsibles/016-browser-heading-large-font-styled.png)

---

## 4. สไตล์ไอคอนลูกศร (Chevron)

กลับไปที่ HTML เพิ่ม class `icon--white` และ `collapsible__chevron` ให้กับ `<svg>` (BEM modifier ซ้อนกันหลายตัว)

![svg icon icon--white collapsible__chevron](26-Collapsibles/017-css-icon-white-collapsible-chevron-class.png)

จากนั้นเขียน CSS `.collapsible__chevron { transform: rotate(-90deg); }` เพื่อหมุนไอคอนลูกศรให้ชี้ไปทางขวา (สถานะปิด/ย่อ) แทนที่จะชี้ลงเหมือนค่า default ของไอคอนในไฟล์ sprite

![collapsible__chevron transform rotate -90deg](26-Collapsibles/018-css-collapsible-chevron-transform-rotate-90deg.png)

```css
.collapsible__chevron {
  transform: rotate(-90deg);
}
```

> 🔧 หลักการ: ไอคอน chevron ในไฟล์ sprite ถูกวาดมาให้ชี้ลงเป็นค่าเริ่มต้น การหมุน `-90deg` ทำให้ชี้ไปทางขวาแทน ซึ่งสื่อความหมายว่า "กดเพื่อขยาย" (คล้ายปุ่ม play หรือลูกศรบอกทิศทางที่จะเปิด)

---

## 5. ซ่อนเนื้อหาเริ่มต้นด้วย `display: none`

เขียน selector `.collapsible__content { display: none; }` เพื่อซ่อนเนื้อหาไว้ก่อนโดย default

![collapsible__content display none](26-Collapsibles/019-css-collapsible-content-display-none.png)

ผลลัพธ์ในเบราว์เซอร์: เนื้อหา Lorem Ipsum หายไป เหลือแค่ header กับไอคอน

![Browser: เนื้อหาถูกซ่อน](26-Collapsibles/020-browser-content-hidden-by-default.png)

---

## 6. สร้าง Modifier `.collapsible--expanded` สำหรับสถานะ "ขยาย"

Mosh อธิบายว่าต้องมี modifier class เพื่อสลับสถานะระหว่าง "ปิด" (ค่า default) กับ "เปิด" (expanded) เขียน selector ใหม่ `.collapsible--expanded .collapsible__chevron`

![selector .collapsible--expanded .collapsible__chevron](26-Collapsibles/021-css-collapsible--expanded-modifier-selector.png)

ใส่ `transform: rotate(0);` เพื่อให้ไอคอนกลับไปชี้ลง (สถานะขยายแล้ว) เมื่อ `.collapsible` มี class `--expanded`

![collapsible--expanded chevron rotate 0](26-Collapsibles/022-css-collapsible--expanded-chevron-rotate-0.png)

```css
.collapsible--expanded .collapsible__chevron {
  transform: rotate(0);
}
```

ตามด้วย selector `.collapsible--expanded .collapsible__content { display: block; }` เพื่อแสดงเนื้อหาเมื่ออยู่ในสถานะขยาย

![collapsible--expanded content display block](26-Collapsibles/023-css-collapsible--expanded-content-display-block.png)

```css
.collapsible--expanded .collapsible__content {
  display: block;
}
```

Mosh ทดสอบโดยเข้า DevTools แล้วเพิ่ม class `collapsible--expanded` ให้กับ `<div class="collapsible">` ด้วยมือ (ผ่าน devtools) เพื่อยืนยันว่า CSS ทำงานถูกต้อง — เนื้อหาปรากฏขึ้นและไอคอนหมุนกลับมาชี้ลง

![DevTools ทดสอบเพิ่ม class collapsible--expanded ด้วยมือ](26-Collapsibles/024-devtools-manually-add-expanded-class-test.png)

> 📌 หลักการ BEM modifier + JavaScript toggle: CSS เตรียมกฎไว้ล่วงหน้าสำหรับทั้งสองสถานะ (ปิด/เปิด) โดยอาศัยการมี-ไม่มี class `--expanded` เป็นตัวตัดสิน ส่วน JavaScript มีหน้าที่แค่ "เพิ่ม/ลบ" class นี้เท่านั้น ไม่ต้องไปยุ่งกับ style โดยตรง — เป็นแนวทางที่ maintainable กว่า

---

## 7. เพิ่มไฟล์ JavaScript

Mosh สลับไปที่ Finder แล้วสร้างโฟลเดอร์ `js/` พร้อมไฟล์ `main.js` (ลากไฟล์เข้ามาใน VS Code)

![Finder: โฟลเดอร์ js พร้อมไฟล์ main.js](26-Collapsibles/025-finder-js-folder-main-js-dragged-in.png)

เขียนโค้ด JavaScript ใน `main.js`:

```js
const collapsibles = document.querySelectorAll(".collapsible");

collapsibles.forEach((item) =>
  item.addEventListener("click", function () {
    this.classList.toggle("collapsible--expanded");
  })
);
```

![code main.js querySelectorAll collapsible forEach addEventListener](26-Collapsibles/026-code-main-js-queryselectorall-collapsible.png)

> 🔍 **อธิบายโค้ดทีละบรรทัด:**
> - `document.querySelectorAll(".collapsible")` — ดึง element ทั้งหมดที่มี class `collapsible` มาเป็น NodeList
> - `.forEach((item) => ...)` — วนลูปในแต่ละ collapsible element
> - `item.addEventListener("click", function () {...})` — ผูก event listener สำหรับ click event บน element นั้น (ใช้ `function` ธรรมดา ไม่ใช่ arrow function เพื่อให้ `this` อ้างอิงถึง element ที่ถูกคลิก)
> - `this.classList.toggle("collapsible--expanded")` — สลับ (toggle) class `collapsible--expanded` บน element ที่ถูกคลิก ถ้ามี class นี้อยู่แล้วจะลบออก ถ้ายังไม่มีจะเพิ่มเข้าไป

กลับไปที่ `index.html` เพิ่ม `<script src="js/main.js"></script>` ก่อนปิด `</body>` เพื่อให้ browser โหลดและรัน JavaScript

![html script src js main.js added](26-Collapsibles/027-html-script-src-js-main-js-added.png)

ทดสอบคลิกที่ header ในเบราว์เซอร์: เนื้อหาขยาย/ย่อได้ และไอคอนหมุนตามสถานะ (แม้ยังไม่มี animation แบบนุ่มนวล — สลับแบบทันที)

![Browser: คลิกแล้ว collapsible ขยาย](26-Collapsibles/028-browser-click-toggle-collapsible-expanded.png)

---

## 8. เพิ่ม Animation ให้ไอคอนหมุนแบบนุ่มนวล

กลับไปที่ CSS เพิ่ม `transition: transform 0.3s;` ให้กับ `.collapsible__chevron` เพื่อให้การหมุนไอคอนเปลี่ยนแปลงอย่างนุ่มนวลแทนที่จะกระตุกทันที

![collapsible__chevron transition transform 0.3s](26-Collapsibles/029-css-collapsible-chevron-transition-transform.png)

```css
.collapsible__chevron {
  transform: rotate(-90deg);
  transition: transform 0.3s;
}
```

ทดสอบผลลัพธ์: ไอคอนหมุนแบบนุ่มนวลเมื่อคลิก

![Browser: ไอคอนหมุนแบบนุ่มนวล](26-Collapsibles/030-browser-chevron-rotates-smoothly.png)

---

## 9. แก้ปัญหา: ทำไมเนื้อหาถึง Animate ไม่ได้ตรงๆ

Mosh อธิบายปัญหาสำคัญ: การ transition ระหว่าง `display: none` กับ `display: block` **ไม่สามารถ animate ได้** เพราะ `display` เป็น property แบบ "มี-หรือไม่มี" (discrete) ไม่มีค่ากลางระหว่างทางให้ interpolate จึงต้องเปลี่ยนวิธีคิดใหม่ทั้งหมด โดยใช้ `max-height` แทน `display`

เขียน CSS ใหม่สำหรับ `.collapsible__content`:

```css
.collapsible__content {
  max-height: 0;
  overflow: hidden;
}
```

![collapsible__content max-height 0 overflow hidden](26-Collapsibles/031-css-collapsible-content-max-height-0-overflow-hidden.png)

> ⚠️ **หลักการสำคัญ:** `max-height: 0` ทำให้เนื้อหาถูกบีบให้ดูเหมือนไม่มีความสูง ในขณะที่ `overflow: hidden` ทำให้เนื้อหาที่ "ล้น" ออกมาเกินขอบเขต `max-height` ถูกซ่อนไว้ไม่ให้แสดงผล การใช้สอง property คู่กันนี้จำลองพฤติกรรมเหมือน `display: none` แต่เป็นค่าตัวเลขที่ **animate ได้**

จากนั้นแก้ selector `.collapsible--expanded .collapsible__content` จาก `display: block;` เป็น `max-height: 100vh;` (ใช้หน่วย viewport height เพื่อให้ครอบคลุมความสูงเนื้อหาได้เกือบทุกกรณี)

![collapsible--expanded content max-height 100vh](26-Collapsibles/032-css-collapsible-expanded-content-max-height-100vh.png)

```css
.collapsible--expanded .collapsible__content {
  max-height: 100vh;
}
```

เพิ่ม `transition: max-height 0.3s;` ให้กับ `.collapsible__content` เพื่อให้การเปลี่ยนค่า max-height เป็นแบบนุ่มนวล

![collapsible__content transition max-height 0.3s](26-Collapsibles/033-css-collapsible-content-transition-max-height.png)

```css
.collapsible__content {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.3s;
}
```

---

## 10. เพิ่ม Fade-in ด้วย Opacity

เพื่อให้ animation ดูนุ่มนวลยิ่งขึ้น Mosh เพิ่ม `opacity: 0;` ให้กับ `.collapsible__content` เพื่อให้เนื้อหาจางหายไปตอนย่อ

![collapsible__content opacity 0](26-Collapsibles/034-css-collapsible-content-opacity-0-added.png)

และเพิ่ม `opacity: 1;` ใน `.collapsible--expanded .collapsible__content` เพื่อให้เนื้อหาค่อยๆ ปรากฏขึ้นตอนขยาย

![collapsible--expanded content opacity 1](26-Collapsibles/035-css-collapsible-expanded-content-opacity-1.png)

CSS สุดท้ายของ collapsible content:

```css
.collapsible__content {
  max-height: 0;
  overflow: hidden;
  opacity: 0;
  transition: max-height 0.3s;
}

.collapsible--expanded .collapsible__content {
  max-height: 100vh;
  opacity: 1;
}
```

ผลลัพธ์ในเบราว์เซอร์: การขยาย/ย่อเนื้อหาเป็นไปอย่างนุ่มนวลทั้งความสูงและความโปร่งใส พร้อมไอคอนที่หมุนไปพร้อมกัน

![Browser: animation ขยาย/ย่อแบบนุ่มนวล](26-Collapsibles/036-browser-smooth-expand-collapse-animation.png)

---

## 11. ทดสอบด้วย Collapsible หลายตัว

Mosh คัดลอกโครงสร้าง HTML ของ collapsible ตัวแรกไปวางเป็นตัวที่สอง (ทั้งสองมี class `collapsible` เหมือนกัน)

![HTML: เพิ่ม collapsible item ที่สอง](26-Collapsibles/037-html-second-collapsible-item-added.png)

ทดสอบในเบราว์เซอร์: คลิกแต่ละ collapsible แยกกันได้อย่างอิสระ (independent toggle) เพราะ JavaScript ใช้ `forEach` ผูก event listener ให้กับ **ทุกตัว** ที่ match selector `.collapsible` แยกกัน

![Browser: collapsible สองตัวทำงานอิสระต่อกัน](26-Collapsibles/038-browser-two-independent-collapsible-items.png)

ปิดท้ายคลิปด้วยการเปิดดู mockup ใน Photoshop เพื่อดูตัวอย่างว่า Collapsible component นี้จะถูกนำไปใช้จริงในคอลัมน์ footer "PRODUCTS" ของเว็บไซต์ในบทเรียนถัดไป

![Photoshop mockup: PRODUCTS footer column](26-Collapsibles/039-photoshop-mockup-products-footer-column-preview.png)

---

## สรุปภาพรวมของคลิปนี้

| หัวข้อ | รายละเอียดสำคัญ |
|---|---|
| โครงสร้าง HTML | `.collapsible` > (`.collapsible__header` [`.collapsible__heading`, svg `.icon.icon--white.collapsible__chevron`], `.collapsible__content`) |
| Flexbox | `.collapsible__header { display: flex; justify-content: space-between; }` จัดหัวข้อกับไอคอนคนละฝั่ง |
| ไอคอนเริ่มต้น | `transform: rotate(-90deg)` ให้ลูกศรชี้ขวา (ปิด) |
| Modifier สถานะเปิด | `.collapsible--expanded` — ใช้ descendant selector ปรับทั้งไอคอนและเนื้อหา |
| JavaScript | `querySelectorAll` + `forEach` + `addEventListener("click")` + `classList.toggle()` |
| ปัญหา `display` | `display: none/block` เปลี่ยนแบบทันที ไม่มีค่ากลาง จึง animate ไม่ได้ |
| ทางแก้ | ใช้ `max-height` + `overflow: hidden` + `opacity` แทน `display` เพื่อให้ transition ทำงานได้ |
| ผลลัพธ์สุดท้าย | ขยาย/ย่อแบบนุ่มนวล พร้อมไอคอนหมุนและเนื้อหา fade-in/out |

### แนวคิดสำคัญที่ได้จากคลิปนี้

1. **`display: none`/`block` ไม่สามารถ animate ได้** เพราะเป็นค่าที่ไม่มีสถานะกลาง (all-or-nothing) — ต้องใช้ property ที่มีค่าตัวเลขต่อเนื่อง เช่น `max-height`, `opacity`, หรือ `transform` แทน เพื่อให้ browser คำนวณค่ากลางระหว่าง transition ได้
2. **`max-height` + `overflow: hidden` คือเทคนิคคลาสสิกสำหรับ animate การขยาย/ย่อเนื้อหา** ที่ความสูงจริงไม่แน่นอน (เพราะ CSS ไม่รองรับการ animate ไปยัง `height: auto` โดยตรง)
3. **BEM modifier (`--expanded`) ทำงานร่วมกับ JavaScript ได้อย่างสะอาด** — CSS กำหนดล่วงหน้าว่าแต่ละสถานะหน้าตาเป็นอย่างไร ส่วน JS มีหน้าที่แค่สลับ class เท่านั้น ทำให้แยกความรับผิดชอบ (separation of concerns) ระหว่าง style กับ logic ได้ชัดเจน
4. **`classList.toggle()`** เป็นวิธีที่กระชับที่สุดในการสลับสถานะเปิด-ปิดของ class บน element โดยไม่ต้องเช็คเงื่อนไขเองว่าตอนนี้มี class อยู่หรือไม่
5. **`function` ธรรมดา (ไม่ใช่ arrow function) ใน event listener สำคัญ** เพราะ `this` ใน `function` แบบปกติจะอ้างอิงถึง element ที่ถูกคลิก ในขณะที่ arrow function จะไม่ bind `this` ใหม่ ทำให้โค้ดพัง
6. **`querySelectorAll` + `forEach`** ทำให้ event listener ถูกผูกกับทุก element ที่ตรงกับ selector โดยอัตโนมัติ รองรับ component หลายตัวในหน้าเดียวกันโดยไม่ต้องเขียนโค้ดซ้ำ

---

*สรุปจากคลิปที่ 26 (Collapsibles) คอร์ส "Building a Website with HTML and CSS" โดย Mosh Hamedani (codewithmosh.com)*
