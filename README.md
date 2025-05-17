# Sparse Feature Matching with DINOv2 Backbone

This project aims to solve a Patch Matching task between two images using a self-supervised transformer-based backbone (DINOv2) and to compare the results with a traditional method like SIFT (Scale-Invariant Feature Transform). This work is inspired by the paper "DINOv2: Learning Robust Visual Features without Supervision". 

## 🧠 Overview

The goal is to evaluate the semantic consistency and robustness of feature embeddings across different viewpoints of the same object. This is achieved by:

- Extracting patch-level features with DINOv2.
![Image 1](https://github.com/user-attachments/assets/039f886b-1e76-4a07-a5e4-9b6dc50b61f6)
- Separating foreground from background using local PCA.
![Image 2](https://github.com/user-attachments/assets/eab82e32-2a96-41a8-9e88-268e9e9caab5)
- Projecting embeddings into a shared space using joint PCA.
![Image 3](https://github.com/user-attachments/assets/8aaccc3b-e52b-410e-a995-d6da33662e7a)
- Matching features using Euclidean distance and optimal assignment.
![Image 4](https://github.com/user-attachments/assets/4314a581-a5b7-4cba-b5e5-c4178fefec98)
- Comparing the results with SIFT
![Image 5](https://github.com/user-attachments/assets/d837ee54-9ead-4844-98ab-44999ee018c7)

## 📁 Dataset

The main dataset used is **SPair-71k**, designed for semantic correspondence under pose, scale, and appearance variation. It provides annotated image pairs for various object categories (e.g., cats, aeroplanes).

## ⚙️ Configuration

Backbones supported:
- `vits14`, `vitb14`, `vitl14`, `vitg14`
- With/without register variants (`*_reg`)

Example configuration:
```python
dataset_path = "/content/SPair-71k/SPair-71k/JPEGImages/cat"
BACKBONE_SIZE = "base_reg"
img_size = 896
patch_size = 14
