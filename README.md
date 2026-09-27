# vision-based-industrial-safety-monitoring
Real-time industrial safety monitoring using YOLOv8-Pose for human posture, fall, and hazardous proximity detection.
---

## 🎯 Objectives

- Detect workers in real time using computer vision.
- Extract human body keypoints using YOLOv8-Pose.
- Identify unsafe postures such as bending.
- Detect sudden falls using temporal body movement.
- Monitor worker proximity to hazardous machinery.
- Apply the ISO 13855 safety-distance concept.
- Generate real-time visual and audio alerts.

---

## 🔍 Key Features

- **Human Pose Estimation** — Detects 17 human body keypoints using YOLOv8-Pose.
- **Posture Detection** — Identifies standing, sitting, sleeping, bending, and unknown postures.
- **Bending Detection** — Uses body orientation and joint angles to identify unsafe bending.
- **Fall Detection** — Uses temporal body movement and body-angle changes to identify falls.
- **Proximity Monitoring** — Monitors worker proximity to predefined machine hazard zones.
- **Safety Alerts** — Provides visual and audio alerts when unsafe conditions are detected.

---

## 🧠 Methodology

The system processes video frames using the **YOLOv8-Pose** model to extract 17 human body keypoints.

Important keypoints such as the shoulders, hips, knees, wrists, and elbows are used to analyze worker posture and movement.

### 1. Pose Estimation

Video input is processed frame-by-frame using the YOLOv8-Pose model.

The model produces 17 skeletal keypoints for each detected person.

### 2. Posture Analysis

The detected keypoints are used to calculate body orientation and joint angles.

These measurements are used to identify postures such as:

- Standing
- Sitting
- Sleeping
- Bending

### 3. Bending Detection

Bending detection considers:

- Body angle
- Spine angle
- Hip-knee angle
- Shoulder and hip positions

An alert is generated when the detected body configuration satisfies the bending conditions.

### 4. Fall Detection

Fall detection uses temporal information from consecutive frames.

The system analyzes:

- Sudden vertical displacement
- Body inclination
- Body orientation
- Motion after a possible fall

### 5. Proximity Monitoring

Worker body keypoints are compared with predefined hazardous zones around machinery.

The distance between the worker and the hazard zone is used to determine whether a safety boundary has been violated.

### 6. Alert Generation

When an unsafe condition is detected, the system provides:

- Visual warning on the video frame
- Audio alert

---

## ⚙️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| YOLOv8-Pose | Human pose estimation |
| OpenCV | Video capture and processing |
| NumPy | Numerical calculations |
| Computer Vision | Safety monitoring |
| Human Pose Estimation | Posture and movement analysis |

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

> **Note:** Fall detection and hazardous proximity monitoring are part of the broader proposed/research system documented in the research paper.

---

## 🚀 Installation

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/vision-based-industrial-safety-monitoring.git
