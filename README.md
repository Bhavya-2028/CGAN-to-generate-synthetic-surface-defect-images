# CGAN to Generate Synthetic Surface Defect Images

## Project Overview
This project implements a **Conditional Generative Adversarial Network (cGAN)** to generate synthetic surface defect images across multiple defect categories. The generated images help improve datasets used in industrial inspection systems and enhance the performance of machine learning models for defect detection.

The system follows a deep learning pipeline consisting of data preparation, generator and discriminator networks, evaluation, and monitoring modules.

---

# System Specifications

| Parameter | Value |
|----------|------|
| Image Size | 128 × 128 |
| Channels | 3 (RGB) |
| Latent Dimension | 100 |
| Number of Classes | 7 |
| Batch Size | 64 |
| Epochs | 50 |

---

# Module 1: Data Pipeline

The **Data Pipeline** module manages the overall flow of data through the system. It loads the dataset, organizes the images into appropriate class folders, and prepares the images for preprocessing and training.

Key functions of the data pipeline include:

- Loading defect image datasets
- Organizing images based on defect categories
- Splitting the dataset into training and validation sets
- Preparing batches of images for model training

This pipeline ensures smooth and efficient data handling during the training process.

---

# Module 2: Data Preprocessing

The **Data Preprocessing** module prepares images before they are fed into the neural network.

Library Used:
- ImageDataGenerator (TensorFlow/Keras)

Preprocessing steps include:

- Image rescaling using factor **1/127.5**
- Normalizing pixel values to the range **[-1, 1]**
- Resizing images to **128 × 128**
- Directory-based class loading
- Data splitting for training and validation

These preprocessing steps standardize the dataset and improve the stability of GAN training.

---

# Module 3: Generator Network

The **Generator** network is responsible for generating synthetic defect images.

Inputs:
- Random noise vector of **100 dimensions**
- Class label representing the defect category

The generator uses conditional information to produce images corresponding to specific defect classes.

Key layers used:

- Embedding layer for class conditioning
- Dense layers
- Reshape layer
- Conv2DTranspose layers for image upsampling
- Batch Normalization
- LeakyReLU activation
- Output activation function **tanh**

Output:

```
128 × 128 × 3 synthetic defect image
```

The generator learns to produce realistic images that resemble real industrial surface defects.

---

# Module 4: Discriminator Network

The **Discriminator** network acts as a classifier that distinguishes between real images and generated images.

Input:

```
128 × 128 × 3 image
```

Layers used:

- Convolutional layers (64 to 512 filters)
- Stride-2 downsampling
- LeakyReLU activation
- Dropout layers
- Flatten layer
- Dense output layer

Output:

```
Real / Fake classification score
```

The discriminator continuously improves its ability to detect fake images, forcing the generator to produce more realistic outputs.

---

# Module 5: Evaluation Module

The **Evaluation Module** measures the quality and performance of generated images.

### Qualitative Evaluation

- Visual inspection of generated images
- Image sharpness analysis
- Detection of mode collapse
- Diversity of defect classes

### Quantitative Evaluation

- Fréchet Inception Distance (FID)
- Inception Score
- Classification accuracy on generated images

These metrics help determine how realistic and useful the synthetic images are.

---

# Module 6: Continuous Evaluation and Monitoring

The **Continuous Evaluation Module** monitors the training progress of the GAN model throughout the training process.

Monitoring techniques include:

- Saving generated images after each epoch
- Using fixed latent vectors for visual comparison
- Generating image grids for all defect classes
- Tracking generator and discriminator losses

This module helps observe improvements in image quality and detect training issues such as mode collapse.

---

# Hardware and Software Requirements

## Software
- Python 3.9+
- TensorFlow / Keras
- NumPy
- Matplotlib
- Seaborn
- Streamlit
- Scikit-learn

## Hardware
- GPU recommended (CUDA supported)
- Minimum 8GB RAM
- Minimum 10GB storage

---

# Applications

- Industrial surface defect inspection
- Data augmentation for imbalanced datasets
- Smart manufacturing systems
- AI-assisted quality control
- Research in generative deep learning models
