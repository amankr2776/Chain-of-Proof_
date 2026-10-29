# Chain of Proof — Web3 Battery Passport Audit Platform & QpiAI Engine

**Chain of Proof** is an EU Battery Directive compliant digital battery passport and supply chain audit platform. It leverages **QpiAI Opt** QUBO (Quadratic Unconstrained Binary Optimization) engines for second-life disposition and recycling facility dispatch, anchored by **QpiAI QCloud** 128-bit quantum QRNG nonces on an immutable append-only proof ledger.

---

## 🚀 Quick Start Guide for Judges

Follow these steps to launch the complete system with the Python FastAPI backend and React frontend.

### 1. Install Python Backend Dependencies
Ensure you have Python 3.9+ installed. In your terminal, run:
```bash
pip install -r requirements.txt
```

*This installs FastAPI, Uvicorn, Pydantic, Python-Dotenv, `qpiai-opt[quantum]`, and `qpiai-quantum`.*

---

### 2. Configure Environment Variables
Copy the `.env.example` file to create your local `.env` file:
```bash
cp .env.example .env
```
Edit `.env` to add your QpiAI API keys (optional if running in simulation mode):
```env
QPIAI_OPT_API_KEY=your_qpiai_opt_key_here
QPIAI_QCLOUD_API_KEY=your_qpiai_qcloud_key_here
```

---

### 3. Start the Python FastAPI Backend
Run the Uvicorn server on port 8000:
```bash
uvicorn main:app --reload --port 8000
```
The FastAPI server will start at `http://localhost:8000`. You can inspect the interactive OpenAPI documentation at `http://localhost:8000/docs`.

---

### 4. Run the React Frontend (AI Studio)
In a second terminal, install Node.js dependencies and start the Vite development server:
```bash
npm install
npm run dev
```
Open `http://localhost:3000` in your web browser.

---

## 🛡️ Demo Safety & Fallback Mode

> **⚠️ WARNING & DEMO GUARANTEE:**
> **If the Python FastAPI backend is not running, the React application will automatically detect the offline state and seamlessly switch to Local Simulation Mode so the UI demo NEVER crashes or blocks live evaluation.**

When the backend is active on `http://localhost:8000`, the top navbar status pill turns **Cobalt Blue** (`QPIAI CLOUD: CONNECTED`). If the backend is offline, the status pill turns **Marigold / Acid Lime** (`LOCAL SIMULATION ACTIVE (FALLBACK)`).

---

## 🏗️ Architecture & QpiAI Integration

1. **QpiAI Opt QUBO Stage 1 (Disposition Console)**
   - Formulates a 2N binary variable Hamiltonian $H(x)$ evaluating State of Health (SOH) safety limits.
   - Batteries with SOH ≥ 65% are assigned to **Second-Life Grid BESS Reuse**.
   - Batteries with SOH < 65% incur an infinite +100,000 penalty, forcing them to **Direct Recycling**.

2. **QpiAI Opt QUBO Stage 2 (Dispatch Optimization)**
   - Solves multi-facility capacity allocation and transport cost optimization for hydrometallurgical recycling facilities.

3. **QpiAI QCloud 128-Bit Quantum QRNG Nonces**
   - Executes 128-qubit Hadamard superposition circuits ($H^{\otimes 128} |0\rangle^{\otimes 128}$) on QCloud quantum simulator/hardware backends.
   - Collapses measured bitstrings into unforgeable 128-bit hex nonces to seal lifecycle block headers and prevent rainbow table hash collisions.

4. **EU Mass Conservation & Fraud Firewall**
   - Verifies hydrometallurgical material recovery claims against stoichiometric passport baselines within a strict **5.0% deviation tolerance**.

---

## 🌐 CORS & Security Configuration

The FastAPI backend includes `CORSMiddleware` configured to allow cross-origin requests from Google AI Studio preview environments (`https://*.run.app`) and local development URLs (`http://localhost:3000`):

```python
app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)
```

---

## 🎨 Design System

- **Canvas**: Ice Silver (`#EAEBEE`)
- **Structure & Ink**: Deep Aubergine (`#2A1B24`)
- **Accent**: Marigold (`#F59E0B`)
- **Cobalt Blue**: (`#3B82F6` / `#60A5FA`)
- **Typography**: Inter (UI font feature settings `'cv11', 'ss01'`)
