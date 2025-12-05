# YOLO-SwinV2: Enhanced YOLO for Vehicle Detection in Adverse Weather

This project explores improving vehicle detection on highway surveillance footage under **fog**, **rain**, **snow**, and **low-contrast** conditions by replacing the YOLO-V5m CNN backbone with a **hierarchical Vision Transformer (SwinV2-Tiny)**. Inspired by the YOLO-LiRT paper, this study investigates whether transformer-based feature extraction improves robustness while maintaining reasonable training efficiency.

---

## Problem Statement

The YOLO-LiRT paper [1] demonstrates that integrating transformer modules into YOLO improves detection in adverse weather by capturing **contextual** and **low-level edge** features—especially for small or distant vehicles. Motivated by these findings, this project replaces YOLO-V5m’s backbone with **SwinV2-Tiny** and evaluates detection performance on harsh-weather highway footage.

### **Goals**
- Evaluate the pre-trained **YOLO-V5m** model on highway video in bad weather.
- Replace its backbone with **SwinV2-Tiny** and train/test the enhanced **YOLO-SwinV2** model.
- Compare:
  - training/validation loss  
  - bounding-box accuracy  
  - detection accuracy  
  - false detection frequency  
  - visual side-by-side outputs
- **Hypothesis:** YOLO-SwinV2 will perform more robustly in adverse weather but may overfit due to the small dataset.

---

## Dataset Description

This project uses ≈1,000 images from each dataset:

### **1. Cars Detection Dataset**  
- 878 training images  
- 250 validation images  
- Clear-weather highway scenes  

### **2. AAU RainSnow Traffic Surveillance Dataset**  
- 13,200 images  
- Includes rain, snow, fog, and low-visibility conditions  

To reduce overfitting, hyperparameters will be tuned and Non-Maximum Suppression (NMS) evaluated.

---

## Proposed Model and Technical Approach

The baseline evaluation uses **YOLO-V5m** on adverse-weather highway footage.  
We then replace its backbone with **SwinV2-Tiny**, chosen for:

- Hierarchical multi-scale feature extraction compatible with YOLO’s PAN-FPN  
- Normalized attention → more stable in fog/snow  
- Continuous positional bias → handles large vehicle motion  
- Large-window attention → stronger global context under blurred edges  
- Clean integration of **SwinV2 Stages 2/3/4** as P3/P4/P5 feature maps  

Training is limited to **5–10 epochs** and **≤90 minutes**, following course constraints.

---

## Expected Results

- YOLO-SwinV2 should achieve **better detection robustness** under adverse weather compared to YOLO-V5m.
- Overfitting may increase false detections due to limited training samples.
- Longer training and better transformer architectures might yield additional improvements but are beyond class requirements.

---

## Timeline

| Week | Tasks |
|------|-------|
| **Week 1** | Data exploration + YOLO-V5m baseline evaluation |
| **Week 2** | Implement YOLO-SwinV2 + ablation studies |
| **Week 3** | Final evaluation on highway video + report writing |

---

## References

[1] Tao Luo, Zhiwei Guan, Dangfeng Pang, Ruzhen Dou. *Enhanced car detection and ranging in adverse conditions using improved YOLO-LiRT and FSGBMN*. J Supercomput 81, 1355 (2025).  
[2] *Cars Detection Dataset*, Kaggle. https://www.kaggle.com/datasets/abdallahwagih/cars-detection  
[3] *AAU RainSnow Traffic Surveillance Dataset*, Kaggle. https://www.kaggle.com/datasets/aalborguniversity/aau-rainsnow  

---
