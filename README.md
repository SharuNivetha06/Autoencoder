# Autoencoders and Variants on MNIST

An end-to-end deep learning project exploring Autoencoders and their variants for image reconstruction, denoising, latent representation learning, and generative modeling using the MNIST handwritten digit dataset.

## Overview

This project implements and compares:

* Fully Connected Autoencoder (FC-AE)
* Convolutional Autoencoder (CAE)
* Denoising Convolutional Autoencoder
* Variational Autoencoder (VAE)

The study investigates reconstruction quality, latent space representations, denoising capability, and image generation using a consistent experimental setup on MNIST.

## Dataset

**MNIST Handwritten Digit Dataset**

* 28 × 28 grayscale digit images
* 10 classes (0–9)
* Normalized to the range [0,1]

## Models Implemented

### 1. Fully Connected Autoencoder

Architecture:

```text
784
 ↓
Dense(128)
 ↓
Dense(32)
 ↓
Latent(16)
 ↓
Dense(32)
 ↓
Dense(128)
 ↓
784
```

Features:

* Dense encoder-decoder architecture
* Binary Cross Entropy loss
* Adam optimizer

---

### 2. Convolutional Autoencoder

Architecture:

```text
Input (28×28×1)
 ↓
Conv2D(32)
 ↓
MaxPooling
 ↓
Conv2D(64)
 ↓
MaxPooling
 ↓
Latent Feature Map
 ↓
UpSampling
 ↓
Conv2D(32)
 ↓
UpSampling
 ↓
Conv2D(1)
```

Features:

* Preserves spatial information
* Better reconstruction quality
* Fewer parameters than FC-AE

---

### 3. Denoising Autoencoder

Noise Types:

* Gaussian Noise
* Salt-and-Pepper Noise

Objective:

```text
Noisy Image → Encoder → Decoder → Clean Image
```

Features:

* Learns noise removal
* Robust reconstruction under corruption
* Evaluated across multiple noise levels

---

### 4. Variational Autoencoder (VAE)

Features:

* Probabilistic latent representation
* Reparameterization trick
* KL Divergence regularization
* Latent space visualization
* Novel digit generation

Loss:

```text
Total Loss = Reconstruction Loss + KL Divergence
```

## Evaluation Metrics

The following metrics are used:

* Mean Squared Error (MSE)
* Mean Absolute Error (MAE)
* Structural Similarity Index (SSIM)

## Experiments Performed

### Reconstruction Analysis

* Original vs Reconstructed images
* Training and validation loss curves
* Reconstruction error distribution

### Latent Space Analysis

* Latent dimension study
* 2D VAE latent space visualization
* Latent space interpolation

### Denoising Analysis

* Clean vs Noisy vs Denoised images
* Noise level vs reconstruction quality
* Gaussian noise experiments
* Salt-and-pepper noise experiments

### Generative Analysis

* Random image generation
* Latent space sampling
* Interpolation between digits

## Results Summary

| Model                     | MSE     | MAE     | SSIM    |
| ------------------------- | ------- | ------- | ------- |
| FC Autoencoder            | 0.02046 | 0.05512 | 0.75860 |
| Convolutional Autoencoder | 0.00264 | 0.01511 | 0.97387 |
| Denoising CAE             | 0.00436 | 0.02051 | 0.94768 |
| Variational Autoencoder   | 0.04315 | 0.10086 | 0.49856 |

## Key Findings

* Increasing latent dimension improves reconstruction quality.
* Convolutional Autoencoders outperform Fully Connected Autoencoders by preserving spatial locality.
* Denoising Autoencoders successfully recover digit structure even under significant corruption.
* VAEs learn smooth latent representations that support interpolation and image generation.
* Reconstruction quality improves rapidly at small latent dimensions and saturates beyond a certain point.

## Sample Outputs

* Original vs Reconstructed Digits
* FC-AE vs CAE Comparison
* Denoised Reconstructions
* VAE Latent Space Visualization
* Generated Digits
* Latent Space Interpolation

## Technologies Used

* Python
* TensorFlow / Keras
* NumPy
* Matplotlib
* scikit-image
* scikit-learn
