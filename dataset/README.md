# Dataset

The dataset is not included in this repository because it is too large to upload to GitHub.

This project uses the **Deepfake and Real Images** dataset from Kaggle, which is derived from the **OpenForensics** dataset by Zenodo. The dataset contains real and fake face images used for deepfake image classification.

## Dataset Sources

* Kaggle dataset used in this project:
  https://www.kaggle.com/datasets/manjilkarki/deepfake-and-real-images

* Original OpenForensics dataset on Zenodo:
  https://zenodo.org/records/5528418

## Dataset Description

The dataset contains real and fake images organized into training, validation, and testing folders. It is designed for binary image classification, where the model predicts whether an image is real or fake.

Expected local folder structure:

```text
dataset/
├── train/
│   ├── real/
│   └── fake/
├── validation/
│   ├── real/
│   └── fake/
└── test/
    ├── real/
    └── fake/
```

## How to Use

1. Download the dataset manually from Kaggle.
2. Extract the dataset on your local machine.
3. Place the dataset in the expected folder structure shown above.
4. Update the dataset path in the notebook if needed.
5. Run `deepfake_detection_cnn_ensemble.ipynb`.

## Important Note

The dataset folder should not be uploaded to GitHub because it is large. This repository only includes the code, documentation, and instructions needed to reproduce the project.
