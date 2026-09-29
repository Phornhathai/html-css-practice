# HTML-CSS-3: 10 - Typography (10:44)

**ไฟล์ต้นทาง:** `10-Typography.mp4`

▶️ **[เปิดวิดีโอต้นฉบับ](../../HTML-CSS-3/10-Typography.mp4)**

---

## ภาพรวมคลิปนี้

คลิปยาวที่สุดคลิปหนึ่งของคอร์สนี้ Mosh พาสร้างระบบ **Typography** ให้กับโปรเจกต์ Moshify ตั้งแต่การเลือกและฝังฟอนต์จาก **Google Fonts**, การตั้งค่า `font-family` พื้นฐาน, การใช้ **CSS Variables** (`var(--color-...)`) ร่วมกับสีที่ประกาศไว้ในคลิปที่ 9, การกำหนดขนาดตัวอักษรของ h1-h3 และ `line-height` ด้วยหน่วย **rem**, การใช้ Chrome DevTools ตรวจสอบ box model และ user agent stylesheet, ไปจนถึงการทำ **Responsive Typography** ด้วย `@media` query ที่ปรับขนาดตัวอักษรให้ใหญ่ขึ้นบนหน้าจอเดสก์ท็อป (`min-width: 1024px`) ปิดท้ายด้วยการ commit งานผ่าน Git

---

## 1. เปิดคลิปด้วยสไลด์ชื่อเรื่อง

สไลด์ชื่อคลิป **"Typography"** พร้อมรูปโปรไฟล์ผู้สอน:

![title slide](10-Typography/01-title-slide.png)

ตามด้วยสไลด์หัวข้อย่อย **"Typography"** พื้นหลังสีฟ้าอ่อน:

![typography title slide](10-Typography/02-typography-title-slide.png)

---

## 2. ตรวจสอบฟอนต์และขนาดตัวอักษรจากไฟล์ดีไซน์

เปิด Adobe Photoshop ตรวจสอบหัวข้อ hero **"Cloud Hosting for Pros"** ด้วย Type Tool แสดงค่าฟอนต์ `Inter`, style `Bold`, ขนาด `70 px`:

![photoshop hero heading inspect](10-Typography/03-photoshop-hero-heading-inspect.png)

ตรวจสอบข้อความ testimonial/บรรยายในดีไซน์เพื่อดูฟอนต์และขนาดของข้อความเนื้อหาทั่วไป:

![photoshop testimonial text inspect](10-Typography/04-photoshop-testimonial-text-inspect.png)

> **แนวคิดสำคัญ:** ก่อนเขียน CSS ทุกครั้ง Mosh จะย้อนไปตรวจสอบค่าจริงจากไฟล์ Photoshop เสมอ (ฟอนต์, น้ำหนักตัวอักษร, ขนาด) โดยใช้ Type Tool คลิกที่ข้อความแล้วดูค่าที่แถบเครื่องมือด้านบนแสดง

---

## 3. เลือกและฝังฟอนต์จาก Google Fonts

เปิด Chrome ไปที่หน้าฟอนต์ **Inter บน Google Fonts** (fonts.google.com):

![chrome google fonts inter page](10-Typography/05-chrome-google-fonts-inter-page.png)

เปิดแผง **"Select styles"** เพื่อเลือกน้ำหนักตัวอักษร (font weight) ที่ต้องการดาวน์โหลด:

![google fonts select styles panel](10-Typography/06-google-fonts-select-styles-panel.png)

เลือกน้ำหนัก **Regular 400** เป็นตัวแรก:

![google fonts regular 400 selected](10-Typography/07-google-fonts-regular-400-selected.png)

แผง **"Use on the web"** แสดงโค้ด `<link>` ที่ต้องนำไปวางใน `<head>` ของ HTML:

![google fonts embed link tags](10-Typography/08-google-fonts-embed-link-tags.png)

เลือกเพิ่มน้ำหนัก **Bold 700** เป็นตัวที่สอง (สำหรับหัวข้อที่ต้องเป็นตัวหนา):

![google fonts regular bold selected](10-Typography/09-google-fonts-regular-bold-selected.png)

โค้ด `<link>` อัปเดตให้รวม URL parameter `wght@400;700` ครอบคลุมทั้งสองน้ำหนัก:

![google fonts link tags two weights](10-Typography/10-google-fonts-link-tags-two-weights.png)

> **แนวคิดสำคัญ:** Google Fonts อนุญาตให้เลือกดาวน์โหลดเฉพาะน้ำหนักตัวอักษร (font weight) ที่โปรเจกต์ใช้จริงเท่านั้น เพื่อลดขนาดไฟล์ฟอนต์ที่ต้องโหลด แทนที่จะดาวน์โหลดทุกน้ำหนักที่มีอยู่ทั้งหมด

---

## 4. วางโค้ด `<link>` ฟอนต์ลงใน `index.html`

สลับไปที่ VS Code เปิดไฟล์ `index.html` ดูส่วน `<head>` ที่ยังไม่มีลิงก์ฟอนต์:

![vscode index html head](10-Typography/11-vscode-index-html-head.png)

วางโค้ด `<link>` ที่คัดลอกมาจาก Google Fonts ลงในส่วน `<head>`:

![vscode paste link tags](10-Typography/12-vscode-paste-link-tags.png)

โค้ด `<link>` ทั้งสองบรรทัด (`preconnect` และ `stylesheet`) ปรากฏอยู่ใน `<head>` เรียบร้อย:

![vscode link tags in head](10-Typography/13-vscode-link-tags-in-head.png)

ย้อนกลับไปที่ Google Fonts เพื่อคัดลอกโค้ดอีกครั้งให้แน่ใจว่าถูกต้องครบถ้วน:

![google fonts copy link code](10-Typography/14-google-fonts-copy-link-code.png)

ผลลัพธ์สุดท้ายของ `<head>` ที่มีลิงก์ฟอนต์ Inter ครบถ้วน:

![vscode head with fonts linked](10-Typography/15-vscode-head-with-fonts-linked.png)

---

## 5. ตั้งค่า `font-family` พื้นฐานใน `body`

เปิดไฟล์ `css/styles.css` ซึ่งยังว่างเปล่าในส่วนนี้:

![vscode styles css empty](10-Typography/16-vscode-styles-css-empty.png)

เริ่มพิมพ์ selector **`body`**:

![vscode body selector start](10-Typography/17-vscode-body-selector-start.png)

พิมพ์ property **`font-family`**:

![vscode font family property](10-Typography/18-vscode-font-family-property.png)

พิมพ์ค่าแรก **`Inter`**:

![vscode font family inter typed](10-Typography/19-vscode-font-family-inter-typed.png)

เพิ่ม fallback fonts ต่อจาก Inter:

![vscode font family fallback stack](10-Typography/20-vscode-font-family-fallback-stack.png)

พิมพ์ต่อจนได้ค่าเต็ม **`font-family: Inter, Arial, Helvetica, sans-serif;`**:

![vscode body selector color start](10-Typography/21-vscode-body-selector-color-start.png)

VS Code IntelliSense แนะนำชื่อ font-family เพิ่มเติมระหว่างพิมพ์:

![vscode font family intellisense](10-Typography/22-vscode-font-family-intellisense.png)

ค่าที่พิมพ์เสร็จสมบูรณ์:

![vscode font family value complete](10-Typography/23-vscode-font-family-value-complete.png)

ตรวจทานรายการ fallback fonts ทั้งหมดอีกครั้ง:

![vscode font family fallback list](10-Typography/24-vscode-font-family-fallback-list.png)

> **แนวคิดสำคัญ (Font Fallback Stack):** การระบุฟอนต์สำรอง (`Arial, Helvetica, sans-serif`) ต่อจากฟอนต์หลัก (`Inter`) เป็นแนวปฏิบัติที่ดี เพราะหากฟอนต์ Inter โหลดไม่สำเร็จ (เช่น อินเทอร์เน็ตขัดข้อง) เบราว์เซอร์จะใช้ฟอนต์ตัวถัดไปในรายการแทน โดยไล่จากซ้ายไปขวาจนกว่าจะเจอฟอนต์ที่มีอยู่ในเครื่อง

---

## 6. เพิ่มหัวข้อทดสอบ (Heading 1, 2, 3) และย่อหน้าด้วย Emmet

เปิดไฟล์ `index.html` เพิ่ม `<h1>`, `<h2>`, `<h3>` เพื่อทดสอบการแสดงผลตัวอักษร:

![vscode index html headings added](10-Typography/25-vscode-index-html-headings-added.png)

พิมพ์ตัวย่อ Emmet **`p>lorem`** เพื่อสร้างย่อหน้าตัวอย่างพร้อมข้อความ Lorem Ipsum อัตโนมัติ:

![vscode emmet p lorem abbreviation](10-Typography/26-vscode-emmet-p-lorem-abbreviation.png)

โค้ด HTML ที่ได้ครบถ้วน (`h1`, `h2`, `h3`, `p` พร้อมข้อความ Lorem Ipsum):

![vscode h1 h2 h3 p lorem html](10-Typography/27-vscode-h1-h2-h3-p-lorem-html.png)

ผลลัพธ์ในเบราว์เซอร์: หัวข้อทั้งสามระดับแสดงเป็นตัวหนาสีดำ (ค่าเริ่มต้นของเบราว์เซอร์) พร้อมย่อหน้า Lorem Ipsum:

![browser heading 1 2 3 lorem black](10-Typography/28-browser-heading-1-2-3-lorem-black.png)

กลับไปที่ `styles.css` ยืนยัน `font-family` ของ `body` ถูกตั้งค่าแล้ว:

![vscode body font family set](10-Typography/29-vscode-body-font-family-set.png)

> **Emmet Abbreviation:** `p>lorem` เป็นตัวย่อพิเศษของ Emmet ที่สร้างแท็ก `<p>` พร้อมข้อความ Lorem Ipsum แบบสุ่มโดยอัตโนมัติ ช่วยประหยัดเวลาเวลาต้องการเนื้อหาตัวอย่างสำหรับทดสอบสไตล์ CSS

---

## 7. กำหนดสีข้อความด้วย CSS Variables (`var()`)

ผลลัพธ์ก่อนกำหนดสี — ย่อหน้ายังเป็นสีดำเริ่มต้น:

![browser lorem paragraph purple body color](10-Typography/30-browser-lorem-paragraph-purple-body-color.png)

กลับมาที่ `body` selector เริ่มพิมพ์ property **`color:`**:

![vscode body color var property](10-Typography/31-vscode-body-color-var-property.png)

พิมพ์ฟังก์ชัน **`var(--co`** ระบบ IntelliSense แสดงรายการตัวแปรสีทั้งหมดที่ประกาศไว้ในคลิปที่ 9 พร้อมสี่เหลี่ยมตัวอย่างสี (swatch) และค่า hex กำกับ:

![vscode color var autocomplete swatches](10-Typography/32-vscode-color-var-autocomplete-swatches.png)

เลือก **`--color-body`** ได้ค่าสมบูรณ์เป็น **`color: var(--color-body);`**:

![vscode color body var complete](10-Typography/33-vscode-color-body-var-complete.png)

เริ่มสร้าง selector กลุ่ม **`h1, h2, h3`** เพื่อกำหนดสีให้หัวข้อทั้งสามระดับพร้อมกัน:

![vscode h1 h2 h3 selector typing](10-Typography/34-vscode-h1-h2-h3-selector-typing.png)

พิมพ์ **`var(--co`** อีกครั้งภายใน selector นี้ ระบบแสดงรายการตัวแปรสีให้เลือก:

![vscode color headings autocomplete](10-Typography/35-vscode-color-headings-autocomplete.png)

> **การใช้ `var()` แทนค่า hex ตรงๆ:** ฟังก์ชัน `var(--ชื่อตัวแปร)` ใช้ดึงค่าที่ประกาศไว้ใน `:root` มาใช้ในทุก selector ที่ต้องการ ทำให้ถ้าต้องการเปลี่ยนโทนสีของทั้งเว็บไซต์ภายหลัง สามารถแก้แค่ค่าใน `:root` จุดเดียว ไม่ต้องไล่แก้ทีละ selector

---

## 8. ตรวจสอบขนาดตัวอักษรหัวข้อจากดีไซน์อีกครั้ง

กลับไปที่ Photoshop ตรวจสอบหัวข้อ **"Cloud Hosting for Pros"** ยืนยันขนาด **70px**:

![photoshop cloud hosting heading 70px](10-Typography/36-photoshop-cloud-hosting-heading-70px.png)

ผลลัพธ์ในเบราว์เซอร์หลังกำหนดสี: หัวข้อเป็นสีม่วงเข้ม (`--color-headings`) ย่อหน้าเป็นสีเทาอมม่วง (`--color-body`):

![browser headings purple body gray](10-Typography/37-browser-headings-purple-body-gray.png)

ยืนยันโค้ด `body { color: var(--color-body); }` เสร็จสมบูรณ์:

![vscode body color var body final](10-Typography/38-vscode-body-color-var-body-final.png)

VS Code แสดงเมนู Emmet suggestion เมื่อพิมพ์ `h1, h2, h3`:

![vscode h1 h2 h3 emmet suggestions](10-Typography/39-vscode-h1-h2-h3-emmet-suggestions.png)

แสดงเมนู CSS property suggestion ภายใน selector กลุ่มนี้:

![vscode h1 h2 h3 css property suggestions](10-Typography/40-vscode-h1-h2-h3-css-property-suggestions.png)

โค้ด `h1, h2, h3 { color: var(--color-headings); }` เสร็จสมบูรณ์:

![vscode h1 h2 h3 color headings done](10-Typography/41-vscode-h1-h2-h3-color-headings-done.png)

---

## 9. กำหนดขนาดตัวอักษร (`font-size`) ให้ H1 ด้วยหน่วย `px` แล้วเปลี่ยนเป็น `rem`

กลับไป Photoshop ยืนยันขนาดฟอนต์หัวข้ออีกครั้งที่ **70px**:

![photoshop heading font size 70px](10-Typography/42-photoshop-heading-font-size-70px.png)

กลับมาที่ VS Code เริ่ม selector ใหม่ **`h1`** พิมพ์ `font-size:` ระบบแสดงรายการค่าคำ (keyword) เช่น `large`, `larger`, `medium`, `small` ให้เลือก:

![vscode h1 font size value suggestions](10-Typography/43-vscode-h1-font-size-value-suggestions.png)

พิมพ์ค่าจริงเป็น **`font-size: 70px;`**:

![vscode h1 font size 70px set](10-Typography/44-vscode-h1-font-size-70px-set.png)

ลบค่าออกแล้วเขียนคอมเมนต์อธิบาย พร้อมเปลี่ยนมาใช้หน่วย **`1rem`** แทน:

![vscode h1 font size comment 1rem](10-Typography/45-vscode-h1-font-size-comment-1rem.png)

VS Code แสดงเมนู Emmet ของแท็กหัวข้อทั้งหมด (`h1` ถึง `h6`, `hatch`, ฯลฯ):

![vscode h1 h2 h3 h4 h5 h6 emmet list](10-Typography/46-vscode-h1-h2-h3-h4-h5-h6-emmet-list.png)

พิมพ์ property ที่ขึ้นต้นด้วย `co` แสดงรายการเช่น `color`, `content`, `column-count`:

![vscode css property autocomplete co](10-Typography/47-vscode-css-property-autocomplete-co.png)

> **แนวคิดสำคัญ (px → rem):** Mosh สาธิตให้เห็นว่าสามารถกำหนด `font-size` เป็น `px` ตรงๆ ได้ (เช่น `70px`) แต่แนะนำให้ใช้หน่วย **`rem`** แทน เพราะ `rem` คำนวณสัมพัทธ์กับ `font-size` ของ `<html>` (ค่าเริ่มต้นเบราว์เซอร์คือ 16px) ทำให้ถ้าผู้ใช้ปรับขนาดตัวอักษรของเบราว์เซอร์ (accessibility) องค์ประกอบทั้งหมดที่ใช้ `rem` จะปรับขนาดตามไปด้วย ต่างจาก `px` ที่เป็นค่าคงที่ตายตัว

---

## 10. กำหนด `font-size: 16px` ให้ `<html>` เพื่อเป็นฐานคำนวณ `rem`

โค้ด `body { color: var(--color-headings); }` ในบริบทของ selector กลุ่ม:

![vscode body color headings block](10-Typography/48-vscode-body-color-headings-block.png)

สร้าง selector **`html`** ใหม่ พร้อมคอมเมนต์อธิบาย **"1 x font size of the html element"**:

![vscode html font size 16px comment](10-Typography/49-vscode-html-font-size-16px-comment.png)

โค้ด `body` selector ที่มี `color: var(--color-headings);` อยู่ในบริบทเดิม:

![vscode body block color var](10-Typography/50-vscode-body-block-color-var.png)

เริ่ม selector `html` ว่างเปล่า:

![vscode html selector empty](10-Typography/51-vscode-html-selector-empty.png)

พิมพ์ `font-size: 16p` ระบบ IntelliSense แนะนำหน่วยเช่น `16pc`, `16pt`, `16px`:

![vscode html font size 16px autocomplete](10-Typography/52-vscode-html-font-size-16px-autocomplete.png)

ค่าสุดท้าย **`html { font-size: 16px; }`**:

![vscode html font size 16px final](10-Typography/53-vscode-html-font-size-16px-final.png)

เว้นบรรทัดว่างก่อน `font-size: 16px;` เพื่อจัดระเบียบโค้ด:

![vscode html font size blank line](10-Typography/54-vscode-html-font-size-blank-line.png)

ภาพรวมไฟล์ทั้งหมดจนถึงจุดนี้ (`html`, `body`, `h1, h2, h3`):

![vscode full file body h1 h2 h3](10-Typography/55-vscode-full-file-body-h1-h2-h3.png)

คอมเมนต์และค่า `h1 { font-size: 1rem; }` ที่ตั้งไว้ชั่วคราวเพื่อสาธิต:

![vscode h1 font size 1rem comment](10-Typography/56-vscode-h1-font-size-1rem-comment.png)

> **สูตรคำนวณ:** เมื่อ `html { font-size: 16px; }` แล้ว `1rem` จะเท่ากับ `16px` เสมอ ดังนั้นหากต้องการฟอนต์ขนาด 70px จะคำนวณได้เป็น `70 ÷ 16 = 4.375rem` — แต่ในคลิปนี้ Mosh เลือกใช้ค่าที่ปัดเป็นตัวเลขลงตัวง่ายกว่าสำหรับ scale ทั่วไปของหัวข้อ (h1/h2/h3) แทนที่จะยึดตามพิกเซลของ hero heading โดยเฉพาะ ซึ่งจะมีการปรับแต่งเฉพาะจุดอีกครั้งในคลิปหลังๆ ที่สร้างส่วน hero header จริง

---

## 11. ย้อนดูดีไซน์ในส่วนอื่นเพื่อเตรียมกำหนด H2/H3

กลับไป Photoshop ยืนยันขนาดฟอนต์หัวข้อ hero อีกครั้งที่ 70px (มุมมอง mobile.psd):

![photoshop cloud hosting 70px final](10-Typography/57-photoshop-cloud-hosting-70px-final.png)

เลื่อนดูส่วน **"The best webhosting Starting at per month"** ในดีไซน์ mobile:

![photoshop mobile webhosting search section](10-Typography/58-photoshop-mobile-webhosting-search-section.png)

ตรวจสอบขนาดฟอนต์ของหัวข้อ **"The best webhosting Starting at per month"** ด้วย Type Tool:

![photoshop webhosting heading inspect](10-Typography/59-photoshop-webhosting-heading-inspect.png)

กลับมาที่ VS Code ยืนยันค่า `h1 { font-size: 1rem; }`:

![vscode h1 font size 1rem](10-Typography/60-vscode-h1-font-size-1rem.png)

---

## 12. ทดลองกำหนด `font-size` ของ `body` เป็น `rem` (สาธิต scale ทั้งหน้า)

ภาพรวมไฟล์ CSS ทั้งหมดจนถึงจุดนี้:

![vscode body h1 h2 h3 headings full](10-Typography/61-vscode-body-h1-h2-h3-headings-full.png)

เว้นบรรทัดว่างใน `body` selector เพื่อเพิ่ม property ใหม่:

![vscode body empty line](10-Typography/62-vscode-body-empty-line.png)

กลับไป Photoshop ดูส่วน **"Super Easy to Use"** feature block เพื่อตรวจสอบขนาดฟอนต์ของเนื้อหาทั่วไป:

![photoshop super easy to use section](10-Typography/63-photoshop-super-easy-to-use-section.png)

กลับมาพิมพ์ **`font-size: 2.4rem;`** ให้กับ `body` เพื่อสาธิตว่าการเปลี่ยนขนาดฟอนต์ฐานจะส่งผลกระทบต่อทุกอย่างที่ใช้ `rem` (รวมถึง `<p>` เพราะ paragraph สืบทอด font-size จาก body):

![vscode body font size 2.4rem autocomplete](10-Typography/64-vscode-body-font-size-2-4rem-autocomplete.png)

ผลลัพธ์ในเบราว์เซอร์: ทั้งหัวข้อและย่อหน้าขยายใหญ่ขึ้นตามสัดส่วน เพราะใช้หน่วย `rem` ที่สัมพัทธ์กับ body:

![browser headings 2.4rem body scaled](10-Typography/65-browser-headings-2-4rem-body-scaled.png)

ยืนยันค่า `font-size: 2.4rem;` ในโค้ด:

![vscode body font size 2.4rem set](10-Typography/66-vscode-body-font-size-2-4rem-set.png)

> **ข้อสังเกตสำคัญ:** แม้ `h1, h2, h3` จะกำหนด `font-size` เป็น `rem` โดยอิงกับ `<html>` (ไม่ใช่ `body`) แต่ค่า `2.4rem` ใน `body` ก็ยังทำให้ย่อหน้า (`<p>`) ที่ **ไม่ได้กำหนด font-size ของตัวเอง** ขยายใหญ่ขึ้นตาม เพราะ `<p>` สืบทอด (inherit) font-size มาจาก `body` ที่เป็น parent — นี่คือตัวอย่างการทำงานของ **CSS Inheritance**

---

## 13. กำหนด `line-height` ให้ `body`

พิมพ์ property ใหม่ **`line-height:`** ใน `body` selector ระบบแสดง suggestion เช่น `line-break`, `line-clamp`, `line-height-step`:

![vscode body line height autocomplete](10-Typography/67-vscode-body-line-height-autocomplete.png)

ตั้งค่าเป็น **`line-height: 1.5;`**:

![vscode body line height 1.5 set](10-Typography/68-vscode-body-line-height-1-5-set.png)

ผลลัพธ์ในเบราว์เซอร์: ระยะห่างระหว่างบรรทัดของย่อหน้า Lorem Ipsum กว้างขึ้น อ่านง่ายขึ้น:

![browser headings line height applied](10-Typography/69-browser-headings-line-height-applied.png)

> **`line-height` แบบไม่มีหน่วย (unitless):** การกำหนด `line-height: 1.5` โดยไม่ใส่หน่วยใดๆ หมายถึง "1.5 เท่าของ font-size ปัจจุบันของ element นั้น" ซึ่งเป็นแนวปฏิบัติที่แนะนำ เพราะจะคำนวณสัมพัทธ์กับแต่ละ element เอง ต่างจากการกำหนดเป็นหน่วยตายตัว (เช่น `24px`) ที่จะไม่ปรับตามเมื่อ font-size เปลี่ยน

---

## 14. กำหนด `font-size` และ `margin-bottom` ให้ H3 พร้อมตรวจสอบด้วย DevTools

กลับไป Photoshop สังเกตข้อความหัวข้อ **"Super Easy to Utse"** (สังเกตว่าในไฟล์ดีไซน์มีการพิมพ์ผิดเป็น "Utse" แทน "Use" — เป็น placeholder text จากดีไซเนอร์):

![photoshop super easy to utse typo](10-Typography/70-photoshop-super-easy-to-utse-typo.png)

กลับมาที่ VS Code ตั้งค่า **`h3 { font-size: 3rem; }`**:

![vscode h3 font size 3rem](10-Typography/71-vscode-h3-font-size-3rem.png)

เพิ่ม property **`margin-bottom:`** ระบบแสดงตัวเลือกหน่วยความยาว เช่น `auto`, `0%`, `0ch`, `0cm`:

![vscode h3 margin bottom autocomplete](10-Typography/72-vscode-h3-margin-bottom-autocomplete.png)

เปิด Chrome DevTools ตรวจสอบ element `<h3>Heading 3</h3>` แผง **Computed** แสดง `h3 { font-size: 3rem; margin-bottom: 2rem; } styles.css:35` พร้อมกล่องแสดงขนาด (557×45):

![browser devtools h3 inspect computed](10-Typography/73-browser-devtools-h3-inspect-computed.png)

เลื่อนดู **user agent stylesheet** (สไตล์เริ่มต้นของเบราว์เซอร์) แสดง `h3 { display: block; font-size: 1.17em; margin-block-start: 1em; margin-block-end: 1em; margin-inline-start: 0px; }` ซึ่งถูกขีดฆ่า (strikethrough) เพราะถูก override โดยโค้ดของเรา:

![devtools h3 user agent stylesheet](10-Typography/74-devtools-h3-user-agent-stylesheet.png)

ตรวจสอบ box model diagram ของ element `<p>` แสดง margin/border/padding และขนาด (557×144):

![devtools p element box model](10-Typography/75-devtools-p-element-box-model.png)

เลือก element `<h3>` เพื่อดู box model margin ที่มีลูกศรสีแดงชี้ไปที่ตัวเลข "20" (margin ด้านล่าง):

![devtools p element selected heading3](10-Typography/76-devtools-p-element-selected-heading3.png)

box model ของ `<p>` แสดง margin ด้านบน "24" ถูกไฮไลต์ด้วยลูกศรสีแดง:

![devtools p margin box highlighted](10-Typography/77-devtools-p-margin-box-highlighted.png)

> **การใช้ Chrome DevTools ตรวจสอบ CSS:** แผง Elements > Styles แสดงว่ากฎ CSS ใดกำลังมีผลกับ element ที่เลือก และกฎใดถูก override (ขีดฆ่า) แผง Computed หรือ diagram ด้านล่างแสดง **Box Model** (margin, border, padding, ขนาดเนื้อหา) เป็นภาพกราฟิกซ้อนกันเป็นชั้นๆ ช่วยให้เห็นภาพระยะห่างจริงของแต่ละ element ได้ชัดเจน

---

## 15. แก้ปัญหา Margin ซ้อนกัน (Margin Collapse) ด้วย `p { margin-top: 0; }`

ยืนยันโค้ด **`h3 { font-size: 3rem; margin-bottom: 2rem; }`**:

![vscode h3 font size margin bottom 2rem](10-Typography/78-vscode-h3-font-size-margin-bottom-2rem.png)

เริ่ม selector **`p`** พิมพ์ **`margin-top:`** ระบบแสดงตัวเลือกหน่วยความยาว:

![vscode p margin top autocomplete](10-Typography/79-vscode-p-margin-top-autocomplete.png)

กลับไปตรวจสอบ `<p>` ใน DevTools อีกครั้งเพื่อดูผลกระทบของ margin:

![devtools p element inspect again](10-Typography/80-devtools-p-element-inspect-again.png)

ปรับค่า `h3 { margin-bottom }` เป็น **`1rem`**:

![vscode h3 margin bottom 1rem](10-Typography/81-vscode-h3-margin-bottom-1rem.png)

ตั้งค่า **`p { margin-top: 0; }`** ให้เสร็จสมบูรณ์:

![vscode p margin top 0 final](10-Typography/82-vscode-p-margin-top-0-final.png)

> **แนวคิดสำคัญ (Margin Collapse):** เมื่อ element สองตัวที่มี margin ติดกัน (เช่น `margin-bottom` ของ h3 กับ `margin-top` ของ p) เบราว์เซอร์จะไม่บวกค่า margin ทั้งสองรวมกัน แต่จะใช้ค่าที่ **มากกว่า** เพียงค่าเดียว (margin collapsing) ซึ่งอาจทำให้ควบคุมระยะห่างได้ยาก วิธีแก้ที่ Mosh สาธิตคือกำหนด `margin-top: 0;` ให้กับ `<p>` เพื่อให้ระยะห่างทั้งหมดถูกควบคุมด้วย `margin-bottom` ของ heading เพียงจุดเดียว ทำให้คาดเดาผลลัพธ์ได้ง่ายขึ้น

---

## 16. กำหนด `font-size` และ `margin-bottom` ให้ H1 และ H2

ตั้งค่า **`h2 { font-size: 4rem; }`** แยกจาก h3:

![vscode h2 font size 4rem h3 block](10-Typography/83-vscode-h2-font-size-4rem-h3-block.png)

กลับไป Photoshop ตรวจสอบขนาดฟอนต์ของ **"Super Easy to Utse"** อีกครั้งที่ **30px**:

![photoshop super easy to utse 30px](10-Typography/84-photoshop-super-easy-to-utse-30px.png)

ตั้งค่า `margin-bottom: 1rem;` ให้ทั้ง h2 และ h3:

![vscode h2 h3 margin bottom 1rem blocks](10-Typography/85-vscode-h2-h3-margin-bottom-1rem-blocks.png)

ตรวจสอบ box model ของ `<p>` ใน DevTools แสดง margin "24" ทั้งด้านบนและด้านล่าง:

![devtools p box model margin 24](10-Typography/86-devtools-p-box-model-margin-24.png)

ตั้งค่า **`h1 { font-size: 7rem; }`**:

![vscode h1 font size 7rem](10-Typography/87-vscode-h1-font-size-7rem.png)

ยืนยัน `h2 { font-size: 4rem; margin-bottom: ... }`:

![vscode h2 font size 4rem margin bottom](10-Typography/88-vscode-h2-font-size-4rem-margin-bottom.png)

กลับไป Photoshop ตรวจสอบหัวข้อ "Super Easy to Utse" อีกครั้งเพื่อยืนยันค่า:

![photoshop super easy utse heading inspect](10-Typography/89-photoshop-super-easy-utse-heading-inspect.png)

ยืนยัน `h3 { font-size: 3rem; margin-bottom: 1rem; }` เสร็จสมบูรณ์:

![vscode h3 font size 3rem margin bottom 1rem](10-Typography/90-vscode-h3-font-size-3rem-margin-bottom-1rem.png)

---

## 17. ภาพรวมโค้ดทั้งหมดของ Typography (Mobile-first)

ภาพรวม `h2 { font-size: 4rem; }` ในบริบทไฟล์เต็ม:

![vscode h2 font size 4rem block](10-Typography/91-vscode-h2-font-size-4rem-block.png)

ภาพรวม `h2` และ `h3` พร้อม `margin-bottom: 1rem;` ครบทั้งคู่:

![vscode h2 h3 margin bottom 1rem full](10-Typography/92-vscode-h2-h3-margin-bottom-1rem-full.png)

ภาพรวม `h1 { font-size: 7rem; }` ในบริบทไฟล์เต็ม:

![vscode h1 font size 7rem block](10-Typography/93-vscode-h1-font-size-7rem-block.png)

ภาพรวมทั้งหมด: `h2`, `h3`, `p` ในหน้าจอเดียว:

![vscode h2 h3 p blocks full view](10-Typography/94-vscode-h2-h3-p-blocks-full-view.png)

ภาพรวม `h1, h2, h3 { color: var(--color-headings); }`:

![vscode headings color var block](10-Typography/95-vscode-headings-color-var-block.png)

ภาพรวม `h1 { font-size: 7rem; }` อีกมุมมอง:

![vscode h1 h2 h3 h1 font size 7rem](10-Typography/96-vscode-h1-h2-h3-h1-font-size-7rem.png)

ภาพรวม `h1, h2, h3` selector พร้อม `color: var(--color-headings);`:

![vscode h1 h2 h3 headings margin 1rem](10-Typography/97-vscode-h1-h2-h3-headings-margin-1rem.png)

```css
html {
  font-size: 16px;
}

body {
  font-family: Inter, Arial, Helvetica, sans-serif;
  color: var(--color-body);
  line-height: 1.5;
}

h1,
h2,
h3 {
  color: var(--color-headings);
}

h1 {
  font-size: 7rem;
}

h2 {
  font-size: 4rem;
  margin-bottom: 1rem;
}

h3 {
  font-size: 3rem;
  margin-bottom: 1rem;
}

p {
  margin-top: 0;
}
```

---

## 18. ทำ Responsive Typography ด้วย `@media` Query

กลับไป Photoshop ดูมุมมอง **desktop (`standard.psd`)** ของส่วน hero "Cloud Hosting for Pros" เปรียบเทียบกับ mobile:

![photoshop cloud hosting desktop view](10-Typography/98-photoshop-cloud-hosting-desktop-view.png)

ยืนยัน `p { margin-top: 0; }` ในบริบทไฟล์เต็ม:

![vscode p margin top 0 block](10-Typography/99-vscode-p-margin-top-0-block.png)

เริ่มพิมพ์ **`@media scre`** ระบบ IntelliSense แสดงตัวเลือก:

![vscode media screen typing](10-Typography/100-vscode-media-screen-typing.png)

พิมพ์ต่อเป็น **`@media screen and (min-w`**:

![vscode media min width typing](10-Typography/101-vscode-media-min-width-typing.png)

พิมพ์ครบเป็น **`@media screen and (min-width: 1024px) { body { font-`** ระบบแสดงรายการ property เช่น `font-size`, `font-weight`, `font-family`:

![vscode media body font size property](10-Typography/102-vscode-media-body-font-size-property.png)

โครงสร้าง `@media screen and (min-width: 1024px) { body { ... } }` พร้อมแล้ว:

![vscode media min width 1024px body](10-Typography/103-vscode-media-min-width-1024px-body.png)

ตั้งค่า **`font-size: 1.8rem;`** ให้ `body` ภายใน media query:

![vscode media body font size 1.8rem](10-Typography/104-vscode-media-body-font-size-1-8rem.png)

เริ่มพิมพ์ selector **`h1`** ใหม่ภายใน media query พร้อม `font-` property:

![vscode media h1 font size typing](10-Typography/105-vscode-media-h1-font-size-typing.png)

ตั้งค่า **`h1 { font-size: 8rem; }`** ภายใน media query:

![vscode media h1 font size 8rem](10-Typography/106-vscode-media-h1-font-size-8rem.png)

ยืนยันโค้ด `h1` ภายใน media query เสร็จสมบูรณ์:

![vscode media h1 font size 8rem block](10-Typography/107-vscode-media-h1-font-size-8rem-block.png)

เริ่มพิมพ์ **`h2`** selector ใหม่ภายใน media query:

![vscode media h2 font size typing](10-Typography/108-vscode-media-h2-font-size-typing.png)

ตั้งค่า **`h2 { font-size: 4rem; }`** ภายใน media query:

![vscode media h2 font size 4rem](10-Typography/109-vscode-media-h2-font-size-4rem.png)

เริ่มพิมพ์ **`h3`** selector ใหม่ภายใน media query:

![vscode media h3 font size typing](10-Typography/110-vscode-media-h3-font-size-typing.png)

ตั้งค่า **`h3 { font-size: 2.4rem; }`** ภายใน media query เสร็จสมบูรณ์ ครบทั้ง body, h1, h2, h3:

![vscode media h3 font size 2.4rem](10-Typography/111-vscode-media-h3-font-size-2-4rem.png)

> **แนวคิดสำคัญ (`@media` Query):** `@media screen and (min-width: 1024px) { ... }` หมายถึง "ใช้กฎ CSS ภายในวงเล็บนี้เฉพาะเมื่อหน้าจอมีความกว้างตั้งแต่ 1024px ขึ้นไป" ซึ่งเป็นเทคนิคพื้นฐานของ **Responsive Web Design** — ทำให้สามารถกำหนดขนาดตัวอักษรที่ใหญ่ขึ้นสำหรับหน้าจอเดสก์ท็อป โดยที่ค่าเริ่มต้น (นอก media query) จะยังคงใช้กับหน้าจอมือถือ/แท็บเล็ตที่มีขนาดเล็กกว่า 1024px ตามแนวทาง **Mobile-first Design** ที่กำหนดสไตล์มือถือเป็นค่าเริ่มต้นก่อน แล้วค่อยขยายสำหรับหน้าจอใหญ่ทีหลัง

---

## 19. ทดสอบผลลัพธ์ Responsive ด้วยการปรับขนาดหน้าต่างเบราว์เซอร์

เปิดเบราว์เซอร์แสดงหัวข้อและภาพพื้นหลังภูเขาคู่กัน (มุมมอง split preview มือถือ/เดสก์ท็อป):

![browser mountain image headings mobile](10-Typography/112-browser-mountain-image-headings-mobile.png)

ปรับหน้าต่างเบราว์เซอร์ให้แคบลง (ต่ำกว่า 1024px) หัวข้อแสดงในขนาดมือถือ (เล็กกว่า):

![browser resize narrow window](10-Typography/113-browser-resize-narrow-window.png)

ปรับหน้าต่างเบราว์เซอร์ให้กว้างขึ้น (เกิน 1024px) หัวข้อขยายใหญ่ขึ้นทันทีตามที่ `@media` query กำหนด:

![browser resize wide window larger headings](10-Typography/114-browser-resize-wide-window-larger-headings.png)

โค้ด CSS ทั้งหมดของ media query ที่เสร็จสมบูรณ์ (h1: 8rem, h2: 4rem, h3: 2.4rem):

![vscode media query final h1 h2 h3](10-Typography/115-vscode-media-query-final-h1-h2-h3.png)

---

## 20. Commit งานด้วย Git

เปิดแผง Source Control แสดงไฟล์ที่เปลี่ยนแปลง 2 ไฟล์: **`index.html`** และ **`styles.css`** (สถานะ "M" = Modified):

![vscode source control two files changed](10-Typography/116-vscode-source-control-two-files-changed.png)

หลัง commit สำเร็จ โค้ด media query ยังคงแสดงครบถ้วนใน styles.css พร้อมสถานะ commit เรียบร้อย:

![vscode media query committed final](10-Typography/117-vscode-media-query-committed-final.png)

---

## สรุปภาพรวมของคลิปนี้

| ประเด็น | รายละเอียด |
|---|---|
| **หัวข้อ** | Typography — ระบบตัวอักษรของโปรเจกต์ (ฟอนต์, ขนาด, สี, ระยะห่าง, responsive) |
| **ไฟล์ที่แก้ไข** | `index.html` (ลิงก์ Google Fonts, เพิ่ม h1/h2/h3/p ทดสอบ), `css/styles.css` |
| **ฟอนต์ที่ใช้** | Inter (น้ำหนัก Regular 400 และ Bold 700) จาก Google Fonts |
| **CSS หลักที่เขียน** | `html { font-size: 16px; }`, `body { font-family; color: var(--color-body); line-height: 1.5; }`, `h1,h2,h3 { color: var(--color-headings); }`, `h1{font-size:7rem}`, `h2{font-size:4rem;margin-bottom:1rem}`, `h3{font-size:3rem;margin-bottom:1rem}`, `p{margin-top:0}` |
| **Responsive** | `@media screen and (min-width: 1024px)` ปรับ body เป็น 1.8rem, h1 เป็น 8rem, h2 เป็น 4rem, h3 เป็น 2.4rem |
| **เครื่องมือที่ใช้** | Google Fonts, Adobe Photoshop (Type Tool), VS Code (IntelliSense, Emmet, Source Control), Chrome DevTools (Elements, Computed, Box Model) |

**แนวคิดสำคัญที่ได้จากคลิปนี้:**

1. **การฝังฟอนต์จาก Google Fonts** ทำได้โดยเลือกเฉพาะน้ำหนัก (weight) ที่ใช้จริง แล้ววางโค้ด `<link>` ที่ได้ลงในส่วน `<head>` ของ HTML พร้อมกำหนด `font-family` พร้อม fallback fonts ใน CSS
2. **หน่วย `rem` สัมพัทธ์กับ `font-size` ของ `<html>`** (ปกติ 16px) ทำให้ควบคุมขนาดตัวอักษรทั้งเว็บไซต์ได้จากจุดเดียว และรองรับการปรับขนาดตัวอักษรของผู้ใช้ (accessibility) ต่างจากหน่วย `px` ที่ตายตัว
3. **CSS Inheritance** ทำให้ elements ลูก (เช่น `<p>`) สืบทอดค่า `font-size`/`color` จาก parent (`body`) โดยอัตโนมัติหากไม่ได้กำหนดค่าของตัวเองไว้
4. **Margin Collapse** คือพฤติกรรมที่ margin ของสอง element ที่ติดกันไม่บวกกัน แต่ใช้ค่าที่มากกว่าเพียงค่าเดียว วิธีแก้คือกำหนด `margin-top: 0` ให้ element ถัดไป เพื่อให้ควบคุมระยะห่างด้วย `margin-bottom` ของ element ก่อนหน้าเพียงจุดเดียว
5. **Chrome DevTools (Elements panel)** ใช้ตรวจสอบ CSS ที่มีผลจริงกับ element, กฎที่ถูก override (ขีดฆ่า), user agent stylesheet ของเบราว์เซอร์ และ Box Model diagram ที่แสดง margin/border/padding เป็นภาพกราฟิก
6. **`@media screen and (min-width: ...)`** คือหัวใจของ Responsive Web Design ตามแนวทาง Mobile-first — กำหนดสไตล์มือถือเป็นค่าเริ่มต้น แล้วใช้ media query ขยาย/ปรับสไตล์สำหรับหน้าจอที่ใหญ่ขึ้น เช่น เพิ่มขนาดตัวอักษรเมื่อหน้าจอกว้างตั้งแต่ 1024px

---

*หมายเหตุ: คลิปนี้เป็นส่วนหนึ่งของคอร์ส "Building a Web Site" โดย Mosh Hamedani (codewithmosh.com) — คลิปที่ 10*
