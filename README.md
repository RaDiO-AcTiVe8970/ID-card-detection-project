# 🪪 AIUB Student ID Card Detection

> A computer vision project that detects AIUB student ID cards in images using a fine-tuned Faster R-CNN model, built with the TensorFlow Object Detection API.

![Python](https://img.shields.io/badge/Python-3.8+-blue?style=for-the-badge&logo=python&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange?style=for-the-badge&logo=tensorflow&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=for-the-badge)

---

## 📌 Project Overview

This was the final project for **CSC 4254: Computer Vision and Pattern Recognition** at American International University-Bangladesh (AIUB). The goal was to build an end-to-end object detection pipeline capable of locating and drawing bounding boxes around AIUB student ID cards in photos.

The project uses **transfer learning** — starting from a pretrained Faster R-CNN model and fine-tuning it on a custom annotated dataset of ID card images.

---

## 🏗️ Pipeline

```
Image Collection → XML Annotation → CSV Conversion → TFRecord Generation → Model Fine-tuning → Inference
```

1. **Data Collection** — Photos of AIUB student ID cards captured under varied conditions
2. **Annotation** — Bounding boxes manually labelled using XML annotation files
3. **Preprocessing** — XML annotations converted to CSV, then to TFRecord format for TensorFlow
4. **Model Training** — Faster R-CNN pretrained model fine-tuned on the custom dataset
5. **Inference** — Trained model used to detect ID cards in new images (and optionally live webcam feed)

---

## 🗂️ Repository Structure

```
ID-card-detection-project/
├── Annotations/              # Label map, train/test CSV and TFRecord files
├── Trained_model/
│   └── my_faster_rcnn/       # Fine-tuned model checkpoints and pipeline config
├── main_script.py            # Full pipeline: annotation → TFRecord generation
├── detect_img.py             # Inference script — runs detection on images
├── Model_Training.ipynb      # Training notebook
├── Saved_img_1/2/3.jpg       # Sample detection output images
└── Project Report Group [D].pdf  # Full project report
```

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python | Core programming language |
| TensorFlow 2.x | Model training and inference |
| TensorFlow Object Detection API | Faster R-CNN architecture and utilities |
| OpenCV | Image loading and visualisation |
| Pandas | XML annotation to CSV conversion |
| PIL / Pillow | Image processing |
| Matplotlib | Output visualisation |
| Protobuf | Pipeline configuration |

---

## 🧠 Model Details

| Property | Value |
|---|---|
| Architecture | Faster R-CNN |
| Base model | Pretrained (transfer learning) |
| Fine-tuning steps | 500 |
| Batch size | 4 |
| Detection class | `id_card` (single class) |
| Input | RGB images |
| Output | Bounding boxes + confidence scores |

---

## 🚀 Getting Started

### Prerequisites
```bash
pip install tensorflow opencv-python pillow pandas matplotlib
# TensorFlow Object Detection API also required
# See: https://tensorflow-object-detection-api-tutorial.readthedocs.io/
```

### Run the Pipeline
```bash
# Step 1: Generate annotations, CSVs and TFRecords
python main_script.py

# Step 2: Train the model (command printed by main_script.py)
python model_main_tf2.py --model_dir="Trained_model/my_faster_rcnn" \
  --pipeline_config_path="Trained_model/my_faster_rcnn/pipeline.config" \
  --num_train_steps=500
```

### Run Inference on Images
Edit `detect_img.py` to set your model and image paths, then:
```bash
python detect_img.py
```
Detection output images will be saved as `Saved_img_1.jpg`, `Saved_img_2.jpg`, etc.

---

## 📸 Sample Output

The model successfully draws bounding boxes around AIUB ID cards with confidence scores. Sample detection results are included in the repo as `Saved_img_1.jpg`, `Saved_img_2.jpg`, and `Saved_img_3.jpg`.

---

## 📄 Project Report

A full written report covering the methodology, results, and analysis is included in the repository: [`Project Report Group [D].pdf`](./Project%20Report%20Group%20%5BD%5D.pdf)

---

## 👥 Team

Group D — CSC 4254, American International University-Bangladesh (AIUB)

**MD. Mohituzzaman Bhuiyan** (contributor)
Currently pursuing Master of Data Science at Adelaide University, Australia

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/mohituzzaman-bhuiyan-98531b159/)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?style=flat&logo=github)](https://github.com/RaDiO-AcTiVe8970)

---

## 📄 License

This project is licensed under the MIT License.
