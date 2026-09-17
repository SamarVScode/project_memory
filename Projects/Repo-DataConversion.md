---
type: github-repo
repo: SamarVScode/DataConversion
url: https://github.com/SamarVScode/DataConversion
stack: [Python 3, FastAPI, Pandas/CSV, Render]
cluster: logistics-stream-engine
tags: [project, backend, data-conversion, dc-hub-filtering]
---

# 🔄 DataConversion (`xlsx-filter-service`)

## 📌 Executive Summary
Stateless, job-based Excel-to-CSV filtering server. Specializes in ingesting complex supply chain spreadsheets, categorizing rows by Distribution Center (DC) vs. Hub headers, and returning isolated, pre-filtered CSV streams for downstream warehouse reporting.

---

## 🛠️ Tech Stack & Key Files
* **Runtime:** Python 3 (FastAPI)
* **Key Files:** `main.py` (FastAPI backend with UI testing route `/test`), `Deployment.md`.
* **Hosting:** Render Web Service (`Starter 512MB RAM` tier recommended).

---

## ⚠️ Known Gotchas & Bugs (Audit)
* **Deployment Root Directory Mismatch:** `Deployment.md` states: *"Root Directory: server_v2"*. However, in this repository, `main.py` and `requirements.txt` are placed directly in the **root directory**. Configuring Render with `server_v2` will cause a build failure (`directory not found`). Set Render Root Directory to `.` (empty/root).
* **Missing Documentation:** No top-level `README.md` exists; only `Deployment.md` is present.

---

## 🚀 Setup & Runbook
```bash
pip install -r requirements.txt
uvicorn main:app --host 0.0.0.0 --port $PORT
```

---

## 🔗 Knowledge Graph Connections
* Related Engine: [[Projects/Repo-XLSX-STREAM-REPORT-GENERATOR|XLSX-STREAM-REPORT-GENERATOR]]
* Connected GAS Scripts:
  * [[Projects/GAS-HourlyConversionReport|GAS: HourlyConversionReport]]
  * [[Projects/GAS-dc-rca-progression|GAS: dc rca progression]]
