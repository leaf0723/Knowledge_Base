# 02 Filtering and Denoising

This folder contains the second notebook in the Image Processing learning series.

The goal is to understand how common filters reduce noise, and what image details they damage in the process.

## Objective

Practice basic denoising methods and compare their behavior under different noise types.

This notebook focuses on:

- Gaussian noise
- Salt-and-pepper noise
- Gaussian blur
- Median filtering
- Bilateral filtering
- visual comparison, zoomed comparison, and difference maps

## Main Notebook

```text
filtering_and_denoising.ipynb
```

The notebook includes explanation, executable code, visual comparison, parameter comparison, quantitative checking, and saved output images.

## Directory Structure

```text
02_filtering_and_denoising/
│
├── README.md
├── filtering_and_denoising.ipynb
└── outputs/
    └── 02_filtering_and_denoising/
```

The `outputs/` folder is generated after running the notebook.

## Tools Used

| Tool | Purpose |
|---|---|
| OpenCV | Gaussian, median, bilateral filtering, image saving |
| scikit-image | Built-in grayscale sample image |
| NumPy | Noise generation, array operation, PSNR calculation |
| Matplotlib | Image visualization |
| pathlib | Output path management |

## How to Run

Install the required packages:

```bash
pip install opencv-python scikit-image matplotlib numpy jupyterlab ipykernel
```

Open the notebook in VSCode:

```text
filtering_and_denoising.ipynb
```

Then run all cells from top to bottom.

## Expected Outputs

After running the notebook, result images will be saved under:

```text
outputs/02_filtering_and_denoising/
```

The saved outputs include:

- clean reference image
- noisy images
- denoised results
- difference maps

## Key Learning Outcome

After completing this notebook, the reader should understand this core idea:

```text
Denoising is not just removing noise. It is choosing which image details are acceptable to lose.
```

Gaussian blur, median filtering, and bilateral filtering all reduce noise, but they do not damage the image in the same way.

## Next Step

Continue to:

```text
../03_thresholding/thresholding.ipynb
```

The next notebook focuses on converting grayscale images into binary masks through thresholding.
