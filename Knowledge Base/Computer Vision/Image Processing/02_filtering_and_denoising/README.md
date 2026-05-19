# 02 Filtering and Denoising

This folder contains the second notebook in the Image Processing practice series.

It focuses on basic filtering and denoising methods, with emphasis on visual comparison, local detail preservation, and practical trade-offs.

## Objective

Compare common denoising filters and understand what each method removes, what it damages, and when it is suitable.

## Main Files

| File | Description |
|---|---|
| `README.md` | English directory entry document |
| `README_zh.md` | Traditional Chinese directory entry document |
| `filtering_and_denoising.ipynb` | English notebook |
| `filtering_and_denoising_zh.ipynb` | Traditional Chinese notebook |

## Directory Structure

```text
02_filtering_and_denoising/
├── README.md
├── README_zh.md
├── filtering_and_denoising.ipynb
├── filtering_and_denoising_zh.ipynb
└── outputs/
    └── 02_filtering_and_denoising/
```

The `outputs/02_filtering_and_denoising/` folder is generated when the notebook is executed.

## What You Will Learn

- Create Gaussian noise and salt-and-pepper noise
- Apply Gaussian blur, median filtering, and bilateral filtering
- Compare filtering results under different noise types
- Use zoomed crops to inspect local detail damage
- Use difference maps to visualize what changed
- Use PSNR as a simple numerical reference
- Save output images for later inspection

## How to Run

Install the required packages:

```bash
pip install opencv-python scikit-image matplotlib numpy jupyterlab ipykernel
```

Open one of the notebooks in VSCode and run all cells from top to bottom:

```text
filtering_and_denoising.ipynb
filtering_and_denoising_zh.ipynb
```

## Expected Outputs

After running the notebook, outputs are saved under:

```text
outputs/02_filtering_and_denoising/
```

Main output files:

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

## Key Outcome

The core outcome of this folder is understanding that denoising is always a trade-off: removing noise often means damaging edges, textures, or small structures.

## Next Step

Continue to:

```text
../03_thresholding/thresholding.ipynb
```

Traditional Chinese version:

```text
../03_thresholding/thresholding_zh.ipynb
```
