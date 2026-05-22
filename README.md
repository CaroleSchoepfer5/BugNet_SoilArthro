# BugNet_SoilArthro

# BugNet Soil Arthropod Image Processing

This repository contains notebooks, model files and environment specifications used for automated processing of soil mesofauna images from BugNet field experiments.

The workflow consists of two main steps:

1. Detection and extraction of individual organisms using a fine-tuned FlatBug model
2. Classification and sorting of extracted crops into broad taxonomic groups using a YOLO-based classifier

Detailed instructions and workflow descriptions are provided in:

**Protocol_Image_Processing.docx**

---

## Repository contents

### BugNet_SoilArthro_FlatBug.ipynb

Notebook used for applying the fine-tuned FlatBug model.

Main functions:

- Load source images
- Run object detection
- Extract individual organisms
- Save cropped images while retaining source image information

Required input:

- source images
- FlatBug model weights

Output:

- cropped organism images

---

### SoilArthro_classifier.ipynb

Notebook used for training and applying the classifier.

Main functions:

- train classifier from manually labelled examples
- apply trained classifier
- automatically sort crops into taxonomic groups
- apply confidence thresholding

Required input:

- cropped images from FlatBug
- classifier weights

Output:

- automatically sorted images

---

### classifier_best.pt

Trained classifier weights used for automatic image classification.

---

### yolov8n-cls.pt

Pre-trained YOLO classification model used as starting point for training.

---

### environment_classifier.yml

Conda environment file containing package information required for reproducing the classifier setup.

Create environment:

```bash
conda env create -f environment_classifier.yml
conda activate bugcls
```

---

## FlatBug model weights

The fine-tuned FlatBug weights are not included in this repository because of file size limitations.

Download model weights here:

[INSERT LINK]

Place the downloaded weights in your local `model` folder before running:

```text
BugNet_SoilArthro_FlatBug.ipynb
```

---

## Notes

Automatic detection and classification are intended to reduce manual work but do not replace manual quality control.

Performance may vary when applied to images acquired under substantially different conditions than the training data.
