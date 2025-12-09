# ANPR-ATCC-SMART-TRAFFIC-MANAGEMENT

# 🚘 Automated Vision System: ANPR & Traffic Classification

This repository presents an end-to-end automated vision solution designed for intelligent transportation applications. It integrates two major computer-vision modules:

1. **Streamlit-based web application (`app.py`)** for real-time inference supporting:
   - **Automatic Number Plate Recognition (ANPR)**
   - **Automatic Traffic Count & Classification (ATCC)**

2. **Jupyter notebooks** explaining dataset preparation and model training procedures for custom **YOLOv8** models.

---

## 🚀 Key Features

- **🔍 ANPR (Automatic Number Plate Recognition):**
  - Detects vehicle license plates from images or video streams using a custom YOLO model (`yolo_ANPR.pt`)
  - Performs OCR (Optical Character Recognition) on detected plates to extract alphanumeric information
  - Generates structured outputs including extracted text and bounding boxes

- **🚗 ATCC (Automatic Traffic Count & Classification):**
  - Detects and classifies various traffic objects (cars, trucks, buses, pedestrians, traffic signs, etc.)
  - Provides real-time object tracking and counting for surveillance and analytics
  - Uses a YOLO-based model (`yolo_ATCC.pt`) trained on multi-class traffic datasets

- **💻 Interactive Streamlit UI**
  - Upload and process images or videos with user-friendly controls
  - Real-time visual output with bounding box overlays
  - Detailed detection logs and ability to download processed results

- **📄 Data Logging & Export**
  - Saves detection results into CSV format including timestamps, object type, confidence scores & OCR results

---

## 🛠️ Setup & Installation

### ✔ Prerequisites
Ensure you have:
- Python **3.8 or newer**
- Recommended: CUDA-enabled GPU for faster processing (optional)

---

### 📦 Step 1 — Install Dependencies

The required Python libraries include YOLOv8 utilities, OCR, Streamlit and OpenCV.

| Dependency | Purpose |
|------------|---------|
| `ultralytics` | YOLOv8 inference and training support |
| `streamlit` | Running the interactive web UI |
| `fast_plate_ocr` | OCR engine for number plate text extraction |
| `opencv-python`, `numpy`, `pillow`, `pandas` | Image manipulation and data processing |

```bash
# Install core dependencies
pip install -qU ultralytics opencv-python pillow pandas streamlit

# Install OCR module
pip install fast_plate_ocr

# Optional: dependencies for training notebooks
pip install numpy opencv-python-headless
