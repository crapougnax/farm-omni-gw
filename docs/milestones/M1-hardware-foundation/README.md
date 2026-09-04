# Milestone 1: Hardware Foundation & Plug-and-Play Basic Station

- **GitHub Milestone:** [**M1: Hardware Foundation**](https://github.com/Quatrain/farm-omni-gw/milestone/1)
- **Status:** 🚀 Active
- **Target BOM:** < $50 (Benchtop Prototype)

---

## 🎯 Goal
Build a working, open-hardware, benchtop prototype gateway running **OpenWrt 23.05**, operating as a **LoRaWAN Basic Station**, and connected via **Wi-Fi** to upstream network servers (The Things Stack / ChirpStack), complete with a zero-touch onboarding captive portal.

---

## 💰 Milestone 1 Bill of Materials (BOM)

| Component | Part / Module | Source / Form Factor | Estimated Cost |
| :--- | :--- | :--- | :--- |
| **Host SoC Core Board** | MediaTek MT7628AN (128MB DDR2, 32MB SPI Flash, Wi-Fi 2.4 GHz) | Widora NEO / HLK-7628N SoM | **$8.50** |
| **LoRaWAN Concentrator**| Seeed Studio WM1302 (Semtech SX1302 + 2× SX1250) | Mini-PCIe form factor (SPI interface) | **$28.00** |
| **Carrier Interconnect** | Open-Hardware SPI Breakout / Adapter PCB | 2-layer PCB (JLCPCB) | **$3.50** |
| **Power Supply Stage** | 5V 2A USB-C input + AMS1117 / SY8089 3.3V 2A Buck | Clean 3.3V rail for SX1302 and MT7628 | **$2.50** |
| **RF Antenna** | 868 MHz / 915 MHz Half-Wave Dipole Antenna + SMA Pigtail | Linx ANT-868 / Taoglas TI.19 | **$6.00** |
| **TOTAL M1 PROTOTYPE** | | | **~$48.50** |

---

## 📋 Milestone Issues Roadmap

| Issue | Title | Status |
| :--- | :--- | :--- |
| [**#1**](https://github.com/Quatrain/farm-omni-gw/issues/1) | **feat(hardware): specify open-hardware host board & SX1302/SX1303 carrier BOM** | 📋 Open |
| [**#2**](https://github.com/Quatrain/farm-omni-gw/issues/2) | **feat(os): configure OpenWrt 23.05 target with SPI, Wi-Fi AP & client interfaces** | 📋 Open |
| [**#3**](https://github.com/Quatrain/farm-omni-gw/issues/3) | **feat(lora): integrate Semtech Basic Station & SX1302 HAL over SPI bus** | 📋 Open |
| [**#4**](https://github.com/Quatrain/farm-omni-gw/issues/4) | **feat(onboarding): zero-touch captive portal onboarding for Wi-Fi and LNS pairing** | 📋 Open |
| [**#5**](https://github.com/Quatrain/farm-omni-gw/issues/5) | **test(validation): benchtop validation of node uplink & packet forwarding over Wi-Fi** | 📋 Open |
