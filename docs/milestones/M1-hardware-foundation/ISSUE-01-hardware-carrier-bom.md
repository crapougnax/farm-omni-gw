# Issue #1: Specify Open-Hardware Host Board & SX1302/SX1303 Carrier Bill of Materials (BOM)

- **Milestone:** M1: Hardware Foundation
- **Type:** Hardware / Specification
- **Component:** Core Carrier Board & Power Architecture

---

## 🎯 Objective
Define and source the foundational open-hardware components for the benchtop prototype gateway:
- Pair an affordable MediaTek MT7628 Linux core board with a Semtech SX1302 LoRa concentrator module.
- Design the carrier interconnect pinout (SPI, Reset, Power) to enable zero-wire breadboarding and custom PCB routing.

---

## 🏗️ Hardware Architecture & Schematics
1. **Host SoC Selection**:
   - MediaTek MT7628AN System-on-Module (SoM) with 128MB DDR2 RAM, 32MB SPI NOR flash, integrated 2.4 GHz 802.11n Wi-Fi.
   - 2mm header pinout exposing SPI (`CLK`, `MOSI`, `MISO`, `CS0`), UART0/1/2, USB 2.0, and GPIOs.
2. **Concentrator Interface**:
   - Mini-PCIe socket wired for SPI transport (pins 8, 10, 14 for reset, power, and SPI signals).
   - Dedicated 3.3V / 2A low-ripple power rail (SX1302 draws up to 1.5A peak during calibration).

---

## 📋 Acceptance Criteria
- [ ] Complete BOM with distributor links (LCSC, Mouser, Seeed) documented under `docs/hardware/bom.md`.
- [ ] Schematics and pinout mapping matrix committed for MT7628 to WM1302 connection.
- [ ] Hardware prototype components procured and validated on lab bench.
