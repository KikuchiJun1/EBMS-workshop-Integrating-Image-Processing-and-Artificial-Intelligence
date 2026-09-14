# EBMS Workshop: Segmentation Tutorial

Welcome to the **Image Segmentation Tutorial**! This repository contains a hands-on workshop combining classical computer vision techniques with deep learning using PyTorch and UNet.

## What You'll Learn

In this tutorial, you'll explore:
- **Classical Segmentation**: Grayscale conversion, Otsu thresholding, morphological operations (opening/closing), and evaluation metrics (Dice, IoU).
- **Deep Learning Segmentation**: Training a small UNet model on real tissue images.
- **Inference**: Loading pretrained weights and running predictions on new images.

All of this runs in **~30-45 minutes** with GPU support (recommended) on Google Colab.

## Dataset

We use a subset of the **NuInsSeg dataset** (human spleen tissue images with binary segmentation masks):
- Small subset included in this repository for quick runs.
- Original data: [`NuInsSeg/human_spleen/`](NuInsSeg/human_spleen/)
- Images: RGB tissue microscopy images.
- Masks: Binary ground truth segmentation labels.

## Prerequisites

- **Python 3.8+**
- **Libraries** (automatically installed):
  - `torch`, `torchvision` (PyTorch)
  - `PIL` (image handling)
  - `numpy`, `matplotlib`, `scikit-image` (data processing & visualization)
- **Hardware**: GPU recommended (CUDA-enabled) but not required. CPU will be slower.
- **Time**: ~30-45 minutes.

## Quick Start

### Google Colab (Recommended for Beginners)

1. Click the badge below to open the notebook in Colab:
   [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/13U6g9ZiqGMeHWACSNUhqWODf-7SNMztC?usp=sharing)

2. Clone the repository to access the dataset and helper modules:
   ```python
   !git clone https://github.com/KikuchiJun1/EBMS-workshop-Integrating-Image-Processing-and-Artificial-Intelligence.git
   %cd EBMS-workshop-Integrating-Image-Processing-and-Artificial-Intelligence/segmentation
   ```

3. Run all notebook cells in order. 
   - **GPU recommended** (Colab provides free GPU access)
   - **CPU sufficient** (Model size and dataset are small, so still should be sufficient for this notebook)

## Notebook Structure

The main notebook [`Segmentation_Tutorial_Classical_and_UNet.ipynb`](Segmentation_Tutorial_Classical_and_UNet.ipynb) is organized into sections:

1. **Setup**: Configure paths, device (GPU/CPU), and parameters.
2. **Data Discovery**: Preview images and masks from NuInsSeg.
3. **Classical Segmentation**: 
   - Grayscale conversion
   - Otsu thresholding
   - Morphological operations (opening/closing)
   - Evaluation: Dice and IoU metrics
4. **UNet Training**:
   - Build and train a small UNet for 10 epochs
   - Validation loop with metrics
   - Save best checkpoint
5. **Inference**:
   - Load pretrained weights
   - Run predictions on test images
   - Visualize results

## Key Parameters

You can customize the tutorial by modifying these parameters in the notebook:

- **`LIMIT`**: Number of image/mask pairs to use. Default: 40 (fast). Increase to 100+ for better results.
- **`IMG_SIZE`**: Image resolution. Default: 256 (balanced speed/quality).
- **`EPOCHS`**: Training epochs. Default: 10 (quick demo).
- **`BATCH_SIZE`**: Samples per batch. Default: 4.
- **`INCLUDE`**: Dataset subsets to use. Default: `['human_spleen']`.

To run a longer training:
```python
LIMIT = 200      # Use more images
EPOCHS = 20      # Train longer
IMG_SIZE = 512   # Higher resolution
```

## Expected Results

After running the notebook, you should see:

1. **Classical Method Performance**: Dice ~0.7-0.85, IoU ~0.5-0.75 (fast, simple).
2. **UNet Performance**: Dice ~0.85-0.95, IoU ~0.75-0.90 (better, with learning).
3. **Training Plots**: Loss curves showing convergence.
4. **Example Predictions**: Side-by-side visualizations of input image, predicted mask, and ground truth.

## File Structure

```
EBMS-workshop-Integrating-Image-Processing-and-Artificial-Intelligence/
├── Segmentation_Tutorial_Classical_and_UNet.ipynb   # Main notebook
├── README.md                                         # This file
├── requirements.txt                                  # Python dependencies
├── .gitignore                                        # Git ignore rules
├── NuInsSeg/
│   └── human_spleen/                               # Dataset (small subset)
│       ├── tissue_images/                          # RGB tissue images
│       └── mask_binary/                            # Binary ground truth masks
├── train_unet/                                      # Helper modules (if included)
│   ├── dataset_nuinsseg.py
│   ├── model_unet.py
│   ├── transforms.py
│   └── utils.py
└── runs/
    └── expD2/                                      # Saved checkpoints & outputs
        └── best.pt                                 # Best UNet weights that you'll download from GDrive
```

## Troubleshooting

### **"ModuleNotFoundError: No module named 'train_unet'"**
   - Ensure you cloned the full repository and are in the correct directory.
   - In Colab: Run `!git clone` and `%cd` as shown above.

### **"No GPU available / CUDA not detected"**
   - On Colab: Enable GPU by going to **Runtime → Change runtime type → GPU**.
   - On local machine: Install `pytorch-cuda` (e.g., `pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118`).
   - The code will still run on CPU, but slower.

### **"NuInsSeg dataset not found"**
   - Ensure the `NuInsSeg/` folder is in the repository root.
   - If using Colab, `git clone` includes it; no extra steps needed.

### **"Out of memory (OOM) error"**
   - Reduce `BATCH_SIZE` (e.g., 2 or 1).
   - Reduce `IMG_SIZE` (e.g., 128).
   - Reduce `LIMIT` (fewer images).

### **Notebook cells fail to run**
   - Restart the kernel: **Kernel → Restart Kernel & Clear Output**.
   - Re-run cells from the top in order.

## Learning Resources

- **PyTorch Basics**: [PyTorch Tutorial](https://pytorch.org/tutorials/)
- **Segmentation Concepts**: [Semantic Segmentation Overview](https://en.wikipedia.org/wiki/Semantic_segmentation)
- **UNet Architecture**: [U-Net: Convolutional Networks for Biomedical Image Segmentation](https://arxiv.org/abs/1505.04597)
- **Review Paper**: [Medical Image Segmentation Using Deep Learning: A Survey](https://arxiv.org/pdf/2009.13120v1) - Comprehensive overview of deep learning approaches for medical image segmentation
- **Meta's Segment Anything**: [Segment Anything](https://arxiv.org/pdf/2304.02643) - Foundation model for image segmentation (Meta)
- **Meta's Segment Anything 2**: [SAM 2: Segment Anything in Images and Videos](https://arxiv.org/abs/2408.00714) - Extended SAM model for video segmentation
- **Evaluation Metrics**: [Dice Coefficient](https://en.wikipedia.org/wiki/S%C3%B8rensen%E2%80%93Dice_coefficient) and [IoU](https://en.wikipedia.org/wiki/Jaccard_index)


## Contributing

Found a bug or have suggestions?
- Open an issue on GitHub.
- Fork the repo, make changes, and submit a pull request.

## License

This project is licensed under the **MIT License**. Feel free to use, modify, and distribute for educational purposes.

## Questions?

- Check the **Troubleshooting** section above.
- Open a GitHub issue with details about your problem.
- For workshop-specific questions, contact the instructor.

---

**Happy segmenting!**

*Last updated: September 2026*
