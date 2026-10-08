# 🐱🐶 CNN Cats vs Dogs Image Classification

A Deep Learning project that uses a **Convolutional Neural Network (CNN)** built with **PyTorch** to classify images into two categories: **Cat** and **Dog**.

The project demonstrates a complete image-classification workflow, including dataset preparation, preprocessing, augmentation, CNN architecture design, model training, validation, best-model selection, and final evaluation using accuracy, precision, recall, and a confusion matrix.

---

## 📌 Project Overview

Image classification is one of the fundamental applications of Computer Vision.

In this project, a CNN was trained to automatically identify whether an input image contains a **Cat** or a **Dog**.

The complete machine learning workflow was implemented:

**Dataset → Data Splitting → Preprocessing → Augmentation → DataLoader → CNN → Training → Validation → Best Model Selection → Testing → Evaluation**

---

## 📊 Dataset

The complete dataset contains **25,103 images**.

### Class Distribution

| Class | Images |
|---|---:|
| 🐱 Cat | 12,588 |
| 🐶 Dog | 12,515 |
| **Total** | **25,103** |

### Dataset Split

| Split | Images | Percentage | Purpose |
|---|---:|---:|---|
| Training | **20,082** | 80% | Used to train the CNN |
| Validation | **2,510** | 10% | Used to monitor performance and select the best model |
| Test | **2,511** | 10% | Used for final unbiased evaluation |
| **Total** | **25,103** | **100%** | |

The dataset was divided into training, validation, and test sets so that model performance could be evaluated on images that were not used for learning the model parameters.

---

# 🔄 Complete Project Pipeline

```text
                    DATASET
                       │
                       ▼
              Load Images using
                 ImageFolder
                       │
                       ▼
           Train / Validation / Test
                    Split
             80% / 10% / 10%
                       │
                       ▼
             IMAGE PREPROCESSING
                       │
             ┌─────────┴─────────┐
             │                   │
             ▼                   ▼
        Resize 128×128       ToTensor
             │                   │
             └─────────┬─────────┘
                       ▼
                  Normalize
                       │
                       ▼
             DATA AUGMENTATION
              (Training Only)
                       │
             ┌─────────┴─────────┐
             ▼                   ▼
     Random Horizontal       Random Rotation
          Flip                   ±10°
             │                   │
             └─────────┬─────────┘
                       ▼
                  DataLoaders
                 Batch Size = 32
                       │
                       ▼
                  CNN MODEL
                       │
             ┌─────────┴─────────┐
             ▼                   ▼
          Feature            Classification
         Extraction              Layers
             │                   │
             └─────────┬─────────┘
                       ▼
                CrossEntropyLoss
                       │
                       ▼
                   Adam Optimizer
                  Learning Rate=0.001
                       │
                       ▼
                TRAIN FOR 10 EPOCHS
                       │
                       ▼
             VALIDATION AFTER EACH
                    EPOCH
                       │
                       ▼
              BEST MODEL SELECTION
          Highest Validation Accuracy
                       │
                       ▼
               LOAD BEST MODEL
             Epoch 2 - 83.71% Val Acc.
                       │
                       ▼
              FINAL TEST EVALUATION
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
       Accuracy     Precision     Recall
       83.27%        81.65%       86.40%
                       │
                       ▼
              CONFUSION MATRIX
