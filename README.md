#  Cats vs Dogs Image Classifier using MobileNetV2

##  Project Overview

This project is an image classification system that identifies whether an uploaded image contains a **Cat** or a **Dog**. Initially, a Convolutional Neural Network (CNN) was built from scratch. However, the model suffered from overfitting and achieved lower validation performance. To improve accuracy and generalization, **Transfer Learning** using **MobileNetV2** was implemented.

The final model achieved **95.88% validation accuracy** and successfully classified unseen images with high confidence.

---

##  Objectives

* Build a deep learning model to classify cats and dogs.
* Understand CNN architecture and image preprocessing.
* Compare a custom CNN with a pretrained MobileNetV2 model.
* Improve performance using Transfer Learning.
* Evaluate model performance on unseen images.

---

##  Dataset

**Dataset:** Microsoft Cats and Dogs Dataset

Dataset Structure:

```text
PetImages/
│
├── Cat/
│   ├── cat.0.jpg
│   ├── cat.1.jpg
│   └── ...
│
└── Dog/
    ├── dog.0.jpg
    ├── dog.1.jpg
    └── ...
```

Total Images: ~25,000

Classes:

* Cat
* Dog

---

## 🛠 Technologies Used

* Python
* TensorFlow
* Keras
* MobileNetV2
* NumPy
* Matplotlib
* PIL
* Google Colab

---

# 🔹 Version 1: Custom CNN Model

## CNN Architecture

Input Image (150×150×3)
↓
Conv2D (32 Filters)
↓
MaxPooling2D
↓
Conv2D (64 Filters)
↓
MaxPooling2D
↓
Flatten
↓
Dense (128)
↓
Output Layer (Sigmoid)

---

## CNN Results

| Metric              | Value       |
| ------------------- | ----------- |
| Training Accuracy   | 99%         |
| Validation Accuracy | 77%         |
| Status              | Overfitting |

### Observation

Although the training accuracy reached 99%, the validation accuracy remained around 77%.

This indicates **Overfitting**, meaning the model memorized the training data and performed poorly on unseen images.

---

# 🔹 Version 2: MobileNetV2 Transfer Learning

## Why MobileNetV2?

MobileNetV2 is a pretrained Convolutional Neural Network trained on the **ImageNet dataset** containing millions of images.

Instead of learning from scratch, the model reuses previously learned image features such as:

* Edges
* Shapes
* Textures
* Patterns
* Object Features

This significantly improves performance and reduces overfitting.

---

## MobileNetV2 Architecture

Input Image (150×150×3)
↓
MobileNetV2 (Pretrained on ImageNet)
↓
GlobalAveragePooling2D
↓
Dense (128, ReLU)
↓
Dense (1, Sigmoid)
↓
Prediction (Cat / Dog)

---

## Training Configuration

* Image Size: 150 × 150
* Batch Size: 32
* Optimizer: Adam
* Loss Function: Binary Crossentropy
* Epochs: 10
* Early Stopping: Enabled
* Data Augmentation: Enabled

### Data Augmentation

* Rotation
* Zoom
* Shear
* Horizontal Flip

Purpose:

* Reduce overfitting
* Improve generalization
* Increase robustness

---

#  Final MobileNetV2 Results

| Metric              | Value                    |
| ------------------- | ------------------------ |
| Training Accuracy   | 96.60%                   |
| Validation Accuracy | 95.88%                   |
| Validation Loss     | 0.1006                   |
| Status              | Excellent Generalization |

---

#  CNN vs MobileNetV2 Comparison

| Feature                   | Custom CNN         | MobileNetV2       |
| ------------------------- | ------------------ | ----------------- |
| Approach                  | Built from Scratch | Transfer Learning |
| Training Accuracy         | 99%                | 96.60%            |
| Validation Accuracy       | 77%                | 95.88%            |
| Overfitting               | High               | Very Low          |
| Generalization            | Poor               | Excellent         |
| Performance on New Images | Moderate           | Excellent         |
| Industry Usage            | Educational        | Production Ready  |

---

#  Testing Results

## Test 1: Cat Image

Prediction:

```text
CAT
Confidence: 100%
```

Raw Prediction:

```text
0.0000169
```

Result:

✅ Correct Prediction

---

## Test 2: Cow Image

Prediction:

```text
DOG
Confidence: 99.97%
```

Result:

 Incorrect Prediction

Reason:

The model was trained only on Cat and Dog images.

Since it performs binary classification, it always predicts either Cat or Dog.

This demonstrates a limitation of binary classification models.

---

# ⚠ Limitation

The model cannot identify animals outside the training classes.

Examples:

* Cow
* Horse
* Elephant
* Bird

These images will still be classified as either Cat or Dog.

---



#  Conclusion

This project demonstrates the effectiveness of Transfer Learning for image classification.

A custom CNN initially achieved high training accuracy but suffered from overfitting. By switching to MobileNetV2, validation accuracy improved from 77% to 95.88%, resulting in significantly better performance on unseen images.

The final model successfully classifies Cat and Dog images with high confidence and serves as a strong example of practical deep learning and computer vision using TensorFlow and Keras.
