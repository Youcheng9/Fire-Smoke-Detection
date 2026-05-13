# Fire and Smoke Detection using YOLO11
***Before understanding how to use the code, please read the following details about this project.***

***The instruction, required packages, and location of the code can be found at the end of this README file.***

## Project Overview

This project creates a fire and smoke detection system using the YOLO11 object detection model. The goal is to detect smoke and fire in images and video for potential real-world applications such as surveillance, wildfire monitoring, and UAV-based emergency response.

This is an applied machine learning project that includes:

- dataset preprocessing and validation
- YOLO11 model training
- validation evaluation
- inference on test images and UAV data
- video demo generation

## Problem Motivation

Early detection of fire and smoke is important for reducing damage and improving emergency response. Traditional sensor-based systems can be limited by range, placement, response time, and cost. An alternative to the solution is to utilize computer vision-based system that can detect visible fire and smoke from camera feeds, UAV images, or surveillance videos.

## Dataset

Datasets were pulled from the following sources, make sure to give proper citations to the original owners if you are using it for research or projects.

- Train/Val/Test Dataset: https://www.kaggle.com/datasets/sayedgamal99/smoke-fire-detection-yolo

Pedro Vinícius Almeida Borges de Venâncio, Adriano Chaves Lisboa, Adriano Vilela Barbosa. "An automatic fire detection system based on deep convolutional neural networks for low-power, resource-constrained devices." Neural Computing and Applications, vol. 34, no. 18, 2022, pp. 15349–15368. DOI: 10.1007/s00521-022-07467-z.

- UAV dataset: https://www.scidb.cn/en/detail?dataSetId=ce9c9400b44148e1b0a749f5c3eb0bda

Wang, M., Yue, P., Jiang, L., Yu, D., Tuo, T., & Li, J. (2025). An open flame and smoke detection dataset for deep learning in remote sensing based fire detection. Geo-spatial Information Science, 28(2), 511-526.

- Video Demo: by Everett Bumstead from Pexels: https://www.pexels.com/video/aerial-view-of-forest-burning-in-british-columbia-30960957/


The dataset is organized in YOLO format:

```text
data/
├── train/
│   ├── images/
│   └── labels/
├── val/
│   ├── images/
│   └── labels/
├── test/
│   ├── images/
│   └── labels/
└── UAV_data/
    └── UAV_images/
    └── UAV_labels/

```

---

### Dataset Validation and Preprocessing

Before training, the dataset was validated to ensure:

- all images have corresponding label files
- all label files follow correct YOLO format
- bounding box values are within valid ranges (0-1)
- no corrupted or unreadable images
- no mismatched image-label pairs

Invalid labels or images were removed or corrected during preprocessing.

---

### Dataset Split Usage

- **Training set**: used to train the YOLO11 model  
- **Validation set**: used during training to monitor performance 
- **Test set**: used for final evaluation on unseen data  

#### Additional Dataset (UAV)

An additional UAV dataset was used for qualitative testing:
This dataset contains aerial images and was used to evaluate the model’s ability to generalize to new environments.

**Note: UAV data was used for qualitative analysis only and does not include ground truth annotations for metric evaluation.**


## Results

Image data are not included in this repository and only a few visualizations of testing metrics are included for evidence. Follow [Data](#dataset) to get the dataset and reproduce your own model by following the [instructions](#how-to-run-the-code).

The YOLO11 model achieved strong overall performance and demonstrated consistent results between validation and test datasets, indicating good generalization.

### Overall Performance (Test Set)

- Precision: 0.782  
- Recall: 0.700  
- mAP50: 0.771  
- mAP50-95: 0.445  

### Per-Class Performance

- **Smoke**: strong detection performance (high recall and mAP)  
- **Fire**: lower recall and localization accuracy  

### Key Observation

The model performs well in detecting smoke, while fire detection remains more challenging. Most errors are due to missed detections (false negatives), rather than confusion between smoke and fire classes.

## How to Run the Code

- Create a virtual environment:
  python -m venv .venv  

- Activate the environment:  
  Windows: .venv\Scripts\activate  
  macOS / Linux: source .venv/bin/activate  

- Install dependencies:
  pip install -r requirements.txt  

- Ensure the dataset is placed in the correct structure:
  data/train/images  
  data/train/labels  
  data/val/images  
  data/val/labels  
  data/test/images  
  data/test/labels  

- Run the main pipeline in main.ipynb:
  - preprocessing and validation  
  - training  
  - evaluation  
  - inference  

***Make sure to modify directory and files path as needed in order to run as different device can ouput or read files differently***


## Required Packages / Dependencies

- ultralytics (YOLO11)  
- torch (PyTorch)  
- torchvision  
- opencv-python  
- numpy  
- matplotlib  
- Pillow  
- PyYAML  

**Note: pip install -r requirements.txt will download all the required packages**


## Code Location
All the following pipeline:
- **Main preprocessing pipeline:**  
- **Model training:**
- **Evaluation (validation)** 
- **Image inference:** 
- **UAV inference:**
- **Video demo:** 

are inside main.ipynb. Each step is organized inside a markdown for ease of navigation and readability.
