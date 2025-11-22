# Autonomous Safe Landing Spot Detection for Quadrotor Systems

**Authors:** Kanishk Lamba (B22ME029) , Yash Golani (B22ME072)

**Department:** Mechanical Engineering, IIT Jodhpur  

---

## Project Overview
This repository contains code, data pointers, and scripts for the project **“Autonomous Safe Landing Spot Detection for Quadrotor Systems”** — a hybrid system combining semantic segmentation (DeepLabV3+) with geometric analysis (RANSAC plane-fitting) to autonomously select safe landing sites during emergencies.

Key components:
- Emergency trigger detection (IMU & system limits)
- Visual segmentation (DeepLabV3+ with Xception backbone)
- Geometric flatness verification (RANSAC on depth point clouds)
- ROS 2 + PX4 SITL integration for simulation and transition to hardware

---

## Highlights / Features
- Pixel-level semantic segmentation to mark safe vs unsafe terrain.
- RANSAC-based plane fitting to ensure geometric safety (slope threshold, area).
- Integrated SITL pipeline: Gazebo (sensors) → PX4 SITL → ROS2 nodes → inference & landing command.
- Scripts for offline inference on videos and live ROS node integration.

---

## Results & Figures 

<img width="989" height="466" alt="Screenshot 2025-11-17 143040" src="https://github.com/user-attachments/assets/96c79164-f253-4f31-aa5d-1a2b05391825" />

**Figure 1 — High-altitude drone segmentation result**

 <img width="820" height="264" alt="Screenshot 2025-11-17 143651" src="https://github.com/user-attachments/assets/f6d48e51-bb3a-4f20-bb8b-277fbd946da3" />

**Figure 2 — IIT Jodhpur campus segmentation result**

 <img width="819" height="258" alt="Screenshot 2025-11-17 143552" src="https://github.com/user-attachments/assets/2fad2b46-fc21-4c87-bfec-008e5ba5bace" />

**Figure 3 — Dim-light segmentation result**  

<img width="1513" height="798" alt="Screenshot 2025-11-17 145342" src="https://github.com/user-attachments/assets/c9e8216b-5d41-430e-947a-1ada3c248eed" />

**Figure 4 — Gazebo simulation + rqt image view**  

---

## Evaluation / Metrics
The project tracks standard segmentation metrics during training and evaluation:
- **mIoU (mean Intersection over Union)**
- **Precision / Recall**  
