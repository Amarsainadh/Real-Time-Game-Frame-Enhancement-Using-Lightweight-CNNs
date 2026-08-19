# Real-Time Game Frame Enhancement Using Lightweight CNN

A lightweight Convolutional Neural Network (CNN) for enhancing game frames by reducing blur, noise, and compression artifacts while maintaining low-latency inference.

## Overview

Game frames can suffer from blur, noise, compression artifacts, and quality degradation during rendering or processing. This project develops a lightweight CNN-based enhancement pipeline that learns to reconstruct cleaner game frames from synthetically degraded inputs.

The project also compares CNN-based enhancement with traditional image processing techniques using PSNR and SSIM metrics.

## Features

- Lightweight CNN architecture using depthwise separable convolutions
- Residual learning for efficient image reconstruction
- Synthetic degradation using blur, noise, downsampling, and JPEG compression
- Traditional enhancement using bilateral filtering, CLAHE, and controlled sharpening
- PSNR and SSIM based quality evaluation
- Low-latency inference measurement
- Direct support for JPG, JPEG, PNG, PDF, and DOCX image inputs
- Enhanced output image generation

## Methodology

The project follows the pipeline:

Input Image  
↓  
Synthetic Degradation  
↓  
Lightweight CNN  
↓  
Enhanced Game Frame

A traditional image processing pipeline is also used for comparison:

Input  
↓  
Bilateral Filtering  
↓  
CLAHE  
↓  
Controlled Sharpening  
↓  
Traditional Enhanced Output

## CNN Architecture

The model uses a lightweight architecture consisting of:

- Initial convolution layer
- Depthwise separable convolution blocks
- ReLU activation
- Residual reconstruction
- Output clipping to the valid image range

The model contains only **1,683 parameters**, keeping the network computationally lightweight.

## Training

Instead of requiring a manually prepared paired dataset, the project generates synthetic degraded versions of the uploaded image.

The degradation process includes:

- Downsampling and upsampling
- Gaussian blur
- Gaussian noise
- JPEG compression artifacts

The original image is used as the reconstruction target.

The model is trained using a combined loss consisting of:

- Mean Squared Error (MSE)
- Structural Similarity (SSIM)

## Traditional Image Processing

The traditional enhancement pipeline uses:

- Bilateral filtering for edge-preserving denoising
- CLAHE for local contrast enhancement
- Controlled unsharp masking for detail enhancement

The CNN output is evaluated against this traditional pipeline using PSNR and SSIM.

## Performance

Sample evaluation on the tested input:

| Metric | Result |
|---|---:|
| Model Parameters | **1,683** |
| Inference Time | **26.24 ms/frame** |
| Training Time | **97.22 sec** |
| CNN PSNR | **31.12 dB** |
| CNN SSIM | **0.9871** |
| PSNR Improvement | **+13.32 dB** |
| SSIM Improvement | **+0.1534** |

### Quality Comparison

| Method | PSNR | SSIM |
|---|---:|---:|
| Degraded Input vs Original | 17.80 dB | 0.8337 |
| Traditional vs Original | 16.87 dB | 0.8401 |
| CNN Enhanced vs Original | **31.12 dB** | **0.9871** |
| CNN Enhanced vs Traditional | 17.11 dB | 0.8368 |

The results show a substantial improvement in reconstruction quality from the degraded input to the CNN-enhanced output.

> Performance metrics are based on a sample evaluation using synthetically degraded input. Inference time depends on the hardware and runtime environment.

## Project Results

The CNN successfully reconstructs a visually cleaner frame from degraded input while maintaining a small model size.

The project demonstrates that a compact CNN can achieve strong image-quality improvements without relying on a large deep-learning architecture.

## Technologies Used

- Python
- TensorFlow / Keras
- OpenCV
- NumPy
- Matplotlib
- Google Colab

## Project Structure

```text
Real-Time-Game-Frame-Enhancement/
│
├── README.md
├── game_frame_enhancement.ipynb
├── game_frame_enhancement.py
├── requirements.txt
└── enhanced_output.png
