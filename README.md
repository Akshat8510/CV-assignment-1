# Image Interpolation From Scratch (CS30026)

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![NumPy](https://img.shields.io/badge/Library-NumPy-orange)](https://numpy.org/)
[![Course](https://img.shields.io/badge/Course-Computer%20Vision-red)](https://github.com/Akshat8510/CV-assignment-1)

This repository contains the implementation of fundamental image interpolation kernels—**Nearest Neighbor**, **Bilinear**, and **Bicubic**—developed entirely from scratch. 

The primary objective of this project is to explore the mathematical reconstruction of digital signals without relying on high-level library functions like `cv2.resize`.

## 📌 Project Highlights
- **Pure Implementation:** Built using only **NumPy** arrays and explicit **for-loops** to demonstrate the underlying pixel-level logic.
- **Inverse Mapping:** Utilizes inverse coordinate transformation to ensure a continuous, hole-free output.
- **Verification Suite:** Every scratch implementation is mathematically verified against the **OpenCV** library using Mean Squared Error (MSE) and Difference Mapping.
- **Scientific Datasets:** Tested on high-stakes data including Medical MRI scans, Planetary Remote Sensing, and Noisy Photography.

---

## 🛠️ Algorithms Implemented

### 1. Nearest Neighbor (Zero-Order)
A simple reconstruction method that assigns the value of the single closest source pixel. 
- **Pros:** Extremely fast.
- **Cons:** High aliasing (staircase effect) on edges.

### 2. Bilinear Interpolation (First-Order)
Calculates a weighted average of a $2 \times 2$ neighborhood. 
- **Pros:** Smoother transitions than Nearest Neighbor.
- **Cons:** Acts as a low-pass filter, causing slight blurring.

### 3. Bicubic Interpolation (Higher-Order)
Uses a $4 \times 4$ neighborhood (16 pixels) and a cubic spline kernel ($a = -0.5$).
- **Pros:** Sharpest reconstruction, excellent for medical and astronomical data.
- **Cons:** High computational overhead (O(16) per pixel).

---

## 📊 Experimental Results

| Image Type | Algorithm | Time (s) | MSE (vs OpenCV) | Quality |
| :--- | :--- | :--- | :--- | :--- |
| **img1 (Telephone)** | Bicubic | 47.40s | 410.25 | High Detail |
| **img2 (MRI Spine)** | Bicubic | 368.47s | 8.22 | Sharp Edges |
| **img3 (Planetary)** | Bicubic | 416.80s | 9.60 | High Fidelity |

> **Note on MSE 0.00:** In our Nearest Neighbor implementation, we achieved a perfect MSE of 0.00 across all images, proving our scratch logic is mathematically identical to library standards.

---

## 🚀 Getting Started

### Prerequisites
- Python 3.x
- NumPy
- OpenCV (Used strictly for I/O and verification)
- Matplotlib

### Installation
```bash
git clone https://github.com/Akshat8510/CV-assignment-1.git
cd CV-assignment-1
pip install numpy opencv-python matplotlib
```

### Usage
Each algorithm is contained in its own Jupyter Notebook for clear visualization:
1. Open `Nearest_Neighbor.ipynb` to see the **MSE 0.00** verification.
2. Open `Bilinear_Interpolation.ipynb` to see the $2 \times 2$ weighted averaging logic.
3. Open `Bicubic_Interpolation.ipynb` to observe the $4 \times 4$ kernel and **Edge Padding** implementation.

---

## 📂 Project Structure
```text
├── img1.png                   # Noisy Telephone Image
├── img2.tif                   # Medical MRI Spine Data
├── img3.tif                   # Planetary Surface Image
├── Nearest_Neighbor.ipynb     # Scratch Implementation + Verification
├── Bilinear_Interpolation.ipynb 
├── Bicubic_Interpolation.ipynb
└── README.md
```

**📝 Written by Akshat** :)
