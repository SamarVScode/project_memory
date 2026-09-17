# 🏢 Myntra Logistics & Operational Infrastructure

## Overview
Comprehensive domain model of the logistics and warehouse operations spanning distribution centers (DC), regional hubs, delivery stations, and agent field networks.

---

## 🗺️ Operational Clusters

### 1. Logistics Stream & Reporting Engine
High-throughput data pipelines calculating pan-India throughput, return pendencies, breach alerts, and shift conversions.
* **Core Hub:** [[Projects/Repo-XLSX-STREAM-REPORT-GENERATOR|XLSX-STREAM-REPORT-GENERATOR]]
* **Conversion Bridge:** [[Projects/Repo-xlsx_to_csv_bridge|xlsx_to_csv_bridge]]
* **Filter Service:** [[Projects/Repo-DataConversion|DataConversion]]
* **GAS Satellites:**
  * [[Projects/GAS-EI-Pan-India-Report|EI Pan India Report]]
  * [[Projects/GAS-HourlyConversionReport|Hourly Conversion Report]]
  * [[Projects/GAS-Lake-Ingestion-Pipeline|Lake Ingestion Pipeline]]
  * [[Projects/GAS-dc-rca-progression|DC RCA Progression]]
  * [[Projects/GAS-spf-final|SPF Final]]
  * [[Projects/GAS-RVP-Q2-AppendAutomation|RVP Q2 Append Automation]]
  * [[Projects/GAS-RTO-Q2-appendAutomation|RTO Q2 Append Automation]]
  * [[Projects/GAS-D-1-SummaryAutomation|D-1 Summary Automation]]
  * [[Projects/GAS-shipment-reco|Shipment Reco]]

### 2. Warehouse Vision & VMS Overlay (Standalone Packing Station)
Station hardware integration recording live packing/bagging operations to verify barcode integrity and store video proof.
* **Workstation Overlay:** [[Projects/Repo-Bagging-VMS-overlay|Bagging-VMS-overlay]]
* **Camera Bridge:** [[Projects/Repo-cameraOverlayBridge|cameraOverlayBridge]]
* **GAS Backend:** [[Projects/GAS-Bagging-VMS-System|Bagging VMS System]]

### 3. Agent Operations & Manpower Tracking (L4D & Payouts)
Mobile and administrative tooling tracking agent shifts, leave requests, commissions, and 4-day inactivity (L4D) attendance.
* **Mobile & Admin Hub:** [[Projects/Repo-agent-summary-mechanism|agent-summary-mechanism]]
* **GAS Engines:**
  * [[Projects/GAS-live-l4d-test|Live L4D Inactivity Engine]]
  * [[Projects/GAS-Agent-payout|Agent Payout]]
  * [[Projects/GAS-agent-backend-payout|Agent Backend Payout]]
  * [[Projects/GAS-userdefinedDB|User-Defined DB]]
  * [[Projects/GAS-App-Dashborad|App Dashboard]]
  * [[Projects/GAS-North-Dashboard-Server|North Dashboard Server]]

### 4. Financial Reconciliation & Cash Management
Automated tracking of cash-on-delivery (COD) remittances, transaction IDs, and float injections.
* **GAS Engines:**
  * [[Projects/GAS-COD-Automation|COD Automation]]
  * [[Projects/GAS-casj|Cash Reconciliation (casj)]]
  * [[Projects/GAS-cash-inject|Cash Inject]]
  * [[Projects/GAS-tidFinder|TID Finder]]
  * [[Projects/GAS-PreAlertAutomation|Pre-Alert Automation]]
