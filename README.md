# 🦺 Vision-Based Industrial Safety Monitoring System

A real-time computer vision-based industrial safety monitoring system using **YOLOv8-Pose** for human pose estimation and posture analysis.

The system detects human body keypoints, classifies human postures, identifies unsafe bending postures, and generates visual and audio alerts. The broader research framework also proposes fall detection and hazardous proximity monitoring based on temporal pose analysis and ISO 13855 safety-distance concepts.

---

## 📌 Overview

Industrial environments contain several safety risks, including unsafe worker postures, falls, and proximity to hazardous machinery.

This project uses computer vision and human pose estimation to monitor workers in real time. **YOLOv8-Pose** is used to detect humans and extract 17 body keypoints. These keypoints are then analyzed using body orientation and joint-angle calculations to classify postures and identify unsafe bending conditions.

The project also presents a broader research framework for integrating:

- Human pose estimation
- Unsafe posture detection
- Fall detection
- Hazardous proximity monitoring
- ISO 13855 safety-distance concepts
- Visual and audio safety alerts

---

## 🎯 Objectives

- Perform real-time human pose estimation using YOLOv8-Pose.
- Extract and analyze human body keypoints.
- Identify different human postures such as standing, sitting, sleeping, and bending.
- Detect unsafe bending postures using body and joint-angle analysis.
- Provide real-time visual and audio alerts for unsafe postures.
- Develop a framework for fall detection and hazardous proximity monitoring.
- Incorporate the ISO 13855 safety-distance concept into the proposed safety-monitoring framework.

---

## 🏗️ System Architecture

```text
                 VIDEO INPUT
              (Webcam / Video)
                     │
                     ▼
              FRAME EXTRACTION
                     │
                     ▼
              YOLOv8-POSE MODEL
                     │
                     ▼
           17 HUMAN BODY KEYPOINTS
                     │
              ┌──────┴──────┐
              │             │
              ▼             ▼
        POSTURE ANALYSIS   SAFETY ANALYSIS
              │             │
              │       ┌─────┴─────┐
              │       │           │
              │       ▼           ▼
              │   FALL DETECTION  PROXIMITY
              │                   MONITORING
              │
              └──────────┬────────┘
                         ▼
                 SAFETY EVALUATION
                         │
                         ▼
                    ALERT SYSTEM
                    ┌────┴────┐
                    ▼         ▼
              VISUAL ALERT  AUDIO ALERT
```

> **Note:** Posture detection and bending alerts are implemented in the current code. Fall detection and proximity monitoring are part of the broader research framework.

---

## 🔍 Key Features

- **Human Pose Estimation** — Detects 17 human body keypoints using YOLOv8-Pose.
- **Posture Detection** — Identifies standing, sitting, sleeping, bending, and unknown postures.
- **Bending Detection** — Uses body orientation, spine angle, and hip-knee angle to identify bending.
- **Real-Time Monitoring** — Processes webcam frames continuously for live safety monitoring.
- **Visual Alerts** — Displays posture labels and warning banners on the video.
- **Audio Alerts** — Generates an audio warning when bending is detected.
- **Fall Detection** — Proposed as part of the broader multi-hazard safety-monitoring system.
- **Proximity Monitoring** — Proposed as part of the broader industrial safety framework.

---

## ⚙️ Methodology

### 1. Pose Estimation

The system uses the pretrained **YOLOv8n-Pose** model to detect humans and extract 17 body keypoints.

The keypoints include major body locations such as:

- Nose
- Shoulders
- Hips
- Knees
- Ankles

These keypoints are used for further posture analysis.

### 2. Posture Analysis

The detected keypoints are used to calculate:

- Shoulder midpoint
- Hip midpoint
- Body orientation
- Spine angle
- Hip-knee angle
- Vertical body compression

These geometric features are used to classify the person's posture.

### 3. Bending Detection

The system identifies bending using a combination of body orientation and joint-angle conditions.

Unsafe bending is detected when the calculated body and joint angles satisfy the predefined bending conditions.

When bending is detected, the system activates the safety alert.

### 4. Fall Detection — Proposed System

The research framework uses temporal information from consecutive frames to identify possible falls.

The proposed approach considers:

- Sudden downward body movement
- Body orientation
- Temporal position changes
- Stationary behavior after a fall

### 5. Proximity Monitoring — Proposed System

The research framework incorporates hazardous proximity monitoring based on worker-machine distance.

The proposed system uses the **ISO 13855 safety-distance concept** to define safe and warning regions around hazardous machinery.

### 6. Alert Generation

When an unsafe condition is detected, the system can provide:

- Visual warning
- Posture label
- Audio alert

---

## 🖥️ Current Implementation

The current implementation provides real-time webcam-based:

- YOLOv8-Pose estimation
- Human keypoint extraction
- Posture classification
- Bending detection
- Visual alerts
- Audio alerts

The implementation uses the `yolov8n-pose.pt` model and processes webcam frames in real time.

### Current Posture Classes

- Standing
- Sitting
- Sleeping
- Bending
- Unknown

> **Note:** Fall detection and hazardous proximity monitoring are part of the broader research framework described in the research paper and are not included in the current `safety_monitor.py` implementation.

---

## 💻 Demo / Output

### Real-Time Pose Detection

The system detects the human body and displays the corresponding skeletal keypoints.

### Posture Classification

The system classifies the detected posture as:

- Standing
- Sitting
- Sleeping
- Bending
- Unknown

### Safety Alert

When an unsafe bending posture is detected:

- A warning is displayed on the video.
- An audio alert is generated.
- The detected person's posture is labelled on the screen.

> Screenshots and demonstration videos can be added to this section.

---

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| YOLOv8-Pose | Human pose estimation |
| OpenCV | Video capture and image processing |
| NumPy | Numerical calculations |
| Computer Vision | Real-time safety monitoring |

---

## 📦 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/Kavanagunaga/vision-based-industrial-safety-monitoring.git
cd vision-based-industrial-safety-monitoring
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Download YOLOv8-Pose Model

The project uses:

```text
yolov8n-pose.pt
```

Place the model file in the project directory before running the program.

> The YOLO model weights are excluded from Git using `.gitignore`.

---

## ▶️ Running the Project

Run the following command:

```bash
python safety_monitor.py
```

The system will:

1. Open the webcam.
2. Detect humans.
3. Extract body keypoints.
4. Classify the detected posture.
5. Display the pose skeleton and posture label.
6. Trigger an alert when bending is detected.

Press:

```text
q
```

to exit the application.

---

## 📊 Research Results

The following results are reported in the research paper for the proposed multi-hazard safety-monitoring framework:

| Metric | Reported Result |
|---|---:|
| Overall Accuracy | 98.8% |
| Fall Detection Accuracy | 99% |
| Proximity Detection | 98.4% |
| Precision / Recall / F1 | >93% |
| Processing Speed | ~28.3 FPS |

> **Important:** These are results reported for the research framework and should not be interpreted as performance measurements of the current `safety_monitor.py` implementation.

---

## ⚠️ Limitations

The research system has limitations under certain operating conditions:

- Poor lighting conditions can affect keypoint detection.
- Rapid human movement can reduce detection reliability.
- Occlusion of body parts can affect pose estimation.
- Changes in camera viewpoint can affect hazard-zone detection.
- Missing or noisy keypoints can influence posture classification.

---

## 🚀 Future Work

Future development can include:

- Multi-camera support
- Improved handling of human occlusion
- More robust fall detection
- Machine-specific object detection
- Improved industrial hazard-zone detection
- Edge-device deployment
- Real-time safety dashboard
- Industrial IoT integration
- Improved calibration for safety-distance estimation

---

## 📁 Project Structure

```text
vision-based-industrial-safety-monitoring/
│
├── README.md
├── requirements.txt
├── .gitignore
├── safety_monitor.py
├── ml_paper_with_authors.pdf

```

### File Description

| File | Description |
|---|---|
| `safety_monitor.py` | Main Python implementation for real-time pose estimation and posture monitoring |
| `requirements.txt` | Python dependencies required to run the project |
| `.gitignore` | Files and folders excluded from Git tracking |
| `ml_paper_with_authors.pdf` | Research paper related to the project |
| `README.md` | Project documentation and usage instructions |

---

## 📄 Research Paper

The research paper associated with this project is available here:

[View Research Paper](ml_paper_with_authors.pdf)

**Title:**  
*Vision-Based Multi-Hazard Industrial Safety Monitoring Using YOLOv8 Pose Estimation*

---

## 👥 Authors

**Kavana Gunaga**  
Department of Electronics and Communication Engineering  
KLE Technological University, Hubli, India

**Pavitra Indi**  
Department of Electronics and Communication Engineering  
KLE Technological University, Hubli, India

**Prof. Satish Chikkamath**  
KLE Technological University, Hubli, India

**Sagar Nadagaddi**  
KLE Technological University, Hubli, India

---


## ⭐ Acknowledgements

- Ultralytics YOLOv8
- OpenCV
- NumPy
- KLE Technological University
