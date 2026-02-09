# 🧠 Brain Tumor Segmentation using U-Net (MRI Images)

This project implements a **Deep Learning–based brain tumor segmentation system** using MRI scans.  
The model automatically detects and segments tumor regions from brain MRI images using a **U-Net convolutional neural network**.

---

## 📌 Project Overview

Manual tumor segmentation in MRI scans is time-consuming and requires expert radiologists.  
This project demonstrates how **deep learning can assist medical image analysis** by performing **pixel-level tumor segmentation**.

The model takes an **MRI brain scan** as input and outputs a **binary mask** highlighting tumor regions.

---

## 🗂 Dataset Used

**Dataset:** MRI-Based Glioma Detection Dataset with Masks  

Each sample contains:

- `.tif` → Brain MRI scan  
- `_mask.tif` → Corresponding tumor segmentation mask  

The dataset provides paired **images and ground-truth masks** for supervised learning.

---

## 🧠 Model Architecture

We implemented a **U-Net architecture**, widely used for biomedical image segmentation.

### 🔹 Key Features
- Encoder–Decoder CNN structure  
- Skip connections for precise localization  
- Input size: **128 × 128 × 3**  
- Output: **128 × 128 × 1** binary segmentation mask  

---

## ⚙️ Training Details

| Parameter | Value |
|----------|-------|
| Optimizer | Adam |
| Learning Rate | 1e-4 |
| Loss Function | Binary Crossentropy + Dice Loss |
| Metric | Dice Coefficient |
| Batch Size | 4 |
| Image Size | 128×128 |
| Early Stopping | Enabled |
| Model Checkpoint | Saves best model based on validation Dice |

---

## 📊 Performance

| Metric | Score |
|--------|-------|
| **Best Validation Dice Coefficient** | **~0.59** |

The model detects tumor regions reasonably well but struggles with fine boundary precision — common in medical segmentation tasks without large datasets or heavy preprocessing.

---

## 🖼 Example Predictions

| MRI Image | True Mask | Predicted Mask |
|----------|-----------|----------------|
| Brain Scan | Ground Truth Tumor | Model Segmentation |

➡️ See the notebook outputs for full visual results.

---

## 🚀 How to Run

### 1️⃣ Install Dependencies

```bash
pip install tensorflow numpy matplotlib opencv-python
