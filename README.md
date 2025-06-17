Here’s a professional and clear **README** for your project that explains the motivation, approach, and results, including how you transitioned from KMeans to CNN for dominant color prediction:

---

# 🌈 Dominant Color Prediction from Natural Scene Images

## 📌 Project Overview

This project aims to **predict the dominant color** (Red, Green, or Blue) in natural scene images. Initially, **KMeans clustering** is used to determine the dominant color in each image based on pixel values. These labels are then used to **train a Convolutional Neural Network (CNN)**, allowing the model to learn how to infer the dominant color directly from raw image input.


## 🛠️ Approach

### 1. **Dataset**

* We use the [Intel Image Classification dataset](https://www.kaggle.com/puneet6060/intel-image-classification).
* Each image belongs to one of six scene classes: *buildings, forest, glacier, mountain, sea, and street*.

### 2. **KMeans for Label Generation**

* Each image is resized and clustered into 3 dominant color regions using **KMeans**.
* The most dominant RGB cluster is converted into a label: `'Red'`, `'Green'`, or `'Blue'`.

### 3. **Labeling Strategy**

* The dominant color is determined by comparing the RGB intensities of the cluster center.
* Labels are stored in a CSV (`kmeans_output.csv`) with:

  * `filename`
  * `dominant_rgb`
  * `dominant_color_name`

### 4. **CNN Training**

* Images and labels from the CSV are loaded.
* Images are normalized and resized to 100×100.
* A CNN is trained to classify each image into one of the 3 dominant color classes.

### 5. **Model Architecture**

```python
Conv2D(32) → MaxPooling2D → 
Conv2D(64) → MaxPooling2D → 
Flatten → Dense(128) → Dropout → Dense(3 softmax)
```

---

## 📊 Results

| Metric       | Value                   |
| ------------ | ----------------------- |
| **Accuracy** | ✅ **93%** (on test set) |
| Classes      | Red, Green, Blue        |
| Model Size   | \~350KB (lightweight)   |

---
