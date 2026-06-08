# Blockflix Desktop — Releases

ที่เก็บ **release สาธารณะ** ของแอป **Blockflix Desktop** เท่านั้น (ไฟล์ติดตั้ง + อัปเดต + ลายเซ็น) — **ไม่มีซอร์สโค้ด**

> ซอร์สโค้ดอยู่ใน repo หลักซึ่งเป็น **private**: `blockflix/blockflix`

---

## repo นี้มีไว้ทำอะไร

Blockflix Desktop เป็นแอป **Tauri** (เดสก์ท็อป) ที่มี **auto-updater** ในตัว + ต้องให้ผู้ใช้ใหม่ดาวน์โหลดมาติดตั้งได้

- ทั้ง auto-updater และผู้ใช้ใหม่ต้องเข้าถึงไฟล์ release ได้ **โดยไม่ต้องล็อกอิน** → endpoint จึงต้องเป็น **สาธารณะ**
- โค้ดเป็น proprietary จึงเก็บไว้ใน repo private ส่วน repo สาธารณะนี้เก็บ **เฉพาะไฟล์ที่ build แล้ว + ลายเซ็น** เพื่อแจกจ่ายโดยไม่เปิดซอร์ส

---

## แต่ละ Release มีไฟล์อะไรบ้าง

| ไฟล์ | คำอธิบาย | มีทุก release? |
|---|---|---|
| `latest.json` | manifest บอก updater ว่ามีเวอร์ชันใหม่ + ที่อยู่ payload + ลายเซ็น | ✅ |
| `*_macos_*.app.tar.gz` (+`.sig`) | payload อัปเดต macOS (ARM + Intel) | ✅ |
| `*_windows_x64-setup.exe` (+`.sig`) | payload อัปเดต Windows | ✅ |
| `*_linux_amd64.deb` (+`.sig`) | payload อัปเดต Linux | ✅ |
| `*.dmg` / `*.msi` / `*.rpm` | **ตัวติดตั้งเต็ม** (สำหรับผู้ใช้ใหม่) | เฉพาะ **FULL release** |

---

## ผู้ใช้ใหม่ติดตั้งยังไง

1. ไปที่ **release ล่าสุดที่เป็น FULL** (มีไฟล์ `.dmg`/`.msi`/`.rpm`)
2. โหลดตัวติดตั้งตามแพลตฟอร์ม:
   - **macOS** → `*.dmg`
   - **Windows** → `*.msi`
   - **Linux** → `*.rpm` หรือ `*.deb`
3. ติดตั้ง แล้วแอปจะ **auto-update** เป็นเวอร์ชันใหม่ล่าสุดให้เองหลังจากนั้น

---

## auto-update ทำงานยังไง

1. แอปเช็ก `https://github.com/blockflix/desktop-releases/releases/latest/download/latest.json`
2. ถ้าเวอร์ชันใน `latest.json` ใหม่กว่าที่ติดตั้งอยู่ → ดาวน์โหลด payload
3. **verify ลายเซ็น** (minisign) เทียบกับ public key ที่ฝังในแอป
4. ติดตั้งทับแบบ **seamless** แล้วรีสตาร์ตเข้าเวอร์ชันใหม่

> ข้ามเวอร์ชันได้ — updater เด้งตรงไปเวอร์ชัน **ล่าสุด** เสมอ ไม่ไล่ทีละขั้น

---

## นโยบายการ release

- **ทุก release** → build *payload อัปเดต* เสมอ (ผู้ใช้เดิมได้ seamless update ทุกครั้ง)
- **FULL release** (มีตัวติดตั้ง `.dmg`/`.msi`/`.rpm`) → สร้างเฉพาะ **patch ที่ลงท้ายด้วย 0** (`0.2.10`, `0.2.20`, `0.2.30` …) เพื่อประหยัดเวลา/ทรัพยากร build
- **Override:** ถ้า commit ของ release มีคำว่า `[release-full]` → จะ **force build ตัวติดตั้ง** แม้ patch จะไม่ลงท้าย 0 (สำหรับสร้างตัวติดตั้งเฉพาะกิจให้ผู้ทดสอบใหม่)

---

## ความปลอดภัย

- ทุกไฟล์มี `.sig` (minisign) → แอป verify ก่อนติดตั้ง → กันการปลอม/แก้ไฟล์ระหว่างทาง
- **private signing key อยู่ใน CI secrets เท่านั้น** ไม่อยู่ใน repo นี้ → ไม่มีใครปลอม signed update ได้
- ไม่มี secret / API key อยู่ในไฟล์ release — ผู้ใช้ใส่ key ของตัวเองตอนใช้งาน

---

## การ build & publish (อัตโนมัติ)

GitHub Actions workflow **"Desktop Release"** ใน repo `blockflix/blockflix` (private):

1. trigger เมื่อ push tag `vX.Y.Z`
2. build 4 แพลตฟอร์ม (macOS ARM + Intel, Windows, Linux) — sidecar (PyInstaller) + webui + Tauri
3. push artifacts + `latest.json` มาที่ repo นี้ (ผ่าน `DESKTOP_RELEASES_TOKEN`)
4. publish + ตั้งเป็น `latest`

---

## License / สิทธิ์การใช้งาน

ไฟล์ติดตั้งในที่นี้ใช้ได้ **เพื่อการติดตั้งและอัปเดตแอป Blockflix Desktop อย่างเป็นทางการเท่านั้น** — ไม่ได้ให้สิทธิ์ในซอร์สโค้ด ซอร์สโค้ดของ Blockflix เป็น private และ **ไม่อนุญาตให้คัดลอก ดัดแปลง เผยแพร่ซ้ำ หรือทำงานต่อยอด** องค์ประกอบของบุคคลที่สามยังอยู่ภายใต้สัญญาอนุญาตของตนเอง

> The installer artifacts may be used only to install and update the official
> Blockflix Desktop application. They do not grant source-code rights. The
> Blockflix source code is private and is not licensed for copying, modification,
> redistribution, or derivative works. Third-party components remain governed by
> their own licenses.

---

<sub>ดูแลโดย **Blockflix** · ซอร์สโค้ด (private): <code>github.com/blockflix/blockflix</code></sub>
