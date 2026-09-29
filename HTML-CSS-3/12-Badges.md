# HTML-CSS-3: 12 - Badges

**ไฟล์ต้นทาง:** 12-Badges.mp4

▶️ [ดูวิดีโอ](../../HTML-CSS-3/12-Badges.mp4)

---

## ภาพรวมคลิปนี้

![สไลด์ชื่อคลิป Badges](12-Badges/01-title-slide-badges.png)

คลิปนี้ Mosh สอนการสร้าง component "Badge" ซึ่งเป็นป้ายข้อความเล็กๆ ทรงแคปซูล (pill shape) ที่ใช้แสดงตัวเลขส่วนลดหรือข้อความสั้นๆ เช่น "10% Off" โดยอ้างอิงจากดีไซน์ใน Photoshop ที่มีทั้งป้ายราคาโดเมน (`.sg $7.91`) และป้าย "Popular" รูปริบบิ้น เนื้อหาสำคัญในคลิปนี้ครอบคลุมตั้งแต่การสร้างคลาสหลัก `.badge`, การสร้างคลาสดัดแปลง (modifier class) ตามหลักการ **BEM (Block Element Modifier)** อย่าง `.badge--primary`, `.badge--secondary`, และ `.badge--small`, การใช้ **DevTools Network tab** ตรวจสอบว่าฟอนต์น้ำหนักที่ต้องการถูกโหลดมาจริงหรือไม่, การแก้ไข Google Fonts import URL เพื่อเพิ่มน้ำหนักฟอนต์ใหม่, การใช้ **VS Code Command Palette** เพื่อเรียงลำดับ CSS properties ตามตัวอักษร, และการขยาย Component Library ด้วยไฟล์ `components/badges.html`

---

## 1. ภาพรวมดีไซน์ Badge ใน Photoshop

![ภาพรวมดีไซน์ badge ป้ายราคาโดเมน](12-Badges/02-photoshop-domain-badge-sg-pill.png)

Mosh เปิดไฟล์ `mobile.psd` ใน Photoshop เพื่อดูตัวอย่าง badge สองรูปแบบที่ปรากฏในหน้าเว็บ Moshify

> รูปแบบแรกคือป้ายราคาโดเมนทรงแคปซูล (เช่น `.sg $7.91`) ที่มีพื้นหลังสีฟ้าอมเขียว (cyan) และตัวอักษรสีขาว ปรากฏอยู่ท่ามกลางราคาโดเมนอื่นๆ ที่ไม่มีพื้นหลัง (`.com $9.26`, `.space $12.98` เป็นต้น) — badge ที่มีพื้นหลังนี้ใช้เน้นว่าเป็นตัวเลือกที่แนะนำ

ถัดมาคือป้ายส่วนลดในการ์ดราคา (Pricing Card) เช่น "10% OFF" และ "20% OFF" ซึ่งเป็นทรงแคปซูลเช่นกันแต่มีสีพื้นหลังต่างกันไปตามธีมสีของการ์ดนั้นๆ

![ภาพรวมดีไซน์ป้าย Popular ทรงริบบิ้น](12-Badges/03-photoshop-popular-ribbon-badge.png)

> อีกรูปแบบหนึ่งที่เห็นในดีไซน์คือป้าย **"Popular"** ทรงริบบิ้น (ribbon) ที่มุมขวาบนของการ์ด Business ซึ่งมีรูปทรงซับซ้อนกว่า (ไม่ใช่ทรงแคปซูล) — Mosh ระบุว่า badge แบบนี้จะไม่ได้ทำในคลิปนี้ แต่จะเน้นที่ badge ทรงแคปซูลแบบง่ายก่อน

---

## 2. สร้างคลาสหลัก `.badge`

Mosh เริ่มต้นด้วยไฟล์ `styles.css` ที่ว่างเปล่า (cursor พร้อมพิมพ์)

![VS Code styles.css ว่างเปล่าพร้อมพิมพ์](12-Badges/04-vscode-styles-css-empty-cursor.png)

สร้าง selector `.badge` และเริ่มด้วย property แรกคือ `border-radius`

![VS Code แสดง suggestions ของ border-radius](12-Badges/05-vscode-badge-border-radius-suggestions.png)

```css
.badge {
  border-radius: 20px;
}
```

![VS Code แสดง badge border-radius 20px เสร็จสมบูรณ์](12-Badges/06-vscode-badge-border-radius-20px.png)

> ค่า `border-radius: 20px` ที่มากกว่าครึ่งหนึ่งของความสูง element จะทำให้มุมโค้งจนกลายเป็นทรงแคปซูล/พิลล์ (pill shape) แบบเดียวกับที่เห็นในดีไซน์ นี่คือหลักการพื้นฐานในการสร้างรูปทรงแคปซูลด้วย CSS โดยไม่ต้องใช้รูปภาพ

จากนั้นเพิ่ม `padding` เพื่อให้มีระยะห่างระหว่างข้อความกับขอบ

![VS Code แสดง suggestions ของ padding](12-Badges/07-vscode-badge-padding-suggestions.png)

![VS Code แสดง padding 0.5rem กำลังพิมพ์](12-Badges/08-vscode-badge-padding-0-5rem-typing.png)

เพิ่ม `font-weight` เพื่อให้ตัวอักษรหนาขึ้น

![VS Code แสดง suggestions ของ font-weight](12-Badges/09-vscode-badge-font-weight-suggestions.png)

```css
.badge {
  border-radius: 20px;
  padding: 0.5rem 2rem;
  font-weight: bold;
}
```

![VS Code แสดง badge padding 2rem font-weight bold](12-Badges/10-vscode-badge-padding-2rem-font-weight-bold.png)

Mosh เปิด Photoshop เทียบดีไซน์อีกครั้งเพื่อยืนยันสัดส่วน

![Photoshop เทียบ sg pill badge กับ 10 percent off](12-Badges/11-photoshop-sg-pill-10-off-badge-compare.png)

![VS Code แสดง badge โค้ดสมบูรณ์รอบแรก](12-Badges/12-vscode-badge-complete-first-pass.png)

---

## 3. ป้องกันข้อความตัดบรรทัดด้วย `white-space: nowrap`

Mosh เพิ่ม property สุดท้ายในคลาสหลัก `.badge`

![VS Code แสดง suggestions ของ white-space](12-Badges/13-vscode-badge-white-space-suggestions.png)

```css
.badge {
  border-radius: 20px;
  padding: 0.5rem 2rem;
  font-weight: bold;
  white-space: nowrap;
}
```

![VS Code แสดง white-space nowrap เสร็จสมบูรณ์](12-Badges/14-vscode-badge-white-space-nowrap-complete.png)

> **`white-space: nowrap;`** สั่งให้ browser ไม่ตัดขึ้นบรรทัดใหม่แม้ว่าพื้นที่จะแคบลง (ปกติ browser จะ wrap ข้อความอัตโนมัติเมื่อพื้นที่ไม่พอ) ซึ่งสำคัญมากสำหรับ badge เพราะถ้าข้อความ เช่น "10% OFF" ถูกตัดขึ้นบรรทัดใหม่ รูปทรงแคปซูลจะเสียสัดส่วนและดูไม่สวยงาม การใช้ `nowrap` การันตีว่าข้อความจะอยู่ในบรรทัดเดียวเสมอไม่ว่าพื้นที่รอบข้างจะเป็นอย่างไร

![Photoshop เทียบ sg pill badge อีกครั้ง](12-Badges/15-photoshop-sg-pill-badge-compare-2.png)

![VS Code แสดง badge โค้ดเต็มก่อนเพิ่ม modifier](12-Badges/16-vscode-badge-full-code-before-primary.png)

---

## 4. สร้าง Modifier Class ตามหลัก BEM: `.badge--primary`

จุดสำคัญของคลิปนี้คือการแนะนำแนวคิด **BEM (Block Element Modifier)** ซึ่งเป็นวิธีตั้งชื่อคลาส CSS ที่นิยมใช้กันในวงการ โดย Mosh สร้างคลาสใหม่ชื่อ `.badge--primary` (สังเกตเครื่องหมายขีดกลางสองตัวคั่นระหว่างคำว่า "badge" กับ "primary")

![VS Code แสดง suggestions ของ CSS Custom Properties](12-Badges/17-vscode-badge-primary-var-color-suggestions.png)

```css
.badge--primary {
  background: var(--color-primary);
}
```

![VS Code แสดง badge-primary background var เสร็จสมบูรณ์](12-Badges/18-vscode-badge-primary-background-var-complete.png)

จากนั้นเพิ่มสีตัวอักษรเป็นสีขาว

![VS Code แสดง badge-primary color กำลังพิมพ์](12-Badges/19-vscode-badge-primary-color-typing.png)

```css
.badge--primary {
  background: var(--color-primary);
  color: #fff;
}
```

![VS Code แสดง badge-primary color fff เสร็จสมบูรณ์](12-Badges/21-vscode-badge-primary-color-fff-complete.png)

> **หลักการ BEM (Block Element Modifier):** `.badge` คือ **Block** (บล็อกหลักของ component) ส่วน `.badge--primary` คือ **Modifier** (ตัวดัดแปลงที่เปลี่ยนรูปลักษณ์ของ Block โดยไม่เปลี่ยนโครงสร้างพื้นฐาน) การใช้เครื่องหมายขีดกลางสองตัว (`--`) เป็นธรรมเนียมมาตรฐานของ BEM ที่บอกว่านี่คือตัวแปรของ Block เดิม ข้อดีของแนวทางนี้คือทำให้ HTML สามารถประกอบหลายคลาสเข้าด้วยกันได้ เช่น `class="badge badge--primary"` โดย `.badge` จะกำหนดโครงสร้างพื้นฐาน (รูปทรง, padding, font-weight) ในขณะที่ `.badge--primary` จะกำหนดเฉพาะสีที่แตกต่างกันไปตามแต่ละ variant

---

## 5. สร้าง Modifier Class ที่สอง: `.badge--secondary`

![VS Code แสดง badge-secondary selector กำลังพิมพ์](12-Badges/20-vscode-badge-secondary-selector-typing.png)

![VS Code แสดง autocomplete list ของ badge selectors](12-Badges/22-vscode-badge-selector-autocomplete-list.png)

![VS Code แสดง suggestions background สำหรับ badge-secondary](12-Badges/23-vscode-badge-secondary-background-suggestions.png)

![VS Code แสดง suggestions var color สำหรับ secondary](12-Badges/24-vscode-badge-secondary-var-color-suggestions.png)

```css
.badge--secondary {
  background: var(--color-secondary);
}
```

![VS Code แสดง badge-secondary background เสร็จสมบูรณ์](12-Badges/25-vscode-badge-secondary-background-complete.png)

![VS Code แสดง suggestions color fff สำหรับ secondary](12-Badges/26-vscode-badge-secondary-color-fff-suggestions.png)

```css
.badge--secondary {
  background: var(--color-secondary);
  color: #fff;
}
```

![VS Code แสดง badge-secondary โค้ดเสร็จสมบูรณ์](12-Badges/27-vscode-badge-secondary-complete.png)

> `--color-secondary` มีค่าเป็น `#00d9ff` (สีฟ้าอมเขียว/cyan) ซึ่งตรงกับสีของป้ายราคาโดเมน `.sg $7.91` ที่เห็นในดีไซน์ ในขณะที่ `--color-primary` (`#2584ff` สีน้ำเงิน) มักใช้กับปุ่มหรือ badge ที่ต้องการเน้นความสำคัญหลัก

---

## 6. ทดสอบ Badge ใน `index.html`

Mosh สลับไปที่ไฟล์ `index.html` เพื่อสร้าง element ทดสอบ

![VS Code แสดงเมนู switcher สลับไฟล์](12-Badges/28-vscode-file-tab-switcher-popup.png)

![VS Code index.html body ว่างเปล่าพร้อมพิมพ์](12-Badges/29-vscode-index-html-body-empty-cursor.png)

ใช้ Emmet พิมพ์ตัวย่อ `span.badge.bad` เพื่อสร้าง element ที่มีหลายคลาสพร้อมกัน

![VS Code แสดง Emmet span abbreviation กำลังพิมพ์](12-Badges/30-vscode-emmet-span-abbreviation-typing.png)

![VS Code แสดง Emmet span badge badge กำลังพิมพ์ต่อ](12-Badges/31-vscode-emmet-span-badge-badge-typing.png)

```html
<span class="badge badge--primary">1</span>
```

![VS Code แสดง span badge badge-primary ขยายเต็มรูปแบบ](12-Badges/32-vscode-span-badge-badge-primary-expanded.png)

> **Emmet abbreviation สำหรับหลายคลาส:** การพิมพ์ `span.badge.badge--primary` แล้วกด Tab จะขยายเป็น `<span class="badge badge--primary"></span>` โดยอัตโนมัติ — จุดที่ (`.`) แต่ละจุดหมายถึงคลาสเพิ่มเติมหนึ่งตัว นี่คือความสามารถของ Emmet ที่ช่วยให้สร้าง HTML element ที่มีหลายคลาสได้รวดเร็วโดยไม่ต้องพิมพ์ `class="..."` ด้วยมือ

Mosh แก้ไขข้อความด้านในจาก "1" เป็น "10% Off" แล้วทดสอบใน browser

![Browser แสดง 10 percent off แบบยังไม่มีสไตล์](12-Badges/33-browser-10-percent-off-unstyled.png)

> ที่จุดนี้ text ยังไม่มีสไตล์เพราะไฟล์ `styles.css` ยังไม่ได้ถูก link เข้ากับ `index.html` — Mosh อธิบายว่าต้องแน่ใจว่ามี `<link rel="stylesheet" href="css/styles.css" />` อยู่ใน `<head>` ก่อน

---

## 7. ทดสอบ Badge Primary และ Secondary ใน Browser

![VS Code แสดง badge-secondary recap](12-Badges/34-vscode-badge-secondary-recap.png)

![Browser แสดง 10 percent off badge สีน้ำเงิน primary](12-Badges/35-browser-10-percent-off-badge-primary-blue.png)

> ผลลัพธ์ badge สีน้ำเงิน (`.badge--primary`) ปรากฏเป็นทรงแคปซูลตามที่ตั้งใจไว้ — ตัวอักษรสีขาว พื้นหลังสีน้ำเงิน ขอบโค้งมนสวยงาม

---

## 8. ตรวจสอบฟอนต์ด้วย DevTools Network Tab

Mosh เปิด Chrome DevTools เพื่อตรวจสอบ DOM และดูว่า class ถูกใส่ถูกต้องหรือไม่

![DevTools Elements แสดง badge-secondary ใน DOM](12-Badges/36-vscode-devtools-elements-badge-secondary-dom.png)

จากนั้นสลับไปที่แท็บ **Network** เพื่อดูการโหลดไฟล์ฟอนต์

![DevTools Network tab กำลังบันทึกการทำงาน](12-Badges/37-devtools-network-tab-recording.png)

![DevTools Network แสดง font woff2 request](12-Badges/38-devtools-network-font-woff2-request.png)

![DevTools Network แสดง font request URL](12-Badges/39-devtools-network-font-headers-request-url.png)

> **Network tab** ใน DevTools แสดงรายการไฟล์ทั้งหมดที่ browser ดาวน์โหลดมาเมื่อโหลดหน้าเว็บ Mosh กรองด้วยปุ่ม **Font** เพื่อดูเฉพาะไฟล์ฟอนต์ที่ถูกดาวน์โหลด พบว่ามีเพียงไฟล์ `.woff2` ไฟล์เดียวถูกโหลดมาจาก Google Fonts (`fonts.gstatic.com`) ซึ่งหมายความว่ามีเพียงน้ำหนักฟอนต์เดียวเท่านั้นที่ถูกดาวน์โหลด (ปกติจะเป็นน้ำหนัก 400 = regular และ 700 = bold ตามที่ระบุไว้ใน URL ของ Google Fonts)

---

## 9. แก้ไข Google Fonts URL เพื่อเพิ่มน้ำหนักฟอนต์ใหม่

Mosh เทียบกับ Photoshop อีกครั้งเพื่อดูน้ำหนักตัวอักษรของ badge

![Photoshop เทียบ sg pill badge อีกครั้ง](12-Badges/40-photoshop-sg-pill-badge-compare-3.png)

จากนั้นเปิดไฟล์ `index.html` ไปที่ `<link>` ของ Google Fonts เพื่อตรวจสอบ URL ปัจจุบัน

![VS Code แสดง Google Fonts link wght 400 700](12-Badges/41-vscode-google-fonts-link-wght-400-700.png)

![VS Code แสดง Google Fonts link เลื่อนดู](12-Badges/42-vscode-google-fonts-link-scrolled.png)

Mosh เปิดแท็บใหม่ไปที่เว็บไซต์ Google Fonts เพื่อดูข้อมูลเกี่ยวกับฟอนต์ Inter

![Chrome แสดงหน้า Google Fonts Inter About tab](12-Badges/43-chrome-google-fonts-inter-about-tab.png)

จากนั้นแก้ไข URL ใน `<link>` โดยเพิ่มน้ำหนัก **600** เข้าไปในรายการ (เดิมมีแค่ `400;700`)

```html
<link
  href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap"
  rel="stylesheet"
/>
```

![VS Code แสดง Google Fonts link wght 400 600 700](12-Badges/44-vscode-google-fonts-link-wght-400-600-700.png)

กลับไปที่ DevTools Network tab เพื่อยืนยันว่าไฟล์ฟอนต์ใหม่ถูกโหลดมาแล้ว

![DevTools Network แสดง font request URL อัปเดตแล้ว](12-Badges/45-devtools-network-font-request-url-updated.png)

![Chrome Google Fonts Inter About page เต็มหน้า](12-Badges/46-chrome-google-fonts-inter-about-page.png)

> **wght@400;600;700** ใน URL ของ Google Fonts คือรายการน้ำหนักตัวอักษร (font weights) ที่ต้องการดาวน์โหลด โดย 400 คือ Regular, 600 คือ Semi-Bold, และ 700 คือ Bold — การเพิ่ม 600 เข้าไปทำให้ browser ดาวน์โหลดไฟล์ฟอนต์เพิ่มอีกหนึ่งไฟล์ ซึ่งจำเป็นเพราะ Mosh ต้องการใช้น้ำหนัก 600 (Semi-Bold) กับ badge แทนที่จะเป็น `bold` (700) เพื่อให้ตรงกับความหนาของตัวอักษรในดีไซน์มากกว่า — นี่คือบทเรียนสำคัญว่าถ้าเราต้องการใช้ font-weight ที่ไม่ได้อยู่ในรายการที่ import มา browser จะ "ปลอมความหนา" ด้วยเทคนิค synthetic bold ซึ่งดูไม่สวยงามเท่าไฟล์ฟอนต์จริงของน้ำหนักนั้น

---

## 10. เปลี่ยน font-weight จาก `bold` เป็น `600`

![VS Code แสดง badge font-weight 600 กำลังพิมพ์](12-Badges/47-vscode-badge-font-weight-600-typing.png)

```css
.badge {
  border-radius: 20px;
  padding: 0.5rem 2rem;
  font-weight: 600;
  white-space: nowrap;
}
```

![Browser แสดง 10 percent off badge secondary น้ำหนัก 600](12-Badges/48-browser-10-percent-off-badge-secondary-600.png)

![Photoshop เทียบ sg pill badge ครั้งที่สี่](12-Badges/49-photoshop-sg-pill-badge-compare-4.png)

> การเปลี่ยนจากคีย์เวิร์ด `bold` (ซึ่งเท่ากับ 700 เสมอ) มาเป็นตัวเลขที่ชัดเจน `600` ทำให้เราสามารถควบคุมน้ำหนักตัวอักษรได้ละเอียดขึ้น และตรงกับดีไซน์มากกว่า

---

## 11. เพิ่ม `font-size` และเรียงลำดับ Properties ด้วย Command Palette

Mosh เพิ่ม property สุดท้ายในคลาส `.badge`

![VS Code แสดง badge font-size 2rem กำลังพิมพ์](12-Badges/50-vscode-badge-font-size-2rem-typing.png)

จากนั้นสาธิตเทคนิคที่มีประโยชน์มากคือการเรียงลำดับ properties ตามตัวอักษรโดยใช้ **Command Palette** ของ VS Code (เปิดด้วย `Cmd+Shift+P` แล้วพิมพ์ `>` ตามด้วยคำสั่ง)

![VS Code Command Palette พิมพ์ sort ค้นหาคำสั่ง](12-Badges/51-vscode-command-palette-sort-search.png)

![VS Code Command Palette แสดง Sort Lines Ascending](12-Badges/52-vscode-command-palette-sort-lines-ascending.png)

หลังจากเลือกทุกบรรทัดภายใน `.badge { }` แล้วรันคำสั่ง **Sort Lines Ascending** ผลลัพธ์คือ properties ถูกเรียงตามตัวอักษร A-Z โดยอัตโนมัติ

```css
.badge {
  border-radius: 20px;
  font-size: 2rem;
  font-weight: 600;
  padding: 0.5rem 2rem;
  white-space: nowrap;
}
```

![VS Code แสดง badge properties เรียงตามตัวอักษรแล้ว](12-Badges/53-vscode-badge-properties-sorted-alphabetically.png)

> **เทคนิค "Sort Lines Ascending":** นี่คือฟีเจอร์ในตัวของ VS Code ที่ช่วยเรียงลำดับบรรทัดโค้ดตามตัวอักษรโดยอัตโนมัติ ใช้งานได้โดยการเลือก (select) บรรทัดที่ต้องการเรียง แล้วเปิด Command Palette (`Cmd+Shift+P` บน Mac หรือ `Ctrl+Shift+P` บน Windows) พิมพ์ "sort" แล้วเลือก "Sort Lines Ascending" ประโยชน์ของการเรียง CSS properties ตามตัวอักษรคือทำให้โค้ดอ่านง่ายขึ้นและหาค่าที่ต้องการแก้ไขได้เร็วขึ้น เพราะทุกคนในทีมจะรู้ว่า property ที่ขึ้นต้นด้วยตัวอักษรใดจะอยู่ตรงไหนในบล็อก นี่เป็นแนวทางปฏิบัติที่ดีในการดูแลรักษาโค้ด CSS ขนาดใหญ่

![Browser แสดง 10 percent off badge primary สุดท้าย](12-Badges/54-browser-10-percent-off-final-badge-primary.png)

![VS Code แสดง badge-secondary selector recap](12-Badges/55-vscode-badge-secondary-selector-recap.png)

![Browser แสดง 10 percent off badge สีฟ้าอมเขียว secondary](12-Badges/56-browser-10-percent-off-cyan-secondary.png)

---

## 12. สร้าง Modifier Class ที่สาม: `.badge--small`

Mosh สร้างคลาสดัดแปลงตัวที่สามสำหรับปรับขนาดของ badge ให้เล็กลง

![VS Code แสดง badge-small selector กำลังพิมพ์](12-Badges/57-vscode-badge-small-selector-typing.png)

![VS Code แสดง autocomplete suggestions ของ badge selector](12-Badges/58-vscode-badge-selector-autocomplete-small.png)

![VS Code แสดง badge-small block ว่างเปล่าที่สร้างแล้ว](12-Badges/59-vscode-badge-small-empty-block-created.png)

---

## 13. ทดสอบ Badge Small ใน `index.html`

Mosh กลับไปที่ `index.html` เพื่อเพิ่มคลาส `badge--small` เข้าไปทดสอบ

![VS Code index.html span badge secondary recap](12-Badges/60-vscode-index-html-span-secondary-recap.png)

![VS Code index.html badge-small class กำลังพิมพ์](12-Badges/61-vscode-index-html-badge-small-class-typing.png)

```html
<span class="badge badge--secondary badge--small">10% Off</span>
```

![VS Code index.html badge-small class เพิ่มเสร็จแล้ว](12-Badges/62-vscode-index-html-badge-small-added.png)

ทดสอบผลลัพธ์ใน browser (แต่ CSS ของ `.badge--small` ยังว่างเปล่าอยู่ ณ จุดนี้)

![Browser แสดง 10 percent off cyan ก่อนมี CSS small](12-Badges/63-browser-10-percent-off-cyan-before-small-css.png)

> ที่จุดนี้ badge ยังคงมีขนาดเท่าเดิม เพราะ `.badge--small { }` ยังไม่มี property ใดๆ อยู่ภายใน — นี่คือขั้นตอนการทดสอบก่อนที่จะเติมโค้ดจริงลงไป ซึ่งเป็นแนวทางที่ดีในการพัฒนาแบบค่อยเป็นค่อยไป (incremental development)

Mosh เปลี่ยนคลาสเป็น `badge--primary` เพื่อทดสอบร่วมกับสีอื่น

![VS Code index.html badge-small recap](12-Badges/64-vscode-index-html-badge-small-recap.png)

![Browser แสดง 10 percent off สีน้ำเงิน primary small](12-Badges/65-browser-10-percent-off-blue-primary-small.png)

![VS Code index.html badge-primary-small class](12-Badges/66-vscode-index-html-badge-primary-small-class.png)

---

## 14. เพิ่มโค้ด `font-size` ให้ `.badge--small`

```css
.badge--small {
  font-size: 1.6rem;
}
```

![Browser แสดง 10 percent off primary small ขนาดเล็กลง](12-Badges/67-browser-10-percent-off-primary-small-smaller.png)

![VS Code แสดง badge-small font-size 1.6rem](12-Badges/68-vscode-badge-small-font-size-1-6rem.png)

> ขนาดตัวอักษรของ badge ลดลงจาก `2rem` (ค่าเริ่มต้นใน `.badge`) เหลือ `1.6rem` เมื่อมีคลาส `.badge--small` กำกับอยู่ด้วย — นี่คือหลักการสำคัญของ CSS Modifier: `.badge--small` **ไม่ได้แทนที่** style ของ `.badge` ทั้งหมด แต่เพียง **override** เฉพาะ property ที่ระบุไว้เท่านั้น (ในที่นี้คือ font-size) ส่วน property อื่นๆ เช่น border-radius, padding, font-weight ยังคงมาจาก `.badge` เหมือนเดิม

---

## 15. เพิ่ม Responsive Style สำหรับจอใหญ่

Mosh เพิ่มขนาด badge สำหรับหน้าจอขนาดใหญ่ในไฟล์ media query ที่มีอยู่แล้ว

![VS Code media query badge selector กำลังพิมพ์](12-Badges/69-vscode-media-query-badge-selector-typing.png)

![VS Code media query font-size suggestions](12-Badges/70-vscode-media-query-font-size-suggestions.png)

```css
@media screen and (min-width: 1024px) {
  .badge {
    font-size: 1.5rem;
  }
}
```

![VS Code media query badge font-size 1.5rem](12-Badges/71-vscode-media-query-badge-font-size-1-5rem.png)

![VS Code media query badge selector autocomplete list](12-Badges/72-vscode-media-query-badge-selector-list.png)

จากนั้นเพิ่ม `.badge--small` เข้าไปใน media query เดียวกัน

![VS Code media query badge-small block ว่างเปล่า](12-Badges/73-vscode-media-query-badge-small-empty.png)

![VS Code media query badge-small font-size suggestions](12-Badges/74-vscode-media-query-badge-small-font-size-suggestions.png)

![VS Code media query font-size Emmet suggestions](12-Badges/75-vscode-media-query-font-size-emmet-suggestions.png)

```css
@media screen and (min-width: 1024px) {
  .badge {
    font-size: 1.5rem;
  }

  .badge--small {
    font-size: 1.2rem;
  }
}
```

![VS Code media query badge-small 1.2rem เสร็จสมบูรณ์](12-Badges/76-vscode-media-query-badge-small-1-2rem-complete.png)

> เช่นเดียวกับคลิปก่อนหน้า (Links) Mosh เลือกเพิ่มโค้ดลงใน media query ที่มีอยู่แล้ว (breakpoint 1024px) แทนการสร้าง media query ใหม่ ซึ่งเป็นแนวทางปฏิบัติที่ดีในการดูแลรักษาโค้ด CSS ให้เป็นระเบียบ

ทดสอบผลลัพธ์สุดท้ายใน browser

![Browser แสดง 10 percent off final large view](12-Badges/77-browser-10-percent-off-final-large-view.png)

---

## 16. ขยาย Component Library ด้วย `components/badges.html`

Mosh กลับไปที่ `index.html` เพื่อดูโค้ดสุดท้าย

![VS Code index.html span badge-primary recap](12-Badges/78-vscode-index-html-span-badge-primary-recap.png)

![VS Code index.html final recap เต็มไฟล์](12-Badges/79-vscode-index-html-final-recap.png)

จากนั้นกลับไปที่โฟลเดอร์ `components` ที่สร้างไว้ในคลิปก่อนหน้า (Links)

![VS Code Explorer components folder recap](12-Badges/80-vscode-explorer-components-folder-recap.png)

![VS Code Explorer เมนู New File](12-Badges/81-vscode-explorer-new-file-context-menu.png)

สร้างไฟล์ใหม่ชื่อ `badges.html`

![VS Code Explorer ตั้งชื่อไฟล์ badges.html](12-Badges/82-vscode-explorer-badges-html-naming.png)

![VS Code badges.html วางบรรทัด badge แรก](12-Badges/83-vscode-badges-html-pasted-badge-line.png)

จากนั้น Mosh คัดลอกบรรทัด `<span>` ซ้ำสามครั้งเพื่อแสดงตัวอย่าง badge ทั้งสามรูปแบบไว้ในไฟล์เดียวกัน (สำหรับใช้ตรวจสอบภาพรวมของ component นี้ในอนาคต)

```html
<span class="badge badge--primary">10% Off</span>
<span class="badge badge--primary">10% Off</span>
<span class="badge badge--primary">10% Off</span>
```

![VS Code badges.html สามบรรทัดตัวอย่าง](12-Badges/84-vscode-badges-html-three-example-lines.png)

> การเก็บตัวอย่าง component หลายรูปแบบไว้ในไฟล์เดียว (`components/badges.html`) ช่วยให้สามารถกลับมาดูภาพรวมของ component "Badge" ทั้งหมดได้ในที่เดียว โดยไม่ต้องเปิดหน้าเว็บจริงทั้งหน้า ซึ่งเป็นประโยชน์อย่างมากเมื่อโปรเจกต์มีขนาดใหญ่ขึ้นและมี component จำนวนมาก

---

## สรุปภาพรวมของคลิปนี้

| หัวข้อ | รายละเอียด |
|---|---|
| Block class | `.badge` (border-radius, padding, font-weight, white-space, font-size) |
| Modifier 1 | `.badge--primary` (background: var(--color-primary), color: #fff) |
| Modifier 2 | `.badge--secondary` (background: var(--color-secondary), color: #fff) |
| Modifier 3 | `.badge--small` (font-size: 1.6rem, ลดเหลือ 1.2rem บนจอใหญ่) |
| Font-weight | เปลี่ยนจาก `bold` (700) เป็น `600` (Semi-Bold) ให้ตรงดีไซน์ |
| Google Fonts URL | เพิ่มน้ำหนัก 600: `wght@400;600;700` |
| DevTools | ใช้ Network tab กรองด้วย Font เพื่อตรวจสอบไฟล์ฟอนต์ที่โหลดมา |
| VS Code เทคนิค | Command Palette → "Sort Lines Ascending" เรียง properties ตามตัวอักษร |
| Responsive | เพิ่ม `.badge` และ `.badge--small` ใน media query 1024px เดิม |
| ไฟล์ใหม่ | `components/badges.html` (ตัวอย่าง badge 3 แบบ) |

### แนวคิดสำคัญที่ได้จากคลิปนี้

1. **หลักการ BEM (Block Element Modifier)** คือแนวทางการตั้งชื่อคลาส CSS ที่แยก Block หลัก (`.badge`) ออกจาก Modifier (`.badge--primary`, `.badge--secondary`, `.badge--small`) ด้วยเครื่องหมายขีดกลางสองตัว ทำให้ HTML สามารถประกอบหลายคลาสเข้าด้วยกันเพื่อสร้าง variant ที่หลากหลายได้โดยไม่ต้องเขียน CSS ซ้ำซ้อน
2. **DevTools Network tab** เป็นเครื่องมือสำคัญในการตรวจสอบว่าไฟล์ฟอนต์ที่ต้องการถูกดาวน์โหลดมาจริงหรือไม่ โดยเฉพาะเมื่อใช้ font-weight ที่ไม่ตรงกับที่ import ไว้ ซึ่งอาจทำให้ browser ใช้เทคนิค synthetic bold แทนไฟล์ฟอนต์จริง
3. **Google Fonts URL** สามารถแก้ไขเพื่อเพิ่มน้ำหนักฟอนต์ (font weight) ใหม่ได้โดยการเพิ่มตัวเลขในพารามิเตอร์ `wght@` คั่นด้วยเครื่องหมายเซมิโคลอน
4. **`white-space: nowrap`** เป็นเทคนิคสำคัญสำหรับ component ที่มีรูปทรงคงที่ (เช่น badge ทรงแคปซูล) เพื่อป้องกันไม่ให้ข้อความตัดขึ้นบรรทัดใหม่และทำให้รูปทรงเสียสัดส่วน
5. **VS Code Command Palette → Sort Lines Ascending** เป็นเทคนิคที่ช่วยจัดระเบียบ CSS properties ให้อยู่ในลำดับตัวอักษร ทำให้โค้ดอ่านง่ายและดูแลรักษาง่ายขึ้นในระยะยาว
6. **CSS Modifier ทำงานแบบ override เฉพาะจุด** ไม่ใช่แทนที่ style ทั้งหมด — element ที่มีทั้ง `.badge` และ `.badge--small` จะได้รับ property ทั้งหมดจาก `.badge` ยกเว้น `font-size` ที่ถูก `.badge--small` override

---

*สรุปจากคลิปที่ 12 ของคอร์ส "Building a Web Site" (Moshify Project) สอนโดย Mosh Hamedani, codewithmosh.com*
