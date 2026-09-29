# 7-Formatting Code (2:15)

**ไฟล์ต้นทาง:** `Web Development Fundamentals/7- Formatting Code (2-15).mp4`

▶️ **[เปิดวิดีโอต้นฉบับ](../../Web%20Development%20Fundamentals/7-%20Formatting%20Code%20%282-15%29.mp4)**

> คลิปสั้นแต่สำคัญมาก — Mosh สอนเรื่อง **การจัดรูปแบบโค้ด (code formatting)** โดยตั้งใจทำโค้ดให้ยุ่งเหยิงก่อน แล้วโชว์ฟีเจอร์ "Format Document" ของ VS Code ที่ช่วยจัดโค้ดให้สวยงามอัตโนมัติ ปิดท้ายด้วยการตั้งค่า Format on Save ทำละเอียดที่สุด เก็บทุกขั้นตอนคลิก

## 1) เปิดคลิป

![Title](images/7-Formatting%20Code/01-title.png)

Title slide: **"Formatting Code"** — Mosh Hamedani, codewithmosh.com

## 2) จุดเริ่มต้น — โค้ดที่จัดรูปแบบเรียบร้อยจากคลิปก่อน

![Starting formatted code](images/7-Formatting%20Code/02-starting-formatted-code.png)

Mosh เปิดไฟล์ `index.html` ที่เขียนต่อจากคลิป CSS Basics ขึ้นมา — โค้ดตอนนี้จัดรูปแบบ (indent) เรียบร้อยดีอยู่แล้ว:
```html
<!DOCTYPE html>
<html>
  <head>
    <title>My first web page</title>
    <style>
      img { width: 100px; border-radius: 50px; float: left; margin-right: 10px; }
      .username { font-weight: bold; }
    </style>
```

## 3) จงใจทำโค้ดให้ "พัง" (ลบการขึ้นบรรทัดใหม่)

Mosh อธิบายว่าบางครั้งโค้ดที่ได้มา (จาก copy-paste, จากเพื่อนร่วมทีม, หรือพิมพ์เร็วๆ) จะไม่มีการจัดบรรทัด/เว้นวรรคที่ดี แล้วสาธิตให้เห็นภาพโดยการ**ลบขึ้นบรรทัดใหม่ทีละจุด** ทำให้โค้ดถูกยุบรวมกันเป็นบรรทัดเดียวมากขึ้นเรื่อยๆ

![HTML head squashed onto one line](images/7-Formatting%20Code/03-html-head-squashed-one-line.png)

ขั้นแรก: `<!DOCTYPE html><html>` ถูกรวมเป็นบรรทัดเดียว ส่วน `<head>` ยังอยู่บรรทัดแยก

![Title tag squashed too](images/7-Formatting%20Code/04-title-tag-squashed-too.png)

ขั้นต่อมา: รวม `<head>` เข้าไปด้วย กลายเป็น `<!DOCTYPE html><html><head>` บรรทัดเดียว ส่วน `<title>My first web page</title>` ยังแยกอยู่บรรทัดถัดมา

![Browser still works fine](images/7-Formatting%20Code/05-browser-still-works-fine.png)

Mosh สลับไปดู Chrome เช็คว่าหน้าเว็บยังทำงานปกติไหม — **หน้าเว็บยังโชว์ผลลัพธ์ถูกต้องทุกอย่าง** (รูป @moshhamedani ตัวหนา + ข้อความ "I love to teach you HTML!") แม้โค้ดจะเริ่มยุ่งแล้วก็ตาม — นี่คือประเด็นสำคัญที่ Mosh จะพูดถึง

![Everything squashed onto one line](images/7-Formatting%20Code/06-everything-on-one-line.png)

Mosh ยุบต่อจนบรรทัดแรกกลายเป็น:
```html
<!DOCTYPE html><html><head><title>My first web page</title>
```
ยาวเป็นบรรทัดเดียวเต็มจอ (ส่วน `<style>` ที่เหลือยังจัด indent อยู่ด้านล่าง) — breadcrumb แสดง `html > head > title`

**ประเด็นสำคัญที่ Mosh อธิบาย:** เบราว์เซอร์ **ไม่สนใจ whitespace/การขึ้นบรรทัดใหม่เลย** — โค้ด HTML จะยุบเป็นบรรทัดเดียวหรือจัดสวยหลายบรรทัด ก็ render ผลลัพธ์เหมือนกันทุกประการ (ตามที่เห็นในข้อ 4) **แต่ปัญหาคือมันอ่านยากมากสำหรับ "คน"** — ยิ่งโปรเจกต์ใหญ่ขึ้น โค้ดแบบนี้จะแก้ไข/debug แทบไม่ได้เลย

## 4) ใช้ VS Code จัดรูปแบบโค้ดอัตโนมัติ — Format Document

![View menu open](images/7-Formatting%20Code/07-view-menu-open.png)

Mosh เปิดเมนู **View** ขึ้นมาดู (โชว์ตัวเลือกต่างๆ เช่น Command Palette ⇧⌘P, Explorer ⇧⌘E, Search ⇧⌘F, Terminal, Toggle Word Wrap ⌥Z, Show Minimap, Show Breadcrumbs ✓, Render Whitespace ✓) เพื่อนำไปสู่คำสั่งที่ต้องการ

![Command Palette Format Document](images/7-Formatting%20Code/08-command-palette-format-document.png)

เปิด **Command Palette** (⇧⌘P) พิมพ์ `>` แล้วมีตัวเลือก **"Format Document"** ขึ้นเป็นอันดับแรกในหมวด "recently used" — นี่คือคำสั่งที่จะจัดรูปแบบไฟล์ทั้งไฟล์ให้อัตโนมัติ (ตัวเลือกอื่นที่โชว์ด้วย: Change Language Mode ⌘K ⌘M, Extensions: Install Extensions, Preferences: Color Theme ⌘K ⌘T)

![Multiple formatters dialog](images/7-Formatting%20Code/09-multiple-formatters-dialog.png)

พอกด Format Document ครั้งแรก VS Code เด้งข้อความแจ้งเตือน: **"There are multiple formatters for 'HTML' files. Select a default formatter to continue."** พร้อมปุ่ม **"Configure..."** — เพราะมี extension มากกว่า 1 ตัวที่รองรับการ format ไฟล์ HTML ต้องเลือกก่อนว่าจะใช้ตัวไหนเป็นค่าเริ่มต้น

![Formatter choices dropdown](images/7-Formatting%20Code/10-formatter-choices-dropdown.png)

รายการตัวเลือก formatter ที่ขึ้นมาให้เลือก:
```
Select a default formatter for 'HTML' files
- Prettier - Code formatter    (esbenp.prettier-vscode)
- HTML Language Features        (vscode.html-language-features)
```
Mosh เลือก **"Prettier - Code formatter"** — extension จัดฟอร์แมตโค้ดยอดนิยมที่สุดตัวหนึ่งในวงการเว็บ (รองรับ HTML, CSS, JavaScript, และอีกหลายภาษา)

![Formatter dropdown state](images/7-Formatting%20Code/11-formatter-choices-dropdown-b.png)

ยืนยันการเลือก Prettier เป็น default formatter สำหรับไฟล์ HTML

![Code reformatted nicely](images/7-Formatting%20Code/12-code-reformatted-nicely.png)

ผลลัพธ์ทันที: **Prettier จัดโค้ดที่ยุ่งเหยิงกลับมาเป็นระเบียบสวยงามอัตโนมัติ** — `<!DOCTYPE html>`, `<html>`, `<head>`, `<title>` กลับมาอยู่คนละบรรทัด indent ถูกต้องตามมาตรฐานทันที โดยไม่ต้องแก้เองทีละบรรทัด

## 5) ตั้งค่าให้ Format อัตโนมัติทุกครั้งที่ Save (Format on Save)

![Code menu open](images/7-Formatting%20Code/13-code-menu-open.png)

Mosh เปิดเมนู **Code** (มุมซ้ายบนสุดของแถบเมนู macOS) — เห็นตัวเลือก About Visual Studio Code, Restart to Update, **Preferences ▸**, Services ▸, Hide Visual Studio Code ⌘H, Quit ⌘Q

![Preferences Settings submenu](images/7-Formatting%20Code/14-preferences-settings-submenu.png)

เข้าไปที่ **Preferences ▸** เจอเมนูย่อย: **Settings ⌘,**, Online Services Settings, Extensions ⇧⌘X, Keyboard Shortcuts ⌘K ⌘S, Keymaps ⌘K ⌘M, User Snippets, Color Theme ⌘K ⌘T, File Icon Theme, Turn on Settings Sync... — Mosh คลิก **Settings**

![Settings tab Commonly Used](images/7-Formatting%20Code/15-settings-tab-commonly-used.png)

แท็บ **Settings** เปิดขึ้นมาเป็นหน้าใหม่ (แยกจากแท็บ index.html) หมวด **"Commonly Used"** โชว์ตัวเลือกยอดฮิต เช่น **Files: Auto Save** (ค่าเริ่มต้น `off`), **Files: Auto Save Delay** (`1000` ms) — มี tab ย่อย User / Workspace ให้เลือกด้วย

![Format on save search](images/7-Formatting%20Code/16-format-on-save-checkbox.png)

Mosh พิมพ์ค้นหาในช่อง Search settings ว่า **"format on save"** → เจอ **"2 Settings Found"** ในหมวด Text Editor > Formatting:
- **Editor: Format On Save** — คำอธิบาย: *"Format a file on save. A formatter must be available, the file must not be saved after delay, and the editor must not be shutting down."* (checkbox ยังไม่ติ๊ก)
- **Editor: Format On Save Mode** — *"Controls if format on save formats the whole file or only modifications."* ตั้งค่าเป็น `file`

Mosh ติ๊กเปิดใช้งาน **Format On Save** — ผลคือ **ทุกครั้งที่กด ⌘S บันทึกไฟล์ VS Code จะเรียก Prettier มาจัดรูปแบบโค้ดให้อัตโนมัติทันที** ไม่ต้องเปิด Command Palette มา Format Document เองอีกต่อไป

![Final code clean](images/7-Formatting%20Code/17-final-code-clean.png)

กลับมาที่แท็บ `index.html` — โค้ดกลับมาสะอาด จัดรูปแบบถูกต้องสมบูรณ์ พร้อมสำหรับการเขียนต่อในคลิปถัดๆ ไป

## สรุปที่ใช้ได้จริง

```
ปัญหา: โค้ดที่ไม่มีการเว้นบรรทัด/จัด indent อ่านยากมาก (แม้ browser จะ render ได้ปกติ เพราะไม่สนใจ whitespace)

ทางแก้ใน VS Code:
1. จัดฟอร์แมตครั้งเดียว: เปิด Command Palette (⇧⌘P) → พิมพ์ "Format Document" → Enter
   - ถ้าขึ้น "multiple formatters" ให้เลือก formatter ที่ต้องการ (แนะนำ Prettier)
2. ตั้งให้จัดฟอร์แมตอัตโนมัติทุกครั้งที่ save:
   Code → Preferences → Settings → ค้นหา "format on save" → ติ๊ก Editor: Format On Save
3. จากนี้ไปแค่กด ⌘S โค้ดจะสวยเป๊ะทุกครั้งโดยอัตโนมัติ
```

## จุดเชื่อมกับงานจริงของ Aum

- **Prettier** คือตัวเดียวกับที่ใช้ในโปรเจกต์ React/Next.js จริงแทบทุกโปรเจกต์ — ตั้งค่า `.prettierrc` ในโปรเจกต์แล้วเปิด Format on Save ก็ทำงานเหมือนกันเป๊ะ เป็นเครื่องมือมาตรฐานที่ทีม frontend ใช้กันเพื่อให้โค้ดทุกคนในทีมมีสไตล์เดียวกัน
- **Format on Save** เป็น setting แรกๆ ที่ควรเปิดตอนตั้งค่า VS Code สำหรับงาน Next.js/React จริง เพราะช่วยลด diff ที่ไม่จำเป็นตอนทำ Pull Request ในทีม (โค้ดจะไม่มี noise จากการจัด format ปนกับการเปลี่ยน logic จริง)
- **Prettier มักถูกใช้คู่กับ ESLint** ในโปรเจกต์ React/Next.js — Prettier จัดการเรื่องหน้าตาโค้ด (formatting) ส่วน ESLint จัดการเรื่องคุณภาพ/ข้อผิดพลาดของโค้ด (linting) ทั้งสองตัวมักตั้งให้รันอัตโนมัติตอน save หรือตอน commit (ผ่าน husky/lint-staged) เหมือนกัน
- **บทเรียนเรื่อง "browser ไม่สนใจ whitespace"** เป็นความเข้าใจพื้นฐานที่มีประโยชน์ตอน debug จริง — เวลาเจอ HTML/JSX ที่ minify มาจาก build process (เช่นตอนเปิด DevTools ดู production build) จะไม่ตกใจว่าทำไมโค้ดถึงเป็นบรรทัดเดียวยาวๆ เพราะเข้าใจว่ามันคือกระบวนการ minify เพื่อลดขนาดไฟล์ ไม่ใช่โค้ดพัง
