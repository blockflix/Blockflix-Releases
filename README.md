<div align="center">

# 🎬 Blockflix Desktop

### Build apps, websites, media, and research — with one AI hub.

**AI agent บนเดสก์ท็อปที่ "ลงมือทำงานจริง" จากเครื่องของคุณเอง**
เขียนโค้ด · สร้างแอป/เว็บไซต์ · วางแผนวิดีโอ-สื่อ · ออกแบบ UI · ทำ deep research · วิเคราะห์ตลาด · automate งาน

[![Latest Release](https://img.shields.io/github/v/release/blockflix/Blockflix-Releases?label=ดาวน์โหลดล่าสุด&color=6366f1)](https://github.com/blockflix/Blockflix-Releases/releases/latest)
![macOS](https://img.shields.io/badge/macOS-Apple%20Silicon%20%2B%20Intel-black?logo=apple)
![Windows](https://img.shields.io/badge/Windows-x64-0078D6?logo=windows)
![Linux](https://img.shields.io/badge/Linux-deb%20%2F%20rpm-FCC624?logo=linux&logoColor=black)

</div>

---

## ✨ Blockflix คืออะไร

**Blockflix** คือ **desktop-first AI agent** — ไม่ใช่แค่ "แชทบอท" แต่เป็น agent ที่ **วางแผน → ลงมือทำ → ตรวจสอบ → ย้อนได้** ทำงานบน **เครื่องของคุณเอง** ด้วย provider และคีย์ของคุณ พร้อม workspace ในเครื่องที่ความจำและไฟล์ทั้งหมดเป็นของคุณ

> หนึ่ง hub เดียว — สั่งให้สร้างแอป สร้างเว็บ ทำสื่อ ออกแบบ วิจัย และทำงานอัตโนมัติ ได้จบในที่เดียว

---

## 🚀 ทำอะไรได้บ้าง

| โหมด | ทำอะไร |
|---|---|
| 🛠️ **Work** | สร้างแอป/เว็บไซต์/มือถือ พร้อม UX flow, data model, build steps + **Live Preview** รันได้ทุก framework (Node, Flutter, React Native) เห็นผลสดในแอป |
| 🎞️ **Cinematic** | สร้างภาพ/วิดีโอ/สื่อ · Canvas node-graph ต่อ workflow สร้างสรรค์ · Works marketplace |
| 🤖 **Agent** | research → plan → execute → validate → สรุป จนจบงานเอง |
| 🧩 **Capabilities** | สร้าง/ติดตั้ง **skills**, **MCP servers**, custom API ที่ใช้ซ้ำได้ |
| 🔌 **Integrations** | เชื่อม 14 แพลตฟอร์มแชต — คุยกับ agent จากที่ไหนก็ได้ |

---

## 💡 ทำไม Blockflix ถึงต่าง

- 🏠 **Local-first** — รันบนเครื่องคุณ ใช้คีย์ของคุณเอง ความจำ + ไฟล์อยู่ในเครื่อง ไม่ส่งขึ้น cloud
- ✅ **Agent ที่ซื่อสัตย์** — มี **Plan pane** เห็นแผนงานอัปเดตสด · **Verify-before-done** ตรวจงานกับของจริง (ไฟล์บนดิสก์ + ผลคำสั่ง) ก่อนบอกว่า "เสร็จ" · **`/undo`** ย้อนการแก้ไฟล์ของ turn ล่าสุดได้
- 🧠 **Dream memory** — ความจำสองเฟส consolidate อัตโนมัติ (ดูดความรู้ + ตัดข้อมูลซ้ำ + archive ของเก่า)
- 🔒 **Sandboxed shell** — จำกัดสิทธิ์คำสั่ง (Seatbelt บน macOS / bwrap บน Linux) + กันอ่าน secret เช่น `~/.ssh`
- 🧰 **เครื่องมือครบ** — ไฟล์ · shell · web search/fetch · MCP · cron · subagent · parallel research · image generation · long-running tasks
- 🌐 **หลาย LLM provider** — Anthropic · OpenAI (+ Codex) · Gemini · Grok · Kimi · Azure · Bedrock · และ OpenAI-compatible อื่นๆ
- 💬 **14 ช่องทางแชต** — Telegram · Discord · Slack · WhatsApp · Feishu · Matrix · MS Teams · QQ · WeChat · WeCom · DingTalk · Email · MoChat · WebSocket

---

# 📦 Repo นี้ (Blockflix-Releases)

ที่เก็บ **release สาธารณะ** ของแอป Blockflix Desktop เท่านั้น (ไฟล์ติดตั้ง + อัปเดต + ลายเซ็น) — **ไม่มีซอร์สโค้ด** (โค้ดอยู่ใน repo `blockflix/blockflix` ที่เป็น private)

repo นี้มีไว้เป็น **endpoint สาธารณะ** ให้ทั้ง auto-updater และผู้ใช้ใหม่เข้าถึงไฟล์ release ได้โดยไม่ต้องล็อกอิน — โดยไม่ต้องเปิดซอร์สโค้ด

## ⬇️ ดาวน์โหลด & ติดตั้ง (ผู้ใช้ใหม่)

1. ไปที่ **[release ล่าสุด](https://github.com/blockflix/Blockflix-Releases/releases/latest)** (ตัวที่เป็น FULL มี `.dmg`/`.msi`/`.rpm`)
2. โหลดตัวติดตั้งตามแพลตฟอร์ม:
   - **macOS** → `*.dmg`  ·  **Windows** → `*.msi`  ·  **Linux** → `*.rpm` หรือ `*.deb`
3. ติดตั้ง แล้วแอปจะ **auto-update** เป็นเวอร์ชันใหม่ล่าสุดให้เองหลังจากนั้น

## 🔄 Auto-update ทำงานยังไง

1. แอปเช็ก `https://github.com/blockflix/Blockflix-Releases/releases/latest/download/latest.json`
2. ถ้าเวอร์ชันใหม่กว่า → ดาวน์โหลด payload → **verify ลายเซ็น** (minisign) กับ public key ที่ฝังในแอป
3. ติดตั้งทับแบบ **seamless** แล้วเข้าเวอร์ชันใหม่ (ข้ามเวอร์ชันได้ — เด้งตรงไปตัวล่าสุดเสมอ)

## 🗂️ ไฟล์ในแต่ละ Release

| ไฟล์ | คำอธิบาย | มีทุก release? |
|---|---|---|
| `latest.json` | manifest บอก updater ว่ามีเวอร์ชันใหม่ + payload + ลายเซ็น | ✅ |
| `*_macos_*.app.tar.gz` / `*-setup.exe` / `*.deb` (+`.sig`) | payload อัปเดต (mac/win/linux) | ✅ |
| `*.dmg` / `*.msi` / `*.rpm` | **ตัวติดตั้งเต็ม** สำหรับผู้ใช้ใหม่ | เฉพาะ **FULL release** |

## 🧭 นโยบายการ release

- **ทุก release** → build payload อัปเดตเสมอ (ผู้ใช้เดิมได้ seamless update)
- **FULL release** (มีตัวติดตั้ง) → เฉพาะ patch ที่ลงท้ายด้วย 0 (`0.2.10`, `0.2.20`, `0.2.30` …) เพื่อประหยัด build
- **Override:** commit ที่มี `[release-full]` → force build ตัวติดตั้งได้แม้ patch ไม่ลงท้าย 0

## 🔒 ความปลอดภัย

- ทุกไฟล์มี `.sig` (minisign) → แอป verify ก่อนติดตั้ง → กันปลอม/แก้ไฟล์ระหว่างทาง
- **private signing key อยู่ใน CI secrets** ไม่อยู่ใน repo นี้ → ปลอม signed update ไม่ได้
- ไม่มี secret / API key ในไฟล์ release — ผู้ใช้ใส่คีย์ของตัวเองตอนใช้งาน
- "Source code (zip/tar.gz)" ที่ GitHub แนบอัตโนมัติ = archive ของ repo สาธารณะนี้ (มีแค่ README) **ไม่ใช่ซอร์สโค้ดแอป**

## ⚙️ Build & publish (อัตโนมัติ)

GitHub Actions **"Desktop Release"** ใน repo `blockflix/blockflix` (private): push tag `vX.Y.Z` → build 4 แพลตฟอร์ม (sidecar + webui + Tauri) → push artifacts + `latest.json` มาที่นี่ → publish เป็น `latest`

---

## 📜 License / สิทธิ์การใช้งาน

ไฟล์ติดตั้งในที่นี้ใช้ได้ **เพื่อการติดตั้งและอัปเดตแอป Blockflix Desktop อย่างเป็นทางการเท่านั้น** — ไม่ได้ให้สิทธิ์ในซอร์สโค้ด ซอร์สโค้ดของ Blockflix เป็น private และ **ไม่อนุญาตให้คัดลอก ดัดแปลง เผยแพร่ซ้ำ หรือทำงานต่อยอด** องค์ประกอบของบุคคลที่สามยังอยู่ภายใต้สัญญาอนุญาตของตนเอง

> The installer artifacts may be used only to install and update the official Blockflix Desktop application. They do not grant source-code rights. The Blockflix source code is private and is not licensed for copying, modification, redistribution, or derivative works. Third-party components remain governed by their own licenses.

---

<div align="center">
<sub>🎬 <b>Blockflix</b> — desktop-first AI agent · สร้างและดูแลโดย Blockflix · ซอร์สโค้ด (private): <code>github.com/blockflix/blockflix</code></sub>
</div>
