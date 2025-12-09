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


### 📁 Step 2 — Model Files

Place the following trained YOLO weights inside the project root folder:

yolo_ANPR.pt → License plate detection model

yolo_ATCC.pt → Traffic classification model

⚠ Large weight files (100MB+) may require Git LFS or external storage such as Google Drive, Kaggle, or HuggingFace.

### 💡 Usage Instructions
▶ Running the Streamlit Application
streamlit run app.py

### 🌐 Application Workflow

Choose Model Type: ANPR or ATCC

Upload an image or video

Real-time inference displays annotated visual results

Download:

Processed video/image

Detection log (CSV)

### 📚 Model Training & Dataset Preparation

The following notebooks guide model development and dataset annotation:

### 🏎 ANPR Model Training (anpr-license-traning.ipynb)

Framework: YOLOv8

Target Class: license_plate (ID: 0)

Training Duration: 30 epochs

Performance Results:

mAP50: 0.854

mAP50-95: 0.475

###  🚌 ATCC Model Training (atcc-bdd100k.ipynb)

Model Type: Multi-class YOLOv8 object detection

Dataset: BDD100K (traffic environment dataset)

Preprocessing Pipeline: JSON → YOLO TXT format conversion

Classes: Includes car, truck, bus, pedestrian, traffic light, etc.

Validation Metrics:

mAP50: 0.587

mAP50-95: 0.325

### 2. Model Files
The Streamlit application requires the following trained YOLO model weights (.pt files) in the root directory:

yolo_ANPR.pt (for license plate detection)
yolo_ATCC.pt (for traffic object detection)
### 💡 Usage
Running the Streamlit App
Start the application from your terminal:

streamlit run app.py
Application Workflow
Select the Model Type in the sidebar: ANPR or ATCC.
Upload an image or video file via the interface.
The application processes the file, displaying the annotated result and providing a Download Processed Video/Image button and a Detailed Detection Log (for videos).
📚 Training and Data Preparation
The provided Jupyter notebooks detail the training and data preparation processes used to create the models.

## 1. ANPR Model Training (anpr-license-traning.ipynb)
Model: YOLOv8 trained specifically for license plate detection.
Target Class: Single class: license_plate (0).
Training Details: Trained using the ultralytics library for 30 epochs.
Validation Performance: Final mAP50: 0.854, mAP50-95: 0.475.
## 2. ATCC Model Training (atcc-bdd100k.ipynb)
Model: YOLOv8 trained for multi-class traffic object classification.
Dataset: Uses the BDD100K dataset.
Preprocessing: The notebook provides scripts to convert BDD100K JSON annotations into the standard YOLO format (.txt files) with normalized bounding box coordinates.
Classes: 10 traffic-related classes including car, truck, bus, pedestrian, traffic light, etc.
Validation Performance: Final mAP50: 0.587, mAP50-95: 0.325.
