# 05 輪廓與連通元件

這個資料夾是 Computer Vision / Image Processing 學習系列的第五部分。

本章記錄如何把 binary mask 轉換成可量測物件，主要包含兩種常見方法：

- contour extraction
- connected component analysis

核心概念是：

> Mask 描述哪些 pixels 屬於前景區域。  
> Boundary 描述這個區域外圍的輪廓線。  
> Contours 和 connected components 則把 mask 轉成可以量測與判斷的證據。

## 檔案內容

```text
05_contours_and_components/
├── README.md
├── README_zh.md
├── contours_and_components.ipynb
├── contours_and_components_zh.ipynb
└── outputs/
    └── 05_contours_and_components/
```

## 主要 Notebook

英文版 notebook 是 GitHub 主要展示版本：

```text
contours_and_components.ipynb
```

繁體中文版 notebook 為：

```text
contours_and_components_zh.ipynb
```

## 涵蓋主題

- Mask 與 boundary 的概念
- Binary mask 作為物件量測的輸入
- 量測前的 progressive mask cleanup
- 使用 `cv2.findContours` 進行 contour extraction
- 使用 `cv2.connectedComponentsWithStats` 進行 connected component analysis
- Boundary-based 與 region-based 分析差異
- Contour retrieval modes 與 hierarchy
- Contour approximation 與點數簡化
- Bounding boxes、centroids、area、perimeter、circularity
- 使用量測特徵進行 shape filtering
- 檢測式影像處理流程總結

## 如何執行

安裝必要套件：

```bash
pip install opencv-python scikit-image matplotlib numpy pandas jupyter
```

開啟 notebook：

```bash
jupyter notebook contours_and_components.ipynb
```

或使用 JupyterLab / VS Code 執行。

## 預期輸出

Notebook 會將輸出影像與 CSV 表格儲存在：

```text
outputs/05_contours_and_components/
```

ZIP 中已經包含產生好的輸出檔案，可以直接檢查結果。

## 工程重點

Contours 偏向 boundary-oriented。  
Connected components 偏向 region-oriented。

兩者都很有用，但回答的問題不同。

實務判斷可以這樣想：

- 如果任務重點是計算與量測分離的前景區域，connected components 通常更直覺。
- 如果任務重點是邊界幾何、周長、形狀、階層或近似輪廓，contours 通常更適合。
