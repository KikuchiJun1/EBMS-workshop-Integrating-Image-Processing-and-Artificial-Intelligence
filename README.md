# Engineered Biological Models & Systems: Artificial Intelligence for Single-Cell Analysis: Detection, Segmentation, Classification, and Tracking

This repository contains two hands-on tutorials for biomedical image analysis using classical and deep learning approaches:

1. **Segmentation Tutorial** - Cell segmentation using classical methods (Otsu thresholding) and UNet
2. **Classification Tutorial** - Sperm morphology classification using DenseNet-169

Both tutorials are designed for beginners and can run in Google Colab with free GPU access. However, GPU is recommended for extensive training on data.

---

## 📚 Repository Structure

```
.
├── segmentation/
│   ├── Segmentation_Tutorial_Classical_and_UNet.ipynb
│   ├── NuInsSeg/                    # Dataset (human_spleen subset)
│   ├── train_unet/                  # Helper modules
│   └── runs/                        # Training outputs
│
├── classification/
│   ├── Classification.ipynb
│   └── Data/                        # Dataset folders (Train/Validation/Test)
│       ├── Train/
│       │   ├── Normal/
│       │   └── Abnormal/
│       ├── Validation/
│       │   ├── Normal/
│       │   └── Abnormal/
│       └── Test/
│           ├── Normal/
│           └── Abnormal/
└── README.md
```

---

## 🎯 Quick Start

### Access via Google Colab (Recommended)

**Tutorial #1: Segmentation Tutorial:**

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1Xgfr8NLCkcNJJBcs5eO119mmG9KnMPu8?usp=sharing)

**Tutorial #2: Classification Tutorial:**

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1_Z_CqJ_2x7F0sHlUSG766rw4Y89gJVPj?usp=sharing)

### Local Installation

```bash
git clone https://github.com/KikuchiJun1/EBMS-workshop-Integrating-Image-Processing-and-Artificial-Intelligence.git
cd EBMS-workshop-Integrating-Image-Processing-and-Artificial-Intelligence
pip install torch torchvision pillow numpy matplotlib scikit-image
```

---

## Tutorial 1: Segmentation

### Overview
Learn nucleus segmentation on the NuInsSeg dataset using:
- **Classical methods**: Otsu thresholding, morphological operations
- **Deep learning**: UNet architecture for semantic segmentation

### What You'll Learn
- Image preprocessing and visualization
- Classical segmentation techniques
- Training a lightweight UNet (10 epochs)
- Evaluation metrics: Dice coefficient and IoU
- Inference on new images

### Dataset
- **NuInsSeg** (subset: human spleen tissue)
- ~40 image/mask pairs for fast training
- Binary segmentation (nucleus vs. background)

### Expected Results
- **Classical (Otsu)**: Dice ~0.60-0.70
- **UNet (10 epochs)**: Dice ~0.85-0.95

### Runtime
- **GPU (Colab)**: ~10-15 minutes
- **CPU**: ~30-45 minutes

### Key Features
- Runs entirely in the browser (no local setup)
- Pretrained weights available for inference
- Modular code with detailed comments

---

## Tutorial 2: Classification

### Overview
Binary classification of sperm morphology (Normal vs. Abnormal) using:
- **DenseNet-169** pretrained on ImageNet
- Transfer learning approach

### What You'll Learn
- Data augmentation for medical images
- Transfer learning with pretrained models
- Training with PyTorch DataLoaders
- Model evaluation and confusion matrices

### Dataset
- TIFF/PNG images of sperm cells
- Two classes: Normal and Abnormal
- ImageFolder structure for easy loading

### Expected Results
- **5 epochs**: Validation accuracy ~75-80%
- **75 epochs (pretrained)**: Validation accuracy ~77%

### Runtime
- **GPU (Colab)**: ~5-10 minutes (5 epochs)
- **CPU**: ~20-30 minutes (5 epochs)

### Key Features
- 800×800 image resolution
- Grayscale normalization (mean=0.2636, std=0.1562)
- Pretrained checkpoint included for evaluation

---

## Prerequisites

### Software
- Python 3.8+
- PyTorch 1.13+
- torchvision
- Pillow, NumPy, Matplotlib
- scikit-image (for segmentation only)

### Hardware
- **Recommended**: GPU with 4GB+ VRAM (free in Colab)
- **Minimum**: CPU with 8GB RAM

---

## Usage Instructions

### Segmentation Tutorial

1. **Open in Colab** using the badge above
2. **Run Setup Cells** (1-4) to clone repo and download weights
3. **Follow the notebook sequentially**:
   - Data exploration
   - Classical segmentation demo
   - UNet training (10 epochs)
   - Pretrained inference
4. **Experiment**: Adjust `LIMIT`, `EPOCHS`, `IMG_SIZE` in Setup Cell 3

### Classification Tutorial

1. **Open in Colab** using the badge above
2. **Mount Google Drive** (if dataset is stored there)
3. **Update `CFG.data_dir`** to point to your dataset
4. **Run all cells** to train for 5 epochs
5. **Evaluate** using the pretrained checkpoint section

---

## Evaluation Metrics

### Segmentation
- **Dice Coefficient**: Overlap between prediction and ground truth
  - Formula: `2 * |A ∩ B| / (|A| + |B|)`
  - Range: 0 (no overlap) to 1 (perfect match)
- **IoU (Intersection over Union)**: Also known as Jaccard Index
  - Formula: `|A ∩ B| / |A ∪ B|`

### Classification
- **Accuracy**: Proportion of correct predictions
- **Precision/Recall**: Per-class performance
- **Confusion Matrix**: Detailed breakdown of predictions

---

## Troubleshooting

### Segmentation

**Issue**: `ModuleNotFoundError: No module named 'train_unet'`  
**Solution**: Ensure you ran Setup Cell 1 to clone the repository

**Issue**: `RuntimeError: CUDA out of memory`  
**Solution**: Reduce `BATCH_SIZE` or `IMG_SIZE` in Setup Cell 3

**Issue**: Pretrained weights fail to download  
**Solution**: Training will proceed normally; newly trained model will be used for inference

### Classification

**Issue**: `FileNotFoundError: [Errno 2] No such file or directory: './Data/Train'`  
**Solution**: Update `CFG.data_dir` to your dataset location

**Issue**: Poor validation accuracy  
**Solution**: Train for more epochs (increase `CFG.epochs`) or check data quality

---

## 🎓 Workshop Information

**Workshop**: EBMS Workshop
**Duration**: 120 minutes  
**Level**: Beginner to Intermediate  
**Prerequisites**: Basic Python knowledge

### Learning Outcomes
By the end of this workshop, you will:
- ✅ Understand classical vs. deep learning approaches for image analysis
- ✅ Train and evaluate segmentation and classification models
- ✅ Use transfer learning for medical imaging tasks
- ✅ Deploy models in Google Colab for quick prototyping

---

## Contact & Support

- **GitHub Issues**: [Report bugs or ask questions](https://github.com/KikuchiJun1/EBMS-workshop-Integrating-Image-Processing-and-Artificial-Intelligence/issues)

- **Workshop Organisers**: 

Jun.Kikuchi@Monash.edu
[![Open webpage](https://img.shields.io/badge/Open-Webpage-0969DA?style=for-the-badge)](https://www.monash.edu/engineering/junkikuchi)

Sahar.Shahali@monash.edu
[![Open webpage](https://img.shields.io/badge/Open-Webpage-0969DA?style=for-the-badge)](https://www.monash.edu/engineering/saharshahali)

- **Event Organisers**: 
Jessica.Frith@monash.edu
[![Open webpage](https://img.shields.io/badge/Open-Webpage-0969DA?style=for-the-badge)](https://www.monash.edu/engineering/jessfrith)

Stephanie.Doyle@monash.edu
[![Open webpage](https://img.shields.io/badge/Open-Webpage-0969DA?style=for-the-badge)](https://scholar.google.com/citations?user=eRAw-MoAAAAJ&hl=en)


---

## License

MIT License - Feel free to use for educational purposes.

---

## 🙏 Acknowledgments

- **NuInsSeg Dataset**: Provided by the medical imaging community
- **PyTorch & torchvision**: Open-source deep learning frameworks
- **Google Colab**: Free GPU access for education

---

**Happy Learning! **
