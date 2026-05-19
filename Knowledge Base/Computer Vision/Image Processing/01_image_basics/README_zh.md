# 01 Image Basics

這個資料夾是 Image Processing 學習系列的第一份 notebook。

目標是在進入 filtering、thresholding、morphology、edge detection 和 defect inspection 之前，先搞清楚影像在 Python 電腦視覺流程中到底是怎麼被表示與處理的。

## Objective

建立套用任何影像處理方法前都應該具備的基本工作習慣：

- 檢查影像 shape、資料型態與數值範圍
- 理解灰階圖與彩色圖的資料表示方式
- 區分 RGB 與 BGR channel order
- 正確進行基本 color space conversion
- 在 notebook 中正確顯示影像
- 建立簡單 mask
- 保存中間結果以利 debug

## Main Notebook

```text
image_basics.ipynb
```

這份 notebook 包含說明、可執行程式碼、視覺化結果與中間輸出影像。

## Directory Structure

```text
01_image_basics/
│
├── README.md
├── image_basics.ipynb
└── outputs/
    └── 01_image_basics/
```

`outputs/` 資料夾會在執行 notebook 後自動產生。

## Tools Used

| Tool | Purpose |
|---|---|
| OpenCV | 影像處理與色彩空間轉換 |
| scikit-image | 內建範例影像來源 |
| NumPy | 影像陣列檢查與 mask 操作 |
| Matplotlib | 影像視覺化 |
| pathlib | 輸出路徑管理 |

## How to Run

安裝需要的套件：

```bash
pip install opencv-python scikit-image matplotlib numpy jupyterlab ipykernel
```

在 VSCode 中開啟 notebook：

```text
image_basics.ipynb
```

接著從上到下執行所有 cells。

## Expected Outputs

執行 notebook 後，結果影像會儲存在：

```text
outputs/01_image_basics/
```

輸出內容包含：

- 原始 RGB 影像
- 灰階影像
- saturation mask
- 高 saturation 區域結果

## Key Learning Outcome

完成這份 notebook 後，應該理解一個核心觀念：

```text
影像就是陣列，而多數影像處理問題都從正確理解這個陣列開始。
```

這包含在套用任何演算法之前，先確認影像尺寸、channel order、pixel value range 與顯示方式。

## Next Step

接續到：

```text
../02_filtering_and_denoising/filtering_and_denoising.ipynb
```

下一份 notebook 會聚焦在 noise removal 與 smoothing methods，包含 Gaussian blur、median filtering 和 bilateral filtering。
