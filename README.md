<p align="center">
  <img width="250" alt="PawChecks Logo" src="https://github.com/user-attachments/assets/f65afcf1-457d-497a-8291-1eb42d203df1" />
</p>

# Canine Lameness Detection System - PawChecks

> **Note:** This is a portfolio display repository. The full source code is not publicly available as the system is under continued development. All training data was collected under veterinary clinic agreements and is not included here.

A clinical web application that automatically grades canine lameness on the standard **0–4 veterinary scale** from an uploaded video - delivering results in under 20 seconds.

Built as a 4-person capstone project in partnership with veterinary clinics, the system brings together computer vision, pose estimation, and graph neural networks into a practical diagnostic tool for clinical use.

---

## Demo Video

Special Thanks to Paul for creating this demo video showcasing the application!

https://github.com/user-attachments/assets/4c2a72e5-7a5a-47c4-9e9b-5498378a089d

---

## Overview

Lameness assessment in dogs is typically performed manually by veterinarians through visual gait observation, which is inherently subjective and time-consuming. This system automates that process using a two-stage AI pipeline:

1. **Pose Estimation** - DeepLabCut extracts skeletal keypoints from each frame of the uploaded video
2. **Gait Classification** - A Spatial-Temporal Graph Convolutional Network (STGCN++) analyzes the keypoint sequences and predicts a lameness grade (0–4)

The result is surfaced to the clinician through a clean web interface with no specialized hardware required - just a standard video upload.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Backend | Python, Flask |
| Pose Estimation | DeepLabCut (DLC) |
| Gait Classification | PySKL STGCN++ |
| Frontend | HTML/CSS/JS |
| Containerization | Docker |

---

## System Architecture

```
Video Upload (Frontend)
        │
        ▼
  Flask REST API
        │
        ▼
 DeepLabCut Module
 (Keypoint Extraction)
        │
        ▼
 Data Translation Layer
 (DLC → STGCN-compatible format)
        │
        ▼
   STGCN++ Model
 (Gait Classification)
        │
        ▼
 Lameness Grade (0–4)
 returned to Frontend
```

---

## Model & Training

- **Dataset:** ~150 annotated gait videos sourced from **5 veterinary clinics**
- **Classification target:** Lameness grade on the standard 0–4 veterinary scale
- **Accuracy:** >85% classification accuracy within ±1 lameness grade
- **Inference time:** <20 seconds end-to-end from upload to result (measured on server-grade hardware; the demo video runs on a standard local machine and may take up to 3 minutes)
- **Pose model:** DeepLabCut trained on canine anatomical landmarks
- **Gait model:** PySKL STGCN++ operating on spatial-temporal keypoint graphs

---

## My Contributions

I served as **Backend & AI Lead** on this project. My primary areas of work:

- **DeepLabCut Integration** - Implemented the DLC module responsible for running pose estimation on uploaded videos and extracting per-frame skeletal keypoints
- **Data Translation Layer** - Designed and built the layer that converts raw DLC keypoint output into the spatial-temporal graph format expected by STGCN++, including handling frame normalization and skeleton graph construction
- **Backend API** - Developed Flask REST API endpoints and overall backend architecture, managing the request lifecycle from video ingestion through to returning predictions
- **Frontend** - Contributed to frontend development alongside the team

---

## SDLC Documentation

The project followed a full software development lifecycle. Documentation produced includes:

- Software Requirements Specification (SRS)
- Software Design Document (SDD)
- Testing Plan & Traceability Matrix
- User Manual
- Development Plan

---

## Team

Developed as a capstone project by a 4-person team.

- [paulwmcs](https://github.com/paulwmcs) - Team, Research, and AI Lead
- [Trevor-D-H](https://github.com/Trevor-D-H) - Documentation and Front-End Lead
- [VerditeB](https://github.com/VerditeB) - Presentation, QA, and Front-end Lead

Special thanks to the veterinary clinic partners who provided training data and clinical expertise, and to Paul for producing the demo video.

---

## References

- [DeepLabCut](https://github.com/DeepLabCut/DeepLabCut) - Mathis et al., Nature Neuroscience 2018
- [PySKL / STGCN++](https://github.com/kennymckormick/pyskl) - Duan et al., 2022

---

## A Note on Source Code & Data
 
This repo is just a showcase - the full source code isn't publicly available. The system is still actively being developed, and the training data contains sensitive medical information from veterinary clinics that we aren't able to share. If you have questions about the project feel free to reach out!
