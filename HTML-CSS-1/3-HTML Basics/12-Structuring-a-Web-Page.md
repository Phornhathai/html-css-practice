# 3-HTML Basics: 12 - Structuring a Web Page (3:23)

**ไฟล์ต้นทาง:** `12-Structuring-a-Web-Page.mp4`

▶️ **[เปิดวิดีโอต้นฉบับ](../../../HTML-CSS-1/3-HTML%20Basics/12-Structuring-a-Web-Page.mp4)**

---

## ภาพรวมคลิปนี้

คลิปสุดท้ายของบท HTML Basics นี้ Mosh สรุปรวบยอด (capstone) โดยนำ **semantic element ระดับโครงสร้างหน้าเว็บ** ทั้งหมดมาประกอบกันเป็นโครงหน้าเว็บสมบูรณ์แบบหนึ่งหน้า ได้แก่ `<header>`, `<nav>`, `<main>`, `<section>`, `<aside>`, และ `<footer>` — เป็นภาพรวมว่าหน้าเว็บทั่วไปหนึ่งหน้าจะถูกแบ่งโครงสร้างอย่างไรด้วย semantic HTML ล้วนๆ โดยยังไม่ใส่เนื้อหาจริงหรือ CSS

---

## 1. โครงสร้างระดับบนสุด: `header`, `main`, `aside`, `footer`

Mosh เริ่มพิมพ์แท็กโครงสร้างหลักของหน้าเว็บทีละตัวด้วย Emmet:

```html
<body>
  <header></header>
  <main></main>
  <aside></aside>
  <footer></footer>
</body>
```

![โค้ดกำลังพิมพ์ footer ด้วย Emmet autocomplete](images/12-Structuring-a-Web-Page/01-code-header-main-typing-footer.png)

![โค้ดครบทั้ง header main aside footer](images/12-Structuring-a-Web-Page/02-code-header-main-aside-footer.png)

> **ความหมายของแต่ละแท็ก:**
> - **`<header>`** — ส่วนหัวของหน้าเว็บ (หรือของ section/article หนึ่งๆ) มักมีโลโก้ เมนูนำทาง
> - **`<main>`** — เนื้อหาหลักของหน้า มีได้เพียงแท็กเดียวต่อหนึ่งหน้าเว็บ
> - **`<aside>`** — เนื้อหาข้างเคียงที่เกี่ยวข้องแต่ไม่ใช่เนื้อหาหลัก เช่น sidebar, โฆษณา, ลิงก์ที่เกี่ยวข้อง
> - **`<footer>`** — ส่วนท้ายของหน้าเว็บ มักมีลิงก์ติดต่อ, ลิขสิทธิ์, โซเชียลมีเดีย

---

## 2. เมนูนำทางใน `<header>`: `<nav>` + `<ul>` + `<li>`

Mosh เพิ่มเมนูนำทางภายใน `<header>` โดยใช้ `<nav>` ครอบ `<ul>`:

```html
<header>
  <nav>
    <ul>
      <li></li>
      <li></li>
      <li></li>
    </ul>
  </nav>
</header>
```

![โค้ด nav ครอบ ul ภายใน header](images/12-Structuring-a-Web-Page/03-code-nav-ul-inside-header.png)

![โค้ดเพิ่ม li สามรายการในเมนู](images/12-Structuring-a-Web-Page/04-code-li-items-in-nav.png)

> **`<nav>` คืออะไร:** ครอบกลุ่มลิงก์นำทางหลักของเว็บไซต์หรือของหน้า (main navigation) — ใช้ได้ทั้งใน `<header>` และ `<footer>` (เช่น footer navigation สำหรับลิงก์ Privacy Policy, Terms of Service)

---

## 3. เนื้อหาหลักใน `<main>`: แบ่งด้วย `<section>` และ `<article>`

Mosh เพิ่ม 2 ส่วนย่อยภายใน `<main>` โดยใช้ `<section>` แบ่งเนื้อหาแต่ละหัวข้อ:

```html
<main>
  <section></section>
  <section></section>
</main>
```

![โค้ด main มี section สองอัน](images/12-Structuring-a-Web-Page/06-code-two-section-in-main.png)

### Section แรก: "Products"

```html
<section>
  <h2>Products</h2>
  <article></article>
  <article></article>
  <article></article>
</section>
```

![โค้ด h2 Products และเริ่มพิมพ์ article ด้วย Emmet](images/12-Structuring-a-Web-Page/07-code-h2-products-article-emmet.png)

![โค้ด section Products มี article สามชิ้น](images/12-Structuring-a-Web-Page/11-code-three-article-products.png)

### Section ที่สอง: "Testimonial"

```html
<section>
  <h2>Testimonial</h2>
  <article></article>
  <article></article>
</section>
```

![โค้ด h2 Testimonial และเริ่มพิมพ์ article](images/12-Structuring-a-Web-Page/09-code-h2-testimonial-article.png)

![โค้ด section Testimonial มี article สองชิ้น](images/12-Structuring-a-Web-Page/10-code-two-article-testimonial.png)

> **`<section>` vs `<article>`:**
> - **`<section>`** — จัดกลุ่มเนื้อหาที่เกี่ยวข้องกันภายใต้**หัวข้อเดียวกัน** (มักมี heading กำกับ เช่น "Products", "Testimonial") ใช้แบ่งหน้าเว็บออกเป็นหมวดหมู่ตามธีม
> - **`<article>`** — เนื้อหาที่**เป็นอิสระสมบูรณ์ในตัวเอง** (ตามที่เรียนในคลิปก่อนหน้า) เช่น สินค้าแต่ละชิ้นใน "Products" หรือรีวิวแต่ละอันใน "Testimonial" — สังเกตว่า `<article>` มักถูกวางซ้อนอยู่ภายใน `<section>` เพราะเนื้อหาแต่ละชิ้นเป็นส่วนหนึ่งของหมวดหมู่นั้น

---

## 4. ภาพรวมโครงสร้างหน้าเว็บที่สมบูรณ์

โค้ดสุดท้ายของทั้งหน้า:

```html
<body>
  <header>
    <nav>
      <ul>
        <li></li>
        <li></li>
        <li></li>
      </ul>
    </nav>
  </header>
  <main>
    <section>
      <h2>Products</h2>
      <article></article>
      <article></article>
      <article></article>
    </section>
    <section>
      <h2>Testimonial</h2>
      <article></article>
      <article></article>
    </section>
  </main>
  <aside></aside>
  <footer>
    <nav>
      <ul></ul>
    </nav>
  </footer>
</body>
```

![โค้ดแสดงภาพรวม header nav ul และ main section](images/12-Structuring-a-Web-Page/12-code-full-header-nav-overview.png)

Mosh ปิดท้ายด้วยสไลด์เน้นย้ำแท็ก `<main>` เป็นแกนกลางของโครงสร้าง:

![สไลด์ main กำลัง fade in](images/12-Structuring-a-Web-Page/13-slide-main-fading-summary.png)

> **ข้อควรระวัง:** `<main>` ใช้ได้เพียง**หนึ่งครั้งต่อหนึ่งหน้าเว็บ**เท่านั้น (ไม่เหมือน `<section>`/`<article>` ที่ใช้ซ้ำได้หลายครั้ง) เพราะเป็นตัวบ่งชี้เนื้อหาหลักที่ไม่ซ้ำกันของหน้านั้นให้กับ screen reader และ search engine

---

## สรุปที่ใช้ได้จริง

- โครงสร้างหน้าเว็บมาตรฐานด้วย semantic HTML: `<header>` → `<main>` (มี `<section>`/`<article>` ข้างใน) → `<aside>` → `<footer>`
- `<nav>` ใช้ได้ทั้งใน `<header>` (เมนูหลัก) และ `<footer>` (เมนูท้ายเว็บ)
- `<section>` แบ่งเนื้อหาตามหัวข้อ/ธีม ส่วน `<article>` คือเนื้อหาย่อยที่สมบูรณ์ในตัวเองภายใน section นั้น
- `<main>` ใช้ได้แค่ 1 ครั้งต่อหน้า ส่วนแท็กอื่นๆ ใช้ซ้ำได้ตามต้องการ
- โครงสร้างนี้เป็น**พิมพ์เขียว (blueprint)** มาตรฐานที่ใช้ได้กับเว็บไซต์เกือบทุกประเภท ตั้งแต่ landing page ธรรมดาไปจนถึงเว็บแอปพลิเคชันเต็มรูปแบบ

### จุดเชื่อมกับงานจริงของ Aum

- โครงสร้างนี้คือแม่แบบเดียวกับที่ใช้ทำ `layout.tsx` (Root Layout) ใน Next.js App Router — โดยทั่วไปจะมี `<Header />`, `{children}` อยู่ใน `<main>`, และ `<Footer />` เป็น component แยกกัน
- แต่ละ `<section>` ใน landing page (เช่น Hero, Features, Testimonials, Pricing, CTA) สามารถแยกเป็น React component ของตัวเองได้ตรงตามโครงสร้าง semantic นี้เป๊ะๆ
- การวางแผนโครงสร้างหน้าเว็บด้วย semantic tag ก่อนเริ่มเขียน component ช่วยให้ code base เป็นระเบียบ อ่านง่าย และ SEO/accessibility ดีตั้งแต่ต้น — เป็นขั้นตอนที่ควรทำก่อนลงมือจัด layout ด้วย Tailwind flex/grid เสมอ
- เมื่อ Aum เริ่มทำโปรเจกต์ full-stack ที่ใช้ JSON server ควรวางโครง `<main><section>` ให้สอดคล้องกับ endpoint ของข้อมูล เช่น section "Products" ดึงจาก `/products`, section "Testimonial" ดึงจาก `/testimonials` เพื่อให้โครงสร้าง HTML และโครงสร้างข้อมูลสอดคล้องกัน
