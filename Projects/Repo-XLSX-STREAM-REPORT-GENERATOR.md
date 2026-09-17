---
type: github-repo
repo: SamarVScode/XLSX-STREAM-REPORT-GENERATOR
url: https://github.com/SamarVScode/XLSX-STREAM-REPORT-GENERATOR
stack: [Python 3.10+, FastAPI, Rust Calamine, OpenXML, Render]
cluster: logistics-stream-engine
tags: [project, backend, excel-streaming, scm, high-throughput]
---

# 📊 XLSX-STREAM-REPORT-GENERATOR (`ei_stream_server`)

## 📌 Executive Summary
High-throughput, Zero-DOM streaming engine designed to process massive production supply chain Excel workbooks (**200 MB+**, **500,000+ rows**) using **less than 35 MB of RAM**. Built specifically to defeat memory exhaustion (OOM crashes) on 512 MB cloud tiers (Render).

---

## 🛠️ Tech Stack & Architecture
* **Runtime:** Python 3.10+ (FastAPI + Uvicorn)
* **Stream Ingestion:** Rust-backed `python-calamine` / SAX event parser (row-by-row streaming, $O(1)$ constant memory).
* **OpenXML Assembler:** Hybrid OpenXML ZIP stitcher combining on-disk XML fragments with micro-workbooks.
* **Hosting:** Render Web Service (`render.yaml`).

### Core Report Generators (`generators/`):
* `conversion_report_generator.py`
* `cpd_breach_report_generator.py`
* `ei_generator.py` & `eob_generator.py`
* `forward_pendency_generator.py` & `reverse_pendency_generator.py`
* `nps_report_generator.py`
* `second_attempt_adherence_generator.py`
* `tat_report_generator.py` & `weekly_scm_tat_generator.py`
* `untraceable_report_generator.py`
* `vms_adherence_report_generator.py`

---

## ⚠️ Known Gotchas & Bugs (Audit)
* **Committed Secret File:** An unencrypted `API_KEY.txt` file is committed to the Git repository. While convenient for local development, production deployments on Render must pull `API_KEY` exclusively from environment variables to prevent token leakage.
* **Single Concurrent Job Semaphore:** In `core/downloader.py` / `core/jobs.py`, `MAX_CONCURRENT_JOBS` is set to `1` by design to protect 512 MB RAM limits. If multiple GAS scripts request reports simultaneously, jobs will queue or time out if not handled with async polling.

---

## 🚀 Setup & Runbook
```bash
# 1. Install dependencies
pip install -r requirements.txt

# 2. Run locally
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

### Environment Variables
* `API_KEY`: Authentication secret for incoming generation jobs.
* `PORT`: Set automatically by Render.

---

## 🔗 Knowledge Graph Connections
### Parent & Sister Bridges:
* [[Projects/Repo-xlsx_to_csv_bridge|xlsx_to_csv_bridge]]
* [[Projects/Repo-DataConversion|DataConversion]]

### Connected Google Apps Script Pipelines:
* [[Projects/GAS-EI-Pan-India-Report|GAS: EI Pan India Report]]
* [[Projects/GAS-HourlyConversionReport|GAS: HourlyConversionReport]]
* [[Projects/GAS-Lake-Ingestion-Pipeline|GAS: Lake Ingestion Pipeline]]
* [[Projects/GAS-dc-rca-progression|GAS: dc rca progression]]
* [[Projects/GAS-spf-final|GAS: spf final]]
