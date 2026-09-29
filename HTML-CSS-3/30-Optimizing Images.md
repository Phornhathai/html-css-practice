# HTML-CSS-3: 30 - Optimizing Images

**ไฟล์ต้นฉบับ:** 30-Optimizing Images.mp4

---

## ภาพรวมคลิปนี้

![ภาพรวมคลิปนี้](30-Optimizing-Images/001-title-slide-optimizing-images.png)

คลิปนี้ Mosh สอนเรื่อง **การปรับให้รูปภาพมีขนาดไฟล์เล็กที่สุดเท่าที่จะทำได้ โดยยังคงความคมชัดที่เหมาะสม** ซึ่งเป็นเรื่องสำคัญมากสำหรับเว็บไซต์ เพราะรูปภาพมักเป็นส่วนที่หนักที่สุดของหน้าเว็บ ทำให้เว็บโหลดช้า โดยเฉพาะบนมือถือหรืออินเทอร์เน็ตความเร็วต่ำ

> 💡 หลักการสำคัญของคลิปนี้คือ **"ส่งรูปที่มีขนาด (dimension) และรูปแบบไฟล์ที่เหมาะสมกับอุปกรณ์ที่แสดงผลจริง ๆ"** ไม่ใช่ส่งรูปต้นฉบับที่ใหญ่เกินความจำเป็นไปให้ทุกคน

---

## 1. ตรวจสอบขนาดไฟล์รูปภาพที่มีอยู่ใน Finder

Mosh เปิดโฟลเดอร์ `images` ของโปรเจกต์ Moshify ใน Finder เพื่อดูขนาดไฟล์ของรูปภาพแต่ละไฟล์

![ตรวจสอบขนาดไฟล์ใน Finder](30-Optimizing-Images/002-finder-images-folder-file-sizes.png)

ขนาดไฟล์ที่พบ:

| ไฟล์ | ขนาด |
|---|---|
| banner.png | 916 KB |
| easy.jpg | 208 KB |
| fast.jpg | 246 KB |
| ipad.png | 457 KB |
| logo.png | 2 KB |
| support.jpg | 273 KB |
| testimonial.jpg | 36 KB |
| wordpress.jpg | 585 KB |

> ⚠️ จะเห็นว่า `banner.png` (รูปที่ใช้ใน Hero section) มีขนาดใหญ่ถึง 916 KB ซึ่งถือว่าหนักมากสำหรับรูปภาพเดียวในหน้าเว็บ

---

## 2. เปิดดูขนาดจริงของรูปภาพใน Photoshop (Image Size)

Mosh เปิดไฟล์ `banner.png` ใน Photoshop แล้วไปที่เมนู **Image > Image Size** เพื่อดูขนาดพิกเซลจริงของรูป

![Photoshop Image Size 7.26MB](30-Optimizing-Images/003-photoshop-image-size-banner-7-26mb.png)

ผลลัพธ์ที่เห็น:
- ขนาดรูปภาพ: **1532px × 1656px**
- ขนาดไฟล์ภายใน (uncompressed): **Image Size: 7.26M**

> 📝 นี่คือรูปที่มีความละเอียดสูงมาก (เหมาะกับการพิมพ์หรือจอ retina ขนาดใหญ่) แต่ในเว็บจริง รูปนี้จะถูกแสดงผลในพื้นที่ที่เล็กกว่านี้มาก จึงเป็นการสิ้นเปลืองแบนด์วิดท์โดยไม่จำเป็น

---

## 3. คำนวณขนาดที่เหมาะสมด้วย Calculator

Mosh สลับไปดู mockup ของ Hero section ใน `standard.psd` แล้วเปิดแอป **Calculator** ของ macOS ขึ้นมาคำนวณ

![Calculator app เปิดขึ้นมา](30-Optimizing-Images/004-calculator-app-opened.png)

![Photoshop standard.psd Hero mockup](30-Optimizing-Images/005-photoshop-standard-hero-mockup.png)

![คำนวณต่อด้วย Calculator](30-Optimizing-Images/006-calculator-continued.png)

![คำนวณขนาด 570px](30-Optimizing-Images/007-calculator-570-width-calc.png)

![ผลลัพธ์การคำนวณ](30-Optimizing-Images/008-calculator-result.png)

> 🔍 Mosh อธิบายว่า ต้องดูว่าพื้นที่จริงที่รูปภาพจะถูกแสดงผลบนหน้าเว็บ (ตาม layout/design) กว้างเท่าไหร่ แล้วนำมาคำนวณเป็นค่าพิกเซลอ้างอิง เพื่อใช้กำหนดขนาดไฟล์รูปที่จะ export ออกมาจริง โดยในกรณีนี้พื้นที่ที่ใช้แสดง banner จะมีความกว้างประมาณ **570px** (สำหรับหน้าจอความละเอียดปกติ)

---

## 4. กลยุทธ์การทำรูปภาพให้ responsive (3 แนวทาง)

Mosh สรุปกลยุทธ์สำหรับการเตรียมรูปภาพให้เหมาะกับทุกอุปกรณ์ไว้เป็นสไลด์ 3 ข้อ

![สไลด์กลยุทธ์ responsive images](30-Optimizing-Images/009-strategy-slide-responsive-images.png)

![รายละเอียดสไลด์กลยุทธ์ 1](30-Optimizing-Images/010-strategy-slide-detail.png)

![รายละเอียดสไลด์กลยุทธ์ 2](30-Optimizing-Images/011-strategy-slide-detail-2.png)

กลยุทธ์ทั้ง 3 ข้อที่ Mosh พูดถึง:

1. **ทำรูปที่มีความกว้างพอดีกับพื้นที่แสดงผลจริง** (เช่น 570px) สำหรับหน้าจอความละเอียดปกติ (1x)
2. **ปล่อยให้เบราว์เซอร์ปรับขนาดเล็กน้อยได้เอง** ไม่จำเป็นต้องสร้างไฟล์สำหรับทุกขนาดหน้าจอ เพราะเบราว์เซอร์ scale รูปลงเล็กน้อยได้โดยไม่เสียคุณภาพมากนัก
3. **สร้างเวอร์ชัน 2x (retina)** สำหรับจอที่มีความหนาแน่นพิกเซลสูง (High-DPI / Retina displays) เพื่อให้ภาพยังคมชัดบนจอเหล่านั้น

> ✅ สรุปคือ เราจะสร้างรูปภาพ 2 ขนาดหลัก คือ **1x (570px)** และ **2x (1140px)** แล้วให้เบราว์เซอร์เลือกใช้เวอร์ชันที่เหมาะสมกับหน้าจอผู้ใช้เองโดยอัตโนมัติ

---

## 5. Resize รูปภาพเป็นเวอร์ชัน 2x (1140px) ด้วย Photoshop

Mosh กลับไปที่ Photoshop เปิด **Image > Image Size** อีกครั้ง คราวนี้ปรับความกว้าง (Width) เป็น **1140px** (= 570 × 2)

![เปิด Image Size dialog เพื่อ resize เป็น 1140](30-Optimizing-Images/012-photoshop-image-size-dialog-1140.png)

![กรอกความกว้าง 1140px](30-Optimizing-Images/013-photoshop-resize-1140-width.png)

![ยืนยันการ resize](30-Optimizing-Images/014-photoshop-resize-confirmed.png)

> 📌 เมื่อกรอกความกว้างแล้วกด Enter ความสูงจะถูกปรับตามสัดส่วนเดิมโดยอัตโนมัติ (เพราะ Photoshop ล็อกอัตราส่วนภาพไว้)

---

## 6. Save As เป็นไฟล์ banner@2x.png ลงโฟลเดอร์ images

จากนั้น Mosh ใช้เมนู **File > Save As** เพื่อบันทึกรูปที่ resize แล้วเป็นไฟล์ใหม่

![Save As dialog](30-Optimizing-Images/015-photoshop-save-as-dialog.png)

![เลือกบันทึกลงโฟลเดอร์ images ของโปรเจกต์](30-Optimizing-Images/016-photoshop-save-as-images-folder.png)

![ตัวเลือก PNG Large File Size](30-Optimizing-Images/017-photoshop-png-large-file-option.png)

![บันทึกไฟล์ banner@2x.png สำเร็จ](30-Optimizing-Images/018-photoshop-saved-2x-banner.png)

> 💡 Mosh ตั้งชื่อไฟล์ว่า `banner@2x.png` ซึ่งเป็นธรรมเนียมการตั้งชื่อที่นิยมใช้กันในวงการเว็บ เพื่อสื่อว่าไฟล์นี้คือเวอร์ชัน 2 เท่าของรูปต้นฉบับ (สำหรับจอ Retina)

---

## 7. Resize อีกครั้งให้เหลือ 570px (เวอร์ชัน 1x) แล้ว Save As

หลังจากได้ไฟล์ 2x แล้ว Mosh กลับไปที่ **Image > Image Size** อีกครั้งเพื่อลดขนาดรูปลงเหลือ **570px** (เวอร์ชัน 1x สำหรับจอทั่วไป)

![กลับไป resize อีกครั้งเป็น 570](30-Optimizing-Images/019-photoshop-resize-again-570.png)

![Image Size dialog กรอก 570](30-Optimizing-Images/020-photoshop-image-size-570-dialog.png)

![ยืนยันการ resize เป็น 570](30-Optimizing-Images/021-photoshop-resize-570-confirmed.png)

![Save As เป็น banner.png (1x)](30-Optimizing-Images/022-photoshop-save-as-1x-banner.png)

ผลลัพธ์: ตอนนี้มีไฟล์ PNG 2 ขนาดคือ `banner.png` (570px, 1x) และ `banner@2x.png` (1140px, 2x)

![Finder แสดงไฟล์ banner และ banner@2x](30-Optimizing-Images/023-finder-banner-1x-2x-png-files.png)

> ⚠️ ข้อควรระวัง: ต้อง resize **จากไฟล์ต้นฉบับความละเอียดสูงเสมอ** ห้าม resize ไฟล์ที่ resize เล็กไปแล้วซ้ำอีกที เพราะจะทำให้ภาพยิ่งเบลอมากขึ้นเรื่อย ๆ (Mosh สลับกลับไปทำจากไฟล์ต้นฉบับใหม่ในแต่ละครั้ง)

---

## 8. แปลงไฟล์ PNG เป็น WebP ด้วย CloudConvert

PNG แม้จะ resize เล็กลงแล้ว ก็ยังไม่ใช่ฟอร์แมตที่บีบอัดได้ดีที่สุด Mosh จึงใช้เว็บไซต์ **CloudConvert.com** ซึ่งเป็นเครื่องมือแปลงไฟล์ออนไลน์ฟรี เพื่อแปลงไฟล์ PNG ทั้งสองขนาดให้เป็นไฟล์ฟอร์แมต **WebP** ซึ่งมีอัตราการบีบอัดที่ดีกว่า PNG มาก โดยยังคงคุณภาพของภาพไว้ใกล้เคียงเดิม

![เว็บไซต์ CloudConvert](30-Optimizing-Images/024-cloudconvert-website-homepage.png)

![เลือกไฟล์ที่จะแปลง](30-Optimizing-Images/025-cloudconvert-select-files.png)

![ตั้งค่ารูปแบบผลลัพธ์เป็น WebP](30-Optimizing-Images/026-cloudconvert-png-to-webp-format.png)

![กดปุ่ม Convert](30-Optimizing-Images/027-cloudconvert-convert-button.png)

![กำลังแปลงไฟล์](30-Optimizing-Images/028-cloudconvert-conversion-progress.png)

![ดาวน์โหลดไฟล์ WebP ที่แปลงเสร็จแล้ว](30-Optimizing-Images/029-cloudconvert-download-webp.png)

![ไฟล์ WebP ในโฟลเดอร์ Downloads](30-Optimizing-Images/030-downloads-folder-webp-files.png)

> 🔧 หลังจากขั้นตอนนี้ Mosh จะมีไฟล์รูปภาพทั้งหมด 4 ไฟล์: `banner.png`, `banner@2x.png`, `banner.webp`, `banner@2x.webp`

---

## 9. ย้ายไฟล์รูปภาพทั้งหมดเข้าโปรเจกต์

Mosh คัดลอกไฟล์ทั้ง 4 ไฟล์ (PNG 2 ไฟล์ + WebP 2 ไฟล์) เข้าไปในโฟลเดอร์ `images` ของโปรเจกต์ผ่าน VS Code

![Explorer โฟลเดอร์ images ใน VS Code](30-Optimizing-Images/031-vscode-images-folder-explorer.png)

![คัดลอกไฟล์รูปภาพทั้ง 4 เข้าโปรเจกต์](30-Optimizing-Images/032-vscode-copy-4-image-files-into-project.png)

---

## 10. เริ่มแก้ไข HTML: จาก `<img>` ธรรมดา เป็น `<picture>`

โค้ดเดิมใน `index.html` ใช้แท็ก `<img>` ธรรมดาชี้ไปที่ `images/banner.png` เพียงไฟล์เดียว

![โค้ด img เดิมก่อนแก้ไข](30-Optimizing-Images/033-index-html-img-banner-png-before.png)

```html
<img class="hero__image" src="images/banner.png" alt="">
```

Mosh พิมพ์ตัวย่อ Emmet คำว่า `picture` แล้วกด Enter เพื่อสร้างแท็ก `<picture>` ครอบ `<img>` เดิมไว้

![พิมพ์ picture ด้วย Emmet abbreviation](30-Optimizing-Images/034-emmet-picture-abbreviation.png)

ผลลัพธ์ที่ได้:

```html
<picture>
  <img class="hero__image" src="images/banner.png">
</picture>
```

> 💡 แท็ก `<picture>` เป็น HTML5 element ที่ออกแบบมาเฉพาะสำหรับการทำ responsive images โดยสามารถใส่แท็ก `<source>` หลายอันไว้ข้างในเพื่อกำหนดเงื่อนไขต่าง ๆ ให้เบราว์เซอร์เลือกไฟล์ที่เหมาะสมเอง และแท็ก `<img>` จะทำหน้าที่เป็น **fallback** (ตัวสำรอง) เผื่อเบราว์เซอร์เก่าที่ไม่รองรับ `<picture>`

---

## 11. เพิ่มแท็ก `<source>` และกำหนด `type="image/webp"`

Mosh พิมพ์ `source` เพื่อสร้างแท็ก `<source>` ไว้ข้างในก่อน `<img>`

![เพิ่ม source tag เข้าไปใน picture](30-Optimizing-Images/035-source-tag-added-inside-picture.png)

จากนั้นเพิ่ม attribute `type` และพิมพ์ `image/webp` โดยใช้ autocomplete ของ VS Code

![กำหนด type เป็น image/webp](30-Optimizing-Images/036-source-type-image-webp.png)

```html
<picture>
  <source type="image/webp">
  <img class="hero__image" src="images/banner.png">
</picture>
```

> 📝 attribute `type="image/webp"` บอกเบราว์เซอร์ว่าไฟล์ที่จะใช้ในแท็กนี้เป็นไฟล์ฟอร์แมต WebP หากเบราว์เซอร์นั้นรองรับไฟล์ประเภทนี้ ก็จะเลือกใช้ไฟล์จาก `<source>` นี้แทนที่จะไปใช้ `<img>`

---

## 12. เพิ่ม `srcset` พร้อมกำหนด 1x และ 2x สำหรับ WebP

Mosh เพิ่ม attribute `srcset` เข้าไปในแท็ก `<source>` โดยใช้ autocomplete เลือก `srcset`

![เลือก srcset จาก autocomplete](30-Optimizing-Images/037-source-srcset-banner-webp-1x.png)

พิมพ์ path ของไฟล์ 1x และ 2x ต่อกัน คั่นด้วยเครื่องหมายจุลภาค

![กำลังพิมพ์ srcset สำหรับ 2x](30-Optimizing-Images/038-source-srcset-2x-webp-in-progress.png)

หลังจัด format ให้สวยงาม (Prettier) โค้ดจะมีลักษณะดังนี้:

![โค้ด srcset จัด format เรียบร้อย](30-Optimizing-Images/039-source-srcset-1x-2x-formatted.png)

```html
<picture>
  <source
    type="image/webp"
    srcset="images/banner.webp 1x, images/banner@2x.webp 2x"
  />
  <img class="hero__image" src="images/banner.png" alt="" />
</picture>
```

> 🔍 ค่า `1x` และ `2x` ที่ต่อท้ายชื่อไฟล์ใน `srcset` เรียกว่า **pixel density descriptor** เป็นตัวบอกเบราว์เซอร์ว่าไฟล์นี้เหมาะกับหน้าจอความหนาแน่นพิกเซลระดับใด เบราว์เซอร์จะเลือกไฟล์ที่เหมาะสมกับหน้าจอของอุปกรณ์นั้น ๆ เองโดยอัตโนมัติ โดยไม่ต้องเขียน media query หรือ JavaScript เพิ่มเติมแต่อย่างใด

---

## 13. เพิ่มแท็ก `<source>` ตัวที่สองสำหรับไฟล์ PNG (fallback)

เนื่องจากเบราว์เซอร์บางตัว (โดยเฉพาะรุ่นเก่า) อาจไม่รองรับไฟล์ WebP ได้ Mosh จึงเพิ่มแท็ก `<source>` ตัวที่สอง กำหนด `type="image/png"` พร้อม `srcset` ของไฟล์ PNG ทั้งสองขนาด

![เพิ่ม source ตัวที่สอง type image/png](30-Optimizing-Images/040-second-source-tag-png-type.png)

![กำลังพิมพ์ srcset ของ PNG](30-Optimizing-Images/041-second-source-srcset-png-in-progress.png)

![srcset PNG 1x และ 2x เสร็จสมบูรณ์](30-Optimizing-Images/042-second-source-srcset-png-1x-2x.png)

สุดท้ายเพิ่ม `alt=""` ให้กับแท็ก `<img>` fallback เพื่อความสมบูรณ์ของโค้ด (เนื่องจากรูปนี้เป็นรูปตกแต่ง ไม่ได้สื่อความหมายที่จำเป็นต้องอ่านออกเสียงให้ผู้ใช้ screen reader ฟัง จึงใส่ `alt` เป็นค่าว่าง)

![img fallback พร้อม alt attribute ฉบับสมบูรณ์](30-Optimizing-Images/043-img-fallback-alt-attribute-final.png)

```html
<picture>
  <source
    type="image/webp"
    srcset="images/banner.webp 1x, images/banner@2x.webp 2x"
  />
  <source
    type="image/png"
    srcset="images/banner.png 1x, images/banner@2x.png 2x"
  />
  <img class="hero__image" src="images/banner.png" alt="" />
</picture>
```

> ✅ ลำดับของแท็ก `<source>` มีความสำคัญ: เบราว์เซอร์จะไล่ตรวจสอบจากบนลงล่าง แล้วเลือกใช้ `<source>` แรกที่มันรองรับ (เบราว์เซอร์ที่รองรับ WebP จะใช้ตัวแรก ส่วนเบราว์เซอร์ที่ไม่รองรับจะข้ามไปใช้ตัวที่สองซึ่งเป็น PNG) และถ้าไม่รองรับ `<picture>` เลย ก็จะใช้ `<img>` เป็นค่าสำรองสุดท้าย

---

## 14. ทดสอบผลลัพธ์บนเบราว์เซอร์ Chrome

Mosh รันโปรเจกต์ผ่าน Live Server และเปิดดูผลลัพธ์ใน Chrome เพื่อตรวจสอบว่าหน้า Hero section ยังแสดงผลถูกต้องเหมือนเดิม

![ผลลัพธ์ Hero section ใน Chrome](30-Optimizing-Images/044-browser-preview-cloud-hosting-hero.png)

จากนั้นเปิด DevTools เพื่อตรวจสอบ Elements panel

![DevTools ตรวจสอบ Elements](30-Optimizing-Images/045-devtools-elements-inspecting-body.png)

> 📌 แม้โค้ดจะซับซ้อนขึ้น แต่หน้าตาที่ผู้ใช้เห็นยังคงเหมือนเดิมทุกประการ ความแตกต่างอยู่ที่เบื้องหลัง คือไฟล์ที่เบราว์เซอร์ดาวน์โหลดจะมีขนาดเล็กลงกว่าเดิมมาก

---

## 15. ตรวจสอบผ่าน Network tab ว่าโหลดไฟล์ WebP จริง

Mosh เปิดแท็บ **Network** ใน DevTools แล้วรีโหลดหน้าเว็บ เพื่อดูว่าเบราว์เซอร์เลือกโหลดไฟล์ไหนจริง ๆ

![Network tab แสดง banner@2x.webp ขนาด 105kB](30-Optimizing-Images/046-network-tab-banner-2x-webp-105kb.png)

ผลลัพธ์ที่เห็น: เบราว์เซอร์เลือกโหลดไฟล์ `banner@2x.webp` ขนาดเพียง **105 KB** (สถานะ 200, ใช้เวลาโหลดเพียง 7 ms)

> 🔍 จากขนาดไฟล์ต้นฉบับ 916 KB (และขนาดจริงในหน่วยความจำ 7.26 MB) เหลือเพียง 105 KB เท่านั้น ถือเป็นการลดขนาดไฟล์ลงกว่า **10 เท่า** โดยที่คุณภาพภาพที่ผู้ใช้เห็นแทบไม่แตกต่างกันเลย เพราะจอของผู้ทดสอบ (MacBook Retina) มีความหนาแน่นพิกเซลสูง จึงเลือกใช้ไฟล์ @2x ของ WebP

---

## 16. ทดสอบข้าม browser ด้วย Firefox และปรับค่า DPR

เพื่อพิสูจน์ว่าเบราว์เซอร์เลือกไฟล์ตามความหนาแน่นพิกเซลของหน้าจอจริง Mosh เปิด **Firefox** ขึ้นมาทดสอบเช่นกัน

![ทดสอบใน Firefox](30-Optimizing-Images/047-firefox-test-cloud-hosting-hero.png)

จากนั้นเปิด **Responsive Design Mode** ใน Firefox DevTools เพื่อจำลองอุปกรณ์ต่าง ๆ

![Responsive Device Toolbar ใน Firefox](30-Optimizing-Images/048-firefox-responsive-device-toolbar.png)

และปรับค่า **DPR (Device Pixel Ratio)** จาก 1 เป็น 2 หรือ 3 เพื่อจำลองหน้าจอความหนาแน่นพิกเซลสูง

![ปรับค่า DPR เป็น 2 ใน Firefox](30-Optimizing-Images/049-firefox-dpr-2-option-selected.png)

> ⚠️ เมื่อปรับ DPR สูงขึ้น เบราว์เซอร์จะเปลี่ยนไปโหลดไฟล์เวอร์ชัน @2x โดยอัตโนมัติ เป็นการยืนยันว่า `srcset` ทำงานถูกต้องตามที่ตั้งใจไว้ โดยไม่ต้องเขียนโค้ด JavaScript เพิ่มเติมแต่อย่างใด

---

## 17. สรุปโค้ดสุดท้ายและนำไปใช้กับ Component File

โค้ด `<picture>` ฉบับสมบูรณ์ใน `index.html`:

![โค้ด picture/source สมบูรณ์ใน index.html](30-Optimizing-Images/050-index-html-final-picture-source-code.png)

```html
<picture>
  <source
    type="image/webp"
    srcset="images/banner.webp 1x, images/banner@2x.webp 2x"
  />
  <source
    type="image/png"
    srcset="images/banner.png 1x, images/banner@2x.png 2x"
  />
  <img class="hero__image" src="images/banner.png" alt="" />
</picture>
```

สุดท้าย Mosh คัดลอกโค้ดชุดนี้ไปอัปเดตไว้ในไฟล์ `components/hero.html` ด้วย เพื่อให้ไฟล์ตัวอย่างคอมโพเนนต์ (component library) ของโปรเจกต์สอดคล้องกับ `index.html`

![อัปเดต hero.html ในโฟลเดอร์ components](30-Optimizing-Images/051-hero-html-component-file-explorer.png)

---

## สรุปภาพรวมของคลิปนี้

| หัวข้อ | รายละเอียด |
|---|---|
| ปัญหาเริ่มต้น | `banner.png` มีขนาดไฟล์ 916 KB (ต้นฉบับ 7.26 MB, 1532×1656px) ซึ่งใหญ่เกินความจำเป็น |
| กลยุทธ์ | สร้างรูป 2 ขนาด (1x = 570px, 2x = 1140px) และ 2 ฟอร์แมต (PNG, WebP) |
| เครื่องมือที่ใช้ | Photoshop (resize + save as), CloudConvert.com (แปลง PNG → WebP), macOS Calculator |
| เทคนิค HTML | แท็ก `<picture>` + `<source type srcset>` + `<img>` เป็น fallback |
| ผลลัพธ์ | ขนาดไฟล์ที่โหลดจริงลดจาก 916 KB เหลือ 105 KB (WebP @2x) |
| การทดสอบ | ตรวจสอบผ่าน DevTools Network tab บน Chrome และ Firefox พร้อมปรับค่า DPR |

### แนวคิดสำคัญที่ได้จากคลิปนี้

1. **อย่าส่งรูปภาพที่มีขนาดใหญ่เกินความจำเป็นไปให้ผู้ใช้** ควร resize ให้พอดีกับพื้นที่แสดงผลจริงบนเว็บ
2. **สร้างรูปภาพ 2 เวอร์ชัน (1x และ 2x)** เพื่อรองรับทั้งจอทั่วไปและจอ Retina/High-DPI โดยใช้ `srcset` ให้เบราว์เซอร์เลือกเอง
3. **WebP เป็นฟอร์แมตที่บีบอัดได้ดีกว่า PNG** มาก ควรใช้ WebP เป็นตัวเลือกแรก และมี PNG เป็นตัวสำรองสำหรับเบราว์เซอร์ที่ไม่รองรับ
4. **แท็ก `<picture>` และ `<source>`** ช่วยให้เบราว์เซอร์เลือกไฟล์ที่เหมาะสมที่สุดโดยอัตโนมัติ ทั้งในแง่ฟอร์แมตไฟล์และความหนาแน่นพิกเซล โดยไม่ต้องพึ่ง JavaScript
5. **ต้อง resize จากไฟล์ต้นฉบับความละเอียดสูงเสมอ** ห้าม resize ซ้อนจากไฟล์ที่ลดขนาดไปแล้ว เพราะจะทำให้ภาพเบลอ
6. **ควรตรวจสอบผลลัพธ์จริงผ่าน DevTools Network tab** เพื่อยืนยันว่าเบราว์เซอร์โหลดไฟล์ที่ถูกต้องตามที่ตั้งใจไว้จริง ๆ

---

*สรุปจากคลิปที่ 30 ในคอร์ส "Building a Website" โดย Mosh Hamedani (codewithmosh.com)*
