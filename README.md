# ⚡ Chain of Proof — Web3 Battery Passport Audit Platform & QpiAI Engine

![Version](https://img.shields.io/badge/version-2.4.0-blue.svg)
![EU Directive](https://img.shields.io/badge/Compliance-EU_Battery_Directive_2023%2F1542-emerald.svg)
![QpiAI Engine](https://img.shields.io/badge/Quantum-QpiAI_QUBO_%26_128--bit_QRNG-purple.svg)
![Web3 Standard](https://img.shields.io/badge/Web3-SHA256_Ledger_%26_Smart_Contracts-gold.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)

**Chain of Proof** is an enterprise-grade Web3 Battery Passport and Audit Platform powered by the **QpiAI Quantum Engine**. Built in full compliance with the **EU Battery Directive 2023/1542**, the platform provides immutable lifecycle tracking, quantum-enhanced end-of-life (EoL) disposition optimization, material mass conservation auditing, and tamper-proof ledger verification across the electric vehicle (EV) battery supply chain.

---

## 📸 Platform Highlights

```
 ┌─────────────────────────────────────────────────────────────────────────────────────────────┐
 │                                     CHAIN OF PROOF ARCHITECTURE                             │
 ├─────────────────────────────────────────────────────────────────────────────────────────────┤
 │                                                                                             │
 │   ┌───────────────────────┐   ┌────────────────────────┐   ┌────────────────────────────┐   │
 │   │  MANUFACTURER (OEM)   │   │ SECOND-LIFE OPERATOR   │   │    RECYCLER 1 (VALENCE)    │   │
 │   │  • Passport Genesis   │   │  • SOH / Telemetry     │   │  • Mass Balance Audit      │   │
 │   │  • QRNG Batch Sign    │   │  • QUBO Disposition    │   │  • Black Mass Recovery     │   │
 │   └───────────┬───────────┘   └───────────┬────────────┘   └─────────────┬──────────────┘   │
 │               │                           │                              │                  │
 │               └───────────────────────────┼──────────────────────────────┘                  │
 │                                           ▼                                                 │
 │                         ┌───────────────────────────────────┐                               │
 │                         │   REACT 18 + VITE FRONTEND CANVAS │                               │
 │                         └─────────────────┬─────────────────┘                               │
 │                                           │                                                 │
 │                                           ▼                                                 │
 │                         ┌───────────────────────────────────┐                               │
 │                         │   EXPRESS BACKEND / API PROXY     │                               │
 │                         └─┬───────────────────────────────┬─┘                               │
 │                           │                               │                                 │
 │                           ▼                               ▼                                 │
 │           ┌──────────────────────────────┐ ┌──────────────────────────────┐                 │
 │           │     QpiAI QUANTUM ENGINE     │ │  WEB3 LEDGER & PROOF ENGINE  │                 │
 │           │ • 128-bit Hadamard QRNG      │ │ • Cryptographic Merkle Tree  │                 │
 │           │ • QUBO Stage 1 Disposition   │ │ • SHA-256 Ledger Audit Log  │                 │
 │           │ • QUBO Stage 2 Route Dispatch│ │ • Solidity Access Control    │                 │
 │           └──────────────────────────────┘ └──────────────────────────────┘                 │
 └─────────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 🎯 Core Personas

The platform enforces strict role-based access control (RBAC) across three distinct industry personas:

| Persona | Primary Function & Focus Area | Key Modules Authorized |
| :--- | :--- | :--- |
| **Manufacturer (OEM)** | Registers new battery cells/packs at birth. Creates baseline genesis records, signs 128-bit QRNG nonces, and mints Digital Battery Passports. | Passport Studio, Dashboard, Chain Explorer |
| **Second-Life Operator** | Ingests real-time field telemetry (SOH, internal short circuit risk, capacity degradation). Runs QpiAI QUBO optimization to assign optimal cascade paths (Direct Reuse vs. Repurpose vs. Recycling). | Disposition Console, Passport Studio, Dashboard |
| **Recycler (Valence)** | Performs hydro/pyrometallurgical recycling. Verifies material mass balance (Lithium, Nickel, Cobalt, Manganese recovery), signs ESG audit claims, and logs final destruction/reclamation records. | Recycling Hub, Reconciliation, Audit Log, Explorer |

---

## ⚡ QpiAI Quantum Engine Integration

Chain of Proof natively interfaces with **QpiAI Cloud** services for both quantum random number generation and combinatorial optimization.

### 1. 128-bit QRNG (Quantum Random Number Generator)
Every battery passport state update is cryptographically anchored using a 128-bit quantum nonce generated via Hadamard quantum state sampling $H|0\rangle = \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle)$.
* **Purpose**: Prevents replay attacks, seed prediction, and counterfeit passport forging.
* **Fallback**: Graceful fallback to browser/Node web-crypto API (`crypto.getRandomValues`) if offline.

### 2. QUBO Disposition Optimization (Stage 1)
Determines whether a degraded battery should undergo **Direct Reuse** (Grid Storage), **Repurpose** (Lower C-rate backup power), or **Direct Recycling**.

Formulated as a Quadratic Unconstrained Binary Optimization (QUBO) problem:

$$\min_{x} \quad H(x) = \sum_{i} Q_{ii} x_i + \sum_{i < j} Q_{ij} x_i x_j$$

Where:
* $x_1 \in \{0,1\}$ = Direct Reuse Decision
* $x_2 \in \{0,1\}$ = Repurpose Decision
* $x_3 \in \{0,1\}$ = Immediate Recycling Decision
* $Q_{ii}$ encodes State-of-Health (SOH), internal short risk, cycle count, and remaining useful life (RUL).
* $Q_{ij}$ enforces single-choice constraint penalty $(x_1 + x_2 + x_3 - 1)^2$.

### 3. QUBO Fleet Logistics & Dispatch (Stage 2)
Optimizes the supply chain logistics for transporting hazardous spent lithium-ion batteries from collection hubs to specialized recycling plants, minimizing carbon footprint and transportation cost under capacity limits.

---

## 🔬 Mass Conservation Engine (Recycling Audit)

For every recycled battery pack, the system enforces conservation of mass:

$$M_{\text{input}} = M_{\text{Lithium}} + M_{\text{Nickel}} + M_{\text{Cobalt}} + M_{\text{Manganese}} + M_{\text{Black Mass Slag}} + M_{\text{Losses}}$$

* **Mass Reconciliation**: Automatically computes recovery efficiency percentage.
* **Audit Verification**: Compares physical weight bridge logs against passport baseline genesis compositions.

---

## 🖥️ Platform Modules

1. **Dashboard**: High-level overview of ecosystem battery metrics, total active claims, QpiAI engine status, and role switcher.
2. **Passport Studio**: Visual battery explorer with detailed genesis specifications, material breakdown charts, and horizontal **Battery Lifecycle Telemetry** visualizers (`Manufactured` $\rightarrow$ `Lifecycle Updates` $\rightarrow$ `QUBO Decision` $\rightarrow$ `Recycling`).
3. **Disposition Console**: Interactive matrix tuner to adjust economic/environmental weight vectors and trigger live QpiAI QUBO execution.
4. **Recycling Hub**: Deep-dive into black mass extraction, material purity analysis, and ESG reclamation compliance.
5. **Reconciliation**: Cryptographic proof reconciliation tool providing side-by-side baseline genesis comparison vs. actual physical claims.
6. **Chain Explorer**: Live block viewer, SHA-256 Merkle tree verification, and interactive **Tamper Simulation** tool.
7. **Audit Log**: Real-time event ledger dynamically calculated from current system state and cryptographic claims.

---

## 🛠️ Tech Stack

* **Frontend**: React 18, TypeScript, Vite, Tailwind CSS, Lucide Icons, Recharts.
* **Backend**: Express.js (Node.js / tsx runtime), Vite Dev Server Middleware.
* **Quantum / AI**: QpiAI API Proxy Client (`/api/qpiai/*`), QUBO Solver algorithms, 128-bit QRNG simulator.
* **Web3 / Cryptography**: SHA-256 Hashing, ECDSA cryptographic signatures, Solidity Access Control guards.

---

## 🚀 Quick Start Guide

### Prerequisites
* **Node.js**: v18.x or higher
* **npm**: v9.x or higher

### Installation & Run

1. **Clone Repository & Install Dependencies**:
   ```bash
   git clone https://github.com/your-org/chain-of-proof.git
   cd chain-of-proof
   npm install
   ```

2. **Start Local Development Server**:
   ```bash
   npm run dev
   ```
   * The app will spin up on `http://localhost:3000`.

3. **Build for Production**:
   ```bash
   npm run build
   ```

4. **Start Production Express Server**:
   ```bash
   npm start
   ```

---

## 📡 API Reference

| Endpoint | Method | Description |
| :--- | :--- | :--- |
| `/api/health` | `GET` | Health check endpoint returning status, uptime, and version. |
| `/api/qpiai/qrng` | `POST` | Requests a 128-bit quantum random nonce from QpiAI Cloud. |
| `/api/qpiai/qubo/disposition` | `POST` | Solves Stage 1 Battery EoL Disposition QUBO matrix. |
| `/api/qpiai/qubo/dispatch` | `POST` | Solves Stage 2 Fleet Dispatch & Route Allocation QUBO. |

---

## 🎨 Design System

The application strictly adopts an ultra-clean, high-contrast dark industrial theme:

* **Background**: Midnight Black (`#0B0E14` / `#121721`)
* **Primary Accent**: Cobalt Blue (`#3B82F6` / `#2563EB`)
* **Quantum Accent**: Acid Lime (`#A3E635` / `#84CC16`)
* **Typography**:
  * Body & Labels: `Inter`, `-apple-system`, `sans-serif`
  * Values, Hashes & Code: `JetBrains Mono`, `monospace`

---

## 📄 Compliance & Governance

Designed to meet the stringent requirements of the **EU Battery Regulation (2023/1542)**:
* **Carbon Footprint Declaration**: Automated calculation per kWh output.
* **Recycled Content Targets**: Mandatory tracking for Li, Ni, Co, and Pb.
* **Due Diligence Policies**: Cryptographic proof of origin for key battery raw materials.

---

© 2026 Chain of Proof Platform — Engineered with QpiAI Engine.
