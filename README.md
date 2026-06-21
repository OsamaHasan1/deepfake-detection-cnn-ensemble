# Deepfake Detection Using CNN Ensemble Models

This project focuses on detecting deepfake images using individual CNN-based models and a weighted voting ensemble model. The main goal is to compare whether combining multiple CNN architectures can improve deepfake detection performance compared to using each model individually.

The project also includes a research component that studies public awareness of deepfake content and its risks through a survey.

---

## Project Objective

The project aims to answer two main questions:

1. How effective is combining multiple CNN architectures into an ensemble model for detecting deepfake images compared to individual CNN architectures?
2. How aware are social media users of deepfake content and its potential risks?

---

## Dataset

The image dataset is not included in this repository because it is too large.

This project uses the **Deepfake and Real Images** dataset from Kaggle, which is derived from the **OpenForensics** dataset by Zenodo.

Dataset sources:

* Kaggle dataset:
  https://www.kaggle.com/datasets/manjilkarki/deepfake-and-real-images

* Original OpenForensics dataset on Zenodo:
  https://zenodo.org/records/5528418

The dataset contains real and fake face images organized into training, validation, and testing folders. The task is binary classification:

* Real image
* Fake image

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

The notebook resizes images before training to make them compatible with the CNN models.

---

## Repository Files

```text
deepfake-detection-cnn-ensemble/
│
├── README.md
├── requirements.txt
├── .gitignore
├── deepfake_detection_cnn_ensemble.ipynb
│
└── data/
    └── README.md
```

## File Description

### `deepfake_detection_cnn_ensemble.ipynb`

This is the main notebook of the project.

It includes:

* Loading image data from training, validation, and testing folders.
* Preprocessing images using resizing and batching.
* Building and training individual CNN-based models.
* Evaluating each model using classification metrics.
* Creating a weighted voting ensemble model.
* Comparing the ensemble model against individual models.
* Reporting the final performance results.

### `data/README.md`

This file explains why the dataset is not included in the repository and provides the Kaggle and Zenodo dataset links.

### `requirements.txt`

This file lists the Python libraries needed to run the notebook.

### `.gitignore`

This file prevents large datasets, saved models, temporary files, and environment files from being uploaded to GitHub.

---

## Methodology

The project used a CNN-based image classification workflow.

### 1. Data Loading and Preprocessing

The image dataset was loaded from folders containing real and fake images. The data was already divided into training, validation, and testing folders.

Preprocessing steps included:

* Loading images as TensorFlow datasets.
* Using binary labels for real and fake classes.
* Resizing images to match the input requirements of CNN architectures.
* Batching images to reduce memory usage during training.

### 2. Individual Models

Three individual models were trained and evaluated:

* Simple CNN
* EfficientNetB0
* ResNet50

The Simple CNN was trained from scratch, while EfficientNetB0 and ResNet50 were used as CNN-based architectures for feature extraction and classification.

### 3. Weighted Voting Ensemble

After training the individual models, a weighted voting ensemble model was created.

The ensemble combined the outputs of:

* Simple CNN
* EfficientNetB0
* ResNet50

The weighted voting strategy gave higher weight to the stronger model and lower weights to the weaker models. The goal was to improve robustness and overall classification performance.

---

## Models Used

| Model                    | Description                                                                        |
| ------------------------ | ---------------------------------------------------------------------------------- |
| Simple CNN               | A custom convolutional neural network trained from scratch.                        |
| EfficientNetB0           | A CNN architecture designed to balance depth, width, and resolution efficiently.   |
| ResNet50                 | A residual CNN architecture that uses skip connections to support deeper learning. |
| Weighted Voting Ensemble | A combined model that uses weighted predictions from the individual models.        |

---

## Model Results

| Model          | Accuracy | Precision | Recall | F1-score |
| -------------- | -------: | --------: | -----: | -------: |
| Simple CNN     |    0.942 |     0.934 |  0.951 |    0.942 |
| EfficientNetB0 |    0.826 |     0.848 |  0.796 |    0.821 |
| ResNet50       |    0.819 |     0.802 |  0.849 |    0.825 |
| Ensemble Model |    0.947 |     0.947 |  0.947 |    0.947 |

---

## Results Interpretation

The Simple CNN achieved the best performance among the individual models, with an accuracy of `0.942` and an F1-score of `0.942`. This shows that the custom CNN was able to learn useful patterns from the dataset.

EfficientNetB0 achieved an accuracy of `0.826`, while ResNet50 achieved an accuracy of `0.819`. Their lower performance may be related to image quality and resolution differences compared to the type of images these architectures are usually trained on.

The weighted voting ensemble achieved the best overall result, with:

* Accuracy: `0.947`
* Precision: `0.947`
* Recall: `0.947`
* F1-score: `0.947`

This means that combining multiple CNN models improved the final classification performance compared to using individual models alone.

---

## Best Model

The best-performing model was the **Weighted Voting Ensemble Model**.

It outperformed all individual models and achieved the highest overall balance across accuracy, precision, recall, and F1-score.

Final ranking:

1. Weighted Voting Ensemble
2. Simple CNN
3. EfficientNetB0
4. ResNet50

---

## Survey Component

In addition to model development, a survey was conducted to measure public awareness of deepfake technology among social media users.

The survey focused on questions such as:

* How familiar people are with deepfakes.
* Whether people can distinguish fake images from real images.
* How concerned people are about deepfakes in cybercrime.
* Whether people trust detection systems.
* Whether people believe deepfakes can influence public opinion.

## Survey Findings

The survey results showed that people had some awareness of deepfake technology, but this awareness was not strong enough.

Key findings:

* Many participants had only moderate understanding of deepfakes.
* More than half of the participants struggled to distinguish real and fake images.
* Many participants were concerned about the use of deepfakes in cybercrime and misinformation.
* Some participants had low trust in current detection systems.
* Most participants believed deepfakes can influence public opinion.

These findings support the need for reliable deepfake detection systems, especially on social media platforms.

---

## Recommendations

Based on the model and survey results, the following recommendations were suggested:

* Use ensemble CNN models for future deepfake detection systems.
* Apply image enhancement techniques to improve low-resolution images.
* Train and test models on multiple datasets to improve generalization.
* Deploy deepfake detection systems on social media platforms.
* Add warning labels to content identified as manipulated.
* Provide probability scores to show how likely content is fake.
* Use visual explanations or heatmaps to improve user trust.

---

## Weaknesses and Limitations

* The dataset is too large to include directly in the repository.
* Some images have low resolution, which may reduce the performance of pretrained models.
* EfficientNetB0 and ResNet50 performed lower than expected, possibly due to image quality and resolution differences.
* The project used one main image dataset, so generalization to other deepfake datasets may be limited.
* The survey sample size was small, so the awareness results may not represent the full population.
* The model was evaluated on images, not videos.
* The system is a research prototype and should be further tested before real-world deployment.

---

## Tools and Libraries

* Python
* TensorFlow / Keras
* NumPy
* Pandas
* Matplotlib
* Scikit-learn
* OpenCV
* Jupyter Notebook

---

## How to Run

1. Clone the repository:

```bash
git clone https://github.com/OsamaHasan1/deepfake-detection-cnn-ensemble.git
```

2. Move into the project folder:

```bash
cd deepfake-detection-cnn-ensemble
```

3. Install the required libraries:

```bash
pip install -r requirements.txt
```

4. Download the dataset manually from Kaggle:

```text
https://www.kaggle.com/datasets/manjilkarki/deepfake-and-real-images
```

5. Extract the dataset and place it locally using this structure:

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

6. Open and run the notebook:

```text
deepfake_detection_cnn_ensemble.ipynb
```

If your dataset path is different, update the path inside the notebook before running.

---

## Conclusion

This project compared individual CNN models with a weighted voting ensemble model for deepfake image detection.

The results showed that the ensemble model achieved the best performance, reaching `0.947` accuracy and `0.947` F1-score. This indicates that combining CNN models can improve deepfake detection compared to relying on individual models alone.

The survey results also showed that public awareness of deepfakes exists, but many users still struggle to identify fake content. Therefore, technical detection systems and awareness efforts are both important for reducing the risks of deepfake technology.
