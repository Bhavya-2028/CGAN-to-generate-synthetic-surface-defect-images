# Uses of Project Modules
### I. 📦 Data Pipeline & Preprocessing

**Dataset Source:**

- **Surface Defect Image Dataset** collected for industrial inspection and defect analysis.
- The dataset contains various types of surface defects commonly found in manufactured materials.
- **6 Defect Classes:**
  1. **Crack** – Thin fractures appearing on the surface.
  2. **Inclusion** – Foreign particles embedded in the material.
  3. **Patch** – Irregular surface marks or patches.
  4. **Pitting** – Small cavities or pits formed on the surface.
  5. **Scale Defect** – Layered surface irregularities caused during manufacturing.
  6. **Scratch** – Linear surface scratches caused by friction or mechanical contact.

**Dataset Characteristics:**

- **Image Format:** Grayscale images converted to RGB for deep learning models
- **Image Resolution:** Resized to **128 × 128 pixels** for model training
- **Total Images:** Approximately **1500–2000 defect images**
- **Label Type:** Each image is associated with a defect class label

**Purpose of Dataset:**

The dataset is used to train the Conditional GAN model to learn defect patterns and generate realistic synthetic defect images that can be used for improving defect detection systems.
*Processed Dataset Structure*

text
data/processed/
├── images.npy     # Shape: (N, 128, 128, 3)
├── labels.npy     # Shape: (N,)
└── class_map.json # Mapping of class index to defect name

**Preprocessing Steps:**

1. Load raw defect images from the dataset.
2. Convert grayscale images to RGB format.
3. Resize all images to **128 × 128**.
4. Normalize pixel values to the range **[-1, 1]**.
5. Store processed images and labels for efficient training.

## 2. GAN Architecture Module
The GAN Architecture module defines the structure of the Conditional Generative Adversarial Network used in the project. It consists of two main components: the Generator and the Discriminator. The Generator creates synthetic defect images, while the Discriminator evaluates whether the generated images are real or fake. Through adversarial training, the Generator learns to produce more realistic images over time.
Uses:
- Defines Generator and Discriminator networks
- Generates synthetic defect images
- Learns patterns from real defect images
- Improves image quality through adversarial learning
- Produces class-specific defect images

---

## 3. Training Module

The Training module controls the learning process of the GAN model. During training, the Generator and Discriminator are trained simultaneously. The Generator tries to create realistic images, while the Discriminator attempts to distinguish between real and generated images. The model parameters are updated using an optimizer and loss function until the generated images become realistic.

Uses:
- Trains the Generator and Discriminator networks
- Updates model parameters using the optimizer
- Minimizes the loss function during training
- Improves the quality of generated images
- Enables the model to learn from real defect images

---

## 4. Evaluation Module

The Evaluation module measures the quality and performance of the generated images. It verifies whether the synthetic images resemble real defect images. Both qualitative and quantitative evaluation methods can be used to assess the model's performance.

Uses:
- Evaluates the quality of generated images
- Compares real and synthetic images
- Detects training issues such as mode collapse
- Measures diversity of generated defect classes
- Calculates evaluation metrics such as FID or Inception Score

---

## 5. Deployment Module

The Deployment module makes the trained model accessible to users through a user interface. In this project, a Streamlit application is used to interact with the trained generator model. Users can select defect classes and generate synthetic images in real time.

Uses:
- Deploys the trained generator model
- Provides a user-friendly interface
- Allows users to select defect categories
- Generates synthetic defect images on demand
- Demonstrates real-world application of the model

---

## 6. Continuous Evaluation Module

The Continuous Evaluation module monitors the performance of the GAN model during the training process. It helps track improvements in generated image quality and ensures that the model is learning properly throughout training.

Uses:
- Monitors generator and discriminator performance
- Saves generated images at regular intervals
- Tracks improvements across training epochs
- Detects problems such as mode collapse
- Helps analyze and improve the training process
