# Garment Detection & Automated Quality Validation Engine

## 📌 Microservice Overview
This repository contains the standalone AI validation microservice for **Member 4**. The system ingests raw fashion product imagery, performs localized object detection to extract garment anchors, enforces asset quality guardrails, and records structured execution analytics.

### Core Responsibilities
* **Garment Detection:** Localizing apparel assets using a pre-trained `yolov8n.pt` computer vision weight matrix.
* **Asset Quality Enforcement:** Bypassing malformed or low-confidence imagery to prevent pipeline crashes.
* **Analytics Ingestion:** Structuring execution logs into a localized metrics matrix via an optimized pandas pipeline.

---

## 🏗️ System Architecture & Data Flow
The microservice functions as an isolated validation gatekeepers hub positioned at the repository root level:
[Raw Product Image] ──> [Member 4: FastAPI Gateway]
│
├──> [YOLOv8 Inference Check] ──> Bounding Box Extractor
├──> [Quality Guardrail Logic] ──> Filter Empty/Blurry Noise
└──> [Pandas Logger Engine] ──> Append to CSV Database

---

## 🌐 API Specifications & Integration Mapping

### 1. Real-Time Image Validation
* **Endpoint:** `POST /validate-image/`
* **Content-Type:** `multipart/form-data`
* **Request Payload:** Raw Image Binary (`.jpg`, `.jpeg`, `.png`, `.webp`)

#### Expected Success Response (`200 OK`)
```json
{
  "status": "Success",
  "filename": "sample_shirt.jpg",
  "detected_objects_count": 1,
  "validation_passed": true,
  "remarks": "Image passed verification standards."
}
2. Analytics Ledger Sync
Endpoint: POST /upload-csv/

Request Payload: Multi-part CSV file tracking data metrics tables.

🛠️ Local Environment Execution Guide
Prerequisites
Ensure your terminal environment is running Python 3.11+ and has the core workspace dependencies installed (fastapi, uvicorn, ultralytics, pandas).

Running the Uvicorn Server
Step directly into the module workspace directory:

PowerShell
cd Member_4
Boot up the local development live-reload server:

PowerShell
uvicorn main:app --reload
Access the interactive API playground docs via your browser at: http://127.0.0.1:8000/docs