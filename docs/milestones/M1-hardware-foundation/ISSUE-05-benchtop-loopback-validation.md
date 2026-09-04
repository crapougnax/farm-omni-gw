# Issue #5: Benchtop Validation: Node Uplink & Live Packet Forwarding over Wi-Fi

- **Milestone:** M1: Hardware Foundation
- **Type:** QA / Validation
- **Component:** System Integration & RF Testing

---

## 🎯 Objective
Execute an end-to-end laboratory bench test to validate the complete Milestone 1 prototype:
- Transmit periodic LoRaWAN uplinks from a sensor node (e.g. NUCLEO-WL55).
- Verify successful reception by the SX1302 concentrator and forwarding over local Wi-Fi to a live ChirpStack or The Things Stack instance.
- Test downlink acknowledgement and ADR (Adaptive Data Rate) round-trip.

---

## 🏗️ Test Methodology
1. **Equipment Under Test**:
   - Prototype Gateway: MT7628 + Seeed WM1302 + dipole antenna + 5V USB-C power supply.
   - Test Node: STM32 NUCLEO-WL55JC1 running standard `LoRaWAN_End_Node` application.
   - Upstream LNS: ChirpStack instance or TTN Community Edition.
2. **Key Performance Indicators**:
   - Packet Delivery Ratio (PDR) > 98% across spreading factors SF7 through SF12.
   - RSSI / SNR reporting fidelity.
   - Gateway ping latency over Wi-Fi < 50ms.

---

## 📋 Acceptance Criteria
- [ ] At least 500 consecutive test packets successfully received on the LNS with zero lost frames.
- [ ] Downlink ACK packets transmitted by gateway and acknowledged by the test node.
- [ ] Test report and oscilloscope power trace documented under `docs/validation/m1-report.md`.
