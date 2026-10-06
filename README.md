# Shams-Ol-Nahan-air-Gapped-Signing-Power-Bank
# 🔋 Shams al-Nahan (شمس‌النهان)

> **Discreet, Self-Powered Hardware Wallet Prototype**  
> An experimental research and prototyping project exploring an air-gapped signing device integrated into an insulated, self-powered portable enclosure.

---

## 📌 Project Overview

**Shams al-Nahan** (*The Concealed Sun*) is an experimental DIY hardware wallet architecture designed to explore:
- **Self-contained power delivery:** Operating independently without physical data connections (USB Data lines isolated).
- **Discreet enclosure design:** Integrating standard prototyping modules into a clean, durable, non-metallic housing.
- **Air-gapped transaction verification:** Communicating via optical data channels (QR codes) using an onboard camera and display.

> ⚠️ **Important Security & Safety Disclaimer:**  
> This repository is strictly for **research, educational, and prototyping purposes**.  
> - General-purpose microcontrollers (e.g., ESP32, RP2040) lack certified Secure Elements (SE/EAL6+) and must **never** be used to store real funds without dedicated cryptographic co-processors and comprehensive auditing.  
> - Lithium battery handling requires strict adherence to certified protection circuits (BMS/PCM). **Never modify or tap into battery packs without certified charge management and thermal separation.**

---

## 📐 High-Level Architecture
```text
+-------------------------------------------------------------------+
|                        Enclosure Housing                          |
|                                                                   |
|   +--------------------------+     +--------------------------+   |
|   |   Independent Certified   |     |    Air-Gapped Wallet     |   |
|   |     Power Bank Module    |     |      Core Subsystem      |   |
|   |                          |     |                          |   |
|   | [BMS + Lithium Cells]    |     | [Microcontroller Core]   |   |
|   | [5V Regulated Output]    |---->| [OLED / Display Unit]    |   |
|   |                          | (5V)| [Optical Camera Module]  |   |
|   +--------------------------+     | [Nav / Touch Input]      |   |
|                                    +--------------------------+   |
|                                                                   |
|   ================ Thermal & Physical Isolation Barrier ========= |
+-------------------------------------------------------------------+
🛠 Hardware Specifications (Candidate Prototype)

Component Subsystem	Candidate Component	Function & Role
Main Processing Core	ESP32-WROOM-32 / RP2040	Execution of open-source wallet firmware & key handling
Cryptographic Co-Processor (Planned)	ATECC608A / SE050	Hardware-grade key isolation and true random number generation
Optical Scanner	ESP32-CAM / OV2640 Sensor	Reading raw PSBT (Partially Signed Bitcoin Transactions) via QR
Display Unit	0.96" Monochrome I2C OLED	Displaying verification prompts and signing QR codes
User Input	Sealed tactile buttons / Touch sensor	Physical transaction confirmation
Enclosure & Power	Flame-retardant ABS Case + Certified 5V Power Supply	Mechanical protection, power isolation, and discreet layout
🔒 Security Principles
Galvanic Data Isolation:The device operates strictly in an air-gapped configuration. Data enters solely through camera input (animated QR) and exits through the display.
Physical & Thermal Partitioning:The MCU/crypto chamber is physically shielded from the battery/charging circuitry using fire-resistant Kapton barriers and isolated mounting posts to prevent thermal transfer and short circuits.
No Wireless Transmissions:All wireless peripherals (Wi-Fi, Bluetooth) are disabled at the firmware bootloader stage to prevent remote vector exploitation.
Separated Power Circuitry:Power is tapped strictly from standard regulated 5V outputs with overcurrent protection—no undocumented direct cell taps.

📂 Repository Structure
text
├── docs/                     # Schematics, safety calculations, and architectural notes
├── firmware/                 # Source code for transaction parsing and display UI
│   ├── src/
│   └── test/
├── hardware/                 # CAD files, 3D mounting brackets, and wiring diagrams
│   ├── cad/
│   └── schematics/
├── LICENSE                   # Open-source license (MIT / Apache 2.0)
└── README.md                 # Project root documentation
🗺 Roadmap
[x] Concept definition & threat modeling.
[ ] Breadboard integration test (Camera + OLED + QR parser).
[ ] Testnet PSBT signing validation (Bitcoin/EVM test networks).
[ ] Design custom 3D internal mounting chassis with thermal clearance.
[ ] Hardware cryptographic co-processor integration (Secure Element).
[ ] Independent code and security review.
📄 License & Contribution
Distributed under the MIT License. Contributions, peer reviews, and security critiques are welcome via Issues and Pull Requests.

---

### دریافت نسخه فایل مستندات:
اگر برای آرشیو یا ارائه نیاز به فایل خروجی داری:
* **[دانلود نسخه PDF](https://gapgpt.app/api/v1/canvas_pdf/e6dbca25-2594-4228-9648-0a280de0392f.pdf)**
* **[دانلود نسخه Word (DOCX)](https://gapgpt.app/api/v1/canvas_docx/e6dbca25-2594-4228-9648-0a280de0392f.docx)**
