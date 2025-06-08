# NanoDet Object Detection on HIT-UAV Thermal Dataset

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-1.10%2B-red.svg)](https://pytorch.org/)
[![NanoDet](https://img.shields.io/badge/NanoDet-v0.3.0-brightgreen.svg)](https://github.com/RangiLyu/nanodet)
[![License](https://img.shields.io/badge/License-Apache%202.0-green.svg)](LICENSE)

> **End-to-end pipeline for training and evaluating a lightweight NanoDet object detector on the HIT-UAV high-altitude thermal infrared dataset.**

---

## 🚀 Project Overview

This repository demonstrates the process of:
- Setting up the environment and dependencies
- Converting the HIT-UAV dataset from YOLO to COCO format
- Training a NanoDet model for object detection
- Evaluating model performance on the test set

**NanoDet** is a real-time, anchor-free object detection model optimized for edge devices. The **HIT-UAV** dataset contains thermal images annotated for objects such as Person, Car, Bicycle, OtherVehicle, and DontCare.

---

## 📁 Directory Structure

```
/nanodet
    ├── config/
    │   ├── nanodet_hituav.yml
    ├── tools/
    │   ├── train.py
    │   ├── test.py
    ├── hituav_coco/
    │   ├── images/
    │   ├── annotations/
    └── ...
```

---

## ⚙️ Environment Setup

1. **Clone the repository:**
    ```bash
    git clone https://github.com/RangiLyu/nanodet.git
    cd nanodet
    ```

2. **Install dependencies:**
    ```bash
    pip install -q pyyaml opencv-python tqdm tensorboard torchmetrics pycocotools
    pip install -e .
    ```

3. **Apply compatibility patches (if needed):**
    - See project report for details on code modifications for PyTorch/PyTorch Lightning compatibility.

---

## 🗂️ Dataset Preparation

- **Source:** [HIT-UAV Dataset](https://github.com/VisDrone/HIT-UAV)
- **Format:** Original YOLO → Converted to COCO

**Conversion Script Example:**
```python
def convert_yolo_to_coco(dataset_root_path, output_dir):
    # ... conversion code ...
```

- Place the converted dataset in `hituav_coco/` with COCO-style `images/` and `annotations/`.

---

## 📝 Configuration

- Copy and modify the template config:
    ```bash
    cp config/legacy_v0.x_configs/nanodet-m.yml config/nanodet_hituav.yml
    ```
- Update:
    - `class_names`: `["Person", "Car", "Bicycle", "OtherVehicle", "DontCare"]`
    - `num_classes`: `5`
    - Data paths for train/val/test splits
    - Training parameters (batch size, epochs, etc.)

---

## 🏋️ Model Training

```python
python tools/train.py config/nanodet_hituav.yml
```

- Training logs and checkpoints will be saved to the specified `save_dir`.

---

## 📊 Training & Validation Performance

| Epoch | mAP@0.50:0.95 | AP@0.50 | AP@0.75 | AR@all |
|-------|---------------|---------|---------|--------|
| 10    | 0.107         | 0.269   | 0.067   | 0.231  |
| 100   | 0.316         | 0.597   | 0.298   | 0.419  |
| 200   | **0.345**     | **0.633** | **0.354** | **0.427** |

**Class-wise AP@0.50 (Epoch 200):**
| Class         | AP50  | mAP   |
|---------------|-------|-------|
| Person        | 59.3  | 22.2  |
| Car           | 93.2  | 60.8  |
| Bicycle       | 63.8  | 28.3  |
| OtherVehicle  | 64.2  | 46.8  |
| DontCare      | 35.8  | 14.2  |

---

## 🧪 Model Evaluation (Test Set)

```python
python tools/test.py --config config/nanodet_hituav.yml --model <path_to_best_checkpoint>
```

**Test Set Results:**

| Metric         | Value  |
|----------------|--------|
| mAP@0.50:0.95  | 0.352  |
| AP@0.50        | 0.649  |
| AP@0.75        | 0.314  |
| AR@all         | 0.444  |

**Class-wise AP@0.50 (Test Set):**
| Class         | AP50  | mAP   |
|---------------|-------|-------|
| Person        | 62.5  | 22.9  |
| Car           | 92.6  | 59.3  |
| Bicycle       | 62.1  | 27.5  |
| OtherVehicle  | 74.8  | 53.2  |
| DontCare      | 32.7  | 12.9  |

---

## 📈 Visualizations

<p align="center">
  <img src="https://user-images.githubusercontent.com/your_image.png" width="600" alt="Sample Detection Results"/>
</p>

---

## 🧠 Key Insights

- **NanoDet** is highly efficient and suitable for edge deployment.
- **HIT-UAV** provides a challenging thermal dataset for robust detection.
- **YOLO→COCO conversion** is essential for framework compatibility.
- **Class-wise performance** highlights strengths and areas for improvement (e.g., "Car" is detected best, "DontCare" is most challenging).

---

## 🔬 Future Work

- Hyperparameter tuning for improved accuracy
- Advanced data augmentation strategies
- Experimentation with other NanoDet variants or backbones
- Deployment on edge devices

---

## 📄 License

This project is licensed under the [Apache 2.0 License](LICENSE).

---

## 🙏 Acknowledgements

- [NanoDet by RangiLyu](https://github.com/RangiLyu/nanodet)
- [HIT-UAV Dataset](https://github.com/VisDrone/HIT-UAV)
- Kaggle for GPU resources

--- 
