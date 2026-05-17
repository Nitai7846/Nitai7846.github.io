---
title: "Photogrammetric Vehicle Speed Estimation from Stationary Roadside Video"
excerpt: "A monocular pipeline for measuring highway vehicle speeds using a single stationary camera — no radar, no GPS, no in-vehicle sensors.<br/><img src='https://raw.githubusercontent.com/Nitai7846/Monocular-Speed-Estimation-TAMIDS-ODS/main/docs/figures/pipeline_main.png'>"
collection: portfolio
---

## Overview

A complete pipeline for measuring highway vehicle speeds using a single stationary camera. Tested on **420+ vehicles across 73 videos** on SH-47 in Brazos County, TX, achieving **63.8% of vehicles within ±10 mph** of radar ground truth.

## Pipeline

The system is organized into five modules:

1. **Detection & Tracking** — YOLOv8x + BotSORT for vehicle detection and multi-object tracking across frames
2. **3D Reconstruction** — Google Street View panoramas processed through COLMAP to build a metric-scale point cloud (GPS-verified to 0.44% scaling error)
3. **Camera Localization** — RoMA dense feature matching + PnP with RANSAC to recover the camera's 6-DoF pose
4. **Speed Estimation** — Bounding-box corners are undistorted, cast as rays from the camera center, and intersected with a RANSAC ground plane to produce 3D trajectories
5. **AOI Selection** — Traffic cones automatically define the measurement zone for standardized speed computation

![Pipeline Overview](https://raw.githubusercontent.com/Nitai7846/Monocular-Speed-Estimation-TAMIDS-ODS/main/docs/figures/end_to_end_pipeline.png)

## Results

![Results](https://raw.githubusercontent.com/Nitai7846/Monocular-Speed-Estimation-TAMIDS-ODS/main/docs/figures/results_scatter.png)

## Tools

Python, PyTorch, COLMAP, YOLOv8, BotSORT, RoMA, OpenCV, Open3D

## Code

[GitHub Repository](https://github.com/Nitai7846/Monocular-Speed-Estimation-TAMIDS-ODS)
