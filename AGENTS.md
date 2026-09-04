# LLM Agent Instructions & Guidelines — Farm Omni Gateway (farm-omni-gw)

> **Audience**: AI Coding Agents & Human Pair Programming  
> **Platform**: OpenWrt Linux + MediaTek MT7628 + Semtech SX1302/SX1303 + Quectel EC200U + GNSS RTK  
> **Upstream Canonical Repository (SOA)**: `https://github.com/Quatrain/farm-omni-gw`  
> **Personal Contributor Fork**: `https://github.com/crapougnax/farm-omni-gw`  
> **License**: AGPL-v3

---

## 🧭 1. Base Guidelines & Primary Hierarchy

All AI coding agents interacting with this workspace **MUST** strictly load and adhere to the author's primary development rules, GitFlow protocol, and 3-tier forking architecture defined in:
👉 **[Author's Global AI Rules, Architecture Standards & GitFlow Protocol (AGENTS.md)](https://gist.github.com/crapougnax/47971b85aa73dd702f4372a89858111c)**

---

## 🏗️ 2. Project-Specific Architecture & Guidelines

### A. Core Architectural Philosophy
`farm-omni-gw` is an open-source, modular, ultra-frugal, off-grid IoT Edge Gateway engineered for precision agriculture (**Hey Brad**) and remote aquaculture (**fshry**):
- **BOM Target**: Under 100 $ base unit (sub-175 $ with centimeter-grade RTK Base).
- **Quad-Capability Edge Hub**:
  1. 8-channel LoRaWAN Concentrator (`SX1302`/`SX1303` over SPI).
  2. Resilient 4G LTE Cat 1 bis cellular backhaul (`Quectel EC200U` over USB).
  3. High-Precision GNSS RTK Base Station (`u-blox ZED-F9P` or `Quectel LC29H` over UART2 + PPS).
  4. Isolated Field Sensor Bus (`SDI-12` for soil moisture + `RS-485 Modbus RTU` for weather + pulse counter for rain gauges).
- **Frugal Off-Grid Solar Power**: 9-28V DC input with integrated MPPT solar charger (`TI BQ24650`) for 12V LiFePO4 batteries (sub-2.5W average power consumption).

### B. Documentation Requirements
Per Rule 1.C and 1.D, all documentation, hardware schematics descriptions, pinouts, and code comments MUST be written strictly in International English:
- **`README.md`**: High-level system overview, complete BOM matrix, architectural block diagrams.
- **`HOWTO.md`**: Step-by-step build, wiring, OpenWrt kernel configuration, ChirpStack setup, and NTRIP Caster streaming.

---

## 🛠️ 3. Verification & Build Commands

| Target | Command |
| :--- | :--- |
| **OpenWrt Firmware Build** | `make -j$(nproc) V=s` |
| **Concentratord Validation** | `chirpstack-concentratord -c /etc/chirpstack-concentratord/sx1302/concentratord.toml` |
| **RTCM3 Stream Verification** | `str2str -in serial://ttyS2:115200#rtcm3 -out stdout#rtcm3` |
