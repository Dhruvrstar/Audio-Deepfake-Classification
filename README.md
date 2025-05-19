---

# 🔊 Audio Deepfake Classification

Detecting synthetic audio has become a critical challenge in the era of deepfakes. This project focuses on building a deep learning-based classifier to distinguish between genuine (bonafide) and manipulated (spoofed) audio recordings using the ASVspoof 2019 dataset.

---

## 📌 Table of Contents

* [Overview](#overview)
* [Dataset](#dataset)
* [Preprocessing](#preprocessing)
* [Model Architecture](#model-architecture)
* [Training](#training)
* [Evaluation](#evaluation)
* [Usage](#usage)
* [Contributors](#contributors)

---

## 🧠 Overview

This project builds a binary classifier using convolutional neural networks (CNNs) that operate on Mel spectrograms extracted from audio clips. The goal is to detect spoofed audio created using voice synthesis and voice conversion techniques.

---

## 📂 Dataset

We use the ASVspoof 2019 dataset provided by the [ASVspoof Challenge](https://www.asvspoof.org/). It includes bonafide and spoofed recordings across multiple attack types.

👉 Download the dataset and place it under the path:

```
/dataset/
```

More details about the dataset structure and protocols can be found in the official [ASVspoof 2019 documentation](https://www.asvspoof.org/index2019.html).

---

## ⚙️ Preprocessing

Audio files are converted to Mel spectrograms with the following preprocessing steps:

* Resampling to a consistent sample rate
* Framing and windowing
* Extraction of 128 Mel-frequency cepstral coefficients
* Spectrogram resizing to 128×109 (height × width)
* Normalization
* Optional data augmentation (time masking, noise injection)

---

## 🏗️ Model Architecture

We use a lightweight but effective CNN model:

```
Input: 128×109×1
 └── Conv2D(32, 3×3) → ReLU
      └── MaxPooling2D(2×2)
           └── Conv2D(64, 3×3) → ReLU
                └── MaxPooling2D(2×2)
                     └── Flatten
                          └── Dense(128) → ReLU
                               └── Dropout(0.5)
                                    └── Dense(2) → Softmax
```

🛠️ Additional Techniques:

* Batch Normalization
* Global Average Pooling (optional variant)
* Early Stopping & Learning Rate Scheduler

---

## 🏋️ Training

* **Loss Function:** Categorical Cross-Entropy
* **Optimizer:** Adam
* **Metrics Tracked:** Accuracy, Precision, Recall, F1-Score
* **Batch Size:** 32
* **Epochs:** 30–50 (with early stopping)

Training can be performed using GPU for faster convergence. Model checkpoints and logs are stored for performance tracking.

---

## 📊 Evaluation

Model is evaluated using:

* ✅ Accuracy
* 🧠 Precision, Recall, F1-Score
* 📉 ROC-AUC Curve
* 🔁 Confusion Matrix
* 🔐 Equal Error Rate (EER)

Visualization tools (e.g., TensorBoard or matplotlib) are used to plot training and validation metrics over epochs.


---

## 👨‍💻 Contributors

* Dhruv Sanmotra – 102206172
* Kashish – 102206027
* Ishaan Bahl – 102206052

---

## 📄 License

This project is licensed under the MIT License. 

---
