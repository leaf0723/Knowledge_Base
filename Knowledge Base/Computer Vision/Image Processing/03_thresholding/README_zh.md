# 03 — 閾值化與形態學處理

這個資料夾是 Computer Vision / Image Processing 學習系列的第三部分。

本章聚焦在使用 thresholding 進行二值分割，並使用 morphology 修正與清理 binary mask。  
目標是建立一個實用的影像處理流程，將灰階影像轉換成可以被量測與判斷的區域。

## 檔案內容

```text
03_thresholding_and_morphology/
├── README.md
├── README_zh.md
├── thresholding_and_morphology.ipynb
└── thresholding_and_morphology_zh.ipynb
```

## 主要 Notebook

英文版 notebook 是 GitHub 主要展示版本：

```text
thresholding_and_morphology.ipynb
```

繁體中文版 notebook 為：

```text
thresholding_and_morphology_zh.ipynb
```

## 涵蓋主題

本章包含：

- Global thresholding
- Threshold 敏感度比較
- Otsu's thresholding
- Adaptive thresholding
- Morphological erosion 與 dilation
- Morphological opening 與 closing
- Kernel size 比較
- Connected component analysis
- 檢測流程式的視覺化
- 適合作品集展示的輸出圖儲存

## 如何執行

如果尚未安裝相關套件，可以先執行：

```bash
pip install opencv-python numpy matplotlib jupyter
```

接著開啟 notebook：

```bash
jupyter notebook thresholding_and_morphology.ipynb
```

或使用 JupyterLab / VS Code 執行。

## 預期輸出

執行 notebook 後，輸出影像會儲存在：

```text
outputs/03_thresholding_and_morphology/
```

產生的輸出包含：

- 合成檢測影像
- 灰階 histogram
- global threshold mask
- threshold 敏感度比較圖
- Otsu threshold mask
- adaptive threshold mask
- thresholding 方法比較圖
- morphology 操作結果
- opening / closing kernel size 比較
- connected component detection 結果
- pipeline summary report image

## 學習目標

完成本章後，讀者應該能理解：

1. Thresholding 如何將灰階影像轉換成 binary mask。
2. 為什麼固定 threshold 容易受到光照與對比影響。
3. Otsu's method 什麼時候有用，什麼時候可能失效。
4. Adaptive thresholding 為什麼能處理光照不均。
5. Morphology 如何清理或修補 binary mask。
6. Kernel size 如何影響誤判與漏判。
7. Connected component analysis 如何將 binary mask 轉成可量測區域。

## 工程重點

本章的核心實務理解是：

> Thresholding 產生候選 mask，morphology 修正 mask，component analysis 將 mask 轉成可量測的證據。

這套流程特別適合傳統電腦視覺任務，例如 AOI、瑕疵檢測、簡單物件分割與 rule-based inspection。

## 下一步

下一部分可以自然銜接到 edge-based processing，例如 Sobel、Laplacian、Canny edge detection 與 contour extraction。