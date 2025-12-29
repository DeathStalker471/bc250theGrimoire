### **BC-250 Hardware Technical Manual**
**Last Updated: December 2025**

---

#### **1. Core SoC (System on Chip)**
*   **Model:** AMD BC-250 (7nm "Oberon" architecture).
*   **CPU:** Zen 2 Architecture | 6 Cores / 12 Threads.
*   **GPU:** RDNA 2 Architecture | 24 Active Compute Units (Cyan Skillfish gfx1013).

#### **2. Memory Subsystem (VRAM)**
*   **Type:** 16GB GDDR6 SGRAM (Unified).
*   **Manufacturer:** Micron.
*   **FBGA Marking:** `D9ZPM`.
*   **Part Number:** `MT61K512M32KPA-14` (Revision `:C` confirmed).
*   **Speed Rating:** 14 Gbps (Native 1750 MHz).
*   **Voltage:** 1.35V VDD/VDDQ | 1.8V VPP (Pump).
*   **Layout:** 8-chip octagonal array surrounding the APU die.

#### **3. Power Delivery & Telemetry**
*   **Primary DC Input (J1000):** 1x 8-pin PCIe Power Connector.
    *   **Pinout:** **GPU/PCIe standard** (+12V on Bottom/Clip side, GND on Top).
    *   **Warning:** Electrically incompatible with 8-pin CPU/EPS cables.
*   **Auxiliary Power (J2000, J2001):** 2x Molex BMI (Blind Mate Interface) Style K connectors.
*   **Voltage Test Points (On-PCB):**
    *   `VTB_VCORE`: APU Core Voltage.
    *   `VTB_3V`: 3.3V System Rail.
    *   `VTB_5V`: 5.0V System Rail.
*   **CMOS Battery:** Standard CR2032 3V Lithium Cell.

#### **4. Thermal Interface & Mechanical Specs**
*   **Heatsink Variants:**
    1.  **Split Fin:** Vertical gaps between fin rows.
    2.  **Solid 8-Row:** Continuous fin stack.
    3.  **Solid 9-Row:** Continuous fin stack; QR code on PCB silkscreen near J1000.
*   **Thermal Interface Material (TIM) Requirements:**
    *   **APU Die:** High-performance Phase Change Material (PTM 7950) or Thermal Paste.
    *   **VRAM Chips (8x):** **2.0mm** Thermal Pads or Thermal Putty.
    *   **VRMs (Voltage Regulators/Mosfets):** **1.5mm** Thermal Pads or Thermal Putty.
*   **Fasteners:**
    *   **Heatsink & Backplate Clamp:** 8x Phillips-head screws.
    *   **Rear I/O Shield & Bracket:** 4x Mini Phillips-head screws.

#### **5. Internal Expansion & Diagnostic Headers**
*   **M.2 Slot (M2_1):**
    *   **Bus:** PCIe 2.0 x2 (~1,000 MB/s bandwidth cap).
    *   **Support:** M.2 Key M (2280); Supports NVMe and SATA III SSDs.
*   **Trusted Platform Module (TPMS1):** 18-pin 2.0mm pitch header.
*   **SPI Flash Header (J4004):** 7-pin 2.54mm pitch (For external BIOS programming).
    *   *Top Row:* [ GND ] [ SCLK ] [ MOSI ] [ 10k Ohm to GND ]
    *   *Bottom Row:* [ VCC ] [ CS ] [ MISO ]
*   **Fan Headers:**
    *   `CPU_FAN1`: 4-pin PWM (Standard).
    *   `J4003`: 4x PWM/Tachometer signals (Signal only; no power pins).
*   **Diagnostic Audio (J5):** Unpopulated 4-pin `SPEAKER_1` header for PC system beeper.
*   **Telemetry Header (I2C_HEADER1):** 3-pin I2C ([SCL] [SDA] [GND]).

#### **6. Jumpers (Pin 1 indicated by White Triangle)**
*   **`AUTO_PWRON1` (Nearest to heatsink):**
    *   **Pins [1-2] Jumped:** Automatic power-on when AC is applied.
    *   **Pins [2-3] Jumped:** Manual power-on (Requires button press).
*   **`CLRCMOS1`:**
    *   **Pins [1-2] Jumped:** Normal operation.
    *   **Pins [2-3] Jumped:** Clear CMOS (Disconnects battery to reset settings).

#### **7. Physical I/O & Interaction**
*   **On-board Controls:**
    *   **Power Button:** Long tactile switch with integrated **Green LED**.
    *   **Reset Button:** Short tactile switch with integrated **Blue LED**.
*   **Rear Ports:**
    *   1x DisplayPort (Revision 1.2/1.4).
    *   1x 1GbE RJ45 Ethernet (Realtek RTL8111H).
    *   2x USB 2.0 (Lower stack).
    *   2x USB 3.0/3.1 (Upper stack).
*   **Audio Output:** No 3.5mm analog hardware. Digital audio only via DisplayPort LPCM.

---
**END OF TECHNICAL DOCUMENT.**