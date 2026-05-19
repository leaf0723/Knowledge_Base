# 01 影像基礎

這個資料夾是 Image Processing 練習系列的第一個單元。

內容聚焦在進入 filtering、thresholding、morphology、edge detection 與 defect inspection 之前，必須先搞清楚的影像資料表示基礎。

## 目標

理解影像在 Python computer vision workflow 中如何被表示、檢查、顯示、轉換與保存。

## 主要檔案

| 檔案 | 說明 |
|---|---|
| `README.md` | 英文版目錄入口文件 |
| `README_zh.md` | 繁體中文版目錄入口文件 |
| `image_basics.ipynb` | 英文版 notebook |
| `image_basics_zh.ipynb` | 繁體中文版 notebook |

## 目錄結構

```text
01_image_basics/
├── README.md
├── README_zh.md
├── image_basics.ipynb
├── image_basics_zh.ipynb
└── outputs/
    └── 01_image_basics/
```

`outputs/01_image_basics/` 會在執行 notebook 後產生。

## 學習重點

- 檢查影像的 `shape`、`dtype` 與數值範圍
- 理解灰階影像與 RGB 彩色影像的資料表示
- 拆開並顯示 RGB channels
- 避免 RGB / BGR 顯示錯誤
- 將 RGB 影像轉成灰階與 HSV
- 從 Saturation channel 建立簡單 mask
- 保存中間結果，方便除錯

## 執行方式

安裝必要套件：

```bash
pip install opencv-python scikit-image matplotlib numpy jupyterlab ipykernel
```

用 VSCode 開啟其中一個 notebook，並從上到下執行所有 cells：

```text
image_basics.ipynb
image_basics_zh.ipynb
```

## 預期輸出

執行後，輸出檔案會儲存在：

```text
outputs/01_image_basics/
```

主要輸出檔案：

```text
01_original_rgb.png
02_grayscale.png
03_saturation_mask.png
04_high_saturation_regions.png
05_rgb_bgr_display_comparison.png
```

## 核心收穫

這個資料夾的核心目標是建立一個觀念：影像本質上就是陣列，因此任何影像處理方法開始前，都應該先確認資料格式是否正確。

## 下一步

繼續到：

```text
../02_filtering_and_denoising/filtering_and_denoising.ipynb
```

繁體中文版：

```text
../02_filtering_and_denoising/filtering_and_denoising_zh.ipynb
```
