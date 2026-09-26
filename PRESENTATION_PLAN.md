# Presentation Plan — Atelier de Flora (Team McKraken, GP02)

> แผนงานสำหรับทำ README (frontend / backend) และ presentation HTML สำหรับ JSD#13 Final Project
> ทุกคนในทีมช่วยเติมเนื้อหาส่วนของตัวเองได้ ช่องที่มี **`TODO`** = รอข้อมูล / รอคนรับผิดชอบ
> อัปเดตล่าสุด: 2026-09-26 · **วันพรีเซนต์: จันทร์ 2026-09-28** (freeze feature แล้ว เหลือ merge + ซ้อม)

---

## 1. งานที่ต้องทำ

| # | ชิ้นงาน | อยู่ที่ repo | branch | สถานะ |
|---|---|---|---|---|
| 1 | `README.md` frontend | `JittrinP/JSD13_Group_Project2_McKraken_sprint2` | `update-readme` | ✅ อัปเดต 2026-09-26 (AI Preview, order, admin dashboard) รอ commit + PR |
| 2 | `README.md` backend | `JittrinP/McKraken_sprint3_Backend` | `update-readme` | ✅ อัปเดต 2026-09-26 (AI Preview, Orders / Inventory / Dashboard API, env ใหม่) รอ commit + PR |
| 3 | Presentation HTML | `Mali-r/GP02-Data-system` (repo นี้) | `presentation` | ✅ ปรับธีม + จัดสไลด์ 00–08 แล้ว · ⏳ **เพิ่ม AI Preview** (ดูข้อ 6) |

ลำดับ: **README ก่อน** (รวบรวมข้อมูลให้ครบ + ทีมเข้าใจตรงกัน) → presentation ดึงเนื้อหาจาก README ไปทำเป็นสไลด์

### PR ที่ต้อง merge ก่อนวันพรีเซนต์ (ต้องมีคน review 2 คน)
| PR | repo | เนื้อหา | กระทบ demo |
|---|---|---|---|
| `custom-image-order` | backend + frontend | รูป AI ของช่อที่เซฟตามไปถึงตะกร้า / order + แก้ราคาช่อ custom ใน order เป็น ฿0 | ✅ ใช่ (demo ขั้น Purchases) — merge backend ก่อน |
| `sprint3-admin-dashboard` (Albert) | backend + frontend | การ์ด 4 ใบ + กราฟ Sale Statistic หน้า Admin Overview | ✅ ถ้าจะโชว์หน้า admin |
| `update-readme` | backend + frontend | README ล่าสุด | — |

### ข้อมูลจาก README ที่ใช้ทำสไลด์ได้เลย
| สไลด์ | ดึงจาก |
|---|---|
| 02 Feature | frontend README → ตาราง Feature ลูกค้า / แอดมิน + "สถานะการต่อ API" |
| 02 AI Preview | backend README → หัวข้อ "AI Preview (สรุป)" |
| 03 Tech stack | ตาราง Tech stack ของทั้ง 2 README |
| 04 Data route | backend README → ตาราง API, Data model, Design rules, การคิดราคา |
| 05 Auth | backend README → diagram Authentication |
| 07 Problem & Solution | backend README → Known issues (ใช้เป็นหัวข้อ "สิ่งที่จะทำต่อ" ได้) |

### Known issues (ควรแจ้งทีม — กระทบ demo)
- **Refresh token บน production ใช้ไม่ได้** — `/auth/refresh` ตั้ง cookie `sameSite: "strict"` → ข้ามโดเมน Vercel → Render ไม่ได้ → ผู้ใช้หลุด login หลัง 15 นาที (ของวิทวัส — ต้องถามก่อนแก้) ⚠️ ให้ login ใหม่ก่อนเริ่ม demo
- **AI Preview**: 3 รูป/วัน/คน, รูปละ 10–30 วิ, quota ฟรีของ Cloudflare ทั้งเว็บ reset 07:00 น. เวลาไทย, โควตาต่อคนเก็บใน memory (Render restart = รีเซ็ต)
- AI วาดจำนวน / ชนิดดอกไม่ตรงเป๊ะ (caption ใต้รูปบอกจำนวนจริง) · ช่อที่ Add to cart โดยไม่เซฟยังไม่มีรูปในตะกร้า / order
- `/payments/create-intent` รับ `amount` จาก frontend + ไม่ต้อง login
- Blog POST / PATCH / DELETE ยังไม่มี auth
- frontend ยังไม่มี route guard หน้า dashboard (แต่ backend ตรวจสิทธิ์ทุก API แล้ว)
- ~~Order API ยังไม่มี route~~ ✅ เสร็จแล้ว (สร้าง / ดู / ยกเลิก order + admin จัดการ order)

---

## 2. โครงสร้างเวลาของคลาส (35 นาที / กลุ่ม)

McKraken = **กลุ่ม #2 เวลา 14:00–14:35** (จาก `time and presentation structure.png`)

| ส่วนของคลาส | เวลา | หัวข้อของเรา |
|---|---|---|
| Introduction of group members | 5 นาที | 00 |
| 1) Project Concept — ทำไมเลือกขายสินค้านี้ | 20 นาที (รวม) | 01 |
| 2) Demo & Product features — highlight features | | 02 (+ live demo) |
| 3) Working Process — tech stack, authentication, เก็บข้อมูล, problem & solution | | 03, 04, 05, 06, 07 |
| 4) BSM ที่ใช้ในการทำโปรเจกต์ | | 08 |
| Feedback / Q&A | 10 นาที | — |

### เวลาที่แนะนำต่อหัวข้อ (20 นาทีของ project) — `TODO` ทีมปรับได้

| # | หัวข้อ | นาที | ผู้พูด |
|---|---|---|---|
| 00 | Introduction group members | 5 (แยก) | ทุกคน ~1 นาที/คน |
| 01 | Overview & Concept | 2 | `TODO` |
| 02 | Feature + **Live Demo** (Custom design + AI Preview, AI chatbot) | 6.5 | `TODO` |
| 03 | Tech stack | 2 | `TODO` |
| 04 | Data route (ER diagram + API) | 2.5 | `TODO` |
| 05 | Auth explanation | 2 | `TODO` (น่าจะวิทวัส — ทำ auth) |
| 06 | Working Process (Sprint / Miro / Git) | 1.5 | `TODO` |
| 07 | Problem & Solution | 2.5 | `TODO` |
| 08 | BSM | 1 | `TODO` |

---

## 3. ทีม (จาก Miro Sprint 2–3) — `TODO` ทุกคนเช็คชื่อ/บทบาท/รูป

| สมาชิก | งานหลัก (จาก kanban) |
|---|---|
| **Jittrin P. (base)** | Cart (model/routes/frontend), Custom design (model/routes/frontend, preset 1–5), **AI chatbot (RAG)**, **AI Preview (รูปช่อ custom)**, Admin Overview, Footer, PopShopBlog, ShopBlog page |
| **Albert Phonbut** | Login / Register / ForgetPassword / RenewPassword (UI), Address (model/routes/frontend), Review, **Stripe PromptPay payment**, Blog model, Admin order, **Admin dashboard (การ์ด + กราฟ)**, AsideAdmin, Cart page UI |
| **Maliwan Rodsomrit** | Landing page, Customer dashboard (Account, Aside), Checkout, OrderConfirmed, OrderList, Blog CRUD, Product model + search, ContentEdit, ShopBlog/Products page API, 3D drag to rotate, **presentation HTML เวอร์ชันแรก** |
| **วิทวัส ภิระบรรณ์** | NavBar, Products page, PopProducts, PurchasesItems, ContentEdit (S2), **Auth backend + frontend** (login/register/logout/forget/reset/edit password), Product CRUD |
| **Poramet N.** | Homepage, CustomerAddress, ProductEdit (admin), Inventory items, Order model/routes, Custom product frontend (3D model) |

> ต้องการจากแต่ละคน: ชื่อที่จะแสดง, บทบาทสั้นๆ 1 บรรทัด, รูป (หรือใช้ตัวอักษรย่อแทน), feature ที่ภูมิใจที่สุด 1 อย่าง (ในสไลด์ 00 มีแล้วบางคน)

---

## 4. เนื้อหาแต่ละหัวข้อ (สำหรับ presentation)

แต่ละหัวข้อ: **เป้าหมาย** / เนื้อหาหลัก / ภาพประกอบ / แหล่งข้อมูล

### 00 · Introduction group members
- การ์ดสมาชิก 5 คน: รูป, ชื่อ, บทบาท, feature หลัก — ✅ มีในสไลด์ `#team` แล้ว (เพิ่ม AI Preview ในการ์ดของ base)
- ชื่อทีม McKraken + ชื่อร้าน **Atelier de Flora**

### 01 · Overview & Concept
- ร้านดอกไม้ออนไลน์: ซื้อช่อสำเร็จรูป + **ออกแบบช่อเอง (custom)** + AI ช่วยแนะนำ + **AI วาดรูปช่อให้ดูก่อนซื้อ**
- **ทำไมเลือกขายดอกไม้** — ✅ มีในสไลด์ `#concept` แล้ว (ของขวัญเป็นส่วนตัว, เลือกไม่เป็น, มีโอกาสซื้อทั้งปี, โจทย์เทคนิค recipe + inventory)
  - เพิ่มได้: ลูกค้า custom ช่อเองแต่ **นึกภาพไม่ออกว่าจะออกมาหน้าตาแบบไหน** → AI Preview
- กลุ่มผู้ใช้: ลูกค้า (customer) / แอดมิน (admin)
- ลิงก์เว็บจริง: Vercel `https://jsd-13-group-project2-mc-kraken-spr.vercel.app`

### 02 · Feature + Live Demo
**Feature ทั้งหมด (สรุปสั้น):**
- ลูกค้า: สมัคร/login/ลืมรหัสผ่าน, ดูสินค้า + search/filter, ตะกร้า + gift note, checkout + จ่าย PromptPay (Stripe), customer dashboard (บัญชี, ที่อยู่, ช่อที่เซฟพร้อมรูป, ประวัติสั่งซื้อ + ยกเลิก), Shop blog, รีวิว
- แอดมิน: Overview (การ์ด + กราฟยอดขาย / สถานะ order / Top 5 ดอก / Recent order), จัดการสินค้า/วัตถุดิบ (CRUD), รายการ order (ค้นหา / กรอง / เปลี่ยนสถานะ), จัดการ content, **ปุ่ม Sync AI**

**Highlight (ใช้ demo จริง):**
1. **Custom design** — เลือก base + ดอกไม้ 3 ชนิด + จำนวน, preview 3D (ลากหมุนได้), เซฟเป็น preset 1–5, แก้ไขจาก dashboard, ใส่ตะกร้า (ราคา = วัตถุดิบ + service fee ฿100)
2. **AI Preview** *(ใหม่)* — ปุ่ม Preview → AI (Cloudflare FLUX.2) วาดรูปช่อสมจริงแทนโมเดล 3D
   - prompt สร้างที่ backend จากชื่อ/สีวัตถุดิบใน DB (ลูกค้าพิมพ์ prompt เองไม่ได้) · ไซส์ S/M/L ตามจำนวนดอก, M/L แนบรูป reference จากโมเดล 3D
   - caption ใต้รูปบอกจำนวนดอกจริง · เปลี่ยนตัวเลือกหลัง preview → ป้ายเตือน "รูปไม่ตรงกับช่อ"
   - history 10 รูปล่าสุดใน localStorage → ช่อเดิมไม่เสียโควตา · 3 รูป/วัน/คน
   - **Save** → รูปขึ้น Vercel Blob ติดไปกับช่อ (Custom List) → Add to cart → order ก๊อปรูปเก็บเป็นของตัวเอง (order = snapshot)
3. **AI chatbot "Ask AI"** — ถามสินค้า/ราคา, **"ช่วยจัดช่อ custom ให้แม่ งบ 800"** (ฟอร์ม 2 ช่อง: ให้ใคร/โอกาส + งบ), ถามตะกร้า/ช่อที่เซฟของตัวเอง, ถามต่อเนื่องได้ → ปุ่ม **Generate preview** พาไปหน้า Custom design + สร้างรูปให้อัตโนมัติ

**Demo script** (`TODO` ซ้อมจับเวลา ~4.5 นาที):
1. login → Ask AI → "ช่วยจัดช่อ custom ให้แม่ งบ 800" → ชี้วิธีคิดราคา → กด **Generate preview**
2. หน้า Custom design เติมตัวเลือกให้ + ได้รูป AI (ใช้รูปใน history ที่เตรียมไว้ → ขึ้นทันที) → ลองเปลี่ยนดอก 1 ชนิด → ป้ายเตือน → กดรูปใน history กลับมา
3. **Save** preset → เปิด Custom List เห็นรูป → Add to cart → ตะกร้ามีรูป
4. ถาม Ask AI "ตะกร้าของฉันรวมเท่าไหร่" → เทียบกับหน้า Cart
5. Checkout → QR PromptPay (Stripe test mode) → Purchases เห็นรูป + ราคาถูกต้อง
- ⚠️ **เตรียมก่อนวันพรีเซนต์**: login บัญชี demo แล้ว Preview ช่อที่จะใช้ไว้ล่วงหน้า (รูปอยู่ใน history → กดแล้วขึ้นทันที ไม่ต้องรอ 10–30 วิ ไม่เสียโควตา) · ใช้ browser / บัญชีเดียวกับตอนเตรียม
- ⚠️ แผนสำรอง: อัดวิดีโอ demo ไว้ก่อน (Render free tier หลับ / quota AI หมด / เน็ตล่ม)
- ⚠️ อย่าเทส AI รัวๆ วันพรีเซนต์ — quota รายวันของ Gemini reset 14:00 น. (ตรงกับเวลาพรีเซนต์พอดี) · Cloudflare reset 07:00 น.

### 03 · Tech stack
| ชั้น | เทคโนโลยี |
|---|---|
| Frontend | React 19, Vite, Tailwind CSS v4, shadcn/ui, React Router v7, axios, recharts, `@google/model-viewer` (3D) |
| Backend | Node.js, Express 5, Mongoose 9, JWT (`jsonwebtoken`) + `cookie-parser`, bcrypt |
| Database | MongoDB Atlas (DB `FlowerShop`) + **Atlas Vector Search** |
| Payment | Stripe (PromptPay QR) |
| AI chatbot | Google Gemini (`gemini-embedding-001`, `gemini-3.5-flash` / `flash-lite` + fallback models) |
| AI Preview | **Cloudflare Workers AI** — FLUX.2 klein 4B (free tier) |
| File storage | **Vercel Blob** (รูปช่อที่เซฟ / order — DB เก็บแค่ URL) |
| Deploy | Vercel (frontend) + Render (backend) |
| Tools | Git/GitHub (branch → PR → review → merge), Miro (sprint kanban), Figma (design), Claude Code |
- ภาพ: diagram Browser (Vercel) → API (Render) → MongoDB Atlas / Stripe / Gemini / **Cloudflare / Vercel Blob**
- สไลด์ `#tech` ยังไม่มี Cloudflare + Vercel Blob → เพิ่ม (ข้อ 6)

### 04 · Data route
- **ER diagram** (`assets/er-diagram.png`) + design rules:
  ทุกอย่างที่ขาย = product / order = snapshot ราคา (**และรูป**) / ช่อ custom เก็บใน `custom_specs` ไม่สร้าง product ใหม่ / inventory = ใช้ภายในร้าน
- Collections: users (ฝัง shipping_addresses, saved_custom_designs + `preview_image_url`), products, inventory_items, carts, orders (+ `custom_specs.preview_image_url`), blog, reviews, ai_knowledge
- API หลัก (`/api/v1`): `/auth`, `/products`, `/inventory-items`, `/cart`, `/custom-design`, `/orders`, `/user/address`, `/payments`, `/dashboard`, `/blog`, `/review`, `/ai` (ask, sync, **preview, preview/quota**)
- Flow ตัวอย่าง: **Add to cart → GET /cart (backend คิดราคา) → Checkout → Stripe → POST /orders (snapshot + ล้างตะกร้า)**
- Flow รูป: **Preview (data URL, ยังไม่เก็บ) → Save → Vercel Blob (URL ใน user) → POST /orders ก๊อปรูปเป็นไฟล์ของ order**

### 05 · Auth explanation
- Register → hash password (bcrypt) → Login → backend สร้าง **accessToken (15 นาที)** + **refreshToken (7 วัน)** เก็บใน **httpOnly cookie** (JavaScript อ่านไม่ได้ กัน XSS)
- ทุก request ส่ง cookie อัตโนมัติ (`withCredentials`) → middleware `authen` ตรวจ token → `authorize(["admin"])` แยกสิทธิ์
- accessToken หมดอายุ → axios interceptor ยิง `/auth/refresh` ให้เอง → ผู้ใช้ไม่ต้อง login ใหม่
- เปิดเว็บ → `GET /auth/me` เช็คว่ายัง login อยู่ไหม
- userId มาจาก token เสมอ ไม่รับจาก URL/body (เช่น cart, custom design, order, AI, โควตา preview ดูได้แค่ของตัวเอง)
- `TODO` วิทวัสเช็ค/เติม: forget/reset password flow

### 06 · Working Process
- Sprint 1–3 บน **Miro kanban** (Backlog → ToDo → In Progress → Code Review → Testing → Done) แต่ละการ์ดมี assignee + วันที่
  - Sprint 1: concept, ER diagram, UI + design system บน Figma
  - Sprint 2: UI / pages / components (mock data)
  - Sprint 3: models + routes + ต่อ API จริง + payment + order + admin dashboard + AI chatbot + AI Preview
- Git flow: แยก branch ต่อ feature → PR → **review 2 คน** → merge เข้า main (frontend PR 84+, backend PR 37+)
- Feature ใหญ่ (AI chatbot, AI Preview) เขียนแผนเป็นไฟล์ก่อน (`AI_CHATBOT_PLAN.md`, `AI_PREVIEW_PLAN.md`) + **ทดสอบ API ฟรีก่อนลงมือ (Phase 0)**
- การสื่อสาร: Discord + Slack · ประชุม จันทร์ / พุธ / ศุกร์ + นัดเพิ่มได้เมื่อจำเป็น (โดยเฉพาะช่วงวางแผนแรกๆ) · daily stand-up แต่ละคนอัปเดตส่วนของตัวเอง ✅ ใส่ในสไลด์แล้ว
- แบ่งงาน: ทุกคน full-stack รับ feature ไปทำครบ design → frontend → backend
- กันงานชนกัน: วางแผนเป็นภาพด้วย diagram, ตกลงการแบ่งไฟล์ / ชื่อไฟล์ / วิธีส่งข้อมูลก่อนเริ่ม, ไฟล์ที่ใช้ร่วมกัน (router, layout) ทำร่วมกัน
- Figma → ออกแบบ UI + design system ก่อนเขียนโค้ด

### 07 · Problem & Solution
เลือก 4–5 ข้อที่เล่าได้ดี (`TODO` แต่ละคนเสนอปัญหาของส่วนตัวเองอย่างน้อย 1 ข้อ)

| ปัญหา | ทางแก้ | ของใคร | ในสไลด์ |
|---|---|---|---|
| ราคาในหน้าเว็บคิดที่ frontend → ปลอมราคาได้ / ไม่ตรงกัน | ให้ backend คิดราคา (`utils/pricing.js`) GET /cart ส่งยอดมาให้ + order เก็บ snapshot | base | ✅ |
| ส่ง userId ใน URL → แก้ URL ดูข้อมูลคนอื่นได้ | เอา userId จาก JWT (`req.user.userId`) แทน | ทีม | ✅ |
| token หมดอายุ 15 นาทีแล้ว request ที่ใช้ `fetch` พัง | ใช้ axios instance ที่มี interceptor refresh token | ทีม | ✅ |
| วาง feature ไว้เยอะเกิน | ตัดบาง feature (Favorite, Dynamic Custom Design) | ทีม | ✅ |
| AI (flash-lite) จัดช่อเกินงบ / คิดเลขผิด | ให้แสดงวิธีคิด + ใช้ model ใหญ่เฉพาะคำถามจัดช่อ + fallback | base | ✅ |
| merge conflict ตอนหลายคนแก้ไฟล์กลาง (Layout, routes/index) | แยก component + แก้ไฟล์กลางให้น้อยที่สุด + แจ้งใน PR | ทีม | ✅ |
| หน่วยราคาไม่ตรงกัน ($ / THB) | เปลี่ยนเป็น ฿ ทั้งเว็บ (PR #73) | base | — |
| seed ใหม่ `_id` เปลี่ยน → id ที่ hardcode / AI หาสินค้าไม่เจอ | ดึงจาก API แทน hardcode + ปุ่ม Sync AI | base / Poramet | — |
| ข้อมูลส่วนตัวรั่วผ่าน AI | ไม่ embed ข้อมูลส่วนตัว ดึงสดตาม token เท่านั้น (ทดสอบ prompt injection แล้ว) | base | — |
| **Gemini free tier สร้างรูปไม่ได้ (`limit: 0`)** | ทดสอบก่อนสร้าง (Phase 0) → เปลี่ยนไปใช้ Cloudflare Workers AI (ฟรี ~90 รูป/วัน) | base | ⏳ เพิ่ม |
| **AI วาดจำนวนดอกไม่ตรง / seed เดิมได้รูปไม่เหมือนเดิม** | ไซส์ S/M/L + แนบรูป reference · caption บอกจำนวนจริง · เก็บ history ในเครื่อง (ช่อเดิมไม่สร้างใหม่) | base | ⏳ เพิ่ม |
| **เก็บรูปใน MongoDB → document ใหญ่ / โหลดช้า** | เก็บไฟล์บน Vercel Blob, DB เก็บแค่ URL · อัปเฉพาะตอน Save | base | ⏳ เพิ่ม |
| **ลบช่อแล้วรูปใน order เก่าหาย** | order ก๊อปรูปเป็นไฟล์ของตัวเอง (order = snapshot) | base | ⏳ เพิ่ม |

### 08 · BSM (Behavior, Skill, Mindset)
อ้างอิง `assets/bsm.png` — ✅ มีในสไลด์ `#bsm` แล้ว ให้แต่ละคนเช็คตัวอย่างของตัวเอง

| หมวด | หัวข้อจากคลาส | ตัวอย่างจากโปรเจกต์ |
|---|---|---|
| Mindsets | Growth Mindset, Persistence, Personal Responsibility, Future Orientation | เรียน RAG / vector search / image AI ใหม่แล้วนำมาใช้จริง |
| Behavioral skills | Proactiveness, Time Management, Teamwork, Orientation to details, Communication | แจ้งในทีมก่อนแก้ไฟล์ของเพื่อน, ใช้ Miro จัด sprint, freeze feature ก่อนพรีเซนต์ |
| Technical skills | JS, React, Node/Express/MongoDB, Final Project, AI Session | เชื่อมกับ tech stack หัวข้อ 03 |

---

## 5. Design system (ตาม Figma = ตรงกับ `index.css` ของ frontend)

| Token | ค่า | ใช้กับ |
|---|---|---|
| primary | `#586158` | หัวข้อ, ปุ่ม, เส้นเน้น |
| secondary | `#F9F6F0` | พื้นหลังการ์ด |
| accent / tertiary | `#F3F3F0` | พื้นหลัง section สลับ |
| neutral | `#4A4A4A` | ตัวอักษรหลัก |
| background | `#FBF9F8` | พื้นหลังหน้า |
| destructive | `#8F4748` | ปัญหา / คำเตือน (หัวข้อ 07) |
| border | `#929B91` (30%) | เส้นขอบการ์ด |

- ฟอนต์: **Literata** (serif) = หัวข้อ / **Plus Jakarta Sans** = เนื้อหา (Google Fonts)
- สไตล์: เรียบ นุ่ม โทนเขียวหม่น-ครีม แบบร้านดอกไม้
- ภาพประกอบ: screenshot จากเว็บจริง, ER diagram, `bsm.png`, รูปดอกไม้ในโปรเจกต์, **รูป AI Preview จริง** (ถ่ายจากเว็บ)

---

## 6. Presentation HTML

`atelier_de_flora_3d_visual_data_system_presentation.html` บน branch `presentation` (Mali อนุญาตแล้ว) · deploy ผ่าน Vercel ของ repo นี้

### ✅ ทำแล้ว
- เปลี่ยนธีมเป็น Literata + Plus Jakarta Sans / palette ข้อ 5
- สไลด์ตามลำดับ: `#title` → 00 `#team` → 01 `#concept` → 02 `#features`, `#filters`, ★ `#custom`, ★ `#ai`, `#demo` → 03 `#tech` → 04 `#data`, `#api` → 05 `#auth` → 06 `#process` → 07 `#problems` → 08 `#bsm` → `#thanks`
- nav ด้านบน + progress bar, การ์ด feature กดดูเส้นทางข้อมูล, API popup แยกตามหมวด, lightbox ขยายรูป

### ⏳ ต้องทำต่อ (อัปเดตเป็นเวอร์ชันปัจจุบัน)
| สไลด์ | แก้อะไร |
|---|---|
| `#title` | เพิ่ม tag AI Preview (Cloudflare) |
| `#team` | การ์ด base เพิ่ม AI Preview · Albert เพิ่ม Admin dashboard |
| `#features` | เพิ่มการ์ด AI Preview (ลูกค้า) และ Admin Overview ที่ต่อ API จริงแล้ว |
| **★ `#preview` (ใหม่)** | Highlight 3: AI Preview — flow Preview → history → Save (Blob) → cart → order + รูปจริงจากเว็บ + ตัวเลข (3 รูป/วัน, 10–30 วิ, S/M/L) — วางต่อจาก `#custom` |
| `#ai` | เพิ่มปุ่ม Generate preview + ฟอร์ม 2 ช่อง |
| `#demo` | ใช้ demo script ใหม่ (ข้อ 4 · 02) + เตรียมรูปใน history |
| `#tech` | เพิ่ม Cloudflare Workers AI + Vercel Blob ใน diagram และตาราง |
| `#data` / `#api` | preview_image_url ใน users / orders · หมวด `/orders`, `/inventory-items`, `/dashboard`, `/ai/preview` |
| `#process` | Sprint 3 เพิ่ม AI Preview · review 2 คน · จำนวน PR ล่าสุด · Phase 0 · เติม TODO การสื่อสาร |
| `#problems` | เพิ่ม 2–3 ข้อของ AI Preview (ตาราง 07 แถว ⏳) |

---

## 7. README — ✅ อัปเดตครบแล้ว (2026-09-26, branch `update-readme`)

> ยังไม่ได้ใส่: screenshot หน้าเว็บใน frontend README — เพิ่มทีหลังได้ตอนถ่ายภาพทำสไลด์
> มีหมายเหตุ "รอ merge" ในทั้ง 2 README → ลบออกหลัง PR `custom-image-order` และ `sprint3-admin-dashboard` merge

### Frontend (`Mckraken-sprint2/README.md`)
1. Atelier de Flora คืออะไร + ลิงก์เว็บ
2. Feature (ลูกค้า / แอดมิน / custom design / **AI Preview** / AI chatbot) + สถานะการต่อ API
3. Tech stack
4. โครงสร้างโฟลเดอร์ + routes
5. วิธีรัน (`npm install`, `.env` → `VITE_API_URL`, `npm run dev`)
6. Design system (สี/ฟอนต์)
7. ทีม + ใครทำส่วนไหน

### Backend (`McKraken_sprint3_Backend/README.md`)
1. ภาพรวม + ลิงก์ Render
2. Tech stack (+ Cloudflare Workers AI, Vercel Blob)
3. โครงสร้างโฟลเดอร์
4. ตาราง API ทั้งหมด (+ Orders, Inventory items, Admin dashboard, AI Preview)
5. Data model / ER + design rules + การคิดราคา
6. Auth flow
7. AI chatbot (สรุป) + **AI Preview (สรุป)**
8. Environment variables (ชื่อเท่านั้น ห้ามใส่ค่า)
9. วิธีรัน + seed + sync AI
10. Known issues + ทีม

---

## 8. คำถามที่ยังค้าง (ถามทีม)

1. ใครพูดหัวข้อไหน (ตารางข้อ 2)
2. ชื่อ/บทบาท/รูปของแต่ละคน (ข้อ 3)
3. ปัญหาของแต่ละคน + ตัวอย่าง BSM (ข้อ 07, 08)
4. ~~ช่องทางสื่อสารของทีม / ประชุมบ่อยแค่ไหน (ข้อ 06)~~ ✅ ได้คำตอบแล้ว
5. Live demo ใช้เว็บจริงบน Vercel หรือ localhost (+ อัดวิดีโอสำรอง) · ใช้บัญชี demo ไหน
6. วิทวัส: แก้ `sameSite` ของ refresh token เป็น `"none"` ทันพรีเซนต์ไหม (ดู Known issues ข้อ 1)
7. ทุกคนช่วย review + merge PR ในข้อ 1 ก่อนวันจันทร์ (ต้อง 2 คนต่อ PR)
8. ทุกคนช่วยอ่าน README ทั้ง 2 repo ว่าส่วนของตัวเองถูกต้องไหม (ตารางทีม, feature, API)
9. ~~Order API จะเสร็จทันไหม~~ ✅ เสร็จแล้ว · ~~เหตุผล "ทำไมเลือกขายดอกไม้"~~ ✅ มีในสไลด์แล้ว
