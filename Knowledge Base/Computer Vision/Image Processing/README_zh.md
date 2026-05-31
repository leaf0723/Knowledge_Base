# Image Processing

此目錄整理的是一系列以 Python、OpenCV、NumPy、Matplotlib 與 scikit-image 為基礎的 Image Processing 實作筆記。

這個系列的重點不是單純呼叫影像處理 API，而是理解每一個操作實際改變了影像中的什麼資訊、可能破壞什麼細節，以及處理結果如何支撐後續的檢測、分割、定位或量測任務。

## 目錄位置

```text
Knowledge Base/
└── Computer Vision/
    └── Image Processing/
        ├── README.md
        ├── README_zh.md
        ├── 01_image_basics/
        ├── 02_filtering_and_denoising/
        ├── 03_thresholding_and_morphlogy/
        ├── 04_edge_detection/
        ├── 05_contours_and_components/
        └── 06_localization_and_matching/
```

> 注意：`03_thresholding_and_morphlogy` 依照目前 GitHub repo 中的實際資料夾名稱保留。

## 系列結構

| Part | Folder | English Notebook | 中文 Notebook | Focus |
|---|---|---|---|---|
| 01 | `01_image_basics/` | `image_basics.ipynb` | `image_basics_zh.ipynb` | 影像陣列結構、色彩空間、通道檢查、RGB/BGR 顯示差異與基礎結果儲存 |
| 02 | `02_filtering_and_denoising/` | `filtering_and_denoising.ipynb` | `filtering_and_denoising_zh.ipynb` | 雜訊模擬、濾波方法、去噪取捨、局部放大比較、差異圖與 PSNR 參考 |
| 03 | `03_thresholding_and_morphlogy/` | `thresholding_and_morphology.ipynb` | `thresholding_and_morphology_zh.ipynb` | 閾值處理、二值 mask、形態學操作、kernel size 影響與檢測式 mask 修正流程 |
| 04 | `04_edge_detection/` | `edge_detection.ipynb` | `edge_detection_zh.ipynb` | 一階與二階導數邊緣檢測、Sobel、Scharr、Laplacian、Canny 與 edge map 判讀 |
| 05 | `05_contours_and_components/` | `contours_and_components.ipynb` | `contours_and_components_zh.ipynb` | mask 清理、輪廓、連通元件、幾何量測與基於形狀特徵的篩選 |
| 06 | `06_localization_and_matching/` | `localization_and_matching.ipynb` | `localization_and_matching_zh.ipynb` | 物件定位、ROI 擷取、模板匹配、多尺度匹配、ORB 特徵匹配、Homography 與可靠性分析 |

## 使用方式

建議依照 01 到 06 的順序閱讀與執行。

整體學習路線如下：

```text
01 Image Basics
→ 02 Filtering and Denoising
→ 03 Thresholding and Morphology
→ 04 Edge Detection
→ 05 Contours and Components
→ 06 Localization and Matching
```

這個順序是有意義的。後面的主題會依賴前面的處理概念，例如 contour extraction 依賴 mask 品質，而 localization 的可信度通常需要區域、邊界或特徵證據來支撐。

## 環境安裝

此系列共用的主要套件如下：

```bash
pip install opencv-python scikit-image matplotlib numpy pandas jupyterlab ipykernel
```

安裝後，可使用 VS Code、JupyterLab 或 Jupyter Notebook 開啟指定 notebook。

例如英文版：

```bash
jupyter notebook 01_image_basics/image_basics.ipynb
```

或中文版：

```bash
jupyter notebook 01_image_basics/image_basics_zh.ipynb
```

## 預期輸出

每個 notebook 都會將產生的圖像或分析結果儲存在各自的 `outputs/` 目錄中。

主要輸出結構如下：

```text
01_image_basics/outputs/01_image_basics/
02_filtering_and_denoising/outputs/02_filtering_and_denoising/
03_thresholding_and_morphlogy/outputs/03_thresholding_and_morphology/
04_edge_detection/outputs/04_edge_detection/
05_contours_and_components/outputs/05_contours_and_components/
06_localization_and_matching/outputs/06_localization_and_matching/
```

這些輸出圖不是裝飾用途，而是用來比較方法、檢查局部差異、驗證中間結果，並支撐工程式觀察。

## 工程重點

此目錄的核心觀念是：影像處理結果應該根據證據判斷，而不是根據函式名稱判斷。

有用的結果不一定是看起來最乾淨的影像，而是能保留下一步任務所需資訊的結果。

例如：

- 去噪濾波可以降低雜訊，但也可能破壞邊界或細小結構。
- threshold mask 看似簡單，但可靠度會受到光照、對比與前處理影響。
- morphology 可以清理 false positives，但也可能移除較細或較弱的前景區域。
- edge map 不是邊緣越多越好；過多紋理邊緣反而可能讓後續輪廓分析更困難。
- localization 結果需要由視覺對齊、幾何一致性或可量測的 response score 來支撐。

因此，此系列重視方法比較、中間結果保存與實務判斷，而不是只展示最後一張結果圖。

## 作品集價值

此目錄是 Computer Vision 基礎能力的作品集展示。

它呈現的能力包括：

- 在處理前檢查影像資料格式；
- 建立可重現的影像處理流程；
- 以視覺與數值方式比較不同方法；
- 保存中間結果與最終輸出，方便檢查與回顧；
- 清楚說明方法的取捨與限制；
- 將低階影像操作連接到檢測、分割、量測與定位任務。

Notebook 是主要技術內容；此 README 只作為整個 Image Processing 目錄的入口文件與學習路線說明。

## 語言版本

每個主題都提供英文版與繁體中文版。

- `README.md`：英文入口文件
- `README_zh.md`：繁體中文入口文件
- `*.ipynb`：英文 notebook
- `*_zh.ipynb`：繁體中文 notebook

英文版作為 GitHub 主要展示版本，繁體中文版則作為同步對照與學習版本。
