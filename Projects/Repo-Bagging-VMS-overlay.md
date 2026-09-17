---
type: github-repo
repo: SamarVScode/Bagging-VMS-overlay
url: https://github.com/SamarVScode/Bagging-VMS-overlay
stack: [HTML5, JavaScript, WebM VP9, postMessage, GitHub Pages]
cluster: warehouse-vision-vms
tags: [project, frontend, vms, camera-overlay, barcode-scanner, warehouse]
---

# 🎥 Bagging-VMS-overlay

## 📌 Executive Summary
High-performance workstation web frontend designed for warehouse bagging tables. Captures live video from external USB cameras, detects barcode scanner input, records video clips in lightweight WebM VP9 (~300 kbps), and streams footage directly into Google Apps Script backend using an iframe `postMessage` bridge.

---

## 🛠️ Architecture & Features
* **Media Engine:** HTML5 Canvas + MediaStream Recording API (WebM VP9 codec).
* **Communication Bridge:** 100% CORS-free bidirectional `postMessage` protocol communicating with embedded Google Apps Script Web Apps.
* **Target Enterprise:** Myntra SCM Workstations (`script.google.com/a/macros/myntra.com/...`).

---

## 🚀 Setup & Runbook
```bash
# Run locally
python -m http.server 8080
# Or deploy to GitHub Pages (Settings -> Pages -> Branch: main)
```

---

## 🔗 Knowledge Graph Connections
* Connected Sister Bridge: [[Projects/Repo-cameraOverlayBridge|cameraOverlayBridge]]
* Connected Google Apps Script Backend:
  * [[Projects/GAS-Bagging-VMS-System|GAS: Bagging VMS System]]
