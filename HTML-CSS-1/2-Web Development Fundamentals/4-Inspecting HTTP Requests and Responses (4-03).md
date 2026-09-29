# 4-Inspecting HTTP Requests and Responses (4:03)

**ไฟล์ต้นทาง:** `Web Development Fundamentals/4-Inspecting HTTP Requests and Responses (4-03).mp4`

▶️ **[เปิดวิดีโอต้นฉบับ](../../Web%20Development%20Fundamentals/4-Inspecting%20HTTP%20Requests%20and%20Responses%20%284-03%29.mp4)**

> คลิปนี้คือ **hands-on demo จริง** ของ Chrome DevTools — ตรงกับที่ Aum สนใจเรื่อง Network tab พอดี ทำละเอียด + แคปภาพครบทุกขั้นตอนคลิก

## 1) เปิดคลิป

![Title](images/4-Inspecting%20HTTP%20Requests%20and%20Responses/01-title.png)

Title: "Inspecting HTTP Requests and Responses" — Mosh Hamedani

## 2) เปิดเว็บ Google.com เป็นตัวอย่าง

![Google page](images/4-Inspecting%20HTTP%20Requests%20and%20Responses/02-google-page.png)

Mosh เปิด Chrome ไปที่ `google.com` เพื่อใช้เป็นเว็บตัวอย่างสาธิต DevTools ทั้งคลิป

## 3) เปิด DevTools ผ่านเมนู

![DevTools menu](images/4-Inspecting%20HTTP%20Requests%20and%20Responses/03-devtools-menu.png)

วิธีเปิด DevTools ที่โชว์ในคลิป: **View → Developer → Developer Tools** (คีย์ลัดที่โชว์คู่กัน: `⌥⌘I`)

*(หมายเหตุ: บน Windows ใช้ `F12` หรือคลิกขวา → Inspect ก็ได้เหมือนกัน)*

## 4) แท็บ Elements

![Elements panel](images/4-Inspecting%20HTTP%20Requests%20and%20Responses/04-elements-panel.png)

พอเปิด DevTools ขึ้นมา แท็บแรกที่เห็นคือ **Elements** — โชว์ HTML/DOM ของหน้าเว็บแบบ real-time (`<!DOCTYPE html>`, `<html>`, `<body>` พร้อม attribute เต็มๆ) — นี่คือ DOM ที่พูดถึงในคลิปที่แล้ว (3-How the Web Works) ตัวจริงที่จับต้องได้

## 5) สลับไปแท็บ Network

![Network recording](images/4-Inspecting%20HTTP%20Requests%20and%20Responses/05-network-recording.png)

คลิกแท็บ **Network** — ขึ้นข้อความ "Recording network activity... Perform a request or hit ⌘R to record the reload." (สื่อว่า Network tab ต้องมีการ record อยู่ก่อน ถึงจะจับ request ได้ — ถ้าเปิด DevTools หลังหน้าโหลดเสร็จแล้ว จะไม่เห็น request เก่าเลย ต้อง reload ใหม่)

## 6) จัดตำแหน่ง DevTools (Dock side)

![DevTools undocked](images/4-Inspecting%20HTTP%20Requests%20and%20Responses/06-devtools-undocked.png)

กดปุ่ม 3 จุด (⋮) → **Dock side** เลือกได้ 4 แบบ: ลอยแยกหน้าต่าง / ติดขวา / ติดล่าง / ติดซ้าย — Mosh เลือกจัดให้ DevTools อยู่ด้านข้างเพื่อดูทั้งหน้าเว็บและ DevTools พร้อมกันได้ถนัดขึ้น (ปุ่มลัดอื่นในเมนูเดียวกัน: Show console drawer = `Esc`, Search = `⌘⌥F`, Run command = `⌘⇧P`)

## 7) Reload หน้าเว็บ → ดู request ทั้งหมดใน Network tab

![Network full list](images/4-Inspecting%20HTTP%20Requests%20and%20Responses/07-network-full-list.png)

หลัง reload หน้า จะเห็น**รายการ request ทั้งหมด**ที่หน้าเว็บยิงออกไป — ตรงตามที่คลิปที่แล้วอธิบายไว้ (1 หน้าเว็บ = หลาย request) คอลัมน์ที่โชว์:

| คอลัมน์ | ความหมาย |
|---|---|
| **Name** | ชื่อไฟล์/URL ที่ถูกขอ |
| **Method** | HTTP method (ในคลิปนี้ทุกตัวเป็น `GET`) |
| **Status** | HTTP status code (ทุกตัว `200`) |
| **Type** | ประเภทไฟล์ — `document`, `png`, `font`, `script`, `webp` ฯลฯ |
| **Size** | ขนาดไฟล์ (บางตัวขึ้น `(memory cache)` / `(disk cache)` แปลว่าโหลดจาก cache ไม่ได้ยิง network จริง) |
| **Time** | เวลาที่ใช้โหลด request นั้น |
| **Waterfall** | กราฟแท่งแสดงจังหวะเวลาที่แต่ละ request เกิดขึ้น |

ตัวอย่างแถวแรก: `www.google.com` — GET — 200 — **document** — 67.8 kB — 280 ms (นี่คือ HTML หลักของหน้า ตรงกับ HTTP Response ที่เรียนในคลิปก่อน)

## 8) แถบสรุปด้านล่าง (สำคัญมาก)

![Summary bar](images/4-Inspecting%20HTTP%20Requests%20and%20Responses/08-summary-bar.png)

ด้านล่างสุดของ Network tab มีแถบสรุปตัวเลขรวม:

```
45 requests | 94.3 kB transferred | 2.6 MB resources | Finish: 5.57 s | DOMContentLoaded: 364 ms | Load: 1.2s
```

- **45 requests** = จำนวน request ทั้งหมดที่หน้าเว็บนี้ยิงออกไป (ยืนยันภาพในคลิปก่อนว่า 1 หน้าเว็บมีได้หลาย request จริง)
- **94.3 kB transferred** = ขนาดข้อมูลที่โหลดจริงผ่านเน็ต (ไม่รวมของที่มาจาก cache)
- **2.6 MB resources** = ขนาดรวมของทุกไฟล์ถ้านับรวม cache ด้วย
- **DOMContentLoaded: 364 ms** = เวลาที่ DOM พร้อมใช้งาน (จุดที่ HTML parse เสร็จ ยังไม่รอรูป/ฟอนต์ทั้งหมด)
- **Load: 1.2s** = เวลาที่ทุกอย่างโหลดเสร็จสมบูรณ์ (รวมรูป/ฟอนต์/สคริปต์ครบ)

*(จุดนี้สำคัญมากสำหรับงานจริง — ตอน debug performance ของเว็บ จะดูตัวเลขพวกนี้เป็นหลัก)*

## 9) คลิกเข้าไปดู request ตัวเดียว → แท็บ Headers

![Headers general](images/4-Inspecting%20HTTP%20Requests%20and%20Responses/09-headers-general.png)

คลิกที่แถว `www.google.com` → ขวามือมีแท็บย่อยขึ้นมา: **Headers | Preview | Response | Initiator | Timing | Cookies**

ในแท็บ Headers ส่วน **General** โชว์:
```
Request URL: https://www.google.com/
Request Method: GET
Status Code: 200
Remote Address: 172.217.11.164:443
Referrer Policy: no-referrer-when-downgrade
```

## 10) เลื่อนลง → Response Headers แบบเต็ม

![Response headers](images/4-Inspecting%20HTTP%20Requests%20and%20Responses/10-response-headers.png)

```
alt-svc: h3-Q050=":443"; ma=2592000, h3-29=":443"; ma=2592000, ...
cache-control: private, max-age=0
content-encoding: br
content-length: 67102
content-type: text/html; charset=UTF-8
date: Fri, 30 Oct 2020 17:45:03 GMT
expires: -1
server: gws
set-cookie: 1P_JAR=2020-10-30-17; expires=Sun, 29-Nov-2020 17:45:03 GMT; ...
```

เทียบกับ HTTP Response แบบง่ายที่เรียนในคลิปก่อน (`HTTP/1.1 200 OK` / `Date` / `Content-Type`) — อันนี้คือของจริงที่มี header เพิ่มเยอะกว่ามาก เช่น `cache-control` (บอก browser ว่า cache ได้ไหม/นานแค่ไหน), `content-encoding: br` (ข้อมูลถูกบีบอัดด้วย Brotli ก่อนส่ง), `server: gws` (ชื่อ server software ฝั่ง Google)

## 11) แท็บ Preview — ดูผลลัพธ์ที่ render ได้

![Preview tab](images/4-Inspecting%20HTTP%20Requests%20and%20Responses/11-preview-tab.png)

คลิกแท็บ **Preview** ของ request `www.google.com` → เห็นหน้าเว็บที่ browser render ออกมาจาก response นั้น (ในคลิปโชว์ 2 ช่วง: เห็นแค่ปุ่ม About/Store/Gmail/Images ก่อน แล้วเลื่อนลงเห็นปุ่ม Google Search/I'm Feeling Lucky) — ต่างจากแท็บ **Response** ที่จะโชว์ raw HTML text ดิบๆ ยังไม่ผ่านการ render

## 12) Filter — กรอง request ตามประเภท

![Filter types](images/4-Inspecting%20HTTP%20Requests%20and%20Responses/12-filter-types.png)

กดไอคอนรูปกรวย (filter) มุมซ้ายบน → เห็นแถบกรองประเภท request:

```
All | XHR | JS | CSS | Img | Media | Font | Doc | WS | Manifest | Other
```

พร้อม checkbox เพิ่มเติม: **Hide data URLs**, **Has blocked cookies**, **Blocked Requests**

*(ฟีเจอร์นี้สำคัญมากสำหรับงานจริง — ตอน debug จะกดกรองเฉพาะ **XHR** (สำหรับดู API call ปกติ) หรือ **WS** (สำหรับดู WebSocket/SSE connection) เพื่อไม่ต้องไล่ดู request รูป/ฟอนต์ที่ไม่เกี่ยวข้อง)*

## สรุปที่ใช้ได้จริง

```
1. เปิด DevTools: View → Developer → Developer Tools (หรือ ⌥⌘I / F12)
2. คลิกแท็บ Network
3. ต้อง Reload หน้า (⌘R) เพื่อให้ DevTools เริ่มจับ request (ไม่งั้นจะไม่เห็น request ที่เกิดไปแล้วก่อนเปิด DevTools)
4. ดูรายการ request ทั้งหมด: Name / Method / Status / Type / Size / Time / Waterfall
5. อ่านแถบสรุปด้านล่าง: จำนวน request, ขนาดรวม, DOMContentLoaded, Load time
6. คลิก request ใดก็ได้ → ดู Headers (Request/Response headers เต็ม), Preview (ผล render), Response (raw text)
7. ใช้ Filter (XHR/JS/CSS/Img/Font/WS/...) กรองเฉพาะประเภทที่สนใจ เวลามี request เยอะ
```

### จุดเชื่อมกับงานจริงของ Aum (สำคัญที่สุดในคลิปนี้)

- **Network tab ทั้งหมดนี้คือเครื่องมือหลักที่ใช้ debug** ตอนเรียก API หรือ SSE ใน Firmware Airflow Dashboard project — พอ API ไม่ทำงานตามคาด เปิด Network tab แล้วดู Status code / Response headers / Response body ได้ตรงจุดเลย
- **Filter → XHR** จะใช้บ่อยมากตอน debug React Query calls (กรองออกจากรูป/ฟอนต์/สคริปต์อื่นๆ)
- **Filter → WS** ใช้ตอน debug SSE connection (แม้ SSE ไม่ใช่ WebSocket เป๊ะๆ แต่บางครั้งจะโผล่ในหมวดใกล้เคียง หรือดูใน XHR/Fetch ก็ได้ขึ้นอยู่กับ browser)
- **DOMContentLoaded vs Load** — ตัวเลข 2 ตัวนี้คือมาตรฐานที่ใช้วัด performance หน้าเว็บจริง ถ้าทำ dashboard แล้วโหลดช้า ดูตัวเลขนี้เป็นจุดเริ่มต้นได้เลย
