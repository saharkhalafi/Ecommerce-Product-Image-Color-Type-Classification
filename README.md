# Ecommerce Product Image: Color & Type Classification

This project provides a **multi-label image classification model** to predict **product color and type** for ecommerce datasets. It uses **EfficientNet-B0** with transfer learning and fine-tuning to achieve high accuracy.

## Labels Information

### Color Labels (14 classes)
The model predicts the following color classes:

مشکی, سفید, سبز, سرمه ای, طوسی, کرم, آبی, قرمز, قهوه ای, صورتی, زرد, بنفش, نارنجی, چند رنگ

### Type Labels (11 classes)
The model predicts the following product types:

پیراهن, تی شرت, شلوار, لباس زیر, کفش, کیف, لباس راحتی و خواب, ژاکت و سویشرت, مانتو, پوشاک ست

The dataset has been augmented to **increase samples for underrepresented labels**, improving model performance and class balance.

## Pre-trained Model

We provide a **pre-trained fine-tuned model** (`.pth`) that you can use **directly for product image classification** in ecommerce:  
- Predicts **both color and type** of clothing items.
- No need to train from scratch — simply load the `.pth` file and run predictions.

## **Project Steps**

### 1. Data Preparation & Augmentation
- Original dataset contained product images with labels: `color` and `type`.
- Extracted image filenames and merged with dataset.
- Performed **data augmentation** on underrepresented labels:
  - Rotation, flipping , zoom, etc.
  - Augmentation increased sample size for rare classes.
- Combined augmented images with original dataset.

### 2. Model Training
- Used **EfficientNet-B0** as backbone for feature extraction.
- Two separate heads:
  - Color classification
  - Type classification
- Trained with **transfer learning**, freezing most layers initially.
- Early stopping applied to prevent overfitting.
- in F1-scores:
  - Color F1: 0.87
  - Type F1: 0.90

### 3. Fine-Tuning
- Unfroze last few EfficientNet blocks and batchnorm layers.
- Trained for a few more epochs with **lower learning rate**.
- Achieved **significant improvement** in F1-scores:
  - Color F1: 0.96
  - Type F1: 0.99



