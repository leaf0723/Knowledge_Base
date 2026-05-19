# 02 濾波與降噪

這個資料夾是 Image Processing 練習系列的第二個單元。

內容聚焦在基本 filtering 與 denoising 方法，重點放在視覺比較、局部細節保留，以及實務上的取捨判斷。

## 目標

比較常見降噪濾波方法，理解每個方法移除了什麼、破壞了什麼，以及適合用在哪些情境。

## 主要檔案

| 檔案 | 說明 |
|---|---|
| `README.md` | 英文版目錄入口文件 |
| `README_zh.md` | 繁體中文版目錄入口文件 |
| `filtering_and_denoising.ipynb` | 英文版 notebook |
| `filtering_and_denoising_zh.ipynb` | 繁體中文版 notebook |

## 目錄結構

```text
02_filtering_and_denoising/
├── README.md
├── README_zh.md
├── filtering_and_denoising.ipynb
├── filtering_and_denoising_zh.ipynb
└── outputs/
    └── 02_filtering_and_denoising/
```

`outputs/02_filtering_and_denoising/` 會在執行 notebook 後產生。

## 學習重點

- 建立 Gaussian noise 與 salt-and-pepper noise
- 套用 Gaussian blur、median filtering 與 bilateral filtering
- 比較不同雜訊類型下的濾波結果
- 用局部放大圖觀察細節破壞
- 用差異圖觀察處理前後變化
- 使用 PSNR 作為簡單數值參考
- 保存輸出影像，方便後續檢查

## 執行方式

安裝必要套件：

```bash
pip install opencv-python scikit-image matplotlib numpy jupyterlab ipykernel
```

用 VSCode 開啟其中一個 notebook，並從上到下執行所有 cells：

```text
filtering_and_denoising.ipynb
filtering_and_denoising_zh.ipynb
```

## 預期輸出

執行後，輸出檔案會儲存在：

```text
outputs/02_filtering_and_denoising/
```

主要輸出檔案：

```text
01_clean_image.png
02_noisy_images_comparison.png
02_gaussian_noise.png
03_salt_pepper_noise.png
04_gaussian_noise_filter_comparison.png
05_salt_pepper_filter_comparison.png
06_zoomed_edge_comparison.png
07_difference_maps.png
08_gaussian_kernel_size_comparison.png
09_gaussian_blur_on_gaussian_noise.png
10_median_filter_on_gaussian_noise.png
11_bilateral_filter_on_gaussian_noise.png
12_gaussian_blur_on_salt_pepper_noise.png
13_median_filter_on_salt_pepper_noise.png
14_bilateral_filter_on_salt_pepper_noise.png
```

## 核心收穫

這個資料夾的核心目標是理解：降噪永遠是取捨。移除雜訊的同時，通常也會破壞邊緣、紋理或小型結構。

## 下一步

繼續到：

```text
../03_thresholding_and_morphology/thresholding.ipynb
```

繁體中文版：

```text
../03_thresholding_and_morphology/thresholding_zh.ipynb
```
