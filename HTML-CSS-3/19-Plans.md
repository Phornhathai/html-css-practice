# HTML-CSS-3: 19 - Plans

**ไฟล์ต้นฉบับ:** 19-Plans.mp4

▶️ [ดูวิดีโอ](../../HTML-CSS-3/19-Plans.mp4)

---

## ภาพรวมคลิปนี้

![Title Slide](19-Plans/001-title-slide-plans.png)

คลิปนี้เป็นคลิปที่ **ยาวที่สุดในคอร์ส** (มีเฟรมสำคัญมากถึง 118 เฟรม) เพราะ Mosh นำ Component `.card` ที่สร้างไว้ในคลิปก่อนหน้า (Cards) มาต่อยอดเป็น **การ์ดแพลนราคา (Pricing Plan Card)** แบบเต็มรูปแบบที่ใช้งานได้จริง โดยอ้างอิงจากดีไซน์ใน Photoshop ที่ชื่อว่า "Entry" ซึ่งประกอบไปด้วย

> 🎯 ส่วนหัว (Header): ชื่อแพลน, ราคา, ป้าย "ลดราคา" (Badge), และคำโปรย (Tagline)
> 🎯 ส่วนเนื้อหา (Body): รายการฟีเจอร์แบบมีเครื่องหมายถูก (Checklist) และปุ่ม "Buy Now"
> 🎯 การปรับ Responsive: ใช้ Media Query แบบ Mobile First เพื่อลดขนาดตัวอักษรบนจอเดสก์ท็อป และแก้บั๊กการจัดวางที่เกิดขึ้น

![Photoshop Recap](19-Plans/002-photoshop-entry-card-recap-price-badge-tagline.png)

ภาพจาก Photoshop (`standard.psd` / `mobile.psd`) แสดงดีไซน์เป้าหมายที่ต้องทำให้เหมือน: การ์ดสีฟ้า (Cyan) หัวข้อ "Entry", ราคา "$14 /month" พร้อมป้าย "10% OFF", คำโปรย "Easy start on the cloud" และด้านล่างเป็นรายการติ๊กถูก เช่น "Unlimited Websites", "Unlimited Bandwidth", "100 GB SSD Storage"

> 💡 **หมายเหตุสำคัญ:** ระหว่างพิมพ์ Mosh พิมพ์คำว่า "Easy" ผิดเป็น **"East"** ในหลายเฟรม (เห็นได้ชัดในบราวเซอร์ว่าขึ้น "East start on the cloud" แทนที่จะเป็น "Easy start on the cloud") ซึ่งเป็นความผิดพลาดขณะสอนสด - ไฟล์นี้บันทึกไว้ตามที่ปรากฏจริงในวิดีโอ

---

## 1. เริ่มต้นจาก Card Component เดิม

![VSCode Card Secondary Carryover](19-Plans/003-vscode-index-html-card-secondary-carryover-from-cards-clip.png)

โค้ดที่สืบทอดมาจากคลิป Cards (คลิปที่แล้ว) คือ

```html
<div style="width: 30%; padding: 4rem">
  <div class="card card--secondary">
    <header class="card__header">Card Title</header>
    <div class="card__body">
      Lorem ipsum dolor sit amet consectetur, adipisicing elit. Eum, assumenda?
    </div>
  </div>
</div>
```

![Card Secondary Selected Breadcrumb](19-Plans/004-vscode-html-card-secondary-selected-breadcrumb.png)

Mosh เลือก `div.card.card--secondary` ใน Breadcrumb (แถบด้านบนของ VS Code ที่แสดงลำดับชั้นขององค์ประกอบ HTML) เพื่อเตรียมดัดแปลงโครงสร้างนี้ให้กลายเป็นการ์ดแพลนราคาจริง

> 📌 **แนวคิดสำคัญ:** นี่คือหลักการ "Bottom Up" ที่สอนไว้ในคลิปก่อนหน้า - เอา Component ทั่วไป (`.card`) ที่สร้างแยกต่างหากมาประกอบเป็นหน้าเพจจริง (Plans) แทนที่จะเริ่มเขียนใหม่ตั้งแต่ต้น

![Plan Div Wrapper Recap](19-Plans/005-vscode-plan-div-wrapper-recap.png)

Mosh ทดลองตำแหน่งที่จะครอบ Element ใหม่ก่อนตัดสินใจใช้คำสั่ง Wrap with Abbreviation

![Wrap with Abbreviation](19-Plans/006-vscode-plan-class-wrap-with-abbreviation-command.png)

Mosh ใช้คำสั่ง **"Wrap with Abbreviation"** ผ่าน Command Palette (Cmd+Shift+P) เพื่อครอบ `<div class="card card--secondary">...</div>` เดิมด้วย `<div class="plan">` ใหม่

```html
<div class="plan">
  <div class="card card--secondary">
    ...
  </div>
</div>
```

![Outer Div Plan Class Added](19-Plans/007-vscode-html-outer-div-plan-class-added.png)

![Plan Div Recap](19-Plans/008-vscode-html-plan-div-recap-full.png)

> ✨ **BEM concept:** `.plan` คือ Block ใหม่ (แยกจาก `.card`) ที่จะครอบคลุมองค์ประกอบเฉพาะของแพลนราคา เช่น `.plan__name`, `.plan__price`, `.plan__billing-cycle`, `.plan__description` - นี่คือการผสมผสาน Component 2 ตัว (`.card` และ `.plan`) เข้าด้วยกันบน Element เดียวกัน

---

## 2. สร้างชื่อแพลน (Plan Name)

![Plan Name Class Typing](19-Plans/009-vscode-html-card-secondary-h3-plan-name-class-typing.png)

Mosh แก้ไข `<header class="card__header">Card Title</header>` โดยเปลี่ยนเป็น heading `<h3>` ที่มี class `plan__name` แทนข้อความ "Card Title"

![H3 Plan Name Added](19-Plans/010-vscode-html-h3-plan-name-class-added-entry.png)

```html
<header class="card__header">
  <h3 class="plan__name">Entry</h3>
</header>
```

![Browser Entry Recap](19-Plans/011-browser-entry-recap-plan-name-class.png)

ผลลัพธ์ในบราวเซอร์: คำว่า "Entry" ปรากฏในกล่องสีฟ้า (จาก `.card--secondary`) แต่ยังใช้สไตล์ default ของ `<h3>` อยู่ (ตัวหนา ขนาดมาตรฐาน)

---

## 3. เพิ่มราคาและรอบบิล (Price + Billing Cycle)

![Card Body Recap](19-Plans/012-vscode-html-card-body-recap-plan-structure.png)

โครงสร้าง Header เสร็จแล้ว ต่อไปเป็นการเพิ่มราคาในส่วน `card__header` เดิม โดยใช้ `<span>` สองตัว

![Price Span Typing](19-Plans/013-vscode-html-price-markup-span-plan-price-typing.png)
![Plan Price Span Added](19-Plans/014-vscode-html-plan-price-14-span-added.png)

```html
<span class="plan__price">$14</span>
```

![Billing Cycle Span Typing](19-Plans/015-vscode-html-billing-cycle-span-month-typing.png)
![Plan Billing Cycle Added](19-Plans/016-vscode-html-plan-billing-cycle-span-added.png)

```html
<span class="plan__billing-cycle">/month</span>
```

![Browser 14 Month Recap](19-Plans/017-browser-14-month-recap.png)

ผลลัพธ์: "Entry" ตามด้วย "$14" และ "/month" เรียงต่อกันแบบข้อความปกติ (ยังไม่มีสไตล์พิเศษ)

> 🔧 **โครงสร้าง HTML ของ Header ในขณะนี้:**
> ```html
> <header class="card__header">
>   <h3 class="plan__name">Entry</h3>
>   <span class="plan__price">$14</span>
>   <span class="plan__billing-cycle">/month</span>
> </header>
> ```

---

## 4. นำ Badge Component กลับมาใช้ซ้ำ (Reusing Badge Component)

![Badge Component Recap](19-Plans/018-vscode-html-badge-component-recap-10-percent-off.png)

ต่อไปคือป้าย "10% OFF" ซึ่ง Mosh **ไม่ได้เขียนใหม่** แต่ไปเปิดไฟล์ `components/badges.html` ที่เคยสร้างไว้ก่อนหน้านี้ในคอร์ส (Component แยกต่างหาก)

![Icons Badges Lookup](19-Plans/019-vscode-icons-badges-html-component-lookup.png)
![Badges HTML Component Markup](19-Plans/020-vscode-badges-html-badge-secondary-markup.png)

โค้ดจาก `badges.html`:
```html
<span class="badge badge--secondary">10% off</span>
```

![Badge Pasted into Plan](19-Plans/021-vscode-html-badge-secondary-pasted-into-plan.png)

Mosh คัดลอกโค้ดนี้มาวางต่อจาก `plan__billing-cycle` ในไฟล์ `index.html`:

```html
<header class="card__header">
  <h3 class="plan__name">Entry</h3>
  <span class="plan__price">$14</span>
  <span class="plan__billing-cycle">/month</span>
  <span class="badge badge--secondary">10% off</span>
</header>
```

![Browser Badge Recap](19-Plans/022-browser-10-percent-off-badge-recap.png)

> ⭐ **แนวคิดสำคัญ (Component Reuse):** นี่คือประโยชน์หลักของแนวทาง "Bottom Up" ที่สอนในคลิปก่อน - เพราะ Badge ถูกสร้างเป็น Component แยกไว้ล่วงหน้า (`components/badges.html`) เมื่อต้องใช้ในหน้าเพจจริงก็แค่ Copy-Paste มาใช้ได้เลย ไม่ต้องเขียน CSS ใหม่ซ้ำอีก

---

## 5. เพิ่มคำโปรย (Tagline / Description)

![Plan Description Span Typing](19-Plans/023-vscode-html-plan-description-span-tagline-typing.png)
![Plan Description Added](19-Plans/024-vscode-html-plan-description-easy-start-on-cloud-added.png)

```html
<span class="plan__description">Easy start on the cloud</span>
```

![Browser Full Header Recap](19-Plans/025-browser-full-plan-header-recap-east-start-typo.png)

> ⚠️ ในเฟรมนี้จะเห็นว่าในบราวเซอร์ขึ้นคำว่า **"East start on the cloud"** (พิมพ์ผิดจาก "Easy") - นี่คือ Typo ที่เกิดขึ้นจริงระหว่างสอน ซึ่งยังคงปรากฏต่อเนื่องไปในหลายเฟรมถัดไปของคลิปนี้

![Full Header Recap 2](19-Plans/026-vscode-html-full-plan-header-recap.png)
![Plan Description Recap 2](19-Plans/027-vscode-html-plan-description-recap-2.png)
![Browser Header Recap 3](19-Plans/028-browser-plan-header-recap-3.png)

**โครงสร้าง HTML ของ `card__header` ที่สมบูรณ์ในตอนนี้:**
```html
<header class="card__header">
  <h3 class="plan__name">Entry</h3>
  <span class="plan__price">$14</span>
  <span class="plan__billing-cycle">/month</span>
  <span class="badge badge--secondary">10% off</span>
  <span class="plan__description">Easy start on the cloud</span>
</header>
```

---

## 6. เริ่มเขียน CSS ให้ Plan Name (`.plan__name`)

![Plans Comment Section Created](19-Plans/029-vscode-styles-css-plans-comment-section-created.png)

Mosh สร้างส่วน comment ใหม่ใน `styles.css`:
```css
/* Plans */
```

![Plan Name Selector Typing](19-Plans/030-vscode-styles-css-plan-name-selector-typing.png)
![Plan Name Color Property Autocomplete](19-Plans/031-vscode-styles-css-plan-name-color-property-autocomplete.png)
![Plan Name Color FFF Typed](19-Plans/032-vscode-styles-css-plan-name-color-fff-typed.png)
![Plan Name Margin 0 Added](19-Plans/033-vscode-styles-css-plan-name-margin-0-added.png)
![Plan Name Recap](19-Plans/034-vscode-styles-css-plan-name-color-margin-font-weight-500-recap.png)

```css
.plan__name {
  color: #fff;
  margin: 0;
  font-weight: 500;
}
```

![Browser Entry White Bold Recap](19-Plans/035-browser-plan-name-entry-white-bold-recap.png)

ผลลัพธ์: "Entry" เปลี่ยนเป็นสีขาว ไม่มี margin รอบตัว และน้ำหนักตัวอักษรลดลงเหลือ 500 (ปานกลาง แทนที่จะเป็น Bold เต็มที่ของ `<h3>` default)

### ตรวจสอบ font-size จาก Photoshop

![Photoshop Entry Header Font Size](19-Plans/036-photoshop-entry-header-font-size-24px-bold-inter.png)

Mosh สลับไปดู Photoshop (`mobile.psd`) เพื่อดูค่า Font ต้นฉบับที่นักออกแบบกำหนดไว้: **Inter, Bold, 24px** สำหรับคำว่า "Entry"

> 💡 **หมายเหตุ:** ค่า 24px ใน Photoshop จะถูกแปลงเป็นหน่วย `rem` ในโค้ด CSS (โดยอิงจากฐาน 10px = 1rem ที่ตั้งค่าไว้ตั้งแต่ต้นคอร์สผ่าน `font-size: 62.5%` ที่ `html` selector) ดังนั้น 24px = 2.4rem

![Browser Entry Recap 2](19-Plans/037-browser-entry-recap-2.png)

### ใช้ DevTools Computed Panel ตรวจสอบค่าปัจจุบัน

![DevTools Computed Plan Name](19-Plans/038-devtools-computed-plan-name-inspect.png)

Mosh เปิด Chrome DevTools แล้วเลือกแท็บ **Computed** (ไม่ใช่ Styles) เพื่อดูว่าขนาดตัวอักษรปัจจุบันของ `.plan__name` คำนวณออกมาเป็นเท่าไหร่ก่อนจะปรับแก้

> 🔍 **เทคนิคสำคัญ:** การใช้แท็บ Computed แทน Styles ช่วยให้เห็นค่าสุดท้ายที่ Browser คำนวณจริง (หลังผ่าน Cascade ทั้งหมด) ซึ่งมีประโยชน์มากเมื่อต้องดีบัก CSS ที่ซับซ้อน

![Plan Name Recap Before Font Size](19-Plans/039-vscode-plan-name-recap-before-font-size.png)

### เพิ่ม font-size ให้ Plan Name

![Font Size Typing Autocomplete Options](19-Plans/040-vscode-plan-name-font-size-typing-autocomplete-options.png)

VS Code แสดง Autocomplete รายการค่า font-size ที่เคยใช้ในโปรเจกต์ เช่น `large`, `larger`, `medium`, `small`, `smaller`, `x-large`, `x-small`, `xx-large`

![Font Size 2.4rem Added](19-Plans/041-vscode-plan-name-font-size-2-4rem-added.png)

```css
.plan__name {
  color: #fff;
  margin: 0;
  font-weight: 500;
  font-size: 2.4rem;
}
```

![Browser Entry Larger Recap](19-Plans/042-browser-entry-larger-heading-recap.png)

ผลลัพธ์: คำว่า "Entry" มีขนาดใหญ่ขึ้นชัดเจน ตรงกับดีไซน์ต้นฉบับใน Photoshop (24px)

![Plan Name Recap Final](19-Plans/043-vscode-plan-name-recap-final.png)

---

## 7. เขียน CSS ให้ Plan Price (`.plan__price`)

![Plan Price Font Size Typing](19-Plans/044-vscode-plan-price-class-created-font-size-typing.png)
![Plan Price Font Size 6rem Typed](19-Plans/045-vscode-plan-price-font-size-6rem-typed.png)

```css
.plan__price {
  font-size: 6rem;
}
```

![Browser Price 14 Large Recap](19-Plans/046-browser-price-14-large-recap.png)

ผลลัพธ์: ตัวเลข "$14" มีขนาดใหญ่มาก (6rem = 60px) โดดเด่นเป็นจุดสนใจหลักของการ์ด ตรงตามดีไซน์ที่ตัวเลขราคาต้องใหญ่ที่สุดในหัวการ์ด

> 📐 **หลักการออกแบบ Typography Hierarchy:** ราคา (Price) คือข้อมูลสำคัญที่สุดสำหรับผู้ใช้ตอนตัดสินใจซื้อ จึงต้องมีขนาดใหญ่ที่สุด ในขณะที่ชื่อแพลน (Name) มีขนาดรองลงมา ส่วนคำโปรยและรอบบิลจะมีขนาดเล็กสุด

---

## 8. เขียน CSS ให้ Billing Cycle (`.plan__billing-cycle`)

![Billing Cycle New Class Autocomplete](19-Plans/047-vscode-plan-billing-cycle-new-class-autocomplete-suggestion.png)

VS Code แสดง Autocomplete ของ class selector ที่เคยประกาศไว้แล้ว: `.plan__name`, `.plan__price` (แสดงว่า IntelliSense จดจำ class ที่ใช้ในโปรเจกต์)

![Billing Cycle Font Size Typing](19-Plans/048-vscode-plan-billing-cycle-font-size-typing.png)
![Billing Cycle Font Size 2.4rem Added](19-Plans/049-vscode-plan-billing-cycle-font-size-2-4rem-added.png)
![Font Weight Value Autocomplete Options](19-Plans/050-vscode-font-weight-value-autocomplete-options.png)

VS Code แสดงตัวเลือกค่า `font-weight` ที่เป็นไปได้: 100, 200, 300, 400, 500, 600, 700, 800

```css
.plan__billing-cycle {
  font-size: 2.4rem;
}
```

![Browser Month Badge Recap](19-Plans/051-browser-month-badge-recap.png)

### ตรวจสอบค่าจาก Photoshop สำหรับข้อความ "/month"

![Photoshop Month Text Recap](19-Plans/052-photoshop-month-text-24px-regular-font-recap.png)

Photoshop แสดงค่า Font ของคำว่า "/month": **24px, Regular** (ไม่ Bold เหมือน "Entry")

---

## 9. ทำให้คำว่า "/month" จางลง (Opacity Technique)

![Photoshop Window Menu Layers](19-Plans/053-photoshop-window-menu-layers-panel-open.png)

Mosh เปิดเมนู **Window > Layers** ใน Photoshop เพื่อดู Layer ของข้อความ "/month"

![Photoshop Layers Panel Opacity 80](19-Plans/054-photoshop-layers-panel-opacity-80-percent.png)

ในแผง Layers พบว่า Layer "/month" มีค่า **Opacity: 80%** ตั้งไว้ - นี่คือเทคนิคที่นักออกแบบใช้เพื่อทำให้ข้อความรองดูจางกว่าข้อความหลัก

![Font Weight 300 Added](19-Plans/055-vscode-plan-billing-cycle-font-weight-300-added.png)

```css
.plan__billing-cycle {
  font-size: 2.4rem;
  font-weight: 300;
}
```

![Opacity Emmet Abbreviation Autocomplete](19-Plans/056-vscode-opacity-emmet-abbreviation-autocomplete.png)

Mosh พิมพ์ `opa` แล้ว Emmet แสดง Abbreviation แนะนำ `opacity: ;` ให้เติมค่าอัตโนมัติ

![Opacity 0.8 Added](19-Plans/057-vscode-plan-billing-cycle-opacity-0-8-added.png)

```css
.plan__billing-cycle {
  font-size: 2.4rem;
  font-weight: 300;
  opacity: 0.8;
}
```

![Browser Month Badge Opacity Applied](19-Plans/058-browser-month-badge-opacity-applied-recap.png)

ผลลัพธ์: คำว่า "/month" จางลงเล็กน้อย (โปร่งใส 80%) ทำให้ดูเป็นข้อความรองอย่างชัดเจน แตกต่างจากตัวเลขราคาหลัก

> 🎨 **CSS Property: `opacity`** เป็นค่าที่กำหนดความโปร่งใสของทั้ง Element (รวมถึงลูกหลานทั้งหมดข้างใน) ค่า 1 = ทึบแสงเต็มที่ (default), ค่า 0 = โปร่งใสหมด (มองไม่เห็น), ค่า 0.8 = มองเห็น 80% (จางลง 20%) เป็นเทคนิคที่ต่างจาก `color` เพราะ opacity ไม่ต้องคำนวณค่าสีใหม่ ทำให้ปรับความจางได้ง่ายโดยไม่ต้องรู้ค่าสีต้นฉบับ

---

## 10. สร้าง Badge สีเฉพาะสำหรับ Card Secondary (Custom Badge Color)

![Card Primary Secondary Header Recap](19-Plans/059-vscode-card-primary-secondary-header-recap-before-badge.png)

ก่อนหน้านี้ Badge ใช้สไตล์ default (`badge--secondary`) แต่เมื่อดูดีไซน์ใน Photoshop จะพบว่าสีของ Badge ในการ์ด Secondary (สีฟ้า) นั้น**แตกต่างจากสี badge--secondary ปกติ** - ต้องสร้างกฎ CSS เฉพาะสำหรับกรณีนี้

![Card Secondary Badge Selector Autocomplete](19-Plans/060-vscode-card-secondary-badge-selector-autocomplete-class-list.png)

VS Code แสดงรายการ class ที่มีให้เลือกเมื่อพิมพ์ `.badge`: `.badge`, `.badge--primary`, `.badge--secondary`, `.badge--small`

![Card Secondary Badge Secondary Selector Typed](19-Plans/061-vscode-card-secondary-badge-secondary-selector-typed.png)

Mosh สร้าง Selector แบบ Descendant Combinator (Compound Selector) ใหม่:
```css
.card--secondary .badge--secondary {
}
```

> 🧬 **แนวคิด CSS Specificity:** Selector นี้มีความจำเพาะเจาะจง (Specificity) สูงกว่า `.badge--secondary` เดี่ยวๆ เพราะประกอบด้วย 2 class รวมกัน (`.card--secondary` + `.badge--secondary`) ดังนั้นกฎนี้จะ Override สไตล์ของ `.badge--secondary` เดิมได้ เฉพาะเมื่อ badge นั้นอยู่ภายใน card ที่มี class `card--secondary` เท่านั้น

### ใช้ Eyedropper Tool ดึงสีจาก Photoshop

![Photoshop Eyedropper Sampling Badge Color](19-Plans/062-photoshop-eyedropper-tool-sampling-badge-color.png)

Mosh ใช้เครื่องมือ **Eyedropper (หลอดดูดสี)** ใน Photoshop คลิกที่พื้นหลังของป้าย "10% OFF" ในดีไซน์ต้นฉบับเพื่อดึงค่าสีที่แท้จริงออกมา

![Photoshop Color Picker Hex 02cdf1](19-Plans/063-photoshop-color-picker-badge-hex-02cdf1.png)
![Photoshop Color Picker Full Detail](19-Plans/064-photoshop-color-picker-full-detail-hex-02cdf1.png)

หน้าต่าง Color Picker แสดงค่าสีที่ดูดมาได้แบบละเอียด:
- **Hex:** `#02cdf1`
- **HSB:** H 189°, S 99%, B 95%
- **Lab:** L 76, a -34, b -30
- **RGB:** R 2, G 205, B 241
- **CMYK:** C 64%, M 0%, Y 5%, K 0%

> 🎨 **เทคนิค Eyedropper:** นี่คือวิธีมาตรฐานที่นักพัฒนาใช้เมื่อได้รับไฟล์ดีไซน์ (PSD/Figma/Sketch) มาแล้วต้องแปลงเป็นโค้ด - แทนที่จะเดาสีเอง ให้ใช้เครื่องมือดูดสีเพื่อให้ได้ค่า Hex ที่ตรงกับต้นฉบับ 100%

![Background Property Typing](19-Plans/065-vscode-card-secondary-badge-secondary-background-property-typing.png)

```css
.card--secondary .badge--secondary {
  background: #02cdf1;
}
```

![Browser Badge Color Applied Recap](19-Plans/066-browser-badge-color-applied-recap.png)

ผลลัพธ์: สีพื้นหลังของป้าย "10% OFF" เปลี่ยนเป็นสีฟ้าอ่อนที่ตรงกับดีไซน์ต้นฉบับ (แตกต่างจากสีของการ์ดพื้นหลังที่เป็นสีฟ้าเข้มกว่า) ทำให้ป้ายดูโดดเด่นแยกออกจากพื้นหลัง

![Photoshop Select Active Layers Fill Swatch](19-Plans/067-photoshop-select-active-layers-fill-cyan-swatch.png)

---

## 11. Recap Badge Small (จากคลิปก่อนหน้า)

![Badge Small Font Size Media Query Recap](19-Plans/068-vscode-badge-small-font-size-media-query-recap.png)

Mosh ทวนโค้ด CSS ของ `.badge--small` ที่เคยเขียนไว้:
```css
.badge--small {
  font-size: 1.6rem;
}

@media screen and (min-width: 1024px) {
  .badge {
    font-size: 1.5rem;
  }

  .badge--small {
    font-size: 1.2rem;
  }
}
```

![Browser Badge Recap Final](19-Plans/069-browser-badge-recap-final.png)

### เพิ่ม padding ให้ badge--small

![Padding Property Typing Autocomplete](19-Plans/070-vscode-badge-small-padding-property-typing-autocomplete.png)

VS Code แสดง Autocomplete: `padding`, `padding-left`, `padding-top`, `padding-bottom`, `padding-right`

![Padding 0.5rem Added](19-Plans/071-vscode-badge-small-padding-0-5rem-added.png)

```css
.badge--small {
  font-size: 1.6rem;
  padding: 0.5rem ;
}
```

![Plan Billing Cycle Recap Full Props](19-Plans/072-vscode-plan-billing-cycle-recap-full-props.png)

![Browser Badge Padding Recap](19-Plans/073-browser-badge-padding-recap.png)

ผลลัพธ์: ป้าย "10% OFF" มีพื้นที่ว่างรอบข้อความมากขึ้น ดูสมส่วนมากขึ้น ไม่แน่นจนเกินไป

---

## 12. เพิ่มระยะห่างให้ Billing Cycle (margin-right)

![Margin Right 1rem Added](19-Plans/074-vscode-plan-billing-cycle-margin-right-1rem-added.png)

```css
.plan__billing-cycle {
  font-size: 2.4rem;
  font-weight: 300;
  opacity: 0.8;
  margin-right: 1rem;
}
```

> 📏 นี่คือการเพิ่ม `margin-right` เพื่อสร้างระยะห่างระหว่างข้อความ "/month" กับป้าย Badge "10% OFF" ที่อยู่ถัดไป ป้องกันไม่ให้ทั้งสองชิดกันเกินไป

---

## 13. เขียน CSS ให้ Plan Description (`.plan__description`)

![Font Size Property Autocomplete](19-Plans/075-vscode-font-size-property-autocomplete-plan-description.png)
![Plan Description Class Created Font Size 2rem](19-Plans/076-vscode-plan-description-class-created-font-size-2rem.png)

```css
.plan__description {
  font-size: 2rem;
}
```

![Browser Plan Description Recap](19-Plans/077-browser-plan-description-recap.png)

### ปรับสีให้คำโปรยด้วย Fill Tool

![Photoshop Fill Tool Active Layers Select Color](19-Plans/078-photoshop-fill-tool-active-layers-select-cyan-color.png)

Mosh ใช้เครื่องมือ Fill/Selection ใน Photoshop เพื่อตรวจสอบสีพื้นหลังของ Layer ที่ Active อยู่

![Browser Tagline Recap](19-Plans/079-browser-plan-description-tagline-recap.png)

### เพิ่ม font-weight ให้เบาลง

![Font Weight 300 Added](19-Plans/080-vscode-plan-description-font-weight-300-added.png)

```css
.plan__description {
  font-size: 2rem;
  font-weight: 300;
}
```

![Browser Tagline Recap Lighter Weight](19-Plans/081-browser-tagline-recap-lighter-weight.png)

ผลลัพธ์: คำโปรย "East start on the cloud" (typo ของ "Easy") มีน้ำหนักตัวอักษรเบาลง (300 = Light) ดูเป็นข้อความรองที่ผ่อนคลายกว่าหัวข้อหลัก

---

## 14. สร้าง Checklist ด้วย List Component (`list--tick`)

![Index HTML Explorer Card Body](19-Plans/082-vscode-index-html-explorer-card-body-selected-breadcrumb.png)

Mosh เปิด Explorer panel ด้านซ้ายของ VS Code แล้วดูโครงสร้างโปรเจกต์ในโฟลเดอร์ `components/` ซึ่งมีไฟล์ `badges.html`, `buttons.html`, `cards.html`, `icons.html`, `input-groups.html`, `inputs.html`, `links.html`, `lists.html`

![Components Folder Expanded Lists HTML](19-Plans/083-vscode-explorer-components-folder-expanded-lists-html.png)

Mosh เปิดไฟล์ **`components/lists.html`** เพื่อดู Component รายการ (List) ที่เคยสร้างไว้

![Lists HTML List Tick Component Markup](19-Plans/084-vscode-lists-html-list-tick-component-markup.png)

โค้ดต้นฉบับใน `lists.html`:
```html
<ul class="list list--tick">
  <li class="list__item">Item 1</li>
  <li class="list__item">Item 2</li>
  <li class="list__item">Item 3</li>
</ul>
```

> ✨ **Component Reuse (อีกครั้ง):** เช่นเดียวกับ Badge ก่อนหน้านี้ - List แบบมีเครื่องหมายถูก (`list--tick`) เป็น Component ที่สร้างแยกไว้ล่วงหน้าแล้ว (คงมาจากคลิปก่อนๆ ในคอร์สที่ไม่ได้อยู่ใน 16 คลิปที่ได้สรุปไว้) เมื่อต้องการ Checklist ใน Card ก็แค่คัดลอกมาวาง

![Index HTML List Tick Pasted](19-Plans/085-vscode-index-html-list-tick-pasted-into-card-body.png)

Mosh คัดลอกโค้ด `<ul class="list list--tick">...</ul>` มาวางใน `card__body` แทนที่ข้อความ Lorem Ipsum เดิม

```html
<div class="card__body">
  <ul class="list list--tick">
    <li class="list__item">Item 1</li>
    <li class="list__item">Item 2</li>
    <li class="list__item">Item 3</li>
  </ul>
</div>
```

![Browser Item Checklist Recap](19-Plans/086-browser-item-1-2-3-checklist-recap.png)
![Browser Item List Scrolled Recap](19-Plans/087-browser-item-list-scrolled-recap.png)

ผลลัพธ์: รายการ "Item 1", "Item 2", "Item 3" พร้อมเครื่องหมายถูกสีเขียว (✓) ปรากฏด้านล่างหัวการ์ด

### เปลี่ยนข้อความรายการให้ตรงกับดีไซน์จริง

![List Items Renamed](19-Plans/088-vscode-list-items-renamed-unlimited-websites-bandwidth-storage-ram.png)

Mosh แก้ไขข้อความในแต่ละ `<li>` ให้ตรงกับฟีเจอร์ที่ระบุใน Photoshop:
```html
<ul class="list list--tick">
  <li class="list__item">Unlimited Websites</li>
  <li class="list__item">Unlimited Bandwidth</li>
  <li class="list__item">100 GB SSD Sotrage</li>
  <li class="list__item">3 GB RAM</li>
</ul>
```

> ⚠️ อีกหนึ่ง Typo ที่เกิดขึ้นในเฟรมนี้: Mosh พิมพ์ "Storage" ผิดเป็น **"Sotrage"** ในโค้ด HTML ซึ่งยังคงปรากฏต่อเนื่องไปจนจบคลิป (เห็นได้ในทุกภาพหน้าจอบราวเซอร์ถัดจากนี้)

---

## 15. เพิ่มปุ่ม "Buy Now" (Buy Now Button)

![Button Emmet Abbreviation Typing](19-Plans/089-vscode-button-emmet-abbreviation-typing.png)

Mosh พิมพ์ `butt` แล้ว Emmet แสดงตัวเลือก Abbreviation: `button`, `button:d` (disabled), `button:r` (reset), `button:s` (submit)

![Button BTN Emmet Suggestion](19-Plans/090-vscode-button-btn-emmet-abbreviation-suggestion.png)

Mosh พิมพ์ Emmet Abbreviation แบบเต็ม: `button.btn`

![Buy Now Button Typed](19-Plans/091-vscode-button-btn-outline-btn-block-buy-now-typed.png)

```html
<button class="btn btn--outline btn--block">Buy Now</button>
```

> 🔘 **การนำ Component Button กลับมาใช้:** `.btn`, `.btn--outline` และ `.btn--block` ล้วนเป็น Class ที่มาจาก Component ปุ่ม (`components/buttons.html`) ที่สร้างไว้แล้วในคอร์ส
> - `.btn` = คลาสหลักของปุ่ม (ฐาน)
> - `.btn--outline` = Modifier ทำให้ปุ่มมีแค่เส้นขอบ ไม่มีพื้นหลังทึบ
> - `.btn--block` = Modifier ทำให้ปุ่มขยายเต็มความกว้างของ container (display: block แทน inline-block)

![Browser Checklist and Buy Now Recap](19-Plans/092-browser-checklist-and-buy-now-button-recap.png)
![Browser Buy Now Outline Style Recap](19-Plans/093-browser-buy-now-button-outline-style-recap.png)
![Browser Buy Now Button Recap 2](19-Plans/094-browser-buy-now-button-recap-2.png)

ผลลัพธ์: ปุ่ม "BUY NOW" ปรากฏเป็นปุ่มขอบมนสีน้ำเงินเข้ม (Outline) เต็มความกว้างของการ์ด อยู่ด้านล่างสุดของ Checklist

![Photoshop Recap Full Design](19-Plans/095-photoshop-recap-full-design-buy-now-button.png)

Mosh เปรียบเทียบผลลัพธ์กับดีไซน์ต้นฉบับใน Photoshop เพื่อยืนยันว่าตรงกัน

![Browser Full Card Recap Scrolled](19-Plans/096-browser-full-card-recap-scrolled.png)

![VSCode Full HTML Recap](19-Plans/097-vscode-full-html-recap-list-tick-buy-now-button.png)

**โครงสร้าง HTML ที่สมบูรณ์ของ `card__body` ในตอนนี้:**
```html
<div class="card__body">
  <ul class="list list--tick">
    <li class="list__item">Unlimited Websites</li>
    <li class="list__item">Unlimited Bandwidth</li>
    <li class="list__item">100 GB SSD Sotrage</li>
    <li class="list__item">3 GB RAM</li>
  </ul>
  <button class="btn btn--outline btn--block">Buy Now</button>
</div>
```

---

## 16. ปรับแต่งรายละเอียดเพิ่มเติม (Fine-tuning)

### เพิ่ม letter-spacing ให้คำโปรย

![Letter Spacing 1px Added](19-Plans/098-vscode-plan-description-letter-spacing-1px-added.png)

```css
.plan__description {
  font-size: 2rem;
  font-weight: 300;
  letter-spacing: 1px;
}
```

> 🔤 **CSS Property: `letter-spacing`** กำหนดระยะห่างระหว่างตัวอักษรแต่ละตัว ค่า `1px` เพิ่มช่องว่างเล็กน้อยระหว่างตัวอักษร ทำให้ข้อความดูโปร่งและอ่านง่ายขึ้นเล็กน้อย เป็นเทคนิคการปรับแต่งระดับละเอียด (Micro-typography) ที่ช่วยให้ดีไซน์ดูประณีตมากขึ้น

### เพิ่มระยะห่างระหว่างรายการ Checklist

![Plan Class Autocomplete List Selectors](19-Plans/099-vscode-plan-class-autocomplete-list-selectors.png)

VS Code แสดง Autocomplete ของ Selector ที่มีอยู่: `.plan__billing-cycle`, `.plan__description`, `.plan__name`, `.plan__price`

![Plan List Item Selector Typed](19-Plans/100-vscode-plan-list-item-selector-typed.png)

Mosh สร้าง Compound Selector ใหม่แบบ Descendant Combinator:
```css
.plan .list__item {
}
```

![Plan Description Recap Before](19-Plans/101-vscode-plan-description-recap-before-plan-list-item.png)
![Plan Class Selector Suggestions](19-Plans/102-vscode-plan-class-selector-suggestions-billing-cycle-description-name-price.png)
![Plan List Item Class Typed](19-Plans/103-vscode-plan-list-item-class-typed.png)

![Margin Bottom Property Typing Autocomplete](19-Plans/104-vscode-margin-bottom-property-typing-autocomplete.png)

VS Code แสดงตัวเลือก Autocomplete: `margin-bottom`, `scroll-margin-bottom`, `-webkit-margin-bottom-collapse`, `margin-block-start`, `scroll-margin-block-start`

![Margin Bottom 2rem Added](19-Plans/105-vscode-plan-list-item-margin-bottom-2rem-added.png)

```css
.plan .list__item {
  margin-bottom: 2rem;
}
```

![Browser Entry Recap Before Media Query](19-Plans/106-browser-entry-recap-before-media-query.png)
![Browser Desktop Scrolled Recap](19-Plans/107-browser-desktop-scrolled-checklist-buy-now-recap.png)

ผลลัพธ์: แต่ละรายการในเช็คลิสต์ (`Unlimited Websites`, `Unlimited Bandwidth`, `100 GB SSD Sotrage`, `3 GB RAM`) มีระยะห่างด้านล่างมากขึ้น ทำให้อ่านง่าย ไม่แน่นติดกันเกินไป

> 🧬 **Selector `.plan .list__item`:** นี่คือ Descendant Combinator แบบเจาะจงเฉพาะเมื่อ `.list__item` อยู่ภายใน `.plan` เท่านั้น (ไม่กระทบ `.list__item` ที่อาจใช้ที่อื่นในเว็บไซต์) เป็นเทคนิคจำกัดขอบเขตผลกระทบของ CSS Rule ให้แคบลง

---

## 17. ปรับ Responsive ด้วย Media Query (Mobile First)

![Media Query 1024px Desktop Sizes](19-Plans/108-vscode-media-query-1024px-plan-name-price-billing-cycle-desktop-sizes.png)

Mosh เพิ่มกฎ CSS ใหม่ภายใน Media Query ที่มีอยู่แล้ว (`@media screen and (min-width: 1024px)`) เพื่อลดขนาดตัวอักษรของ Plan Header บนหน้าจอเดสก์ท็อป:

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

![Media Query Font Sizes Recap](19-Plans/109-vscode-media-query-plan-price-billing-cycle-font-sizes-recap.png)

```css
  .plan__billing-cycle {
    font-size: 1.6rem;
  }

  .plan__description {
    font-size: 1.7rem;
  }
```

> 📱💻 **หลักการ Mobile First:** ค่า font-size หลัก (เช่น `.plan__name { font-size: 2.4rem; }`) ถูกออกแบบมาสำหรับหน้าจอมือถือ (มือถือมีพื้นที่จำกัด จึงต้องการตัวอักษรที่ใหญ่พอสมควรเพื่อให้อ่านง่ายในระยะใกล้) แต่บนหน้าจอเดสก์ท็อปที่มีความกว้างมากกว่า (ตั้งแต่ 1024px ขึ้นไป) ตัวอักษรขนาดเท่าเดิมจะดูใหญ่เกินสัดส่วน จึงต้องลดขนาดลงผ่าน Media Query `min-width: 1024px`
>
> สรุปตารางขนาด Font-size ระหว่าง Mobile vs Desktop:
>
> | Element | Mobile (default) | Desktop (≥1024px) |
> |---|---|---|
> | `.plan__name` | 2.4rem | 1.4rem |
> | `.plan__price` | 6rem | 5rem |
> | `.plan__billing-cycle` | 2.4rem | 1.6rem |
> | `.plan__description` | 2rem | 1.7rem |

![Browser Desktop 1024px Recap](19-Plans/110-browser-desktop-1024px-plan-name-price-recap.png)

ผลลัพธ์เบื้องต้น: ที่ความกว้างจอ ≥1024px ขนาดตัวอักษรของ Plan Name และ Price ลดลงตามที่กำหนด

---

## 18. แก้บั๊ก: คำโปรยล้นบรรทัด (Tagline Inline Wrapping Bug)

![Browser Desktop Tagline Wrapping Bug](19-Plans/111-browser-desktop-tagline-wrapping-bug-inline-issue.png)

**🐛 บั๊กที่พบ:** เมื่อทดสอบบนหน้าจอเดสก์ท็อป (กว้าง ≥1024px) จะเห็นว่า **`.plan__description` ("Easy start on the cloud")** ไปเรียงต่อท้ายบรรทัดเดียวกันกับ badge "10% OFF" แทนที่จะขึ้นบรรทัดใหม่แยกต่างหากเหมือนตอนอยู่บนมือถือ

สาเหตุ: `<span>` เป็น Inline Element โดย default ซึ่งจะพยายามเรียงต่อกันในบรรทัดเดียวกันกับ Element ข้างเคียงถ้ามีพื้นที่ว่างพอ (บนจอกว้างมีพื้นที่ว่างเยอะกว่ามือถือ ทำให้บั๊กนี้ปรากฏเฉพาะบนเดสก์ท็อป)

![Media Query Description Font Size](19-Plans/112-vscode-media-query-plan-description-font-size-1-7rem-added.png)

### วิธีแก้: เปลี่ยน display เป็น block

![Display Block Typing](19-Plans/113-vscode-plan-description-display-block-typing.png)

Mosh พิมพ์ `dis` แล้ว Emmet แสดง Abbreviation แนะนำ `display: inline...` และตัวเลือกอื่นๆ

![Display Block Added Fixing Bug](19-Plans/114-vscode-plan-description-display-block-added-fixing-bug.png)

```css
.plan__description {
  font-size: 2rem;
  font-weight: 300;
  letter-spacing: 1px;
  display: block;
}
```

![Browser Desktop Tagline Fixed](19-Plans/115-browser-desktop-tagline-fixed-display-block-recap.png)

ผลลัพธ์: หลังเพิ่ม `display: block;` คำโปรย "East start on the cloud" ขึ้นบรรทัดใหม่ทันที แยกออกจาก badge อย่างชัดเจน ตรงกับดีไซน์ที่ตั้งใจไว้บนทุกขนาดหน้าจอ

> 🛠️ **แนวคิดสำคัญ (Display Property Fix):** นี่คือตัวอย่างคลาสสิกของปัญหา Inline vs Block ใน CSS - Element แบบ `inline` (เช่น `<span>`) จะไม่ยอมขึ้นบรรทัดใหม่เองแม้จะมีเนื้อหายาว การบังคับ `display: block` (หรือ `display: inline-block` ในบางกรณี) คือวิธีแก้ปัญหาการจัดวางที่พบบ่อยที่สุดเมื่อ Element ไม่ยอมตัดขึ้นบรรทัดใหม่ตามที่ต้องการ

![Browser Desktop Scrolled Down Recap](19-Plans/116-browser-desktop-scrolled-down-recap.png)

---

## 19. รีแคปผลลัพธ์สุดท้าย (Final Recap)

![Browser Desktop Final Recap Scrolled](19-Plans/117-browser-desktop-final-full-recap-scrolled.png)

![Browser Desktop Final Recap Scrolled 2](19-Plans/118-browser-desktop-final-full-recap-scrolled-2.png)

การ์ดแพลนราคา "Entry" เสร็จสมบูรณ์แล้วบนทั้งมือถือและเดสก์ท็อป ประกอบด้วย: ชื่อแพลน, ราคาตัวใหญ่, รอบบิลจางๆ, ป้ายส่วนลดสีฟ้าอ่อน, คำโปรยที่ขึ้นบรรทัดใหม่อย่างถูกต้อง, รายการ Checklist 4 ข้อพร้อมเครื่องหมายถูก และปุ่ม "Buy Now" แบบเต็มความกว้าง

---

## สรุปภาพรวมของคลิปนี้

| CSS Class | คุณสมบัติหลัก | ค่าที่ตั้ง (Mobile) | ค่าที่ตั้ง (Desktop ≥1024px) |
|---|---|---|---|
| `.plan__name` | สี, margin, น้ำหนัก, ขนาด | `color:#fff; margin:0; font-weight:500; font-size:2.4rem;` | `font-size:1.4rem;` |
| `.plan__price` | ขนาดตัวเลขราคา | `font-size:6rem;` | `font-size:5rem;` |
| `.plan__billing-cycle` | ขนาด, น้ำหนัก, ความจาง, ระยะห่าง | `font-size:2.4rem; font-weight:300; opacity:0.8; margin-right:1rem;` | `font-size:1.6rem;` |
| `.plan__description` | ขนาด, น้ำหนัก, ระยะห่างตัวอักษร, การแสดงผล | `font-size:2rem; font-weight:300; letter-spacing:1px; display:block;` | `font-size:1.7rem;` |
| `.card--secondary .badge--secondary` | สีพื้นหลังเฉพาะ | `background:#02cdf1;` | - |
| `.badge--small` | ขนาด, padding | `font-size:1.6rem; padding:0.5rem;` | `font-size:1.2rem;` (จากคลิปก่อน) |
| `.plan .list__item` | ระยะห่างรายการ | `margin-bottom:2rem;` | - |

### แนวคิดสำคัญที่ได้จากคลิปนี้

1. **การผสม Component หลายตัวเข้าด้วยกัน** - `.card`, `.badge`, `.list`, `.btn` ล้วนเป็น Component อิสระที่สร้างแยกไว้ในคอร์สนี้ (Bottom Up) แล้วนำมาประกอบร่วมกันเป็นหน้า Plans ที่สมบูรณ์
2. **การใช้ Eyedropper Tool ใน Photoshop** เพื่อดึงค่าสีที่แม่นยำจากดีไซน์ต้นฉบับ (Hex `#02cdf1`) แทนการเดาสีเอง
3. **การใช้แท็บ Layers และ Opacity ใน Photoshop** เพื่อดูค่าความโปร่งใสที่นักออกแบบตั้งไว้ (80%) แล้วนำมาแปลงเป็น CSS `opacity: 0.8`
4. **Compound/Descendant Selector** เช่น `.card--secondary .badge--secondary` และ `.plan .list__item` ช่วยจำกัดขอบเขตของกฎ CSS ให้เจาะจงเฉพาะบริบทที่ต้องการ ไม่กระทบ Element เดียวกันในที่อื่นของเว็บไซต์
5. **Typography Hierarchy** - การกำหนดขนาดตัวอักษรตามลำดับความสำคัญของข้อมูล (ราคาใหญ่ที่สุด, ชื่อแพลนรองลงมา, คำโปรยและรอบบิลเล็กที่สุด)
6. **Mobile First Media Query** - กำหนดค่า default สำหรับมือถือก่อน แล้วค่อยลดขนาดลงสำหรับเดสก์ท็อปผ่าน `@media screen and (min-width: 1024px)`
7. **การแก้บั๊ก Inline vs Block** - ปัญหาคลาสสิกที่ `<span>` (inline) ไม่ยอมขึ้นบรรทัดใหม่ แก้ด้วยการเปลี่ยน `display: block;`
8. **letter-spacing** เป็นเทคนิค Micro-typography ที่ช่วยปรับความประณีตของงานดีไซน์ในระดับละเอียด

---

*สรุปจากคลิปที่ 19 (Plans) คอร์ส HTML & CSS โดย Mosh Hamedani จาก codewithmosh.com*
