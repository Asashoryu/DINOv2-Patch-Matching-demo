# Sparse Feature Matching with DINOv2 Backbone

This project implements and compares sparse feature matching techniques using a self-supervised transformer-based backbone (DINOv2) and traditional methods like SIFT. It includes semantic segmentation, patch-wise feature extraction, PCA-based foreground/background separation, and feature matching via the Hungarian Algorithm.

## 🧠 Overview

The goal is to evaluate the semantic consistency and robustness of feature embeddings across different viewpoints of the same object. This is achieved by:

- Extracting patch-level features with DINOv2.
- Separating foreground from background using local PCA.
- Projecting embeddings into a shared space using joint PCA.
- Matching features using Euclidean distance and optimal assignment.

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
