# HTML-CSS-3: 11 - Links

**ไฟล์ต้นทาง:** 11-Links.mp4

▶️ [ดูวิดีโอ](../../HTML-CSS-3/11-Links.mp4)

---

## ภาพรวมคลิปนี้

![สไลด์ชื่อคลิป Links](11-Links/01-title-slide-links.png)

คลิปนี้ Mosh พาเราสร้างสไตล์ให้กับลิงก์ "Learn More" ที่เป็นส่วนหนึ่งของ Feature Block ในหน้าเว็บ Moshify โดยอ้างอิงจากดีไซน์ใน Photoshop ที่มีลิงก์สีแดง (accent color) พร้อมลูกศรชี้ไปทางขวา คลิปนี้มีเนื้อหาสำคัญหลายเรื่องคือ (1) การสร้าง element `<a>` ด้วย Emmet และการจัด class ให้กับมัน (2) **การเปลี่ยนเทคนิคการตั้งค่า base font-size ของ `html` จาก `16px` (ที่ตั้งไว้ในคลิป 10) มาเป็น `62.5%`** ซึ่งเป็นเทคนิคยอดนิยมที่ทำให้คำนวณค่า `rem` ง่ายขึ้นมาก (3) การใช้ pseudo-element `::after` เพื่อแปะ arrow เข้ากับข้อความลิงก์โดยไม่ต้องเขียนลงใน HTML โดยตรง (4) การทำ hover animation ให้ลูกศรค่อยๆ เลื่อนออกไปทางขวาด้วย `transition` (5) การเพิ่ม responsive style ให้ลิงก์ในจอใหญ่ผ่าน media query เดิมที่มีอยู่แล้ว และ (6) การเริ่มต้นระบบ **Component Library** ด้วยการสร้างโฟลเดอร์ `components` และไฟล์ `links.html` เพื่อดูตัวอย่าง component แต่ละชิ้นแยกจากหน้าเว็บจริง

---

## 1. ภาพรวมดีไซน์ลิงก์ใน Photoshop

![ภาพรวมดีไซน์ลิงก์ใน Photoshop](11-Links/02-photoshop-mobile-learn-more-link.png)

Mosh เปิดไฟล์ `mobile.psd` ใน Adobe Photoshop เพื่อดูตัวอย่างดีไซน์ของลิงก์ "LEARN MORE →" ที่อยู่ใต้ Heading และย่อหน้าข้อความในแต่ละ Feature Block โดยสังเกตจาก panel ด้านบนของ Photoshop จะเห็นว่า:

> - ฟอนต์ที่ใช้คือ **Inter**
> - น้ำหนักตัวอักษร (Font Style) คือ **Bold**
> - ขนาดตัวอักษรคือ **20px**
> - สีของข้อความเป็นสีแดง/ส้ม ซึ่งตรงกับ `--color-accent: #ff3400` ที่ตั้งไว้ในคลิป 9 (Color Palette)
> - ข้อความเป็นตัวพิมพ์ใหญ่ทั้งหมด (UPPERCASE) แม้ว่าในเลเยอร์อาจจะพิมพ์เป็นตัวพิมพ์เล็ก แต่ browser จะแปลงให้เป็นตัวใหญ่ด้วย CSS
> - มีลูกศรชี้ไปทางขวา `→` อยู่ท้ายข้อความ โดยเว้นระยะห่างจากข้อความเล็กน้อย

---

## 2. สร้าง Element `<a>` ด้วย Emmet

![VS Code แสดง index.html ที่ยังเป็นโค้ดทดสอบเก่า](11-Links/03-vscode-index-html-old-heading-test.png)

ก่อนเริ่ม Mosh เปิดไฟล์ `index.html` ซึ่งยังมีโค้ดทดสอบเก่าจากคลิปก่อนหน้า (คลิป 10 - Typography) ค้างอยู่คือ:

```html
<h1>Heading 1</h1>
<h2>Heading 2</h2>
<h3>Heading 3</h3>
<p>Lorem ipsum dolor sit amet...</p>
```

จากนั้นลบโค้ดทดสอบทิ้ง แล้วพิมพ์ตัวย่อ Emmet เพียงตัวอักษร `a` ลงไป

![VS Code แสดง Emmet abbreviation suggestions สำหรับ a](11-Links/04-vscode-emmet-a-abbreviation-suggestions.png)

> เมื่อพิมพ์ `a` ตัวเดียว VS Code (พร้อม Emmet extension) จะเสนอตัวเลือกอัตโนมัติ 3 แบบคือ **`a`** (ธรรมดา), **`a:blank`** (ลิงก์ที่เปิดแท็บใหม่พร้อม `target="_blank"` และ `rel="noopener noreferrer"`), และ **`a:link`** (ลิงก์ที่มี `href="http://"` เต็มรูปแบบ) การกด Tab หรือ Enter บนตัวเลือกที่ต้องการจะขยายเป็นแท็ก HTML แบบเต็มให้ทันที นี่คือพลังของ Emmet ที่ช่วยลดเวลาในการพิมพ์โค้ด HTML ซ้ำๆ

หลังจากเลือก Emmet abbreviation ธรรมดา (`a`) ผลลัพธ์ที่ได้คือ:

![VS Code แสดง a tag ที่สร้างเสร็จแล้ว](11-Links/05-vscode-a-href-class-tag-created.png)

```html
<a href="#" class=""></a>
```

> Emmet จะสร้าง attribute `href="#"` และ `class=""` ให้อัตโนมัติเป็นค่าตั้งต้น (placeholder) ซึ่ง cursor จะกระโดดไปอยู่ในช่อง `class=""` ให้ทันทีเพื่อให้พิมพ์ชื่อ class ต่อได้เลย โดยในคลิปนี้ Mosh จะตั้งชื่อ class ว่า `link-arrow` (เพราะลิงก์นี้มีลูกศรกำกับอยู่ด้วย)

---

## 3. ย้อนดู Typography CSS เดิมจากคลิปก่อนหน้า

ก่อนเขียน CSS ใหม่ Mosh สลับไปที่ไฟล์ `styles.css` เพื่อทบทวนโค้ด Typography ที่เขียนไว้แล้วในคลิปที่แล้ว

![VS Code styles.css แสดง media query ส่วนท้ายของคลิปก่อน](11-Links/06-vscode-styles-css-media-query-h3-tail.png)

![VS Code styles.css แสดง h1 และ h2 blocks](11-Links/07-vscode-styles-css-h1-h2-blocks.png)

> ตอนนี้เรายังเห็นค่าที่ตั้งไว้จากคลิปก่อนคือ `h1 { font-size: 7rem; }` และ `h2 { font-size: 4rem; }` และเมื่อเลื่อนลงมาดูจุดเริ่มต้นของไฟล์อีกครั้ง จะเห็นว่ายังมี `html { font-size: 16px; }` อยู่ (ค่าที่ตั้งไว้ในคลิป 10)

![VS Code แสดง html font-size ยังเป็น 16px](11-Links/08-vscode-html-font-size-16px-still.png)

---

## 4. จุดเปลี่ยนสำคัญ: เทคนิค "62.5%" สำหรับ base font-size

นี่คือหัวใจสำคัญของคลิปนี้ Mosh อธิบายปัญหาของการใช้ `html { font-size: 16px; }` เป็นฐานคำนวณ `rem` คือ **1rem จะเท่ากับ 16px ซึ่งเป็นเลขที่คำนวณในใจได้ยาก** (เช่น ถ้าอยากได้ 24px ต้องคิดว่า 24/16 = 1.5rem) จึงมีเทคนิคยอดนิยมในวงการที่เรียกว่า **"62.5% Trick"** โดยเปลี่ยนมาตั้งค่า:

```css
html {
  /* 62.5% of 16px = 10px */
  font-size: 62.5%;
}
```

![VS Code แสดง h1 h2 blocks ระหว่างเลื่อนดู](11-Links/09-vscode-h1-h2-blocks-scroll.png)

![VS Code แสดง html font-size เปลี่ยนเป็น 62.5 เปอร์เซ็นต์](11-Links/10-vscode-html-font-size-62-5-percent.png)

![VS Code แสดง comment อธิบาย 62.5 ของ 16px เท่ากับ 10px](11-Links/11-vscode-comment-625-of-16px-10px.png)

![VS Code แสดง cursor อยู่เหนือ html block ที่แก้ไขแล้ว](11-Links/12-vscode-cursor-above-html-block.png)

> **หลักการทำงาน:** ค่า browser default ของ `font-size` คือ `16px` เสมอ (ถ้าผู้ใช้ไม่ได้ปรับตั้งค่าเอง) ดังนั้นเมื่อเราตั้ง `html { font-size: 62.5%; }` มันจะหมายถึง **62.5% ของ 16px** ซึ่งคำนวณได้เท่ากับ **10px พอดี** ผลคือ **1rem จะเท่ากับ 10px แทนที่จะเป็น 16px** ทำให้การแปลงค่า pixel เป็น rem ง่ายขึ้นมาก เพียงแค่หารด้วย 10 เช่น 20px = 2rem, 30px = 3rem, 24px = 2.4rem เป็นต้น
>
> **ข้อสำคัญ:** ค่า `h1 { font-size: 7rem; }`, `h2 { font-size: 4rem; }`, `h3 { font-size: 3rem; }` ที่ตั้งไว้ในคลิปที่แล้วนั้น **ไม่ต้องแก้ไขใหม่** เพราะระบบ `rem` จะคำนวณสัดส่วนใหม่โดยอัตโนมัติตาม base font-size ที่เปลี่ยนไป (เพียงแต่ขนาดจริงบนหน้าจอจะเปลี่ยนจาก 7×16=112px ไปเป็น 7×10=70px) — Mosh เลือกไม่ปรับค่าตัวเลขของ Heading ใหม่ในคลิปนี้ เพียงเปลี่ยนแค่ระบบฐานคำนวณเท่านั้น

![VS Code แสดง comment 62.5 percent อีกมุม](11-Links/13-vscode-typography-comment-html-62-5.png)

![VS Code แสดง h2 h3 font-size blocks](11-Links/14-vscode-h2-h3-font-size-blocks.png)

---

## 5. สร้าง CSS Rule แรกให้ `.link-arrow`

Mosh เริ่มสร้าง selector `.link-arrow` ใหม่ในไฟล์ `styles.css` และพิมพ์ `color: var(--col` เพื่อเรียกใช้ CSS Custom Property ที่ตั้งไว้ในคลิป 9

![VS Code แสดง suggestions ของ CSS Custom Properties สีต่างๆ](11-Links/15-vscode-link-arrow-var-color-suggestions.png)

> IntelliSense ของ VS Code จะเสนอ Custom Properties ทั้งหมดที่ประกาศไว้ใน `:root` มาให้เลือกพร้อมแสดง swatch สีและ hex code กำกับ ได้แก่ `--color-accent (#ff3400)`, `--color-body (#918ca4)`, `--color-headings (#1b0760)`, `--color-primary (#2584ff)`, และ `--color-secondary (#00d9ff)` — Mosh เลือก `--color-accent` เพราะตรงกับสีแดง/ส้มของลิงก์ในดีไซน์

```css
.link-arrow {
  color: var(--color-accent);
}
```

![VS Code แสดง link-arrow color var accent เสร็จสมบูรณ์](11-Links/16-vscode-link-arrow-color-var-accent.png)

จากนั้นเพิ่ม `text-transform` เพื่อทำให้ข้อความเป็นตัวพิมพ์ใหญ่ทั้งหมด

![VS Code แสดง suggestions ของ text-transform](11-Links/17-vscode-text-transform-suggestions.png)

> ตัวเลือกของ `text-transform` ที่ IntelliSense เสนอมามีทั้ง `capitalize` (ทำให้ตัวอักษรแรกของแต่ละคำเป็นตัวใหญ่), `lowercase` (แปลงเป็นตัวเล็กทั้งหมด), `none` (ไม่แปลง), `uppercase` (แปลงเป็นตัวใหญ่ทั้งหมด), `inherit`, `initial` เป็นต้น Mosh เลือก `uppercase` เพื่อให้ตรงกับดีไซน์

Mosh เปิด Photoshop มาเทียบดีไซน์อีกครั้งเพื่อยืนยัน

![Photoshop แสดง Super Easy to Utse และ Learn More](11-Links/18-photoshop-super-easy-to-utse-learn-more.png)

```css
.link-arrow {
  color: var(--color-accent);
  text-transform: uppercase;
}
```

![VS Code แสดง link-arrow uppercase เสร็จสมบูรณ์](11-Links/19-vscode-link-arrow-uppercase-complete.png)

---

## 6. Global Reset: `a { text-decoration: none; }`

ก่อนไปต่อ Mosh สังเกตว่าลิงก์ทุกตัวใน browser มักจะมีเส้นขีดเส้นใต้ (underline) โดยอัตโนมัติจาก **User Agent Stylesheet** ของ browser ซึ่งไม่ตรงกับดีไซน์ จึงเพิ่ม global selector `a` (ไม่ใช้ class) เพื่อ reset ค่านี้ให้กับลิงก์ทุกตัวในเว็บไซต์

![VS Code แสดง selector a ว่างเปล่า](11-Links/20-vscode-a-selector-text-decoration.png)

![VS Code แสดง suggestions ของ text-decoration](11-Links/21-vscode-text-decoration-none-suggestions.png)

> ตัวเลือกของ `text-decoration` ที่เสนอมามี `dashed`, `dotted`, `double`, `line-through`, `none` เป็นต้น Mosh เลือก `none` เพื่อลบเส้นใต้ทิ้งทั้งหมด

```css
a {
  text-decoration: none;
}
```

![VS Code แสดง a text-decoration none เสร็จสมบูรณ์](11-Links/22-vscode-a-text-decoration-none-complete.png)

![VS Code แสดงภาพรวม a และ link-arrow ทั้งสอง selector](11-Links/23-vscode-full-view-a-and-link-arrow.png)

> **ข้อสังเกตสำคัญ:** นี่คือหลักการ CSS ที่ดีคือการแยก style เป็น 2 ระดับ — ระดับ **Global/Element selector** (`a`) สำหรับ style ที่ต้องใช้กับลิงก์ทุกตัวในเว็บไซต์ (เช่น การลบ underline) และระดับ **Component/Class selector** (`.link-arrow`) สำหรับ style เฉพาะของลิงก์แบบมีลูกศรเท่านั้น ทำให้โค้ด CSS ยืดหยุ่นและนำกลับมาใช้ซ้ำได้ง่าย

---

## 7. เพิ่มขนาดตัวอักษรและความหนา

```css
.link-arrow {
  color: var(--color-accent);
  text-transform: uppercase;
  font-size: 2rem;
  font-weight: bold;
}
```

![VS Code แสดง link-arrow font-size 2rem](11-Links/24-vscode-link-arrow-font-size-2rem.png)

![VS Code แสดง link-arrow font-weight bold](11-Links/25-vscode-link-arrow-font-weight-bold.png)

> เนื่องจากตอนนี้ 1rem = 10px (จากเทคนิค 62.5%) ค่า `2rem` จึงเท่ากับ **20px** พอดี ซึ่งตรงกับที่เห็นใน Photoshop panel ด้านบน (Font size: 20px) — นี่คือตัวอย่างที่แสดงให้เห็นชัดเจนว่าเทคนิค 62.5% ทำให้การแปลงค่าง่ายขึ้นมากเพียงใด

ผลลัพธ์ที่ได้ใน browser:

![Browser แสดง Learn More สไตล์แดง ตัวหนา พิมพ์ใหญ่](11-Links/26-browser-learn-more-styled-red-uppercase.png)

> ตอนนี้ข้อความ "LEARN MORE" ปรากฏเป็นสีแดง ตัวหนา ตัวพิมพ์ใหญ่ทั้งหมด และไม่มีเส้นใต้แล้ว ตรงตามดีไซน์เกือบสมบูรณ์ เหลือเพียงลูกศรที่ยังไม่ได้เพิ่ม

---

## 8. เพิ่มลูกศรด้วย Pseudo-element `::after`

Mosh สร้าง selector ใหม่ชื่อ `.link-arrow::after` เพื่อแปะเนื้อหาเพิ่มเติมต่อท้าย element โดยไม่ต้องแก้ไข HTML

![VS Code แสดง link-arrow after pseudo element ที่สร้างใหม่](11-Links/27-vscode-link-arrow-after-pseudo-created.png)

```css
.link-arrow::after {
  content: "-->";
}
```

ผลลัพธ์ที่ได้ใน browser:

![Browser แสดง Learn More พร้อมลูกศร](11-Links/28-browser-learn-more-with-arrow.png)

> **`::after`** คือ Pseudo-element ใน CSS ที่ใช้แทรกเนื้อหาเสมือน (virtual content) เข้าไปหลังเนื้อหาจริงของ element โดยต้องใช้คู่กับ property `content` เสมอ (ถ้าไม่มี `content` pseudo-element จะไม่แสดงผลอะไรเลย) ในที่นี้ Mosh ใช้ `content: "-->"` ซึ่งประกอบด้วยเครื่องหมายลบสองตัวตามด้วยเครื่องหมายมากกว่า และเมื่อ browser render ออกมาจะแสดงผลเป็นสัญลักษณ์ลูกศรชี้ไปทางขวา นี่คือเทคนิคที่นิยมใช้กันในวงการเว็บเพื่อสร้างไอคอนลูกศรแบบง่ายๆ โดยไม่ต้องใช้รูปภาพหรือ icon font เพิ่มเติม

จากนั้นเพิ่ม `margin-left` เพื่อให้มีระยะห่างระหว่างข้อความกับลูกศร

![VS Code แสดง link-arrow after content margin กำลังพิมพ์](11-Links/29-vscode-link-arrow-after-content-margin.png)

![VS Code แสดง link-arrow after content margin 5px](11-Links/30-vscode-link-arrow-after-content-margin-5px.png)

```css
.link-arrow::after {
  content: "-->";
  margin-left: 5px;
}
```

![Browser แสดง Learn More กับลูกศรที่มีระยะห่าง](11-Links/31-browser-learn-more-arrow-spaced.png)

---

## 9. ทำ Hover Effect ให้ลูกศรเคลื่อนที่

Mosh เอาเมาส์ไปวางเหนือลิงก์เพื่อดูว่า cursor เปลี่ยนเป็นรูปมือ (pointer) หรือไม่ (ซึ่งเป็นพฤติกรรม default ของ `<a>` tag อยู่แล้ว)

![Browser แสดง hover cursor pointer เหนือลิงก์](11-Links/32-browser-hover-cursor-pointer.png)

จากนั้นเริ่มสร้าง selector `.link-arrow:hover::after` เพื่อกำหนดสไตล์ของลูกศรเฉพาะตอนที่ผู้ใช้เอาเมาส์ไปชี้ (hover) เหนือลิงก์

![VS Code แสดง suggestions ของ hover margin](11-Links/33-vscode-link-arrow-hover-margin-suggestions.png)

```css
.link-arrow:hover::after {
  margin-left: 10px;
}
```

![VS Code แสดง link-arrow hover margin-left 5px](11-Links/34-vscode-link-arrow-hover-margin-left-5px.png)

> ครั้งแรกที่พิมพ์ Mosh อาจพิมพ์ค่าเป็น `5px` ก่อนแล้วปรับเป็น `10px` เพื่อให้เห็นความแตกต่างชัดเจนขึ้นเมื่อ hover (ระยะห่างเพิ่มขึ้นเป็นสองเท่าจากค่าปกติ 5px)

ทดสอบผลลัพธ์ใน browser โดยยังไม่ได้ hover:

![Browser แสดงก่อน hover ยังไม่มีการเปลี่ยนแปลง](11-Links/35-browser-hover-no-change-yet.png)

และหลัง hover ลูกศรขยับออกไปทางขวาเล็กน้อย:

![Browser แสดง hover ลูกศรขยับออกไปทางขวา](11-Links/36-browser-hover-arrow-moved-slightly.png)

> ที่จุดนี้การเปลี่ยนแปลงยังเป็นแบบ **กระตุกทันที (instant)** ไม่มีความนุ่มนวล เพราะ CSS ยังไม่มี `transition` กำกับไว้

---

## 10. เพิ่ม Transition ให้การเคลื่อนไหวลื่นไหล

Mosh กลับไปที่ `.link-arrow::after` (ไม่ใช่ `:hover`) เพื่อเพิ่ม property `transition`

![VS Code แสดง link-arrow after เสร็จสมบูรณ์ก่อนเพิ่ม transition](11-Links/37-vscode-link-arrow-after-complete.png)

![VS Code แสดง new selector link-arrow suggestions](11-Links/38-vscode-new-selector-link-arrow-suggestions.png)

![VS Code แสดง link-arrow hover selector กำลังพิมพ์](11-Links/39-vscode-link-arrow-hover-selector-typing.png)

![VS Code แสดง link-arrow hover after suggestions](11-Links/40-vscode-link-arrow-hover-after-suggestions.png)

![VS Code แสดง link-arrow hover after block ว่างเปล่า](11-Links/41-vscode-link-arrow-hover-after-empty-block.png)

ทดสอบ browser ก่อน hover อีกครั้ง:

![Browser แสดงก่อน hover state](11-Links/42-browser-before-hover-state.png)

จากนั้นเติม `margin-left: 10px;` ใน `:hover::after`

![VS Code แสดง link-arrow hover after margin-left](11-Links/43-vscode-link-arrow-hover-after-margin-left.png)

แล้วกลับไปเพิ่ม `transition` ใน `.link-arrow::after` (selector หลัก ไม่ใช่ hover):

![VS Code แสดง transition property suggestions](11-Links/44-vscode-transition-property-suggestions.png)

![VS Code แสดง link-arrow after transition กำลังพิมพ์](11-Links/45-vscode-link-arrow-after-transition-typing.png)

![VS Code แสดง transition cubic-bezier suggestions](11-Links/46-vscode-transition-cubic-bezier-suggestions.png)

```css
.link-arrow::after {
  content: "-->";
  margin-left: 5px;
  transition: margin 0.15s;
}

.link-arrow:hover::after {
  margin-left: 10px;
}
```

![VS Code แสดง transition margin 0.15s เสร็จสมบูรณ์](11-Links/47-vscode-transition-margin-0-15s-complete.png)

![VS Code แสดงโค้ด link-arrow hover animation เต็มรูปแบบ](11-Links/48-vscode-full-link-arrow-hover-animation-code.png)

> **`transition: margin 0.15s;`** หมายความว่า เมื่อค่า `margin` (ในที่นี้คือ `margin-left`) ของ element เปลี่ยนแปลง (เช่นจาก 5px เป็น 10px ตอน hover) ให้ browser **ค่อยๆ เปลี่ยนแปลงค่าอย่างนุ่มนวลภายในเวลา 0.15 วินาที** แทนที่จะเปลี่ยนทันทีแบบกระตุก โดย syntax เต็มของ transition คือ `transition: <property> <duration> <timing-function> <delay>` แต่ในที่นี้ Mosh ระบุแค่ property (`margin`) กับ duration (`0.15s`) เท่านั้น ส่วน timing-function จะใช้ค่า default คือ `ease`
>
> **ทำไมต้องใส่ transition ที่ selector หลัก (`::after`) ไม่ใช่ที่ `:hover::after`?** เพราะ transition ต้องถูกกำหนดไว้ที่ **สถานะปกติ (base state)** ของ element เพื่อให้ browser รู้ว่าเมื่อไหร่ก็ตามที่ค่า margin เปลี่ยนแปลง (ไม่ว่าจะเข้าสู่ hover หรือออกจาก hover) ให้ animate ทั้งสองทิศทาง ถ้าใส่ transition ไว้ใน `:hover` เพียงอย่างเดียว การเคลื่อนไหวตอนเข้า hover จะนุ่มนวล แต่ตอนเมาส์ออกจาก hover จะกระตุกทันที

ทดสอบผลลัพธ์:

![Browser แสดง hover ก่อนทดสอบ animation](11-Links/49-browser-hover-arrow-not-yet-tested.png)

![Photoshop เปรียบเทียบดีไซน์อีกครั้ง](11-Links/50-photoshop-super-easy-to-utse-learn-more-2.png)

![VS Code แสดงโค้ดสุดท้ายของ link-arrow hover animation](11-Links/51-vscode-full-link-arrow-hover-code-final.png)

---

## 11. เพิ่ม Responsive Style สำหรับจอใหญ่

Mosh เลื่อนลงไปยัง media query ที่สร้างไว้แล้วในคลิปก่อนหน้า (คลิป 10 - Typography) ซึ่งมี breakpoint ที่ `min-width: 1024px`

![VS Code เลื่อนดู h3 p และ media query](11-Links/52-vscode-scroll-h3-p-media-query.png)

![VS Code แสดง media query 1024px block](11-Links/53-vscode-media-query-1024px-block.png)

![VS Code แสดง cursor อยู่บรรทัดว่างใน media query](11-Links/54-vscode-media-query-cursor-blank-line.png)

Mosh พิมพ์ `.link-arrow` เข้าไปในบรรทัดว่างภายใน media query นี้

![VS Code แสดง suggestions ของ link-arrow selector ใน media query](11-Links/55-vscode-media-query-link-arrow-suggestions.png)

![VS Code แสดง link-arrow font-size 1 percent suggestions](11-Links/56-vscode-link-arrow-font-size-1-percent-suggestions.png)

```css
@media screen and (min-width: 1024px) {
  .link-arrow {
    font-size: 1.5rem;
  }

  body {
    font-size: 1.8rem;
  }

  h1 {
    font-size: 8rem;
  }
  /* ...ต่อด้วย h2, h3 ตามที่ตั้งไว้ในคลิปก่อน */
}
```

![VS Code แสดง link-arrow font-size 1.5rem ใน media query](11-Links/57-vscode-link-arrow-font-size-1-5rem-media.png)

> **1.5rem** ในระบบใหม่ (base 62.5%) เท่ากับ **15px** ซึ่งหมายความว่าเมื่อหน้าจอกว้างขึ้น (เข้า breakpoint 1024px) ตัวอักษรของลิงก์ "LEARN MORE" จะมีขนาดเล็กลงเล็กน้อยจาก 20px (2rem) เหลือ 15px (1.5rem) เพื่อความสมดุลกับองค์ประกอบอื่นๆ ในหน้าจอขนาดใหญ่ — Mosh เลือก **ใช้ media query เดิมที่มีอยู่แล้วซ้ำ** (ไม่สร้าง media query ใหม่) เพราะเป็นการดีไซน์ที่ดีกว่าในแง่การจัดการโค้ด (การรวม breakpoint เดียวกันไว้ในที่เดียว)

![VS Code แสดง link-arrow after โค้ดเต็มอีกครั้ง](11-Links/58-vscode-link-arrow-after-full-code-recap.png)

![VS Code แสดง media query body h1 recap](11-Links/59-vscode-media-query-body-h1-recap.png)

![VS Code แสดง link-arrow hover after recap](11-Links/60-vscode-link-arrow-hover-after-recap.png)

### 11.1 ข้อควรระวัง: การสร้าง Media Query ซ้ำโดยไม่ตั้งใจ

ที่จุดหนึ่งในคลิป Mosh เผลอพิมพ์ `@media screen` ใหม่ทั้งที่ media query เดิมก็มีอยู่แล้ว

![VS Code แสดง media screen new block กำลังพิมพ์](11-Links/61-vscode-media-screen-new-block-typing.png)

![VS Code แสดง media query 1024px ถูกสร้างซ้ำ](11-Links/62-vscode-media-query-1024px-created-again.png)

![VS Code แสดง media query font-size suggestions](11-Links/63-vscode-media-query-font-size-suggestions.png)

หลังจากนั้นได้ทำการรวม (merge) โค้ดกลับเข้าไปใน media query เดียวกันตามที่ตั้งใจไว้ในตอนแรก

![VS Code แสดง media query ที่ merge link-arrow เข้าด้วยกันแล้ว](11-Links/64-vscode-media-query-merged-link-arrow.png)

> นี่คือตัวอย่างที่ดีของ "ข้อผิดพลาดที่เกิดขึ้นจริงระหว่างสอน" ซึ่งแสดงให้เห็นว่าการมี media query ซ้ำกันในไฟล์เดียว (มี `@media screen and (min-width: 1024px) { }` สองอันที่มีเงื่อนไขเดียวกัน) แม้จะทำงานได้ (เพราะ CSS จะอ่านและ apply กฎทั้งสองอันตามลำดับ) แต่ **ไม่ใช่แนวทางปฏิบัติที่ดี (best practice)** เพราะทำให้โค้ดกระจัดกระจายและดูแลรักษายาก ควรรวม breakpoint เดียวกันไว้ใน media query เดียวเสมอ

ทดสอบผลลัพธ์โดยย่อขนาดหน้าต่าง browser ให้แคบลง (ต่ำกว่า 1024px):

![Browser หน้าต่างแคบ แสดง Learn More](11-Links/65-browser-narrow-window-learn-more.png)

![Browser หน้าต่างแคบ แสดง Learn More อีกมุม](11-Links/66-browser-narrow-window-learn-more-2.png)

![VS Code แสดง media query 1024px ถูก highlight](11-Links/67-vscode-media-query-1024px-highlighted.png)

---

## 12. เริ่มต้นระบบ Component Library

ช่วงท้ายคลิป Mosh แนะนำแนวคิดใหม่คือการสร้างโฟลเดอร์แยกต่างหากชื่อ **`components`** เพื่อเก็บไฟล์ HTML ตัวอย่างของแต่ละ component โดยไม่ต้องปนกับหน้าเว็บจริง (`index.html`) ซึ่งจะช่วยให้ทดสอบและดู component แต่ละชิ้นแบบแยกโดดๆ ได้ง่ายในคลิปต่อๆ ไป

![VS Code แสดงเมนู New Folder ใน Explorer](11-Links/68-vscode-explorer-new-folder-menu.png)

![VS Code แสดงโฟลเดอร์ components ที่สร้างเสร็จแล้ว](11-Links/69-vscode-explorer-components-folder-created.png)

![VS Code แสดงเมนู New File](11-Links/70-vscode-explorer-new-file-menu.png)

![VS Code แสดงโฟลเดอร์ components มองเห็นในแถบ Explorer](11-Links/71-vscode-explorer-components-folder-visible.png)

![VS Code แสดงเมนู context ของ New File](11-Links/72-vscode-explorer-new-file-context-menu.png)

จากนั้นตั้งชื่อไฟล์ใหม่ว่า `links.html` ภายในโฟลเดอร์ `components`

![VS Code แสดงการตั้งชื่อไฟล์ links.html](11-Links/73-vscode-explorer-links-html-naming.png)

![VS Code แสดงไฟล์ links.html ที่ว่างเปล่าถูกสร้างแล้ว](11-Links/74-vscode-links-html-empty-file-created.png)

Mosh กลับไปที่ `index.html` เพื่อคัดลอกโค้ด `<a>` ของลิงก์มาวางในไฟล์ใหม่

![VS Code แสดง index.html บรรทัด a link-arrow ถูก highlight](11-Links/75-vscode-index-html-a-link-arrow-highlighted.png)

![VS Code แสดง links.html ว่างเปล่า cursor พร้อมพิมพ์](11-Links/76-vscode-links-html-empty-cursor.png)

```html
<a href="#" class="link-arrow">Learn More</a>
```

![VS Code แสดง links.html หลังวางโค้ด a tag](11-Links/77-vscode-links-html-a-tag-pasted.png)

> การสร้าง Component Library แบบนี้เป็นแนวคิดที่ใกล้เคียงกับหลักการ **Component-Based Design** ในการพัฒนาเว็บสมัยใหม่ (คล้ายกับแนวคิดของ Storybook ใน React/Vue ที่ front end developer ใช้กันจริงในปัจจุบัน) โดยแยกแต่ละชิ้นส่วน UI ออกมาเป็นไฟล์ย่อยเพื่อทดสอบและพัฒนาสไตล์แยกจากกัน ก่อนนำไปประกอบรวมเป็นหน้าเว็บที่สมบูรณ์

---

## 13. Commit การเปลี่ยนแปลงด้วย Git

ปิดท้ายคลิปด้วยการเปิด Source Control panel ใน VS Code เพื่อ commit งานที่ทำเสร็จแล้ว

![VS Code แสดง Source Control panel รายการไฟล์ที่เปลี่ยนแปลง](11-Links/78-vscode-source-control-changes-panel.png)

> รายการไฟล์ที่เปลี่ยนแปลง (Changes) มีทั้งหมด 3 ไฟล์คือ `index.html` (M = Modified), `links.html` (U = Untracked/ไฟล์ใหม่), และ `styles.css` (M = Modified)

![VS Code แสดงข้อความ commit "Build the arrow link component."](11-Links/79-vscode-git-commit-message-build-arrow-link.png)

```
Build the arrow link component.
```

> Mosh พิมพ์ข้อความ commit สั้นๆ ที่อธิบายว่าทำอะไรไปในรอบนี้ ตามหลักการเขียน commit message ที่ดีคือ **สั้น กระชับ และสื่อความหมายชัดเจน** (imperative mood — "Build..." ไม่ใช่ "Built..." หรือ "Building...")

---

## สรุปภาพรวมของคลิปนี้

| หัวข้อ | รายละเอียด |
|---|---|
| Element ที่สร้าง | `<a href="#" class="link-arrow">Learn More</a>` |
| Base font-size ใหม่ | `html { font-size: 62.5%; }` (1rem = 10px) |
| CSS Class หลัก | `.link-arrow` (สี, ตัวพิมพ์ใหญ่, ขนาด, น้ำหนัก) |
| Global Reset | `a { text-decoration: none; }` |
| ลูกศร | `.link-arrow::after { content: "-->"; margin-left: 5px; }` |
| Hover Effect | `.link-arrow:hover::after { margin-left: 10px; }` |
| Animation | `transition: margin 0.15s;` บน `::after` |
| Responsive | `.link-arrow { font-size: 1.5rem; }` ใน media query 1024px เดิม |
| ไฟล์ใหม่ | `components/links.html` (Component Library เริ่มต้น) |
| Git Commit | "Build the arrow link component." |

### แนวคิดสำคัญที่ได้จากคลิปนี้

1. **เทคนิค 62.5%** เป็นวิธีที่ช่วยให้การคำนวณค่า `rem` ง่ายขึ้นมาก โดยเปลี่ยนจาก 1rem=16px เป็น 1rem=10px และไม่จำเป็นต้องแก้ไขค่า rem ของ Heading ที่ตั้งไว้ก่อนหน้าเพราะระบบจะคำนวณสัดส่วนใหม่ให้อัตโนมัติ
2. **Pseudo-element `::after`** ใช้สำหรับแทรกเนื้อหาเสมือนต่อท้าย element โดยต้องมี property `content` เสมอ เหมาะสำหรับการเพิ่มไอคอนหรือสัญลักษณ์ตกแต่งโดยไม่ต้องแก้ไข HTML
3. **`transition`** ต้องกำหนดไว้ที่ selector สถานะปกติ (base state) ไม่ใช่ที่ `:hover` เพื่อให้การเคลื่อนไหวนุ่มนวลทั้งตอนเข้าและออกจาก hover
4. **การแยก Global selector กับ Class selector** (เช่น `a` กับ `.link-arrow`) ช่วยให้จัดการ CSS ได้อย่างเป็นระบบ — ใช้ element selector สำหรับ reset ค่าพื้นฐานที่ต้องการทุกที่ และใช้ class selector สำหรับ style เฉพาะจุด
5. **การรวม media query breakpoint เดียวกันไว้ในที่เดียว** เป็นแนวทางปฏิบัติที่ดีกว่าการสร้าง media query ซ้ำหลายจุดในไฟล์เดียวกัน
6. **Component Library** (โฟลเดอร์ `components/`) เป็นจุดเริ่มต้นของแนวคิด Component-Based Development ที่ช่วยให้พัฒนาและทดสอบแต่ละชิ้นส่วน UI แยกจากกันได้ง่ายขึ้น

---

*สรุปจากคลิปที่ 11 ของคอร์ส "Building a Web Site" (Moshify Project) สอนโดย Mosh Hamedani, codewithmosh.com*
