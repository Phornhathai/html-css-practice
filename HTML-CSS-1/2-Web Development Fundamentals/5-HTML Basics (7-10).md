# 5-HTML Basics (7:10)

**ไฟล์ต้นทาง:** `Web Development Fundamentals/5-HTML Basics (7-10).mp4`

▶️ **[เปิดวิดีโอต้นฉบับ](../../Web%20Development%20Fundamentals/5-HTML%20Basics%20%287-10%29.mp4)**

> คลิปนี้คือ **hands-on coding เต็มรูปแบบครั้งแรก** ของคอร์ส — Mosh ลงมือเปิด VS Code แล้วเขียนหน้าเว็บ HTML จริงตั้งแต่บรรทัดแรกจนจบ พร้อมสอนใช้ Emmet abbreviation + Live Server extension ทำละเอียดที่สุดเท่าที่จะทำได้ เก็บทุกบรรทัดโค้ดที่ Mosh พิมพ์

## 1) เปิดคลิป

![Title](images/5-HTML%20Basics/01-title.png)

Title slide: **"HTML Basics"** — Mosh Hamedani, codewithmosh.com

## 2) สร้างโฟลเดอร์โปรเจกต์ใน Finder

![Finder new folder menu](images/5-HTML%20Basics/02-finder-new-folder-menu.png)

Mosh สลับไปหน้า Desktop (macOS) → **คลิกขวาที่พื้นที่ว่าง** → เมนูคลิกขวาของ Finder เด้งขึ้นมา เลือก **"New Folder"** (ไฮไลต์อยู่บนสุดของเมนู) — เมนูนี้ยังมีตัวเลือกอื่นให้เห็นด้วย: Get Info, Import from iPhone, Change Desktop Background, Use Stacks, Sort By, Clean Up, Clean Up By, Show View Options

![Finder HTML folder named](images/5-HTML%20Basics/03-finder-html-folder-named.png)

โฟลเดอร์ใหม่ถูกสร้างขึ้นบน Desktop แล้ว Mosh พิมพ์ชื่อโฟลเดอร์ว่า **`HTML`** (ช่องกรอกชื่อไฮไลต์สีฟ้าพร้อมให้พิมพ์ทับ) — นี่คือโฟลเดอร์โปรเจกต์ที่จะใช้เก็บไฟล์เว็บทั้งหมดในคลิปนี้

## 3) เปิด VS Code แล้วเปิดโฟลเดอร์โปรเจกต์

![VS Code empty](images/5-HTML%20Basics/04-vscode-no-folder-opened.png)

เปิดโปรแกรม **VS Code (Visual Studio Code)** ขึ้นมา — หน้าจอ Explorer ทางซ้ายขึ้นข้อความ **"NO FOLDER OPENED"** พร้อมข้อความ *"You have not yet opened a folder."* และมีปุ่ม 2 ปุ่ม: **"Open Folder"** กับ **"Clone Repository"** (พร้อมลิงก์ "read our docs" สำหรับ git/source control)

![Open Folder dialog](images/5-HTML%20Basics/05-vscode-open-folder-dialog.png)

Mosh กดปุ่ม **"Open Folder"** → หน้าต่าง dialog เลือกไฟล์ของ macOS เปิดขึ้นมา อยู่ที่ตำแหน่ง **Desktop** โชว์รายการโฟลเดอร์ **HTML** ที่เพิ่งสร้าง (พร้อม sidebar Favorites: Desktop, HTML, Courses, YouTube, Recents, Applications, Dropbox, Downloads, Documents, Creative Cloud..., Shared, iCloud Drive) จากนั้น **คลิกเลือกโฟลเดอร์ HTML** (แถวไฮไลต์สีฟ้า) แล้วกดปุ่ม **"Open"** มุมขวาล่าง

![VS Code HTML folder opened](images/5-HTML%20Basics/06-vscode-html-folder-opened.png)

โฟลเดอร์ **HTML** ถูกเปิดเข้ามาใน VS Code แล้ว — ชื่อโฟลเดอร์ขึ้นเป็น header ของหน้าต่าง (`HTML`) และในแถบ Explorer มีหัวข้อ **HTML** อยู่ (ยังไม่มีไฟล์ข้างในเลย เพราะเป็นโฟลเดอร์เปล่าที่เพิ่งสร้าง)

## 4) สร้างไฟล์ index.html และเริ่มพิมพ์ด้วย Emmet

Mosh สร้างไฟล์ใหม่ชื่อ **`index.html`** ในโฟลเดอร์ (ชื่อไฟล์มาตรฐานที่ browser จะโหลดเป็นหน้าแรกโดยอัตโนมัติ) แล้วเริ่มพิมพ์โค้ด

![Emmet DOCTYPE suggestion](images/5-HTML%20Basics/07-emmet-doctype-suggestion.png)

พอพิมพ์ `<` ตัวแรกในไฟล์ **VS Code auto-complete (Emmet)** เด้ง dropdown ขึ้นมาทันที แสดงรายการ tag ให้เลือก: `!DOCTYPE`, `a`, `abbr`, `address`, `area`, `article`, `aside`, `audio`, `b`, `base`, `bdi`, ... โดยตัวแรกสุด **`!DOCTYPE`** มีคำอธิบายกำกับด้านข้างว่า **"A preamble for an HTML document."** — Mosh เลือกตัวนี้

![DOCTYPE html done](images/5-HTML%20Basics/08-doctype-html-done.png)

ผลลัพธ์ที่ได้จากการกด Tab/Enter เลือก suggestion:
```html
<!DOCTYPE html>
```
บรรทัดนี้คือสิ่งที่ต้องมีบรรทัดแรกสุดของทุกไฟล์ HTML เสมอ (ตรงกับที่เรียนในคลิป "How the Web Works" ก่อนหน้านี้)

![Emmet html tag suggestion](images/5-HTML%20Basics/09-emmet-html-tag-suggestion.png)

ขึ้นบรรทัดใหม่ พิมพ์ **`html`** → Emmet เด้ง suggestion 3 แบบ: `html`, `html:5`, `html:xml` พร้อม preview ผลลัพธ์ทางขวาว่า **`<html>|</html>`** (เครื่องหมาย `|` คือตำแหน่ง cursor ที่จะไปหยุดหลัง expand) — Mosh เลือกตัวแรก `html` เปล่าๆ

ผลลัพธ์:
```html
<!DOCTYPE html>
<html></html>
```
(สังเกตว่า Emmet expand แท็บเปิด-ปิดให้พร้อมกันในบรรทัดเดียว ยังไม่ได้ขึ้นบรรทัดแยก)

## 5) พิมพ์โครงสร้าง head/title ด้วย Emmet ต่อ

หลังจากนั้น Mosh กด Enter เพื่อขยาย `<html>` ให้เป็นหลายบรรทัด และพิมพ์ **`head`** ตามด้วย Emmet expand เป็น `<head></head>` เข้าไปข้างใน `<html>` เช่นเดียวกับ `html`

![Emmet title suggestion](images/5-HTML%20Basics/10-emmet-title-suggestion.png)

ข้างใน `<head>` พิมพ์ **`tit`** → Emmet เด้ง suggestion **`title`** พร้อม preview **`<title>|</title>`** — เลือกแล้วได้ `<title></title>` มาวางเคอร์เซอร์ไว้ตรงกลางพอดี

จากนั้น Mosh พิมพ์ **`body`** ต่อท้าย `</head>` แบบเดียวกัน ได้ `<body></body>` เพิ่มเข้ามา

![Title text My first web page](images/5-HTML%20Basics/11-title-my-first-web-page.png)

Mosh พิมพ์ข้อความลงในแท็บ `<title>` ว่า **"My first web page"** — โครงไฟล์ ณ จุดนี้:
```html
<!DOCTYPE html>
<html>
    <head>
        <title>My first web page</title>
    </head>
    <body>

    </body>
</html>
```
(หมายเหตุ: title นี้คือข้อความที่จะไปโชว์บน tab ของ browser)

## 6) เปิดหน้าเว็บด้วย Live Server extension

![Live Server context menu](images/5-HTML%20Basics/12-live-server-context-menu.png)

Mosh **คลิกขวาในไฟล์ index.html** → เมนูคลิกขวาของ VS Code เด้งขึ้นมา มีตัวเลือกมาตรฐาน (Go to Definition F12, Go to References ⇧F12, Peek, Find All References, Rename Symbol F2, Change All Occurrences ⌘F2, Format Document ⌥⇧F, Format Document With..., Cut ⌘X, Copy ⌘C, Paste ⌘V, Command Palette... ⇧⌘P) และที่สำคัญ **2 รายการจาก Live Server extension**:
- **"Open with Live Server [⌘L ⌘O]"**
- **"Stop Live Server [⌘L ⌘C]"**

Mosh คลิก **"Open with Live Server"** — extension นี้จะรัน local dev server แล้วเปิดไฟล์ HTML ให้ดูใน browser ทันที พร้อม **auto-reload** ทุกครั้งที่ save ไฟล์ (ไม่ต้องกด refresh เองเวลาแก้โค้ด)

![Full HTML skeleton](images/5-HTML%20Basics/13-full-html-skeleton.png)

โค้ดในไฟล์ ณ จุดที่กด Live Server ครบสมบูรณ์แบบเป็น skeleton พื้นฐาน:
```html
<!DOCTYPE html>
<html>
    <head>
        <title>My first web page</title>
    </head>
    <body>

    </body>
</html>
```

![Browser blank page 5500](images/5-HTML%20Basics/14-browser-blank-page-5500.png)

Chrome เปิด tab ใหม่ชื่อ **"My first web page"** (ตรงกับ `<title>`) ที่ URL **`127.0.0.1:5500/index.html`** — หน้าเว็บยังเป็น**หน้าว่างเปล่าสีขาวล้วน** เพราะใน `<body>` ยังไม่มีเนื้อหาอะไรเลย (สังเกตว่า port `5500` คือ port มาตรฐานที่ Live Server extension ใช้รันเสมอ)

## 7) เพิ่มรูปภาพด้วย `<img>` tag (Emmet)

![Emmet img suggestion](images/5-HTML%20Basics/15-emmet-img-suggestion.png)

กลับไปที่ VS Code พิมพ์ **`im`** ในบรรทัดว่างใน `<body>` → Emmet เด้ง suggestion: `img`, `img:s`, `img:sizes`, `img:srcset`, `img:z` พร้อม preview ผลลัพธ์ทางขวา:
```
<img src="|" alt="|">
```

![Img tag inserted](images/5-HTML%20Basics/16-img-tag-inserted.png)

หลังเลือก `img` ได้โค้ดเต็มดังนี้ (attribute `src` และ `alt` เป็นค่าว่างรอกรอก):
```html
<!DOCTYPE html>
<html>
    <head>
        <title>My first web page</title>
    </head>
    <body>
        <img src="" alt="">
    </body>
</html>
```
- **`src`** (source) = ที่อยู่ไฟล์รูปที่จะโชว์ — ต้องกรอก path ของไฟล์จริง
- **`alt`** (alternative text) = ข้อความสำรองกรณีรูปโหลดไม่ขึ้น หรือใช้เพื่อ accessibility (screen reader อ่านให้คนตาบอดฟัง)

![Explorer index.html only, unsaved](images/5-HTML%20Basics/17-explorer-index-html-only.png)

เปิดแถบ Explorer ทางซ้ายดูโครงสร้างไฟล์ปัจจุบัน: โฟลเดอร์ **HTML** มีไฟล์เดียวคือ **`index.html`** และแท็บของไฟล์ขึ้นป้าย **"1 UNSAVED"** สีเทา (แปลว่ายังไม่ได้กด ⌘S บันทึก)

## 8) สร้างโฟลเดอร์ images แล้วลากรูปเข้า VS Code

![Finder drag mosh.jpg](images/5-HTML%20Basics/18-finder-drag-mosh-jpg.png)

Mosh สลับไป **Finder** สร้างโฟลเดอร์ย่อยชื่อ **`images`** ข้างใน `HTML` แล้ว**ลาก (drag) ไฟล์รูป `mosh.jpg`** (รูปโปรไฟล์ของตัวเอง มีไอคอน "+" สีเขียวตอนกำลังลากแปลว่าเป็นการ copy) เข้าไปวางในโฟลเดอร์ images — เห็น VS Code เปิดอยู่เบื้องหลังแสดง `<img src="" alt="">` ในไฟล์ index.html รออยู่

![Explorer images folder with mosh.jpg](images/5-HTML%20Basics/19-explorer-images-folder-mosh-jpg.png)

กลับมาที่ VS Code Explorer — ตอนนี้มีโฟลเดอร์ **`images`** โผล่ขึ้นมาในรายการไฟล์ (ขยายออกแล้วเห็นไฟล์ `mosh.jpg` อยู่ข้างใน) เรียงคู่กับไฟล์ `index.html`

![VS Code image preview](images/5-HTML%20Basics/20-vscode-image-preview-mosh.png)

Mosh **ดับเบิลคลิกที่ `mosh.jpg`** ใน Explorer → VS Code เปิด**แท็บพรีวิวรูปภาพ**ขึ้นมาโดยตรง (breadcrumb แสดง `images > mosh.jpg`) โชว์รูปถ่ายจริงของ Mosh Hamedani (หัวโล้น ใส่แว่น พื้นหลังสีแดง/ส้ม ใส่แจ็กเก็ตหนังสีดำ) — นี่คือฟีเจอร์ **image preview ในตัว** ของ VS Code ที่เปิดไฟล์รูปดูได้เลยไม่ต้องออกไปโปรแกรมอื่น (มีทั้ง tab `index.html` และ `mosh.jpg` เปิดค้างพร้อมกัน)

## 9) กรอก path รูปเข้า attribute `src`

![Img src empty before fill](images/5-HTML%20Basics/21-img-src-empty-before-fill.png)

สลับกลับมาที่แท็บ `index.html` — `<img src="" alt="">` ยังว่างอยู่ เคอร์เซอร์อยู่ในตำแหน่ง `src=""` รอพิมพ์ path

Mosh พิมพ์ path แบบ **relative path** (เส้นทางสัมพัทธ์ นับจากตำแหน่งไฟล์ index.html) เข้าไปใน `src`:

![Img src filled, p tag started](images/5-HTML%20Basics/22-img-src-filled-p-tag-start.png)

```html
<img src="images/mosh.jpg">
```
- **`images/mosh.jpg`** = บอก browser ว่ารูปอยู่ใน**โฟลเดอร์ images ที่อยู่ข้างๆ ไฟล์ index.html** แล้วตามด้วยชื่อไฟล์ `mosh.jpg` — ไม่ใช่ absolute path (เต็มระบบ) แต่เป็น relative path ที่อ้างอิงจากตำแหน่งไฟล์ HTML เอง ทำให้ย้ายโปรเจกต์ทั้งโฟลเดอร์ไปเครื่องอื่นก็ยังใช้งานได้โดยไม่ต้องแก้ path

จากนั้น Mosh ขึ้นบรรทัดใหม่ พิมพ์ **`p`** → Emmet โชว์ dropdown ให้เลือกแท็บ `<p></p>` (paragraph)

## 10) เพิ่มข้อความบรรยาย (caption) ด้วยแท็บ `<p>`

![p tags caption typing](images/5-HTML%20Basics/23-p-tags-caption-typing.png)

Mosh สร้างแท็บ `<p>` สองอัน แล้วพิมพ์ข้อความเข้าไป — โค้ดที่ได้ (จากที่จับภาพระหว่างพิมพ์):
```html
<body>
    <img src="images/mosh.jpg">
    <p>@moshhamedani</p>
    <p>I love to teach you HTML!</p>
</body>
```
- แท็บแรก **`<p>@moshhamedani</p>`** = ข้อความ handle/username ของ Mosh
- แท็บสอง **`<p>I love to teach you HTML!</p>`** = ประโยคแนะนำตัวสั้นๆ (ยืนยันข้อความเต็มจากภาพหน้าเว็บสุดท้ายในข้อ 11)

*(จุดนี้สำคัญ: `<p>` คือแท็บมาตรฐานสำหรับ "ข้อความเป็นย่อหน้า" — ทุกครั้งที่มีเนื้อหาเป็นประโยค/ข้อความปกติ ให้ครอบด้วย `<p>...</p>`)*

## 11) ผลลัพธ์สุดท้ายในเบราว์เซอร์ (auto-reload จาก Live Server)

![Browser image rendered](images/5-HTML%20Basics/24-browser-image-rendered.png)

พอ save ไฟล์ (⌘S) **Live Server reload หน้าเว็บให้อัตโนมัติทันที** (ไม่ต้องกด refresh เอง) — เห็นรูปภาพ `mosh.jpg` โชว์เต็มขนาดจริงในหน้าเว็บที่ `127.0.0.1:5500/index.html`

![Browser final zoomed out](images/5-HTML%20Basics/25-browser-final-zoomed-out.png)

Mosh ซูมหน้าเว็บออก (กดปุ่มซูมใน Chrome ปรับเป็น **80%**) เพื่อให้เห็นผลลัพธ์ทั้งหมดในจอเดียว — หน้าเว็บที่ได้ประกอบด้วย 3 ส่วนเรียงจากบนลงล่าง:
1. รูปภาพของ Mosh (จาก `<img src="images/mosh.jpg">`)
2. ข้อความ **"@moshhamedani"** (จาก `<p>` อันแรก)
3. ข้อความ **"I love to teach you HTML!"** (จาก `<p>` อันที่สอง)

นี่คือหน้าเว็บ HTML แรกที่ Mosh เขียนสำเร็จครบทุกองค์ประกอบพื้นฐานในคลิปนี้: skeleton (`DOCTYPE/html/head/title/body`) + รูปภาพ (`img`) + ข้อความ (`p`)

## สรุปที่ใช้ได้จริง (โค้ดฉบับเต็มของคลิปนี้)

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

ขั้นตอนทั้งหมดที่ทำ (ทำซ้ำได้ทุกโปรเจกต์ใหม่):
```
1. สร้างโฟลเดอร์โปรเจกต์ใน Finder (คลิกขวา → New Folder)
2. เปิด VS Code → Open Folder → เลือกโฟลเดอร์นั้น
3. สร้างไฟล์ index.html
4. พิมพ์ !DOCTYPE + Tab → <!DOCTYPE html>
5. พิมพ์ html + Tab → <html></html> แล้วขยายเป็นหลายบรรทัด
6. พิมพ์ head + Tab, tit + Tab (title), body + Tab ข้างใน html
7. ใส่ข้อความใน <title>
8. คลิกขวาไฟล์ → Open with Live Server (รันที่ 127.0.0.1:5500)
9. พิมพ์ im + Tab (img) ใน <body> → ได้ <img src="" alt="">
10. สร้างโฟลเดอร์ images ใน Finder → ลากไฟล์รูปเข้าไป
11. กรอก src="images/ชื่อไฟล์.jpg"
12. พิมพ์ p + Tab สร้าง <p>ข้อความ</p> สำหรับ caption
13. Save (⌘S) → Live Server reload หน้าเว็บให้อัตโนมัติ
```

### จุดเชื่อมกับงานจริงของ Aum

- **Emmet abbreviation** (`!`, `html`, `tit`, `im`, `p` + Tab) — ฟีเจอร์นี้ยังใช้ได้เหมือนเดิมตอนเขียน JSX ใน React (พิมพ์ `div.container` แล้ว Tab ก็ยังช่วยประหยัดเวลาได้เหมือนกัน)
- **Live Server / auto-reload** — concept เดียวกับ **Vite dev server / `npm run dev`** ที่ใช้ตอนพัฒนา React project จริง (Firmware Airflow Dashboard) คือแก้โค้ดแล้วเห็นผลทันทีโดยไม่ต้อง refresh เอง
- **Relative path (`images/mosh.jpg`)** — concept นี้สำคัญมากตอน import รูป/asset ใน React (`import logo from "./assets/logo.png"` หรือ path ใน `public/` folder) ต้องเข้าใจ relative path ให้แม่นเพราะเป็นสาเหตุ bug "รูปไม่ขึ้น" ที่พบบ่อยที่สุด
- **`<img>` กับ `alt` attribute** — ตรงกับ accessibility best practice ที่ใช้ตอนเขียน component รูปภาพใน React เช่นกัน (`<img src={url} alt="คำอธิบาย" />`)
- **การจัดโครงสร้างโฟลเดอร์ (index.html + images/)** — เป็นต้นแบบง่ายๆ ของ folder structure ที่ขยายไปเป็น `src/assets/`, `public/` ใน Next.js/React project ที่ Aum ใช้งานจริง
