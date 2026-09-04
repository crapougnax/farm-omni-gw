# Open-Source Hardware & Software License Audit
### *Living BOM Compliance Matrix & Intellectual Property Register*

- **Repository License:** [**AGPL-v3**](../../LICENSE)
- **Governing Policy:** [**AGENTS.md (Section 2.C)**](../../AGENTS.md#c-open-source-license-verification-for-component-libraries-strict-rule)
- **Last Updated:** September 4, 2026
- **Status:** 🛡️ **100% COMPLIANT — ZERO PROPRIETARY BINARY BLOBS**

---

## 🎯 Purpose & Scope

Per the strict open-source mandate of **Farm Omni Gateway**, this living document audits every semiconductor component, module, peripheral transceiver, host driver, and firmware library across the Bill of Materials (BOM).

It enforces that:
1. All host drivers and HALs are compilable from public open-source codebases under permissive (BSD, MIT, Apache 2.0) or copyleft (GPL, LGPL, AGPL) licenses.
2. No hardware requires non-redistributable proprietary binary blobs or firmware binaries loaded into the Linux host kernel.
3. No vendor NDAs or proprietary commercial software agreements encumber the physical gateway or its digital twin data models.

---

## 📊 Comprehensive Component Compliance Matrix

| Sub-System | Hardware Component | Interface | Host Driver / HAL | License | Host Binary Blob? | Compliance Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Host Compute SoC** | **MediaTek MT7628AN** | Memory-mapped | Mainline Linux `arch/mips/ralink` + `mt76` Wi-Fi driver | **GPL-2.0 / ISC** | **NONE** (No runtime firmware blob needed) | 🟢 **APPROVED** |
| **LoRa Concentrator**| **Semtech SX1302 / SX1303** | High-speed SPI | Semtech `sx1302_hal` + `chirpstack-concentratord` | **BSD-3-Clause / MIT** | **NONE** (MCU microcode distributed as open C arrays) | 🟢 **APPROVED** |
| **Cellular Modem** | **Quectel EC200U-EU** | USB 2.0 (CDC) | Mainline `qmi_wwan` / `option.c` + `uqmi` | **GPL-2.0** | **NONE** on host (Firmware isolated on modem chip) | 🟢 **APPROVED** |
| **GNSS RTK Base** | **Quectel LC29H / u-blox F9P** | UART2 Serial | RTKLIB (`str2str`) + `gpsd` (`ubxtool`) | **BSD-2-Clause** | **NONE** (Standard open NMEA & RTCM3 streams) | 🟢 **APPROVED** |
| **Microclimate Bus**| **Maxim MAX13487 (RS-485)** | Hardware Auto-Dir| `libmodbus` (Modbus RTU) + Linux 8250 UART | **LGPL-2.1** | **NONE** (Pure hardware level transceiver) | 🟢 **APPROVED** |
| **Soil Dynamics Bus**| **2N7002 MOSFET (SDI-12)** | Open-Drain GPIO | Public SDI-12 v1.4 ASCII parser over UART/GPIO | **GPL-2.0 / Public** | **NONE** (Open agricultural standard) | 🟢 **APPROVED** |
| **Solar MPPT Stage** | **TI BQ24650 Controller** | Autonomous Analog| *Zero software required* (Hardware analog loop) | **Hardware Autonomous** | **NONE** (Zero firmware execution) | 🟢 **APPROVED** |

---

## 🔍 Detailed Component Audits

### 1. Host Compute Engine: MediaTek MT7628AN
- **Architecture**: MIPS 24KEc (580 MHz).
- **Kernel Upstream Status**: Fully integrated in upstream Linux kernel since v3.18.
- **Wi-Fi Driver Audit (`mt76`)**:
  - Mainline kernel driver: `drivers/net/wireless/mediatek/mt76/mt7603`.
  - **Blob Analysis**: Unlike MT7612E or newer Wi-Fi 6 chipsets that require firmware loaded into RAM at boot (`ath10k`, `brcmfmac`), the MT7628 MAC and Baseband Processor (BBP) are hardwired and directly memory-mapped into SoC registers (`MT7620_WIFI_BASE`). EEPROM RF calibration values are read as raw plaintext from the SPI flash `factory` partition.
  - **Verdict**: 100% open-source, zero proprietary binary blobs required.

---

### 2. 8-Channel LoRaWAN Concentrator: Semtech SX1302 / SX1303
- **Hardware Module**: Seeed Studio WM1302 / RAK5146 (Mini-PCIe form factor).
- **HAL & Driver Source**: Semtech official repository ([`github.com/Lora-net/sx1302_hal`](https://github.com/Lora-net/sx1302_hal)).
- **License**: **BSD-3-Clause** (Semtech Corporation).
- **Microcode Audit**: The SX1302 integrates an internal MCU for AGC (Automatic Gain Control) and packet arbitration. Semtech distributes the complete microcode hex tables directly in source header files (`loragw_sx1302_timestamp.c`), completely auditable and compilable with standard GCC toolchains.
- **Upstream Network Protocol**:
  - `chirpstack-concentratord`: **MIT License**.
  - `basicstation`: **BSD-3-Clause**.
- **Verdict**: Permissive, zero proprietary blobs, fully redistributable under AGPL-v3.

---

### 3. 4G LTE Cat 1 bis Modem: Quectel EC200U-EU
- **Baseband Architecture**: Unisoc UIS8910DM cellular SoC inside the encapsulated module.
- **Host Isolation Boundary**: The baseband RTOS executes strictly inside the shielded Quectel module.
- **Host Linux Drivers**:
  - USB Serial Driver: `drivers/usb/serial/option.c` (**GPL-2.0**).
  - Network Data Driver: `drivers/net/usb/qmi_wwan.c` (**GPL-2.0**).
  - Cellular Management: `uqmi` daemon (**GPL-2.0**) communicating via standard QMI protocols.
- **Verdict**: Zero host-side binary drivers. The cellular modem presents standard USB CDC interfaces.

---

### 4. Precision GNSS RTK Base Station: Quectel LC29H / u-blox ZED-F9P
- **Protocols Used**:
  - **NMEA 0183**: Standard ASCII telemetry.
  - **RTCM 3.3 (RTCM 10403.3)**: Standardized by the *Radio Technical Commission for Maritime Services*. Open standard for differential carrier phase corrections.
- **Caster Software**:
  - `RTKLIB` (`str2str`): **BSD-2-Clause** ([`github.com/tomojitakasu/RTKLIB`](https://github.com/tomojitakasu/RTKLIB)).
  - `gpsd` (`ubxtool`): **BSD-2-Clause**.
- **Avoided Pitfall**: Rejection of proprietary subscription-locked correction engines (Trimble RTX, NovAtel TerraStar).
- **Verdict**: 100% open-source software stack, zero binary dependencies.

---

### 5. Agricultural Field Buses: RS-485 (MAX13487) & SDI-12 (2N7002)
- **MAX13487 RS-485 Transceiver**: Pure hardware level shifter with internal auto-direction sensing. Requires no proprietary software driver. Handled via standard Linux UART and open-source `libmodbus` (**LGPL-2.1**).
- **SDI-12 Soil Probes**: Open specification governed by the SDI-12 Support Group (v1.4). Physical translation achieved via a generic discrete 2N7002 N-channel MOSFET circuit.
- **Verdict**: Hardware-level transparent integration. Zero vendor lock-in.

---

## 📋 Mandatory Audit Checklist for Future Milestone Components

Whenever a contributor or agent proposes a new component for Milestones 2 through 6:
- [ ] **License Check**: Are the Linux kernel drivers, user-space libraries, and HAL available under MIT, BSD, Apache, GPL, or LGPL?
- [ ] **Firmware Verification**: Does the device boot without requiring `/lib/firmware/<vendor>.bin` proprietary blobs?
- [ ] **NDA Check**: Can complete register maps, AT commands, and communication protocol specifications be published publicly without an NDA?
- [ ] **Upstream Reproducibility**: Can the package be built directly inside the vanilla OpenWrt buildroot from public source repositories?
- [ ] **Matrix Update**: This file (`docs/compliance/LICENSE_AUDIT.md`) must be updated with the audit results before the PR can be merged.
