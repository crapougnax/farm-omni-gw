# Farm Omni Gateway — Operating System & Kernel (`os/`)

[![License: GPL-2.0](https://img.shields.io/badge/License-GPL%20v2.0-blue.svg)](./LICENSE)

This directory contains OpenWrt buildroot configurations, Linux kernel patches, Device Tree Source (DTS) definitions, and hardware driver configurations for the **Farm Omni Gateway**.

---

## 📜 Licensing Notice
All materials in this directory are governed by the **GNU General Public License v2.0 (GPL-2.0-only)**, in strict compliance with the upstream Linux kernel and OpenWrt licensing models.
- Any kernel modifications, DTS device trees, or driver patches are licensed under GPL-2.0.

---

## 📂 Directory Contents
- `openwrt/` — Buildroot `.config` recipes for `ramips/mt7628`
- `dts/` — Device Tree Source files declaring SPI `/dev/spidev0.0`, UARTs, and GPIO mappings
- `patches/` — Upstream kernel and driver compatibility patches
