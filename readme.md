🧠 Brain Tumor Segmentation using U-Net (MRI Images)

This project implements a Deep Learning–based brain tumor segmentation model using MRI scans.
The model is trained to automatically detect and segment tumor regions from brain MRI images.

📌 Project Overview

Manual tumor segmentation in MRI scans is time-consuming and requires medical expertise.
This project uses a U-Net convolutional neural network to perform pixel-level segmentation of brain tumors.

The model takes an MRI image as input and outputs a binary mask highlighting the tumor region.

🗂 Dataset Used

Dataset: MRI-Based Glioma Detection Dataset with Masks
Contains:

Brain MRI images

Corresponding tumor masks

Each sample includes:

.tif MRI scan

_mask.tif binary segmentation mask

🧠 Model Architecture

We implemented a U-Net architecture, which is widely used for biomedical image segmentation.

Key Features:

Encoder–Decoder CNN structure

Skip connections for precise localization

Input size: 128 × 128 × 3

Output: 128 × 128 × 1 segmentation mask

⚙️ Training Details
Parameter	Value
Optimizer	Adam
Learning Rate	1e-4
Loss Function	BCE + Dice Loss
Metric	Dice Coefficient
Batch Size	4
Image Size	128×128
Early Stopping	Enabled
Model Checkpoint	Saves best model based on validation Dice
📊 Performance
Metric	Score
Best Validation Dice Coefficient	~0.59

The model successfully detects tumor regions but still struggles with fine boundary precision — which is common in medical image segmentation without heavy preprocessing or large compute resources.

🖼 Example Predictions

The model outputs a binary mask showing predicted tumor areas.

MRI Image	True Mask	Predicted Mask
Brain Scan	Ground Truth Tumor	Model Segmentation

(See notebook outputs for visual examples)

🚀 How to Run
1️⃣ Install Dependencies
pip install tensorflow numpy matplotlib opencv-python

2️⃣ Open Notebook

Run the Jupyter Notebook:

imageseg.ipynb

3️⃣ Train the Model

The notebook includes:

Data loading

Preprocessing

Model training

Evaluation

Visualization

💾 Saved Models
File	Description
best_brain_tumor_unet.keras	Model trained with BCE loss
best_brain_tumor_unet_dice.keras	Best model trained using BCE + Dice Loss

To load the best model:

from tensorflow import keras

model = keras.models.load_model(
    "best_brain_tumor_unet_dice.keras",
    custom_objects={
        "dice_coef": dice_coef,
        "bce_dice_loss": bce_dice_loss
    }
)

📈 Future Improvements

Use a pretrained encoder (Transfer Learning)

Add stronger data augmentation

Train on higher resolution images

Use more advanced loss functions (Focal Tversky, Combo Loss)

🎯 Conclusion

This project demonstrates how Deep Learning can assist in medical image analysis by automatically segmenting brain tumors from MRI scans. While not production-ready, the model provides a strong baseline for further research and improvement.

Author: Debasish
Project Type: Medical Image Segmentation
Framework: TensorFlow / Keras