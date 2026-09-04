# Issue #2: Configure OpenWrt 23.05 Target with SPI, Wi-Fi AP & Client Interfaces

- **Milestone:** M1: Hardware Foundation
- **Type:** Firmware / OS
- **Component:** OpenWrt Buildroot, Device Tree & Networking

---

## 🎯 Objective
Configure and build a minimal, hardened OpenWrt 23.05 LTS Linux image for the MT7628 target supporting:
- Hardware SPI bus driver for `/dev/spidev0.0`.
- Concurrent dual-role Wi-Fi: Access Point (`Omni-Gateway-Setup`) for local onboarding + Client mode (`wlan0-sta`) connecting to the farm's local Wi-Fi router.

---

## 🏗️ Technical Specification
1. **DTS (Device Tree) Configuration**:
   - Enable `spidev@0` with max-frequency set to 10000000 (10 MHz).
   - Configure `GPIO11` as an active-high output for SX1302 hardware reset.
2. **Network Topology**:
   - `br-lan`: Static IP `192.168.88.1/24` with local dnsmasq DHCP server (serving IP addresses to onboarding devices).
   - `wwan`: DHCP client connected to upstream Wi-Fi SSID with NAT masquerading.

---

## 📋 Acceptance Criteria
- [ ] Reproducible OpenWrt `.config` and DTS patch checked into `firmware/openwrt/`.
- [ ] Gateway boots in under 15 seconds to a ready state with Wi-Fi AP broadcast.
- [ ] `/dev/spidev0.0` is successfully probed and accessible by user-space applications.
