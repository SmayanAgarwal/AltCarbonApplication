# Vibe Map Predictor

This project predicts the **"vibe"** of a place in Delhi — such as *Chill*, *Trendy*, or *Cultural* — using spatial and contextual urban data. The model is part of a broader system to understand how different places feel, based on measurable features.

---

## 📍 Dataset Overview

The final dataset includes **93 locations** across Delhi. Each location is tagged with a `Vibe` category based on human judgment and is paired with spatial features such as:

- Distance to nearest metro station
- Number of eateries within 1km
- Number of metro stations within 1km
- Forest cover of the region
- School quality score

The data was compiled manually and programmatically through:
- Google Maps queries for location coordinates
- QGIS spatial queries for proximity features
- Area-wise forest and school data via public databases

---

## 🧠 Model and Features

We trained a **Random Forest Classifier** using:

### Features:
1. Distance to Nearest Metro Station
2. Eateries Within 1KM
3. Metro Stations Within 1KM
4. Forest Cover
5. School Quality
6. One-hot encoded Location (administrative zone)

### Target:
- `Vibe` (5 classes): `Chill`, `Commercial`, `Cultural`, `Residential`, `Trendy`

---

## ⚙️ Parameters

- `RandomForestClassifier(n_estimators=100, class_weight='balanced', random_state=9)`
- `StandardScaler` for preprocessing numeric features
- Train-test split: 80/20

---

## 📊 Results

| Metric         | Score |
|----------------|-------|
| Accuracy       | 44%   |
| Macro F1 Score | 25%   |
| Weighted F1    | 29%   |

> Note: Some categories (like `Residential`, `Trendy`) had fewer examples and underperformed. `Cultural` was best predicted, followed by `Chill` and `Commercial`.

![Confusion Matrix](<insert-path-if-you-commit-image>)  <!-- Optional image -->

---

## 🛠️ How the Data Was Created

1. **Places and Vibes**: Manually labeled based on familiarity with Delhi.
2. **Coordinates**: Extracted via Google Maps or geocoding.
3. **Metro and Eateries**:
   - Loaded into QGIS
   - Counted using buffer zones (1km)
4. **School Quality / Forest Cover**: Merged from external CSV datasets using location-level VLOOKUPs.

---

## 🔮 Next Steps

The follow-up system will allow users to:
- Enter the name of any place
- Automatically geocode coordinates
- Calculate metro and eatery proximity using spatial queries
- Pull forest and education indicators by administrative region
- Predict the vibe of the place using the trained model

This will eventually be turned into a simple web-based tool.

---

## 📁 Files in this Repository

- `Minimum Data Document.csv`: Final dataset used for training
- `vibe_predictor.py`: Code for preprocessing, training, and predicting
- `README.md`: This file

---

## ✍️ Author

Smayan Agarwal  
[GitHub](https://github.com/smayanagarwal) | [Email](mailto:your.email@example.com)

---
