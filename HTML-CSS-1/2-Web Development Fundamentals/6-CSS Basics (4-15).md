# 6-CSS Basics (4:15)

**ไฟล์ต้นทาง:** `Web Development Fundamentals/6-CSS Basics (4-15).mp4`

▶️ **[เปิดวิดีโอต้นฉบับ](../../Web%20Development%20Fundamentals/6-CSS%20Basics%20%284-15%29.mp4)**

> คลิปนี้คือภาคต่อของคลิป "HTML Basics" — Mosh ใช้ไฟล์ `index.html` เดิมที่เขียนไว้ (รูป + 2 ย่อหน้า) แล้วเริ่มเพิ่ม **CSS** เข้าไปทีละ property เพื่อจัดหน้าตาให้สวยขึ้น ทำละเอียดที่สุด เก็บทุกบรรทัด CSS ที่พิมพ์และผลลัพธ์ในเบราว์เซอร์ทุกจังหวะที่เปลี่ยน

## 1) เปิดคลิป

![Title](images/6-CSS%20Basics/01-title.png)

Title slide: **"CSS Basics"** — Mosh Hamedani, codewithmosh.com

## 2) จุดเริ่มต้น — ไฟล์ HTML เดิมจากคลิปที่แล้ว

![Starting HTML](images/6-CSS%20Basics/02-starting-html-from-clip5.png)

Mosh เปิดไฟล์ `index.html` ที่เขียนไว้ตอนจบคลิป "HTML Basics" ขึ้นมาต่อ:
```html
<!DOCTYPE html>
<html>
    <head>
        <title>My first web page</title>
    </head>
    <body>
        <img src="images/mosh.jpg">
        <p>@moshhamedani</p>
        <p>I love to teach you HTML!</p>
    </body>
</html>
```

## 3) เพิ่มแท็บ `<style>` ในส่วน `<head>`

![Style tag added](images/6-CSS%20Basics/03-style-tag-added.png)

Mosh เพิ่มแท็บ **`<style></style>`** เข้าไปใน `<head>` ต่อจาก `<title>`:
```html
<head>
    <title>My first web page</title>
    <style>

    </style>
</head>
```
*(จุดสำคัญ: นี่คือวิธีเขียน CSS แบบ **internal stylesheet** — เขียน CSS ปนอยู่ในไฟล์ HTML เอง ผ่านแท็บ `<style>` ต่างจาก external stylesheet ที่แยกเป็นไฟล์ `.css` ต่างหาก)*

![Browser starting point](images/6-CSS%20Basics/04-browser-starting-point.png)

หน้าเว็บใน Chrome ที่ `127.0.0.1:5500/index.html` ยังหน้าตาเหมือนคลิปที่แล้ว: รูป Mosh ขนาดเต็ม (ไม่มี CSS จัดสไตล์) ตามด้วยข้อความ 2 บรรทัด

## 4) เริ่มเขียน CSS Selector ตัวแรก: `img`

![img selector empty braces](images/6-CSS%20Basics/05-img-selector-empty-braces.png)

ในแท็บ `<style>` Mosh พิมพ์ **`img`** ตามด้วยปีกกาเปิด-ปิด `{ }`:
```css
img {

}
```
- **`img`** ตรงนี้คือ **CSS Selector แบบ element/tag selector** — บอกว่า "กฎ CSS นี้จะไปใช้กับทุกแท็บ `<img>` ในหน้าเว็บ"

![Browser still unchanged](images/6-CSS%20Basics/06-browser-still-unchanged.png)

หน้าเว็บยังไม่เปลี่ยนแปลง เพราะข้างใน `{ }` ยังว่างเปล่า ไม่มี property ใดๆ

## 5) Property แรก: `width`

![Width 100px property](images/6-CSS%20Basics/07-width-100px-property.png)

Mosh พิมพ์ property แรกเข้าไปใน `img { }`:
```css
img {
    width: 100px;
}
```
- **`width: 100px;`** = กำหนดความกว้างของรูปให้เป็น 100 พิกเซลตายตัว (ย่อรูปให้เล็กลงจากขนาดเต็ม)

## 6) Property ที่สอง: `border-radius`

![border-radius autocomplete](images/6-CSS%20Basics/08-border-radius-autocomplete.png)

พิมพ์ **`border-ra`** → VS Code เด้ง IntelliSense autocomplete ของ CSS property ขึ้นมา แสดง **`border-radius`** เป็นตัวเลือกแรก พร้อมคำอธิบายกำกับด้านขวา: *"Defines the radii of the outer border edge."* พร้อม syntax `<length-percentage>{1,4}[...]`

![border-radius 10 typing](images/6-CSS%20Basics/09-border-radius-10-typing.png)

พิมพ์ค่าต่อ: `border-radius: 10` (ยังไม่ใส่หน่วย)

![border-radius 10px value](images/6-CSS%20Basics/10-border-radius-10px-value.png)

ใส่หน่วยครบ:
```css
img {
    width: 100px;
    border-radius: 10px;
}
```

![Browser rounded corners 10px](images/6-CSS%20Basics/11-browser-rounded-corners-10px.png)

**Live Server reload อัตโนมัติ** — หน้าเว็บอัปเดตทันที: รูปเล็กลงเหลือ 100px และมุมโค้งมนเล็กน้อย (10px)

## 7) ปรับ `border-radius` เป็น 50px → กลายเป็นวงกลม

![border-radius 10px saved](images/6-CSS%20Basics/12-border-radius-10px-saved.png)

ยืนยันโค้ดปัจจุบัน (`border-radius: 10px;` เซฟแล้ว)

![Browser slightly rounder](images/6-CSS%20Basics/13-browser-slightly-rounder.png)

หน้าเว็บกับรูปมุมโค้ง 10px, ข้อความ 2 บรรทัดอยู่ด้านล่าง (ยังไม่ได้จัดให้อยู่ข้างๆ กัน)

![border-radius 50px circle](images/6-CSS%20Basics/14-border-radius-50px-circle.png)

Mosh แก้ค่าเป็น **`border-radius: 50px;`**:
```css
img {
    width: 100px;
    border-radius: 50px;
}
```

![Browser circle image](images/6-CSS%20Basics/15-browser-circle-image.png)

ผลลัพธ์: รูปกลายเป็น**วงกลมสมบูรณ์** — เพราะ 50px คือครึ่งหนึ่งของ 100px (ความกว้าง/สูงของรูป) พอดี ทำให้มุมโค้งจนกลมเต็มวง (หลักการ: ถ้าอยากได้วงกลมสมบูรณ์ ให้ตั้ง border-radius เป็นครึ่งหนึ่งของขนาดรูป หรือใช้ 50% ก็ได้ผลเหมือนกัน)

## 8) จัดตำแหน่งด้วย `float` และ `margin`

![float left typing](images/6-CSS%20Basics/16-float-left-typing.png)

พิมพ์ property ต่อ: **`float: left;`**

![float left value](images/6-CSS%20Basics/17-float-left-value.png)

```css
img {
    width: 100px;
    border-radius: 50px;
    float: left;
}
```
- **`float: left;`** = ดึงรูปให้ลอยไปชิดซ้าย แล้วให้เนื้อหาอื่น (ข้อความ `<p>`) ไหลขึ้นมาอยู่ข้างๆ รูปแทนที่จะตกลงไปด้านล่าง

![margin-right autocomplete](images/6-CSS%20Basics/18-margin-right-autocomplete.png)

พิมพ์ **`margin-ri`** → IntelliSense เด้ง `margin-right` เป็นตัวเลือกแรก พร้อมคำอธิบาย *"Shorthand property to set values the thickness of the margin area..."*

![margin-right 10px typing](images/6-CSS%20Basics/19-margin-right-10px-typing.png)

พิมพ์ค่า `margin-right: 10px` (มี tooltip preview ค่า "10px" ที่เคยใช้มาก่อนโผล่ขึ้นมาให้เลือกด้วย)

![Browser image beside text](images/6-CSS%20Basics/20-browser-image-beside-text.png)

ผลลัพธ์ในเบราว์เซอร์: **รูปวงกลมลอยชิดซ้าย และข้อความ 2 บรรทัด (@moshhamedani, I love to teach you HTML!) ขึ้นมาเรียงอยู่ทางขวาของรูปพอดี** — เว้นระยะห่างจากรูป 10px ตามที่ `margin-right` กำหนด (สังเกตว่า "I love to teach you HTML!" ยังเป็นตัวหนาอยู่จากค่า `font-weight` เดิมที่ตั้งไว้ในขั้นถัดไป — ในเฟรมนี้จริงๆ ยังไม่ได้ตั้ง แต่ผลลัพธ์ตรงนี้แสดง layout float สำเร็จแล้ว)

![img style block complete](images/6-CSS%20Basics/21-img-style-block-complete.png)

CSS ของ `img` เสร็จสมบูรณ์:
```css
img {
    width: 100px;
    border-radius: 50px;
    float: left;
    margin-right: 10px;
}
```

![Full HTML with CSS so far](images/6-CSS%20Basics/22-full-html-with-css.png)

โค้ดไฟล์เต็ม ณ จุดนี้:
```html
<!DOCTYPE html>
<html>
    <head>
        <title>My first web page</title>
        <style>
            img {
                width: 100px;
                border-radius: 50px;
                float: left;
                margin-right: 10px;
            }
        </style>
    </head>
    <body>
        <img src="images/mosh.jpg">
        <p>@moshhamedani</p>
        <p>I love to teach you HTML!</p>
    </body>
</html>
```

## 9) Selector ตัวที่สอง: `p` (จัดสไตล์ข้อความ)

![Typing p selector](images/6-CSS%20Basics/23-typing-p-selector.png)

ขึ้นบรรทัดใหม่ต่อจาก `img { }` พิมพ์ **`p`** เพื่อสร้าง selector ใหม่

![p selector empty braces](images/6-CSS%20Basics/24-p-selector-empty-braces.png)

```css
p {

}
```
- **`p`** = element selector อีกตัว คราวนี้ใช้กับทุกแท็บ `<p>` ในหน้า (ซึ่งมี 2 อันคือ `@moshhamedani` และ `I love to teach you HTML!`)

![font-weight autocomplete](images/6-CSS%20Basics/25-font-weight-autocomplete.png)

พิมพ์ **`font-wei`** → IntelliSense เด้ง **`font-weight`** พร้อมคำอธิบาย *"Specifies weight of glyphs in the font, their degree of blackness or stroke thickness."* syntax `<font-weight-absolute>{1,2...}`

![font-weight bold value](images/6-CSS%20Basics/26-font-weight-bold-value.png)

```css
p {
    font-weight: bold;
}
```
- **`font-weight: bold;`** = ทำให้ข้อความหนาขึ้น

![Browser both p bold](images/6-CSS%20Basics/27-browser-both-p-bold.png)

ผลลัพธ์: **ข้อความทั้ง 2 บรรทัดกลายเป็นตัวหนาพร้อมกัน** (`@moshhamedani` และ `I love to teach you HTML!`) เพราะ selector `p` จับทุกแท็บ `<p>` ในหน้าโดยไม่เลือก

![Full HTML both bold](images/6-CSS%20Basics/28-full-html-both-bold.png)

โค้ดเต็ม ณ จุดนี้:
```html
<style>
    img {
        width: 100px;
        border-radius: 50px;
        float: left;
        margin-right: 10px;
    }

    p {
        font-weight: bold;
    }
</style>
...
<body>
    <img src="images/mosh.jpg">
    <p>@moshhamedani</p>
    <p>I love to teach you HTML!</p>
</body>
```

## 10) ปัญหา: อยากให้หนาแค่บรรทัดเดียว → ใช้ `class` + Class Selector

Mosh อธิบายปัญหา: ถ้าอยากให้ **เฉพาะ `@moshhamedani` เป็นตัวหนา** แต่ไม่อยากให้ "I love to teach you HTML!" หนาไปด้วย จะใช้ selector `p` เฉยๆ ไม่ได้ (เพราะมันจับทุก `<p>`) ต้องแยกแท็บที่ต้องการออกมาด้วย **attribute `class`**

![class username added](images/6-CSS%20Basics/29-class-username-added.png)

Mosh แก้ไข `<p>` ตัวแรกใน `<body>` โดยเพิ่ม attribute `class`:
```html
<p class="username">@moshhamedani</p>
```
- **`class="username"`** = ตั้งชื่อ "ป้ายกำกับ" ให้แท็บนี้ว่า `username` เพื่อให้ CSS เลือกจับเฉพาะแท็บที่มี class นี้ได้

![class username full code](images/6-CSS%20Basics/30-class-username-full-code.png)

โค้ด HTML เต็มหลังเพิ่ม class:
```html
<body>
    <img src="images/mosh.jpg">
    <p class="username">@moshhamedani</p>
    <p>I love to teach you HTML!</p>
</body>
```

![Browser still both bold](images/6-CSS%20Basics/31-browser-still-both-bold.png)

*(ณ จุดนี้ ก่อนแก้ CSS selector หน้าเว็บยังโชว์ตัวหนาทั้ง 2 บรรทัดเหมือนเดิม เพราะ CSS ยังใช้ selector `p` แบบเดิมอยู่ — ยังไม่ได้เปลี่ยนเป็น class selector)*

![CSS class selector .username](images/6-CSS%20Basics/32-css-class-selector-username.png)

ขั้นตอนสุดท้าย Mosh แก้ CSS selector จาก `p` เป็น **`.username`** (จุดนำหน้า `.` คือสัญลักษณ์ของ Class Selector ใน CSS):
```css
<style>
    img {
        width: 100px;
        border-radius: 50px;
        float: left;
        margin-right: 10px;
    }

    .username {
        font-weight: bold;
    }
</style>
```
- **`.username { font-weight: bold; }`** = ตอนนี้กฎนี้จะไปใช้ **เฉพาะแท็บที่มี `class="username"`** เท่านั้น (คือ `@moshhamedani`) ส่วน `<p>I love to teach you HTML!</p>` ที่ไม่มี class นี้จะไม่ถูกทำตัวหนาไปด้วย — นี่คือทางแก้ปัญหา "อยากจัดสไตล์เฉพาะบางอัน ไม่ใช่ทุกอันที่เป็นแท็บเดียวกัน"

## สรุปที่ใช้ได้จริง (โค้ด CSS ฉบับเต็มของคลิปนี้)

```html
<head>
    <title>My first web page</title>
    <style>
        img {
            width: 100px;
            border-radius: 50px;
            float: left;
            margin-right: 10px;
        }

        .username {
            font-weight: bold;
        }
    </style>
</head>
<body>
    <img src="images/mosh.jpg">
    <p class="username">@moshhamedani</p>
    <p>I love to teach you HTML!</p>
</body>
```

Selector ที่เรียนในคลิปนี้ (เรียงตามลำดับที่สอน):
```
1. img { ... }        → Element/Tag Selector — จับทุกแท็บ <img>
2. p { ... }           → Element/Tag Selector — จับทุกแท็บ <p> (ทุกอันพร้อมกัน)
3. .username { ... }   → Class Selector — จับเฉพาะแท็บที่มี class="username"
```

Property ที่เรียนในคลิปนี้:
| Property | ความหมาย | ค่าที่ใช้ในคลิป |
|---|---|---|
| `width` | กำหนดความกว้าง | `100px` |
| `border-radius` | มุมโค้งของขอบ (ค่าเท่ากับครึ่งความกว้าง/สูง = วงกลมสมบูรณ์) | `10px` → `50px` |
| `float` | ให้ element ลอยไปด้านที่กำหนด แล้วเนื้อหาอื่นไหลมาอยู่ข้างๆ | `left` |
| `margin-right` | ระยะห่างด้านขวาของ element | `10px` |
| `font-weight` | ความหนาของตัวอักษร | `bold` |

## จุดเชื่อมกับงานจริงของ Aum

- **Element selector vs Class selector** — concept นี้คือรากฐานเดียวกับที่ React ใช้ `className="username"` แทน `class` (เพราะ `class` เป็นคำสงวนใน JavaScript) แล้วจับคู่กับ CSS/Tailwind class `.username` หรือ `bg-blue-500` ก็ใช้หลักการเดียวกันเป๊ะ
- **`float: left` + `margin`** — เป็นวิธีจัด layout แบบเก่า ปัจจุบันงานจริงของ Aum (Firmware Airflow Dashboard) น่าจะใช้ **Flexbox (`display: flex`) หรือ Grid** แทน แต่หลักคิดเรื่อง "จัดตำแหน่งให้ element อยู่ข้างกัน + เว้นระยะห่าง" ยังเป็นแนวคิดเดียวกัน ตรงกับที่ต้องเข้าใจก่อนจะไปเรียน `flex`, `gap`, `justify-between` ใน Tailwind ต่อ
- **`border-radius: 50%` ทำวงกลม** — เทคนิคนี้ยังใช้บ่อยมากตอนทำ avatar/profile picture ด้วย Tailwind (`rounded-full`) ใน React component จริง
- **Internal `<style>` tag** — ตรงกับขั้นตอนพื้นฐานก่อนจะไปเรียน CSS แยกไฟล์ (external stylesheet) และท้ายที่สุดคือ CSS-in-JS/Tailwind utility classes ที่ Aum ใช้อยู่ในโปรเจกต์ Next.js จริง
