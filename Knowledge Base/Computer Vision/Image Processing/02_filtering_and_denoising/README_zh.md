# 02 Filtering and Denoising

這個資料夾是 Image Processing 學習系列的第二份 notebook。

目標是理解常見 filters 如何降低雜訊，以及它們在過程中會破壞哪些影像細節。

## Objective

練習基礎去雜訊方法，並比較它們在不同雜訊類型下的行為。

這份 notebook 聚焦：

- Gaussian noise
- Salt-and-pepper noise
- Gaussian blur
- Median filtering
- Bilateral filtering
- 視覺比較、局部放大比較與 difference maps

## Main Notebook

```text
filtering_and_denoising.ipynb
```

這份 notebook 包含說明、可執行程式碼、視覺比較、參數比較、簡單量化檢查與輸出影像保存。

## Directory Structure

```text
02_filtering_and_denoising/
│
├── README.md
├── filtering_and_denoising.ipynb
└── outputs/
    └── 02_filtering_and_denoising/
```

`outputs/` 資料夾會在執行 notebook 後自動產生。

## Tools Used

| Tool | Purpose |
|---|---|
| OpenCV | Gaussian、median、bilateral filtering 與影像保存 |
| scikit-image | 內建灰階範例影像來源 |
| NumPy | 雜訊生成、陣列操作與 PSNR 計算 |
| Matplotlib | 影像視覺化 |
| pathlib | 輸出路徑管理 |

## How to Run

安裝需要的套件：

```bash
pip install opencv-python scikit-image matplotlib numpy jupyterlab ipykernel
```

在 VSCode 中開啟 notebook：

```text
filtering_and_denoising.ipynb
```

接著從上到下執行所有 cells。

## Expected Outputs

執行 notebook 後，結果影像會儲存在：

```text
outputs/02_filtering_and_denoising/
```

輸出內容包含：

- clean reference image
- noisy images
- denoised results
- difference maps

## Key Learning Outcome

完成這份 notebook 後，應該理解一個核心觀念：

```text
去雜訊不是單純移除雜訊，而是在選擇哪些影像細節可以被犧牲。
```

Gaussian blur、median filtering 和 bilateral filtering 都能降低雜訊，但它們破壞影像的方式並不相同。

## Next Step

接續到：

```text
../03_thresholding/thresholding.ipynb
```

下一份 notebook 會聚焦在透過 thresholding 將灰階影像轉成 binary masks。
