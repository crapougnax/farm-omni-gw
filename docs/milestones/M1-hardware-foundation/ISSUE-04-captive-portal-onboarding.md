# Issue #4: Zero-Touch Captive Portal Onboarding for Wi-Fi and LNS Pairing

- **Milestone:** M1: Hardware Foundation
- **Type:** Software / UX
- **Component:** Web Onboarding Portal, Network Manager

---

## 🎯 Objective
Enable farm technicians to configure and onboard a brand-new gateway from an unboxed state without requiring an SSH terminal, serial cable, or Linux expertise:
- Broadcast a setup Wi-Fi network with an automatic captive portal popup on smartphones/laptops.
- Web UI to scan and join local farm Wi-Fi, view the unique Gateway EUI, and paste LNS credentials.

---

## 🏗️ Technical Specification
1. **Captive Portal Architecture**:
   - `dnsmasq` intercepts DNS queries (`*.local`, captive Apple/Android test domains) and redirects HTTP port 80 to the local web server.
   - Lightweight micro-webserver written in Lua (uHTTPd) or Go (embedded binary).
2. **Onboarding Workflow**:
   - Step 1: Scan 2.4 GHz Wi-Fi networks and select farm SSID + enter WPA2/WPA3 passphrase.
   - Step 2: Display unique Gateway EUI (derived from MT7628 MAC address).
   - Step 3: Choose target LNS (The Things Stack / ChirpStack / Custom) and paste API Key / LNS URL.
   - Step 4: Click "Save & Connect" $\rightarrow$ Gateway validates Wi-Fi, switches AP off or hides SSID, and connects to upstream LNS.

---

## 📋 Acceptance Criteria
- [ ] Connecting to `Omni-Gateway-Setup` automatically triggers the captive browser portal on iOS and Android.
- [ ] Wi-Fi and LNS credentials safely written to `/etc/config/` and survive reboots.
- [ ] Status LED or web UI confirms successful upstream connection.
