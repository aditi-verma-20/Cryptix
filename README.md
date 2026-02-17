## 🚀 Quick Start

```bash
# 1. Install dependencies
pip install -r requirements.txt

# 2. # Mockaroo key
$env:MOCKAROO_API_KEY="your-mockaroo-key"

#3 Anthropic key (for SAR narrative AI)
$env:GROQ_API_KEY="sk-ant-your-actual-key-here"

# 3. Seed demo data
python seed_demo.py

# 4. Launch the app
streamlit run app.py
```

---

## 🏗️ Architecture

```

cryptix_sar/
├── app.py ← Streamlit front-end (all UI pages)
├── risk_engine.py ← AML rules engine, scoring logic
├── database.py ← SQLite back-end, a drop-in replacement for PostgreSQL
├── seed_demo.py ← populate with 6 literal demo cases
├── requirements.txt
└── cryptix_sar.db ← created automatically on first run
```
Back end: Python (risk_engine.py)
Database: SQLite (just change connection string for postgres)

Functionality of the three-tier architecture

Frontend: Streamlit + Plotly
Backend: Python (risk_engine.py)
Database: SQLite (just change connection string for postgres)

Distribution of features 4 AML detection rules

Rule    
Trigger     
Weight    

Dormant Activation  
Account inactive for more than 90 days and HVT  
30 from 100 

Frequency Spike  
More than five times today’s average transaction count for the last historical period    
25 from 100  

Profile Mismatch  
The transaction value is more than three times what is declared as monthly income.   
25 from 100  

Near-Threshold Structuring   
More than three transactions just below the reporting limit (per the respective reporting organization) in seven or fewer days   
20 from 100  

Risk Classification for Banking-Grade Customers
Score                  Classification
80-100                  🔴 Immediate Action Required
60-79                     🟠 Escalate for Review and Consider
40-59                     🟡 Additional Due Diligence Required   
20-39                     🟢 Normal Monitoring
0-19                            🔵 Routine Surveillance

Features
✅ Four AML detection rules with their associated weighting and scoring
✅ Amalgamation of CLAUDE AI AI-generated SAR narrative using a five-section template 
✅ A risk radar (interactive) plus breakdown bar chart 
✅ All activities are logged in a complete audit trail in SQLite (and will include an integrity hash)
✅ Allow human analysts to edit and approve/reject SARs
✅ A dashboard with analytical data on ongoing cases, trends, etc.
✅ A registry of cases with the ability to search and filter for case records
✅ A data seeder for demonstration purposes
✅ Dark theme for CRYPTIX UI 
Regulatory Compliance
PMLA 2002 (India)  
FIU-IND regulations  
FATF recommendation R.20, 
RBI KYC Master Direction

---

*Team CRYPTIX*
