# Task-5
Capture and Analyze Network Traffic Using Wireshark.

## 🎯 Objective
Capture live network packets using Wireshark and analyze UDP, TCP, and QUIC protocols.

## 🧰 Tools Used
- Wireshark v4.4.6
- Command Prompt (Windows `ping` command)
- Web Browser (for generating QUIC/HTTP traffic)

## 📝 Steps Performed
1. Installed Wireshark (Windows x64 Installer).
2. Captured traffic using the active network interface: **Wi-Fi 2**.
3. Visited multiple websites and ran.

4. Applied filters (`udp`, `tcp`, `quic`) to analyze specific protocols.
5. Saved the capture as `task5_capture.pcap`.

---

## 📊 Protocol Analysis

### 1️⃣ UDP (User Datagram Protocol)
- **Filter used**: `udp`
- **Observed communication**:
- Source: `192.168.0.105` (my device)
- Destination: Google server `142.250.192.106`
- Ports: Source `51318` → Destination `443`
- **Use Case**: Likely QUIC traffic over UDP.
- **Payload**: Mostly encrypted, length ~71 bytes.
- **Behavior**: Connectionless, no handshakes or retransmissions.

---

### 2️⃣ TCP (Transmission Control Protocol)
- **Filter used**: `tcp`
- **Observed communication**:
- Destination IPs like `20.189.173.17`, `172.217.194.188`, etc.
- Port `443` → HTTPS traffic
- Handshake (SYN, ACK), retransmissions, duplicate ACKs observed.
- **Behavior**:
- Reliable, connection-oriented.
- Includes segment tracking and flow control.
- Shows error handling (e.g., TCP Dup ACK, retransmissions).

---

### 3️⃣ QUIC (Quick UDP Internet Connections)
- **Filter used**: `quic`
- **Observed communication**:
- From: `192.168.0.105` to `142.250.71.100`
- Port: `443`
- Includes fields like `PING`, `CRYPTO`, `ACK`, `PADDING`.
- **Use Case**: HTTP/3 traffic between browser and Google.
- **Highlights**:
- Fast encrypted traffic over UDP.
- Combines reliability of TCP + speed of UDP.
- Common with Chrome/YouTube/Google services.

## 🧩 Key Findings
- All three protocols were captured and analyzed.
- QUIC is increasingly replacing traditional TCP for HTTPS.
- TCP showed detailed handshakes and retransmission behavior.
- UDP is fast but lacks reliability features — QUIC builds on it.

## 📁 Deliverables
- `task5_capture.pdf` – saved Wireshark capture



