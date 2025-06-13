---

# Brain Tumor Segmentation with U-Net (TensorFlow)

This project focuses on segmenting brain tumors from MRI scans using a manually implemented U-Net architecture in TensorFlow. The model is trained and tested on preprocessed brain images with corresponding ground truth masks.

---

## Features

* Manually implemented **U-Net** architecture in TensorFlow
* End-to-end pipeline: data loading, preprocessing, training, evaluation
* Segmentation performance visualized using **original images, ground truth masks, and predicted masks**
* Works with binary tumor masks and grayscale brain MRIs
* Model tested on real-world cases to validate prediction accuracy

---

## Sample Results

![Sample-Results](assets/Screenshot%202025-06-13%20114039.png)

> *Visual examples of the model's performance on unseen data.*

---

## Model Architecture

The model uses a custom-built U-Net, designed from scratch in TensorFlow.

```
Input (256x256x1)
        |
       [E1]─┬→ [P1] → 
        |   |
       [E2]─┬→ [P2] → 
        |   |
       [E3]─┬→ [P3] → 
        |   |
       [E4]─┬→ [P4] →
        |   |
       [Bottleneck (B)]
        |
       [D1] ←─── skip: [E4]
        |
       [D2] ←─── skip: [E3]
        |
       [D3] ←─── skip: [E2]
        |
       [D4] ←─── skip: [E1]
        |
      Output (256x256x1)
```

### Legend:

* `[E1]` to `[E4]`: Encoder blocks (`encoder_block`)
* `[P1]` to `[P4]`: Pooling layers (MaxPooling2D)
* `[B]`: Bottleneck (`conv_block`)
* `[D1]` to `[D4]`: Decoder blocks (`decoder_block`)
* Arrows `←─── skip:` represent skip connections via concatenation
* Final `Output`: Single-channel (`Conv2D(1, (1,1), activation='sigmoid')`)

---

## Dataset Structure

Organized into separate folders for input images and masks:

```
datasets/
└── Brain-Tumor-Classification-2D/
    └── Astrocytoma/
```

---

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/Deuterrr/brain-tumor-segmentation
cd brain-tumor-segmentation
```
---

## Main Files

```
├── .git/                      # Git configuration folder
├── assets/                   # Images and visual assets (e.g., model diagrams)
├── datasets/                 # Dataset files (e.g., training and testing data)
├── models/                   # Saved models or model checkpoints
├── .gitattributes            # Git attributes configuration
├── LICENSE                   # License information
├── Mini-Project              # Report or project description document
├── README                    # Project overview (you can rename to README.md)
├── testing                   # Test scripts or logs
```

---

## Tools & Libraries

* Python
* TensorFlow / Keras
* NumPy, Matplotlib

---

## License

This is a private research/learning project. Contact for permissions or collaborations.

---
