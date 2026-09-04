# LLM Agent Instructions & Guidelines — Farm Omni Gateway (farm-omni-gw)

> **Audience**: AI Coding Agents & Human Pair Programming  
> **Platform**: OpenWrt Linux + MediaTek MT7628 + Semtech SX1302/SX1303 + Quectel EC200U + GNSS RTK  
> **License**: AGPL-v3

---

## 🧭 1. Mission & Core Problem Statement

**The Problem**: How to equip an entire agricultural farm or aquaculture site to construct its live, high-fidelity **Digital Twin for under $500**?

All documentation, code, hardware definitions, and firmware configurations in this repository must directly serve this goal:
- Eliminating proprietary agricultural gatekeeping ($10,000+ proprietary stations).
- Frugal, off-grid solar edge hardware (sub-$400 complete physical BOM).
- Quad-capability integration:
  1. 8-channel LoRaWAN mesh.
  2. Resilient 4G cellular backhaul.
  3. Centimeter-grade RTK base station.
  4. SDI-12 and RS-485 microclimate and soil moisture field buses.

---

## 🏗️ 2. Architectural Guidelines

### A. Frugal & Off-Grid by Design
- The system must operate indefinitely on a compact solar panel (25-35W) and a 12V LiFePO4 battery (average power draw < 2.5W).
- Local-first operation: All sensor and topography data must be preserved and queryable on-device (via local SQLite) even during multi-week cellular outages.

### B. Language & Communication Standards
- All code, schematics descriptions, comments, documentation, and commit messages MUST be written strictly in **International English**.
- No vendor lock-in or proprietary cloud dependencies.

### C. Open-Source License Verification for Component Libraries (Strict Rule)
- **Mandatory License Audit:** Whenever selecting, integrating, or packaging a hardware component, sensor, transceiver, or modem, **ALWAYS verify whether the vendor-provided SDKs, HALs, drivers, and firmware libraries are 100% compatible with open-source licensing** (e.g., MIT, BSD, Apache 2.0, GPL, or AGPL-3.0).
- **Zero Proprietary Blobs & NDA Traps:** Strictly reject components that require non-redistributable binary blobs, proprietary commercial runtimes, or vendor NDAs that would compromise the project's **AGPL-v3** compliance and open-hardware accessibility. Every driver must be upstreamable or compilable directly from source under OpenWrt.

---

## 🛠️ 3. Verification & Build Commands

| Target | Command |
| :--- | :--- |
| **OpenWrt Firmware Build** | `make -j$(nproc) V=s` |
| **Concentratord Validation** | `chirpstack-concentratord -c /etc/chirpstack-concentratord/sx1302/concentratord.toml` |
| **RTCM3 Stream Verification** | `str2str -in serial://ttyS2:115200#rtcm3 -out stdout#rtcm3` |
