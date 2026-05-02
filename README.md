 
# 🧠 Transfer Learning & Fine-Tuning: Cats vs Dogs Classifier

> Harnessing the power of **pre-trained deep learning models** to classify images of cats and dogs with high accuracy and minimal training effort.

---

## 🚀 Project Overview

This project demonstrates how to leverage **Transfer Learning** using a pre-trained convolutional neural network to classify images of cats and dogs.

Instead of training a deep network from scratch, we reuse knowledge learned from a large-scale dataset and adapt it to our specific task.

 
---

## 🧩 Core Idea

A **pre-trained model** is a neural network already trained on a large dataset (like ImageNet). It has already learned useful visual patterns such as edges, textures, shapes, and structures.

We explore two powerful strategies:

### 🔹 1. Feature Extraction
- Use the convolutional base as a fixed feature extractor
- Add a new classifier on top
- Train only the new classification layers

💡 The base model acts like a *visual brain*, and we just teach it how to label cats vs dogs.

---

### 🔹 2. Fine-Tuning
- Unfreeze top layers of the base model
- Train them alongside the classifier
- Adapt high-level features to our dataset

💡 This allows the model to *specialize its visual understanding* for our problem.

---

## 🏗️ Workflow

The project follows a standard deep learning pipeline:

- 📊 Examine and understand the dataset  
- ⚙️ Build input pipeline using `ImageDataGenerator`  
- 🧱 Load pre-trained model (MobileNetV2)  
- 🧠 Stack custom classification head  
- ❄️ Freeze base model (feature extraction)  
- 🔥 Fine-tune top layers  
- 📈 Train & evaluate model  

---

## 🧬 Model Architecture

We use **MobileNetV2**, pre-trained on ImageNet (1.4M images, 1000 classes).

- Exclude top classification layer (`include_top=False`)
- Use **bottleneck layer** for feature extraction
- Add:
  - Global Average Pooling
  - Dense classifier head

---

## ⚡ Performance Optimization

### 📦 Data Pipeline
- Buffered prefetching to avoid I/O bottlenecks

### 🎨 Data Augmentation
To improve generalization and reduce overfitting:
- Random flips
- Rotations
- Transformations

### 🔄 Pixel Normalization
- Rescale images from `[0, 255] → [-1, 1]`
- Matches MobileNetV2 input requirements

---

## 🧪 Training Results

### 📊 Feature Extraction Phase
- Initial Loss: `0.64`
- Initial Accuracy: `0.65`

After training:
- Validation Accuracy: **~96%**

---

### 🔥 Fine-Tuning Phase
- Unfroze top layers of MobileNetV2
- Recompiled with lower learning rate
- Trainable variables: `56`

---

## 🧾 Final Evaluation
On unseen test data:
Test Accuracy: 98.58%
Test Loss: 0.0360


🚀 The model achieves **state-of-the-art performance for a lightweight setup**

---

## 📈 Learning Curves

Training shows:
- Rapid accuracy improvement
- Stable convergence
- Strong generalization with augmentation

---

## 🧠 Key Insights

- Pre-trained CNNs act as powerful feature extractors
- Freezing layers prevents catastrophic forgetting
- Fine-tuning unlocks dataset-specific specialization
- Transfer learning is ideal for small-to-medium datasets




