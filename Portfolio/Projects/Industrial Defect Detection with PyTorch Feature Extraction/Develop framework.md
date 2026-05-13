
## 1. Project Objective

此專案建立一個基於 PyTorch 的工業瑕疵異常分類流程。

核心目標是：

```text
Input Image → Feature Extraction → Anomaly Score → Threshold Decision → Normal / Anomaly
```

本專案使用 MVTec AD dataset。該資料集是工業檢測 anomaly detection benchmark，包含多個物件與材質類別；每個類別的 training set 只包含 defect-free images，而 test set 同時包含正常與異常影像。

---

# 2. Task Definition

## 2.1 Task Type

本專案定義為：

```text
Image-level anomaly classification
```

也就是對單張影像進行二分類：

```text
Normal / Good
Anomaly / Defect
```

## 2.2 Non-Goal

本階段不處理：

```text
Pixel-level anomaly localization
Defect mask prediction
Segmentation model training
```

MVTec AD 雖然提供 pixel-level annotation，但本專案第一版只使用 image-level normal / anomaly label。

---

# 3. Dataset Preparation

## 3.1 Dataset Source

使用：

```text
MVTec AD Dataset
```

第一版只選擇一個子類別進行開發，例如：

```text
bottle
```

原因：

```text
降低開發複雜度
快速完成完整 pipeline
方便檢查資料載入、特徵提取、評估與視覺化流程
```

## 3.2 Dataset Structure

MVTec AD 單一類別的典型結構：

```text
category/
├── train/
│   └── good/
├── test/
│   ├── good/
│   ├── defect_type_1/
│   ├── defect_type_2/
│   └── ...
└── ground_truth/
    ├── defect_type_1/
    ├── defect_type_2/
    └── ...
```

本專案只使用：

```text
train/good/
test/good/
test/defect_type/
```

不使用：

```text
ground_truth/
```

因為 `ground_truth/` 是給 anomaly localization / segmentation 使用。

---

# 4. Data Split Strategy

## 4.1 Training Data

訓練階段只使用正常影像：

```text
train/good/
```

用途：

```text
建立正常樣本的 feature representation
```

## 4.2 Validation Data

從 `train/good/` 中切出一部分作為 validation set。

建議比例：

```text
train_normal: 80%
val_normal: 20%
```

validation set 用途：

```text
估計 normal feature distance 的分布
設定 anomaly threshold
避免直接使用 test set 調整 threshold
```

## 4.3 Test Data

test set 包含：

```text
test/good/       → label = 0
test/defect_x/   → label = 1
```

測試階段才使用 test set。

---

# 5. Model Design

## 5.1 Model Role

本專案不從零訓練 CNN，也不 fine-tune classification head。

模型角色是：

```text
Pretrained CNN Feature Extractor
```

TorchVision 提供多種 pretrained model，例如 ResNet、MobileNet、EfficientNet 等，可直接載入 pretrained weights；TorchVision 也提供 feature extraction utilities 以取得模型中間層輸出。([PyTorch Docs](https://docs.pytorch.org/vision/main/models.html?utm_source=chatgpt.com "Models and pre-trained weights — Torchvision main ..."))

## 5.2 Recommended Backbone

第一版建議使用：

```text
ResNet18
```

原因：

```text
模型輕量
速度快
容易理解
適合快速完成 prototype
```

後續可比較：

```text
ResNet50
MobileNetV3
EfficientNet-B0
```

---

# 6. Feature Extraction Pipeline

## 6.1 Input Preprocessing

所有影像需經過一致的 preprocessing：

```text
Resize
Center Crop or Direct Resize
ToTensor
Normalize with ImageNet mean and std
```

原因：

```text
pretrained model 通常基於 ImageNet normalization 訓練
輸入格式需與 pretrained model 預期一致
```

## 6.2 Feature Vector Generation

流程：

```text
image
→ pretrained ResNet18
→ remove final classification layer
→ output feature vector
```

每張影像轉換成一個 feature vector：

```text
image_i → feature_i
```

---

# 7. Normal Pattern Modeling

## 7.1 Normal Feature Center

使用所有 normal training features 建立正常中心：

```text
normal_center = mean(normal_features)
```

此中心代表正常樣本在 feature space 中的平均 pattern。

## 7.2 Anomaly Score

對每張測試影像計算：

```text
anomaly_score = distance(test_feature, normal_center)
```

第一版建議使用：

```text
Euclidean distance
```

判斷邏輯：

```text
distance 越小 → 越接近正常樣本
distance 越大 → 越可能是異常樣本
```

---

# 8. Threshold Strategy

## 8.1 Threshold Source

threshold 不應直接用 test set 調整。

第一版建議使用 validation normal scores 設定：

```text
threshold = mean(val_scores) + k * std(val_scores)
```

例如：

```text
k = 2
```

或使用 percentile：

```text
threshold = 95th percentile of val_scores
```

## 8.2 Classification Rule

```text
if anomaly_score > threshold:
    prediction = anomaly
else:
    prediction = normal
```

---

# 9. Evaluation

## 9.1 Evaluation Data

使用：

```text
test/good/
test/defect_type/
```

建立 image-level label：

```text
good image    → 0
defect image  → 1
```

## 9.2 Metrics

輸出以下指標：

```text
Accuracy
Precision
Recall
F1-score
Confusion Matrix
```

重點觀察：

```text
False Positive：正常影像被判為異常
False Negative：異常影像被判為正常
```

在工業檢測情境中，false negative 通常更嚴重，因為代表瑕疵品漏檢。

---

# 10. Visualization

## 10.1 Required Figures

第一版至少輸出：

```text
confusion_matrix.png
score_distribution.png
sample_predictions.png
```

## 10.2 Figure Purpose

|Figure|Purpose|
|---|---|
|Confusion Matrix|檢查 normal / anomaly 判斷結果|
|Score Distribution|觀察 normal 與 anomaly score 是否分離|
|Sample Predictions|直觀展示模型預測結果|

---

# 11. Result Analysis

分析內容應包含：

```text
1. Normal 與 anomaly 的 score 分布是否明顯分開
2. 哪些 defect type 容易被判出
3. 哪些 defect type 容易漏判
4. False positive 與 false negative 的數量
5. Threshold 是否過於寬鬆或嚴格
6. Global feature-based method 的限制
```

---

# 12. Project Structure

建議專案結構：

```text
PyTorch_Industrial_Anomaly_Classification/
├── README.md
├── requirements.txt
├── src/
│   ├── dataset.py
│   ├── transforms.py
│   ├── feature_extractor.py
│   ├── build_reference.py
│   ├── evaluate.py
│   └── visualize.py
├── data/
│   └── README.md
├── results/
│   ├── metrics.md
│   ├── confusion_matrix.png
│   ├── score_distribution.png
│   └── sample_predictions.png
└── docs/
    └── method.md
```

---

# 13. Development Stages

## Stage 1: Minimal Working Pipeline

目標：

```text
完成資料讀取、feature extraction、anomaly score、threshold classification
```

產出：

```text
可執行 evaluation script
基本 metrics
```

## Stage 2: Evaluation and Visualization

目標：

```text
輸出 evaluation figures
整理結果
```

產出：

```text
confusion_matrix.png
score_distribution.png
sample_predictions.png
metrics.md
```

## Stage 3: Documentation

目標：

```text
完成 README 與 method documentation
```

產出：

```text
README.md
docs/method.md
```

---

# 14. First Version Scope

第一版只包含：

```text
single category
image-level classification
pretrained ResNet18 feature extractor
normal feature center
distance-based anomaly score
threshold-based decision
basic evaluation figures
```

第一版不包含：

```text
multi-category training
fine-tuning
segmentation
defect localization
deployment
GUI
```

---

# 15. Final Pipeline Summary

```text
MVTec AD category selection
→ Load train/good images
→ Extract normal features with pretrained ResNet18
→ Build normal feature center
→ Compute validation anomaly scores
→ Set threshold
→ Load test/good and test/defect images
→ Compute test anomaly scores
→ Predict normal or anomaly
→ Evaluate metrics
→ Generate figures
→ Analyze results
```