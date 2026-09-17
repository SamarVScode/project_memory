---
type: github-repo
repo: SamarVScode/cameraOverlayBridge
url: https://github.com/SamarVScode/cameraOverlayBridge
stack: [HTML5, JavaScript, WebRTC, Iframe Bridge]
cluster: warehouse-vision-vms
tags: [project, frontend, webrtc, camera, bridge, myntra]
---

# 📹 cameraOverlayBridge

## 📌 Executive Summary
Dedicated hardware bridge interface providing low-latency camera and microphone permission passthrough to an embedded Myntra enterprise Google Apps Script deployment.

---

## 🛠️ Architecture
* **Interface:** Standalone HTML5 web shell with embedded high-privilege `<iframe>`.
* **Permissions:** Explicit `allow="camera; microphone"` hardware permission bypass.
* **Embedded Endpoint:** Direct Myntra GAS deployment endpoint (`AKfycbyEcPUQIhHSLjaBpsJcxHGg0KTs9qiluWUef1D8i8OhNTOp9xp2wos3ZoIMChNlhP3jtw`).

---

## ⚠️ Known Gotchas & Bugs (Audit)
* **Hardcoded Script Deployment URL:** Unlike `Bagging-VMS-overlay` which has a settings UI to change the GAS URL in `localStorage`, `cameraOverlayBridge` has the `/exec` URL **hardcoded on line 134**. If the GAS script is redeployed with a new deployment ID, this HTML file must be manually edited and committed.
* **Corrupted UTF-8 Characters:** Lines 131, 234, 244, and 256 contain broken multi-byte encoding characters (`"`) in comment headers.
* **Missing README:** The repository lacks any `README.md` documentation.

---

## 🔗 Knowledge Graph Connections
* Related Interface: [[Projects/Repo-Bagging-VMS-overlay|Bagging-VMS-overlay]]
* Connected GAS Endpoint: [[Projects/GAS-Bagging-VMS-System|GAS: Bagging VMS System]]
