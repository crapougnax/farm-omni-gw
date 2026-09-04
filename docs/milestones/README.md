# Engineering Roadmap & Milestones — Farm Omni Gateway

This directory outlines the progressive engineering milestones to transition from an initial open-hardware benchtop prototype to a fully autonomous, solar-powered, multi-modal farm digital twin edge station.

---

## 🗺️ Master Milestone Roadmap

| Milestone | GitHub Link | Focus & Deliverables | Target BOM | Status |
| :--- | :--- | :--- | :--- | :--- |
| **M1: Hardware Foundation** | [**Milestone 1**](https://github.com/Quatrain/farm-omni-gw/milestone/1) | **OpenWrt Plug & Play Prototype** : MT7628 + SX1302 LoRaWAN Basic Station connected via Wi-Fi with captive portal onboarding. | **~$48.50** | 🚀 **Active** |
| **M2: Cellular 4G/5G Connectivity** | [**Milestone 2**](https://github.com/Quatrain/farm-omni-gw/milestone/2) | **Cellular Backhaul** : Integrated LTE Cat 1 bis modem (Quectel EC200U), automatic QMI reconnect watchdog, multi-WAN failover. | **+$8.00** | 📋 Planned |
| **M3: Satellite Connectivity** | [**Milestone 3**](https://github.com/Quatrain/farm-omni-gw/milestone/3) | **Off-Grid Space Uplink** : Direct-to-satellite LoRaWAN (LR-FHSS) and Astrocast/Iridium satellite backhaul for 100% white-zone autonomy. | **+$72.00** *(optional)* | 📋 Planned |
| **M4: Photovoltaic Solar Power** | [**Milestone 4**](https://github.com/Quatrain/farm-omni-gw/milestone/4) | **Off-Grid Solar Stage** : Integrated TI BQ24650 MPPT controller, 12V LiFePO4 battery management, and sub-2.2W power budgeting. | **+$65.00** | 📋 Planned |
| **M5: GPS RTK Modular Extensibility** | [**Milestone 5**](https://github.com/Quatrain/farm-omni-gw/milestone/5) | **Centimeter Precision Base** : Dual-band GNSS RTK receiver (LC29H / ZED-F9P), RTCM3 generation, and local/remote NTRIP Caster. | **+$45.00** | 📋 Planned |
| **M6: Weather Station Extensibility** | [**Milestone 6**](https://github.com/Quatrain/farm-omni-gw/milestone/6) | **Field Sensors Suite** : Isolated SDI-12 multi-depth soil probes, RS-485 ultrasonic wind/solar pyranometer, tipping bucket rain gauge. | **+$110.00** | 📋 Planned |

---

## Detailed Milestone Documentation
- 👉 [**M1: Hardware Foundation Documentation**](./M1-hardware-foundation/README.md)
