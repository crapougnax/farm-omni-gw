# Farm Omni Gateway — Software & Applications (`software/`)

[![License: AGPL-3.0](https://img.shields.io/badge/License-AGPL%20v3.0-blue.svg)](./LICENSE)

This directory contains the user-space applications, telemetry daemons, captive portal onboarding web UI, RTK caster integrations, and digital twin data models for the **Farm Omni Gateway**.

---

## 📜 Licensing Notice
All materials in this directory are licensed under the **GNU Affero General Public License v3.0 (AGPL-3.0-or-later)**.
- In accordance with Section 13 (Remote Network Interaction), anyone interacting with this software over a network (Wi-Fi portal, LoRa mesh, NTRIP caster, or REST/WebSocket API) is entitled to receive the corresponding source code.
- Protects the open-source community from closed, proprietary SaaS misappropriation.

---

## 📂 Directory Contents
- `portal/` — Zero-touch captive onboarding web application (Wi-Fi setup, Gateway EUI, LNS pairing)
- `daemons/` — Microclimate RS-485 Modbus and SDI-12 soil telemetry acquisition daemons
- `rtk/` — RTCM3 streamer and NTRIP caster integration scripts
- `twin/` — SQLite digital twin database schemas and sync adapters
