##  Start

```bash
# 1. Install dependencies
pip install -r requirements.txt

# 2. # Mockaroo key
$env:MOCKAROO_API_KEY="your-mockaroo-key"

#3 Groq key (for SAR narrative AI)
$env:GROQ_API_KEY="sk-ant-your-actual-key-here"

# 3. Seed demo data
python seed_demo.py

# 4. Launch the app
streamlit run app.py
```

---

##  Architecture

```


cryptix_sar/
├── app.py           ← Streamlit frontend (all UI pages)
├── risk_engine.py   ← AML rules engine + scoring logic
├── database.py      ← SQLite backend (drop-in for PostgreSQL)
├── seed_demo.py     ← Populates 6 realistic demo cases
├── requirements.txt
└── cryptix_sar.db   ← Auto-created on first run
```

**Stack:**
- **Frontend:** Streamlit + Plotly
- **Backend:** Python (risk_engine.py)
- **Database:** SQLite (swap connection string for PostgreSQL)
- **LLM:** Groq API (Llama 3.3 70B) for SAR narrative generation  
- **Data Source:** Mockaroo API (synthetic financial data generation) 
- **Charts:** Plotly (interactive)

---

##  4 AML Detection Rules

| Rule | Trigger | Weight | Formula |
|------|---------|--------|---------|
| **Dormant Activation** | Account inactive >90 days + high-value txn | 30/100 | dormancy_factor × 0.6 + amount_factor × 0.4 |
| **Frequency Spike** | Today's txn count >5× historical avg | 25/100 | min((ratio / 20) × 100, 100) |
| **Profile Mismatch** | Transaction >3× monthly declared income | 25/100 | min((income_ratio / 15) × 100, 100) |
| **Near-Threshold Structuring** | ≥3 txns just below reporting limit in 7 days | 20/100 | min((count / 10) × 100, 100) |

---

##  Risk Classification (Banking-Grade)

| Score | Classification |
|-------|---------------|
| 80–100 | 🔴 **IMMEDIATE ACTION REQUIRED** |
| 60–79  | 🟠 **ESCALATE FOR REVIEW** |
| 40–59  | 🟡 **ENHANCED DUE DILIGENCE** |
| 20–39  | 🟢 **STANDARD MONITORING** |
| 0–19   | 🔵 **ROUTINE SURVEILLANCE** |

---

##  Features

- Rule-based technology providing 4 anti-money laundering (AML) detection rules, each rule has a weighted risk score.
- Anti-Money Laundering (AML) Llama AI SAR narrative generation using a 5-section process.
- Interactive risk radar with a breakdown bar chart.
- Audit trail of all SQLite activity with integrity hash enforced.
- Human analyst editing workflow with a review and approve/reject process.
- Case analytics and trends available via a single dashboard.
- Case registry with search and filter capabilities.
- Demo data generator for demo purposes.
- Platform dark theme user interface (UI).

---

## Regulatory Alignment

- PMLA 2002 (India)
- FIU-IND reporting standards
- FATF Recommendation R.20
- RBI KYC Master Direction 2016

---
This is a demo UI showing how the final project is expected to look.
*Team CRYPTIX*
