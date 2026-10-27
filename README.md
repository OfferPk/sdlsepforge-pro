# SDLSEPForge Pro (v1.0.0)
> **Autonomous Digital Product Factory — Catalog Record #448**  
> **CCSDS 355.1-B-1 & CCSDS 352.0-B-2 Space Data Link Security Extended Procedures Studio & Compliance Auditor**

---

## 🌟 Overview
**SDLSEPForge Pro** is an aerospace-grade Over-The-Air Rekeying (OTAR), Security Association Management (SAM), Security Monitoring & Reporting (SMR), and 10-point normative compliance engine strictly implementing **CCSDS 355.1-B-1** and **CCSDS 352.0-B-2** (*Space Data Link Security Extended Procedures*), **ISO 18377**, and **NIST SP 800-38F / RFC 3394**.

Designed for defense smallsat constellations, civil Earth observation fleets, deep space probes, and ground station Mission Operations Centers (MOC), SDLSEPForge Pro automates the complete cryptographic key lifecycle—from Master Key Encryption Key (KEK) wrapping to on-orbit key activation, Anti-Replay Counter (ARC) re-synchronization, and emergency cryptographic zeroization.

---

## 🚀 Key Features

* **Normative CCSDS 355.1-B-1 PDU Engine**:
  - Full 8-octet primary header generation: Protocol ID `0x35`, 16-bit Transaction ID, 10-bit Spacecraft ID (SCID 0..1023), 6-bit Virtual Channel ID (VCID 0..63), and 16-bit PDU length.
  - Complete support for OTAR Directives (`UPLOAD`, `VERIFY`, `ACTIVATE`, `REVOKE`, `ZEROIZE`).
* **NIST SP 800-38F / RFC 3394 AES Key Wrap Engine**:
  - Encrypts and wraps Traffic Encryption Keys (TEK) using Master Key Encryption Keys (KEK) with strict 64-bit integrity tag validation (`0xA6A6A6A6A6A6A6A6`).
* **Security Association (SA) State Machine Manager**:
  - Full lifecycle tracking: `UNINITIALIZED`, `OPERATIONAL`, `SUSPENDED`, `EXPIRED`, `REVOKED`.
  - Automatic zero-reset of Anti-Replay Counters (ARC) upon new key activation to prevent telecommand lockout or replay vulnerability.
* **Security Monitoring & Reporting (SMR) Telemetry Engine**:
  - Packages and parses security status telemetry: active key stores, SA expiration countdowns, authentication failure alerts, and replay violation counts.
* **Dual-Language High-Performance Implementations**:
  - **JavaScript ES6 Web Engine (`sdlsep-engine.js` & `sdlsep-auditor.js`)**: Powers zero-dependency in-browser security operations consoles and Mission Control dashboards.
  - **Python 3 Standalone CLI (`sdlsep_cli.py`)**: Zero-dependency CLI tool for automated flight software key injection, EGSE rekeying tests, and CI/CD pipelines.
* **10-Point Normative Aerospace Cybersecurity Audit Engine**:
  - Automated rules `SEP-001` through `SEP-010` verifying protocol IDs, PDU bounds, key wrapping integrity, SA transitions, and emergency zeroization.
* **Interactive Mission Operations Web Studio**:
  - Live parameter synthesis, key wrapping, SA activation, emergency zeroize, color-coded hex dissection, and interactive audit scorecards.

---

## 📁 Repository & Directory Layout

```
2026-10-17 — SDLSEPForge Pro/
├── README.md                               # Master technical documentation
├── PROGRESS_REPORT.md                      # Factory cycle release & validation report
├── source-code/
│   ├── index.html                          # Mission Control web operations console
│   ├── sdlsep-engine.js                    # JavaScript ES6 SDLS-EP synthesis & key engine
│   ├── sdlsep-auditor.js                   # 10-point normative compliance auditor
│   ├── sdlsep_cli.py                       # Python 3 CLI telecommand tool
│   └── test_runner.py                      # 10-suite automated regression test runner
├── build/
│   └── sdlsep-forge-pro-v1.0.0.zip         # Complete standalone production distribution
├── documentation/
│   ├── CCSDS_SDLSEP_SPECIFICATION.md       # Deep-dive protocol architecture specification
│   └── SDLSEP_COMPLIANCE_MATRIX.md         # 10-point normative requirements traceability matrix
└── screenshots/
    ├── architecture-diagram.svg            # Protocol pipeline & key lifecycle diagram
    └── sdlsep-studio-preview.svg           # Mission Control UI preview graphic
```

---

## 🛠️ Quick Start & CLI Usage

### 1. Run Automated Test Suite (10/10 PASS)
```bash
python3 source-code/test_runner.py
```

### 2. Wrap Traffic Encryption Key via AES-KW (RFC 3394)
```bash
python3 source-code/sdlsep_cli.py --mode otar-wrap --key-hex 00112233445566778899AABBCCDDEEFF
```

### 3. Generate OTAR Key Upload PDU
```bash
python3 source-code/sdlsep_cli.py --mode otar-upload --key-id 101 --kek-id 1 --scid 42 --vcid 0
```

### 4. Create Security Association (SAM)
```bash
python3 source-code/sdlsep_cli.py --mode sa-create --spi 42 --key-id 101
```

### 5. Run 10-Point Normative Cybersecurity Audit
```bash
python3 source-code/sdlsep_cli.py --mode audit
```

---

## 🛡️ Normative Audit Scorecard (10/10 PASS)

| Rule ID | Clause | Rule Description | Status |
| :--- | :--- | :--- | :--- |
| **SEP-001** | §4.1.2.2 | Protocol Identifier equals `0x35` | **PASS** |
| **SEP-002** | §4.1.2.3 | Valid PDU Type Code allocation | **PASS** |
| **SEP-003** | §4.1.2.4 | 16-bit Monotonic Transaction ID bounds | **PASS** |
| **SEP-004** | §4.1.2.5 | Spacecraft ID (0..1023) and VCID (0..63) bounds | **PASS** |
| **SEP-005** | §4.1.2.6 | PDU Length consistency with total octets | **PASS** |
| **SEP-006** | §5.2.2.1 | NIST SP 800-38F / RFC 3394 AES Key Wrap integrity | **PASS** |
| **SEP-007** | §6.1.3.2 | Security Association (SA) State Machine Lifecycle | **PASS** |
| **SEP-008** | §7.2.1.4 | Anti-Replay Counter (ARC) re-synchronization on key activation | **PASS** |
| **SEP-009** | §4.1.3.1 | PDU Frame Error Control Field (FECF) CRC-16 CCITT | **PASS** |
| **SEP-010** | §8.3.1.2 | Emergency Cryptographic Zeroization & Revocation Boundary | **PASS** |

---

## 💼 Commercialization & Monetization
* **Target Audience**: Defense satellite primes, commercial constellation operators, NASA/DoD flight software contractors, ground station network providers, and space cybersecurity researchers.
* **Pricing Tier**:
  - **Community Tier (Free / OSS)**: Core CLI and basic key wrapping utility.
  - **Commercial Flight Team License ($1,490/seat)**: Full Mission Control studio GUI, custom KEK/TEK profiles, automated EGSE rekeying hooks, and formal compliance audit exports.
  - **Constellation Ground Station Enterprise License ($6,800/unlimited)**: Multi-satellite live OTAR rekeying server, CI/CD telemetry qualification harness, and dedicated protocol customization support.
