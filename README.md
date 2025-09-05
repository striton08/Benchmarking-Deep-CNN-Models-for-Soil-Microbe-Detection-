# 🦠 Microorganism Detection and Classification in Soil

This project presents a complete deep learning pipeline for the detection and classification of soil microorganisms using state-of-the-art computer vision techniques. It combines object detection with YOLOv11 and image classification using a variety of CNN-based architectures to automate the analysis of microscopic soil images.

---

## 📌 Project Overview

Manual identification of microbes in soil is time-consuming and error-prone. This project leverages deep learning to automate microbe detection and classification from microscopy images. The pipeline is divided into two stages:

1. Object Detection using YOLOv11 to localize microbes.  
2. Classification of cropped microbes using multiple CNN models including:
   - ResNet18
   - VGG16
   - AlexNet (Baseline)
   - Custom CNNs (No Dropout, With Dropout, With Attention)

---

## 🗂 Dataset

- Total Classes: 8
  - Amoeba
  - Rod-shaped bacteria
  - Spherical bacteria
  - Spiral bacteria
  - Yeast
  - Microalgae
  - Rotifer
  - Nematode
- Input Resolution: 224×224 pixels
- All images are preprocessed and balanced.

### 🔧 Preprocessing Techniques:
- Class Merging & Folder Structuring
- Gaussian Noise Addition
- Data Augmentation (Flip, Zoom, Rotate)
- Class Balancing

### 📝 Annotation:
- Roboflow was used to annotate bounding boxes for YOLOv11 training.
- Exported in YOLO format and resized automatically.

---

## ⚙️ Pipeline Workflow

1. Preprocess dataset (augmentation, noise, balancing)  
2. Annotate and train YOLOv11 for detection  
3. Crop detected regions  
4. Train CNN models for classification using cropped images  
5. Evaluate models using accuracy and F1 scores  

---

## 🔍 Object Detection – YOLOv11

| Metric         | Value |
|----------------|-------|
| mAP@0.5        | 0.881 |
| mAP@0.5:0.95   | 0.721 |
| Precision      | 0.893 |
| Recall         | 0.83  |

→ Output: Cropped microorganisms used for downstream classification

---

## 🧠 Classification Models & Performance

| Model                | Accuracy | Macro F1 | Weighted F1 | Remarks                                |
|----------------------|----------|----------|-------------|----------------------------------------|
| ResNet18             | 86%      | 0.82     | 0.86        | Best performer, high generalization    |
| Custom CNN (No Drop) | 86%      | 0.82     | 0.85        | Comparable to ResNet, simpler design   |
| VGG16                | 77%      | 0.74     | 0.76        | Good baseline, simple structure        |
| Custom CNN (Dropout) | 75%      | 0.71     | 0.76        | Slight performance drop due to dropout |
| Custom CNN (Attention)| 67%     | 0.60     | 0.67        | Attention didn’t improve performance   |
| AlexNet              | 28%      | —        | —           | Underperformed, used for comparison    |

---

## 📈 Key Insights

- YOLOv11 provides high-quality detection across diverse microbes.  
- ResNet18 and Custom CNN (No Dropout) offer the best classification performance.  
- Regularization and attention need tuning to show gains.  
- Data augmentation and class balancing significantly improved performance.

---


