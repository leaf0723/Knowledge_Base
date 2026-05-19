# 01 Image Basics

This folder contains the first notebook in the Image Processing practice series.

It focuses on the minimum image representation details required before moving into filtering, thresholding, morphology, edge detection, and defect inspection.

## Objective

Understand how images are represented, inspected, displayed, converted, and saved in a Python computer vision workflow.

## Main Files

| File | Description |
|---|---|
| `README.md` | English directory entry document |
| `README_zh.md` | Traditional Chinese directory entry document |
| `image_basics.ipynb` | English notebook |
| `image_basics_zh.ipynb` | Traditional Chinese notebook |

## Directory Structure

```text
01_image_basics/
├── README.md
├── README_zh.md
├── image_basics.ipynb
├── image_basics_zh.ipynb
└── outputs/
    └── 01_image_basics/
```

The `outputs/01_image_basics/` folder is generated when the notebook is executed.

## What You Will Learn

- Inspect image `shape`, `dtype`, and value range
- Understand grayscale and RGB image representation
- Split and visualize RGB channels
- Avoid RGB / BGR display mistakes
- Convert RGB images to grayscale and HSV
- Create a simple mask from the Saturation channel
- Save intermediate results for debugging

## How to Run

Install the required packages:

```bash
pip install opencv-python scikit-image matplotlib numpy jupyterlab ipykernel
```

Open one of the notebooks in VSCode and run all cells from top to bottom:

```text
image_basics.ipynb
image_basics_zh.ipynb
```

## Expected Outputs

After running the notebook, outputs are saved under:

```text
outputs/01_image_basics/
```

Main output files:

```text
01_original_rgb.png
02_grayscale.png
03_saturation_mask.png
04_high_saturation_regions.png
05_rgb_bgr_display_comparison.png
```

## Key Outcome

The core outcome of this folder is understanding that an image is an array, and most image processing problems should start by checking the array format before applying any algorithm.

## Next Step

Continue to:

```text
../02_filtering_and_denoising/filtering_and_denoising.ipynb
```

Traditional Chinese version:

```text
../02_filtering_and_denoising/filtering_and_denoising_zh.ipynb
```
