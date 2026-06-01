# 06 定位與匹配

這個資料夾是 Computer Vision / Image Processing 學習系列的第六部分。

本章聚焦於接近工業檢測情境的 object localization。Notebook 不只說明如何產生位置結果，也強調如何判斷該位置是否有足夠的視覺、幾何或數值證據支持。

## 檔案內容

```text
06_localization_and_matching/
├── README.md
├── README_zh.md
├── localization_and_matching.ipynb
├── localization_and_matching_zh.ipynb
└── outputs/
    └── 06_localization_and_matching/
```

## 主要 Notebook

英文版 notebook 是 GitHub 主要展示版本：

```text
localization_and_matching.ipynb
```

繁體中文版 notebook 為：

```text
localization_and_matching_zh.ipynb
```

## 涵蓋主題

- Localization 概念與影像座標系統
- Bounding boxes、center points、ROI cropping
- Mask-based localization
- Contour-based localization
- Template matching 與 response maps
- Multi-scale template matching
- ORB feature-based matching
- Homography-based localization
- 定位可靠性分析
- 定位失敗案例分析
- 方法選擇指南
- 最終工程流程

## 如何執行

```bash
pip install opencv-python matplotlib numpy pandas jupyter
jupyter notebook localization_and_matching.ipynb
```

## 預期輸出

產生的結果圖會儲存在：

```text
outputs/06_localization_and_matching/
```

ZIP 中已包含生成好的輸出圖，可以直接檢查。
