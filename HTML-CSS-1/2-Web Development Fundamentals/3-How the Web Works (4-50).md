# 3-How the Web Works (4:50)

**ไฟล์ต้นทาง:** `Web Development Fundamentals/3-How the Web Works (4-50).mp4`

▶️ **[เปิดวิดีโอต้นฉบับ](../../Web%20Development%20Fundamentals/3-How%20the%20Web%20Works%20%284-50%29.mp4)**

> ฉบับละเอียด + แคปภาพจริงจากคลิป — รูปเก็บไว้ในโฟลเดอร์ `images/3-How the Web Works/` ข้างไฟล์นี้

## 1) เปิดคลิป

![Title slide](images/3-How%20the%20Web%20Works/01-title.png)

Title slide "How the Web Works" — Mosh Hamedani, codewithmosh.com

จากนั้นตัดไปสไลด์ **URL ตัวอย่างที่ใช้ทั้งคลิป**:

![URL example](images/3-How%20the%20Web%20Works/02-url-example.png)

```
http://www.codewithmosh.com
```
Mosh ใช้ URL นี้เป็นตัวอย่างอ้างอิงตลอดทั้งคลิป

## 2) Resources — server เก็บอะไรบ้าง

![Resources list](images/3-How%20the%20Web%20Works/03-resources.png)

1. **Web pages (HTML documents)**
2. **Images**
3. **Video files**
4. **Fonts**

*(คำตอบของ "server เก็บอะไรไว้บ้าง" — ไม่ใช่แค่ไฟล์ HTML แต่รวมถึงรูป วิดีโอ และฟอนต์ด้วย ซึ่งแต่ละอย่างถูกเรียกผ่าน HTTP request แยกกันคนละตัว)*

## 3) Client คือใคร

![Client](images/3-How%20the%20Web%20Works/04-client.png)

ใช้ stock footage คนใช้มือถือ เพื่ออธิบายว่า **"Client"** คือฝั่งที่ขอข้อมูล — คนที่เปิดเบราว์เซอร์/แอปมือถือแล้วพิมพ์ URL หรือกดลิงก์

## 4) HTTP vs HTTPS

![HTTP vs HTTPS](images/3-How%20the%20Web%20Works/05-http-vs-https.png)

| Protocol | ความหมาย |
|---|---|
| HTTP | Hypertext Transfer Protocol — โปรโตคอลมาตรฐานที่ client กับ server คุยกัน |
| HTTPS | **HTTP + Encryption** (เข้ารหัสข้อมูลระหว่างทาง เพื่อความปลอดภัย) |

## 5) HTTP Request จริง (โค้ดที่ขึ้นจอ)

![GET request](images/3-How%20the%20Web%20Works/06-get-request.png)

```
GET /index.html HTTP/1.1
Host: www.codewithmosh.com
Accept-Language: en-us
```

- **`GET`** = HTTP method ที่ใช้ขอข้อมูล (ตรงข้ามกับ POST ที่ใช้ส่งข้อมูล)
- **`/index.html`** = path ของไฟล์ที่ต้องการบนเซิร์ฟเวอร์
- **`HTTP/1.1`** = เวอร์ชันของโปรโตคอล
- **`Host: www.codewithmosh.com`** = โดเมนปลายทางที่ request นี้จะส่งไปหา
- **`Accept-Language: en-us`** = บอก server ว่า client ต้องการเนื้อหาภาษาอะไร

## 6) Client → Server (diagram)

![Client server diagram](images/3-How%20the%20Web%20Works/07-client-server-diagram.png)

วงกลมฟ้า (Client) มีลูกศรชี้ไปวงกลมชมพูมีไอคอนเฟือง (Server) — นี่คือภาพสรุปว่า HTTP Request ที่เห็นข้อ 5 เดินทางจากฝั่งไหนไปฝั่งไหน

## 7) HTTP Response จริง (โค้ดที่ขึ้นจอ — แคปเวอร์ชันเต็มแล้ว)

![HTTP response](images/3-How%20the%20Web%20Works/08-http-response.png)

```
HTTP/1.1 200 OK
Date: 1 Jan 2021 09:00
Content-Type: text/html

<!DOCTYPE html>
<html>
    ...
</html>
```

- **`200 OK`** = HTTP status code บอกว่า request สำเร็จ (พื้นฐานของการอ่าน network response ใน DevTools)
- **`Date`** = วันเวลาที่ server ตอบกลับมา
- **`Content-Type: text/html`** = บอก browser ว่าเนื้อหาที่ส่งมาเป็นชนิดไฟล์อะไร (ในที่นี้คือ HTML) — *จุดนี้เก็บตกเพิ่มจากรอบก่อน เพราะรอบนี้จับภาพได้ชัดกว่าเดิม*
- ตามด้วยตัวเนื้อหา HTML จริงที่ส่งมาด้วยกันในก้อนเดียวกัน (response body)

## 8) DOM คืออะไร

![DOM](images/3-How%20the%20Web%20Works/09-dom.png)

สไลด์ **"DOM — Document Object Model"** — เนื้อหา HTML ที่ browser ได้รับมาจาก response จะถูกแปลงเป็นโครงสร้างที่เรียกว่า DOM เพื่อให้ browser นำไป render เป็นหน้าเว็บได้

## 9) โครงสร้าง HTML พื้นฐาน

![HTML skeleton](images/3-How%20the%20Web%20Works/10-html-skeleton.png)

```
<!DOCTYPE html>
<html>
    ...
</html>
```

- **`<!DOCTYPE html>`** = บอก browser ว่านี่คือเอกสาร HTML5
- **`<html>...</html>`** = tag ครอบเนื้อหาทั้งหมดของหน้าเว็บ

## 10) ไฟล์ HTML อ้างอิงถึง resource อื่นๆ ยังไง

![Resource arrows](images/3-How%20the%20Web%20Works/11-resource-arrows.png)

จากกล่องโค้ด HTML เดิม มีจุดสี 3 จุด (เหลือง / ฟ้า / ชมพู) แต่ละจุดมีลูกศรยิงไปหา server (ไอคอนเฟือง) — สื่อว่า **ภายในไฟล์ HTML เดียว อาจมีการอ้างอิงถึงไฟล์อื่นเพิ่ม** (เช่น รูปภาพ, CSS, JavaScript) และแต่ละไฟล์เหล่านั้น **ต้องยิง HTTP request แยกไปขอจาก server อีกรอบ** — จุดนี้เชื่อมกับ "Inspect network traffic using DevTools" ที่พูดถึงในคลิป intro บทที่ 1 (จะเห็น request หลายตัวพร้อมกันใน Network tab)

## 11) Render — จาก HTML ไปเป็นหน้าเว็บที่มองเห็น

![Render](images/3-How%20the%20Web%20Works/12-render.png)

กล่องโค้ด HTML (พร้อมจุดสี resource 3 จุด) → ลูกศรพร้อม label **"Render"** → ภาพหน้าเว็บจริงที่ประกอบเสร็จแล้ว

สรุป: **HTML + resources ที่โหลดมาครบ → ผ่านกระบวนการ Render ของ browser → กลายเป็นหน้าเว็บที่ผู้ใช้เห็นจริง**

## 12) วงจร Request/Response (สรุปทั้งหมด)

![Request response cycle](images/3-How%20the%20Web%20Works/13-request-response-cycle.png)

วงกลม **CLIENT** (ฟ้า, มีไอคอน DOM ข้างใน) ↔ วงกลม **SERVER** (ชมพู, ไอคอนเฟือง) มีลูกศร 2 เส้น:
- เส้นทึบ ชี้จาก Client → Server label **"REQUEST"**
- เส้นประ ชี้จาก Server → Client label **"RESPONSE"**

ไอคอนในวงกลม Client เปลี่ยนเป็นไอคอน **"DOM"** — สื่อว่า **หลัง client ได้รับ response กลับมา ก็จะแปลงเป็น DOM แล้วพร้อมสำหรับการ request รอบถัดไป** (เช่น ตอนคลิกลิงก์ไปหน้าอื่น หรือโหลด resource เพิ่ม) วนเป็น cycle นี้ไปเรื่อยๆ ซึ่งคือหัวใจของ "How the Web Works"

## สรุปที่ใช้ได้จริง (ภาพรวมทั้ง flow)

```
1. Client พิมพ์ URL (http://www.codewithmosh.com) หรือกดลิงก์
2. Client ส่ง HTTP Request → Server
   GET /index.html HTTP/1.1
   Host: www.codewithmosh.com
   Accept-Language: en-us
3. Server ประมวลผล แล้วส่ง HTTP Response กลับ
   HTTP/1.1 200 OK
   Date: 1 Jan 2021 09:00
   Content-Type: text/html
   (พร้อมเนื้อหา HTML)
4. Browser แปลง HTML ที่ได้รับเป็น DOM (Document Object Model)
5. ถ้า HTML อ้างอิงถึงไฟล์อื่น (รูป/CSS/JS) → ยิง request แยกไปขอเพิ่มอีกรอบ (ข้อ 2-3 วนซ้ำ)
6. เมื่อโหลด resource ครบ → Browser Render ออกมาเป็นหน้าเว็บที่มองเห็น
7. ทุกครั้งที่ผู้ใช้คลิกลิงก์/โหลดหน้าใหม่ → วนกลับไปข้อ 1-2 ใหม่ (Request/Response cycle)
```

### จุดเชื่อมกับงานจริงของ Aum
- **DOM** ตรงนี้คือรากฐานของ React เลย — React ก็คือเครื่องมือที่ช่วยจัดการ DOM ให้เราแบบ declarative แทนที่จะ manipulate DOM เองด้วยมือ
- **HTTP Request/Response + status code 200 + Content-Type** — ตรงกับที่ใช้ debug ตอนเรียก API/SSE ใน Firmware Airflow Dashboard project เป๊ะๆ พอเปิด DevTools → Network tab จะเห็น request/response แบบนี้จริงๆ
- **"HTML อ้างอิงไฟล์อื่นแล้วยิง request แยก"** — อธิบายว่าทำไมหน้าเว็บถึงมีหลาย request ใน Network tab พร้อมกัน (ไม่ใช่แค่ 1 request ต่อ 1 หน้า)
