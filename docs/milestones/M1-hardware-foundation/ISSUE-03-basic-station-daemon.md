# Issue #3: Integrate Semtech Basic Station & SX1302 HAL over SPI Bus

- **Milestone:** M1: Hardware Foundation
- **Type:** Software / LoRaWAN
- **Component:** Basic Station Daemon, SX1302 HAL

---

## 🎯 Objective
Package and execute Semtech **Basic Station** (or ChirpStack Concentratord) as a background system service on OpenWrt to handle:
- SX1302/SX1303 multi-channel demodulation (EU868 standard frequencies).
- Secure WebSocket (WSS) LNS protocol connection to upstream network servers (The Things Stack / ChirpStack).
- Automatic SX1302 reset and restart watchdog upon SPI communication stalls.

---

## 🏗️ Technical Specification
1. **Packaging**:
   - Cross-compile `basicstation` or `chirpstack-concentratord-sx1302` for `mipsel_24kc` architecture.
   - Install binary into `/usr/bin/` with minimal memory footprint (< 12MB RSS).
2. **Configuration (`station.conf` / `concentratord.toml`)**:
   - Set radio parameters for 8 multi-SF channels (868.1 to 868.5 MHz, 867.1 to 867.7 MHz).
   - Configure CUPS (Configuration and Update Server) and LNS (LoRaWAN Network Server) endpoints.
3. **Init Script (`/etc/init.d/basicstation`)**:
   - Procd-managed service with auto-respawn on crash.
   - Pre-start hook pulsing `GPIO11` low (100ms) then high to guarantee clean hardware reset.

---

## 📋 Acceptance Criteria
- [ ] Daemon automatically starts on boot and establishes a persistent WSS connection to ChirpStack/TTN.
- [ ] Zero memory leaks observed over a continuous 48-hour bench run.
- [ ] Concentrator health status and stats successfully reported to LNS dashboard.
