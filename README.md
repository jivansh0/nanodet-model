# 🔥 Thermal Object Detection with NanoDet on HIT-UAV Dataset

## 🚀 Project Overview

This project focuses on building and evaluating a real-time, lightweight object detection model using **NanoDet** to identify various objects in high-altitude infrared thermal imagery from the **HIT-UAV dataset**. The goal is to provide a robust solution for thermal object detection, especially useful in scenarios where visible light cameras are less effective (e.g., night, smoke, fog).

<p align="center">
  <img src="https://github.com/RangiLyu/nanodet/raw/main/figures/nanodet-plus.png" width="400" alt="NanoDet Logo">
  <br>
  <em>NanoDet: A lightweight, real-time object detection model.</em>
</p>

## ✨ Features

* **NanoDet Implementation:** Utilizes the efficient NanoDet architecture for fast inference.
* **HIT-UAV Dataset Integration:** Adapts NanoDet for the High-Altitude Infrared Thermal (HIT-UAV) dataset.
* **YOLO to COCO Conversion:** Includes a custom script to convert YOLO-formatted annotations to COCO, a standard for object detection frameworks.
* **Automated Configuration:** Programmatically modifies NanoDet's configuration for seamless training.
* **Training & Evaluation Pipeline:** Comprehensive setup for training the model and evaluating its performance using standard COCO metrics (mAP, AR).
* **Kaggle-Optimized:** Designed to run smoothly within a Kaggle Notebook environment with GPU acceleration.

## 📁 Project Structure

The project builds upon the cloned NanoDet repository and organizes the dataset as follows:
