# Autonomous Safe Landing Spot Detection for Quadrotor Systems

**Authors:** Kanishk Lamba (B22ME029) , Yash Golani (B22ME072)
**Supervisors:** Dr. Riby Abraham Boby, Dr. Jayant Kumar Mohanta  
**Department:** Mechanical Engineering, IIT Jodhpur  
**Submitted:** November 2025

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

## Results & Figures (from report)
> The images below are taken directly from the submitted report. If you want PNG copies inside the repo, extract them from the PDF pages linked below.

<img width="989" height="466" alt="Screenshot 2025-11-17 143040" src="https://github.com/user-attachments/assets/96c79164-f253-4f31-aa5d-1a2b05391825" />

- **Figure 1 — High-altitude drone segmentation result**

 
- **Figure 2 — IIT Jodhpur campus segmentation result**  
  `![Figure 2 — Campus segmentation](/mnt/data/report btp.pdf#page=13)` (see report page 13). :contentReference[oaicite:3]{index=3}

- **Figure 3 — Dim-light segmentation result**  
  `![Figure 3 — Dim-light segmentation](/mnt/data/report btp.pdf#page=13)` (see report page 13). :contentReference[oaicite:4]{index=4}

- **Figure 4 — Gazebo simulation + rqt image view**  
  `![Figure 4 — Gazebo / rqt view](/mnt/data/report btp.pdf#page=11)` (see report page 11). :contentReference[oaicite:5]{index=5}

> Notes: Figures are referenced from the project PDF. Use the page-linked PDF images above or extract them (recommended `pdfimages` or a PDF viewer export) into `docs/figures/` for nicer display on GitHub.

---

## Evaluation / Metrics
The project tracks standard segmentation metrics during training and evaluation:
- **mIoU (mean Intersection over Union)**
- **Precision / Recall**
- Qualitative results and edge-case discussion are in the report (boundary fuzziness, small-object misses, dim-light robustness). :contentReference[oaicite:6]{index=6}

### Quick plotting snippet
If you log training metrics to `training_logs/metrics.csv` with columns `epoch, mIoU, precision, recall`, run this script to plot them locally:

```python
# tools/plot_metrics.py
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv('training_logs/metrics.csv')
plt.figure()
plt.plot(df['epoch'], df['mIoU'], label='mIoU')
plt.plot(df['epoch'], df['precision'], label='Precision')
plt.plot(df['epoch'], df['recall'], label='Recall')
plt.xlabel('Epoch')
plt.ylabel('Metric value')
plt.legend()
plt.title('Training metrics')
plt.grid(True)
plt.savefig('training_logs/metrics_plot.png', dpi=200)
print('Saved training_logs/metrics_plot.png')
