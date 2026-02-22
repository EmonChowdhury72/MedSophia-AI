<div align="center">

# MedSophia AI

### *Turning Bangladesh's $105M medicine waste crisis into a zero-stockout, zero-waste future.*

**Strategy · Product · Execution · Decisions by Precision Health Innovators**

</div>

---

## 1. The Problem

Every year, Bangladesh wastes **$105 million** on expired medicines sitting unused in urban hospital warehouses. At the same time, patients in rural areas face life-threatening stockouts of critical drugs — insulin, antibiotics, saline — simply because the system has no way to see where surplus exists and move it in time.

These two crises are not separate problems. They are two sides of the same broken supply chain.

Current tools track inventory. They do not act on it. By the time aggregated data reaches a decision-maker at the district or national level, it is weeks old. By the time an emergency re-order is placed, the patient has already been turned away.

---

## 2. The Solution

MedSophia AI is an intelligent supply chain system built for public health medicine.

It does not replace existing government infrastructure. It sits on top of it as an intelligence layer — predicting shortages weeks in advance and routing surplus stock from overstocked urban facilities to under-supplied rural clinics before medicines expire.

We do not just forecast what to buy. We determine where to move what already exists.

---

## 3. Core System Architecture

MedSophia AI is built on three engines designed specifically for the infrastructure realities of developing healthcare systems.

### Engine 1 — Predictive Demand

**Problem:** Procurement decisions are based on outdated static records that ignore seasonal disease patterns, flood cycles, and population shifts.

**Solution:** Long Short-Term Memory (LSTM) models trained on up to 5 years of historical disease data, weather patterns, and population movement. The system generates localized demand forecasts for critical medicines weeks before a shortage occurs — accounting for events like dengue season or monsoon flooding that predictably spike demand.

### Engine 2 — Redistribution Intelligence

**Problem:** Urban hospitals accumulate buffer stock that expires unused while rural clinics run out of the same medicines. No existing system connects the two.

**Solution:** Graph optimization algorithms calculate the most efficient routing of expiring surplus stock from well-supplied urban hospitals to under-supplied rural clinics. The system produces transfer manifests that work within existing government transport networks — no new logistics infrastructure required.

### Engine 3 — SMS-First Interface

**Problem:** Complex dashboards and internet-dependent apps fail in the rural areas where the crisis is most severe. Low connectivity cannot be assumed.

**Solution:** A Twilio-powered two-way SMS gateway that works on any basic feature phone. Rural health officers receive plain-text alerts and respond with a single reply:

```
Warning: Insulin running low at UHC Ukhiya.
Reply YES to request transfer from Cox's Bazar Sadar Hospital.
```

No internet connection required. High-tech backend. Low-tech frontend.

---

## 4. Technical Stack

| Layer | Technology |
|---|---|
| Backend and Data | Python 3.10+, PostgreSQL |
| Machine Learning | PyTorch / TensorFlow — LSTM for demand forecasting |
| Optimization | NetworkX / SciPy — Graph-based inventory routing |
| Communication | Twilio API — Two-way SMS integration |
| Dashboard | Streamlit — Data-centric dashboards for health administrators |
| Government Integration | DHIS2 API — Health data ingestion (Phase 2) |

---

## 5. Engineering Principles

These are not preferences. They are hard constraints applied at every stage of development and enforced in the deployment pipeline.

**Equity is a Metric**
An automated Equity Audit runs inside the CI/CD pipeline. If any update measurably improves outcomes for urban facilities at the expense of rural clinics, the build fails. Serving under-resourced communities is not a goal statement — it is a pass/fail condition in the codebase.

**The Nokia Rule**
If a rural health officer cannot complete a critical interaction using a standard SMS on a basic feature phone, the feature does not ship. No exceptions.

**Resilience Over Optimization**
The system is designed for the worst operating conditions — floods, road blockages, power cuts, network outages. It must degrade gracefully and remain functional when physical infrastructure fails. We optimize for the hardest day, not the average one.

---

## 6. Local Development Setup

> **Note:** Access to the `.env` configuration and live datasets requires written clearance from
> the CTO. Local development uses synthetic mock data only.

### Prerequisites

- Python 3.10 or higher
- A Twilio Developer Account (free tier is sufficient for local testing)
- PostgreSQL, or SQLite for lightweight local mock testing

### Installation

**Step 1 — Clone the repository**

```bash
git clone https://github.com/PrecisionHealthInnovators/medsophia-ai.git
cd medsophia-ai
```

**Step 2 — Create and activate a virtual environment**

```bash
python -m venv venv
source venv/bin/activate
# On Windows: venv\Scripts\activate
```

**Step 3 — Install dependencies**

```bash
pip install -r requirements.txt
```

**Step 4 — Configure environment variables**

```bash
cp .env.example .env
```

Open `.env` and fill in your credentials:

```
TWILIO_ACCOUNT_SID=your_value_here
TWILIO_AUTH_TOKEN=your_value_here
DATABASE_URL=your_value_here
```

**Step 5 — Run the Streamlit dashboard**

```bash
streamlit run src/app.py
```

**Step 6 — Start the SMS webhook listener**

*Requires ngrok for local development.*

```bash
python src/api/sms_webhook.py
```

---

## 7. Project Structure

```
medsophia-ai/
├── data/                  # Synthetic and mock datasets for local development
├── notebooks/             # Jupyter notebooks for LSTM and graph logic experimentation
├── src/
│   ├── ai/                # Core ML models — LSTM demand forecasting
│   ├── routing/           # Graph optimization and redistribution logic
│   ├── api/               # FastAPI endpoints and Twilio webhook receivers
│   ├── app.py             # Streamlit dashboard entry point
│   └── utils/             # Equity Audit scripts and SMS formatters
├── tests/                 # Pytest suite — mandatory before any pull request
├── requirements.txt
└── README.md
```

---

## 8. Roadmap

| Phase | Name | Description | Status |
|---|---|---|---|
| Phase -1 | Ideation and Research | Problem definition, system design, and team formation | Complete |
| Phase 0 | Validation | Train baseline LSTM on public health data; simulate redistribution savings; validate SMS workflows with real health officers | In Progress |
| Phase 1 | Operational MVP | 10-clinic pilot across Dhaka and Cox's Bazar with human-in-the-loop SMS alerts | Upcoming |
| Phase 2 | System Integration | Live DHIS2 API connection; automated redistribution manifests; Equity Audit reporting | Upcoming |
| Phase 3 | Scale and Resilience | Nationwide rollout to all 492 Upazila Health Complexes; Cyclone Simulation module for disaster pre-positioning | Upcoming |

---

## 9. Contributing

We welcome contributors who care about health equity, AI for social good, and building systems that work under real-world constraints.

Before contributing, please read the following:

- All pull requests must pass the full Pytest suite in `tests/` before review
- New features must comply with the Nokia Rule — SMS-accessible on a basic feature phone
- Any change to routing or forecasting logic must include an updated Equity Audit result
- Do not commit real patient data, facility credentials, or environment files under any
  circumstances

To get started, open an issue describing what you want to build or fix. The team will review and respond before you begin development.

---

## 10. Founding Team

| Name | Role | Area of Responsibility |
|---|---|---|
| **Md Emon Chowdhury** | Co-Founder and CEO | Business model, government relations, supply chain economics |
| **Jannatul Ferdous** | Co-Founder and CTO | AI development, system architecture, security |
| **Rafia Antara** | Co-Founder and Chief Medical Officer | Clinical accuracy, hospital workflow, user experience |

---

## 11. License

Copyright 2026 Precision Health Innovators. All rights reserved.

This project is currently closed source. The codebase, algorithmic logic, and system architecture are proprietary. Viewing this repository does not grant permission to copy, modify, distribute, or use any part of this software without explicit written permission from **Precision Health Innovators**.

If you are a researcher, health organization, or government body interested in a partnership or
pilot deployment, please open an issue or contact the team directly through GitHub.

---

<div align="center">

*Built with purpose. Deployed with equity. Scaled for impact.*

</div>
