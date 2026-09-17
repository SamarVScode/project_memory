# ⚡ FastAPI Render Bridges & Stream Processing

## Overview
A cluster of microservices hosted on Render (`0.0.0.0:$PORT`) designed to handle streaming data transformations with flat $O(1)$ memory footprints.

---

## 🏛️ Microservice Fleet
1. **[[Projects/Repo-XLSX-STREAM-REPORT-GENERATOR|XLSX-STREAM-REPORT-GENERATOR (`ei_stream_server`)]]**
   * Multi-sheet Excel workbook generator.
   * Processes 500,000+ rows using Rust Calamine and streaming OpenXML ZIP stitchers under 35 MB RAM.
2. **[[Projects/Repo-xlsx_to_csv_bridge|xlsx_to_csv_bridge]]**
   * Bi-directional streaming conversion bridge for Google Apps Script.
   * CORS locked to `https://script.google.com`.
3. **[[Projects/Repo-DataConversion|DataConversion]]**
   * Job-based DC vs. Hub filtering engine returning isolated CSV chunks.

---

## 🔐 Security & Auth
* All endpoints validate the `X-API-KEY` or `API_KEY` header.
* Communication between Render and GAS uses HTTPS POST streams.
