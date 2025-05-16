# Fined-Tuned-OCR-Model
# Handwritten Text Recognition Using TrOCR

This repository implements a solution for handwritten text recognition (HTR) using the transformer-based **TrOCR (Transformer OCR)** model. It leverages robust preprocessing techniques, diverse datasets, and fine-tuned strategies to deliver accurate recognition of handwritten text.

---

## Table of Contents

- [Overview](#overview)
- [Datasets](#datasets)
- [Model](#model)
- [Preprocessing](#preprocessing)
- [Fine-Tuning Strategy](#fine-tuning-strategy)
- [Challenges and Improvements](#challenges-and-improvements)
- [Results](#results)
- [Future Enhancements](#future-enhancements)
- [How to Use](#how-to-use)
- [License](#license)

---

## Overview

This project focuses on utilizing **TrOCR (microsoft/trocr-base-handwritten)**, a transformer-based OCR model, to convert handwritten text images into readable strings. The key features include:

- Integration of diverse datasets for training and evaluation.
- Use of preprocessing techniques to enhance text visibility.
- Fine-tuned parameters for optimal model performance.

---

## Datasets

1. **IAM Handwriting Dataset**
   - **Source:** Hugging Face
   - **Features:** Large set of handwritten text lines with corresponding transcriptions.

2. **Imgur5K Dataset**
   - **Source:** Hugging Face
   - **Features:** Additional handwritten text images to enhance variability and generalizability.

---

## Model

- **TrOCR (microsoft/trocr-base-handwritten):**
  - A sequence-to-sequence transformer model designed for OCR tasks.
  - Combines a Vision Transformer (ViT) encoder for image feature extraction and a Transformer decoder for text generation.

---

## Preprocessing

### Image Processing
- **Grayscale Conversion:** Simplifies images to reduce complexity.
- **Noise Reduction:** Fast non-local means denoising and median blurring.
- **Adaptive Thresholding:** Enhances text contrast against the background.
- **Perspective Augmentation:** Simulates handwriting variations.
- **Resizing:** Standardized to 224x224 pixels for model compatibility.

### Text Processing
- **Tokenization:** Converts text labels into token IDs with padding and length standardization using the TrOCR processor.

---

## Fine-Tuning Strategy

1. **Training Configuration**:
   - **Batch Size:** Adapted based on GPU availability.
   - **Learning Rate:** 5e-5 with a warmup ratio of 0.1.
   - **Mixed-Precision Training:** Optimizes memory and speeds up training.
   - **Gradient Checkpointing:** Manages memory usage for large datasets.
   - **Early Stopping:** Uses CER with a patience of 3 epochs to avoid overfitting.

2. **Evaluation**:
   - Metrics: **Character Error Rate (CER)** and **Word Error Rate (WER)**.
   - Regular evaluations performed at each epoch.

---

## Challenges and Improvements

### Challenges
- Variability in handwriting styles and image quality.
- GPU memory limitations with large batch sizes.

### Potential Improvements
1. **Enhanced Data Augmentation:**
   - Introduce elastic distortions or synthetic noise.
2. **Model Exploration:**
   - Use `trocr-large-handwritten` for improved accuracy.
3. **Post-Processing:**
   - Add a spell-checking layer or language model to refine predictions.

---

## Results

- The model achieved competitive results in terms of CER and WER on diverse handwritten datasets.

---

## Future Enhancements

1. Implement additional preprocessing techniques to handle complex handwriting styles.
2. Use advanced models like `trocr-large-handwritten` for increased recognition accuracy.
3. Explore ensemble methods or integrate domain-specific language models.

---

## How to Use

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/your-repo-name.git
