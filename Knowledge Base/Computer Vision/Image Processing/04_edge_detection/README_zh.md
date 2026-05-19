# 04 邊緣偵測

這個資料夾是 Computer Vision / Image Processing 學習系列的第四部分。

本章記錄 edge detection 的學習與實作筆記。  
重點不只是套用 OpenCV 函式，而是理解每個方法實際在量測什麼、會產生什麼結果，以及這些結果如何放進實務影像處理流程中。

Notebook 使用 `skimage.data` 內建真實影像範例，並且附上預先產生的輸出圖片，方便直接檢查結果。

## 檔案內容

```text
04_edge_detection/
├── README.md
├── README_zh.md
├── edge_detection.ipynb
├── edge_detection_zh.ipynb
└── outputs/
    └── 04_edge_detection/
```

## 主要 Notebook

英文版 notebook 是 GitHub 主要展示版本：

```text
edge_detection.ipynb
```

繁體中文版 notebook 為：

```text
edge_detection_zh.ipynb
```

## 涵蓋主題

- 影像處理中的 edge 代表什麼
- 一階導數與二階導數的直覺差異
- Kernel design 如何影響 convolution-based edge detector
- Sobel 作為帶有平滑效果的方向性梯度 operator
- Scharr 作為改良版 3x3 gradient operator
- Sobel 與 Scharr 的 difference-map 比較
- Laplacian 作為二階局部變化偵測
- 為什麼 Laplacian 對雜訊與紋理敏感
- Canny 作為完整 edge-detection pipeline
- 使用真實 coin image 說明 Canny threshold sensitivity
- Edge map 到 contour extraction
- 邊緣偵測方法選擇的工程筆記

## 如何執行

安裝必要套件：

```bash
pip install opencv-python scikit-image matplotlib numpy jupyter
```

開啟 notebook：

```bash
jupyter notebook edge_detection.ipynb
```

或使用 JupyterLab / VS Code 執行。

## 預期輸出

Notebook 會將輸出影像儲存在：

```text
outputs/04_edge_detection/
```

ZIP 中已經包含產生好的輸出圖片，可以直接檢查結果。

## 工程重點

不同 edge detector 不是只是函式名稱不同。

對 convolution-based 方法而言，kernel 決定它要量測哪一種局部變化。  
對 Canny 而言，它不是單一 kernel，而是包含 gradient、細線化、雙閾值與邊緣連接邏輯的完整流程。

好的 edge map 不是 edge 越多越好。  
好的 edge map 是能為下一步保留有用邊界，同時移除干擾。
