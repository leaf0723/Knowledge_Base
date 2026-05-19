# 01 Image Basics

This folder contains the first notebook in the Image Processing learning series.

The goal is to understand how images are represented and handled in Python-based computer vision workflows before moving into filtering, thresholding, morphology, edge detection, and defect inspection.

## Objective

Build the basic working habits needed before applying any image processing algorithm:

- inspect image shape, data type, and value range
- understand grayscale and color image representation
- distinguish RGB and BGR channel order
- convert basic color spaces correctly
- display images correctly in notebooks
- create simple masks
- save intermediate results for debugging

## Main Notebook

```text
image_basics.ipynb
```

The notebook includes explanation, executable code, visual outputs, and saved intermediate images.

## Directory Structure

```text
01_image_basics/
│
├── README.md
├── image_basics.ipynb
└── outputs/
    └── 01_image_basics/
```

The `outputs/` folder is generated after running the notebook.

## Tools Used

| Tool | Purpose |
|---|---|
| OpenCV | Image processing and color space conversion |
| scikit-image | Built-in sample image source |
| NumPy | Image array inspection and mask operation |
| Matplotlib | Image visualization |
| pathlib | Output path management |

## How to Run

Install the required packages:

```bash
pip install opencv-python scikit-image matplotlib numpy jupyterlab ipykernel
```

Open the notebook in VSCode:

```text
image_basics.ipynb
```

Then run all cells from top to bottom.

## Expected Outputs

After running the notebook, result images will be saved under:

```text
outputs/01_image_basics/
```

The saved outputs include:

- original RGB image
- grayscale image
- saturation mask
- high-saturation region result

## Key Learning Outcome

After completing this notebook, the reader should understand this core idea:

```text
An image is just an array, and most image processing problems begin with understanding the array correctly.
```

This includes checking image dimensions, channel order, pixel value range, and display behavior before applying any algorithm.

## Next Step

Continue to:

```text
../02_filtering_and_denoising/filtering_and_denoising.ipynb
```

The next notebook focuses on noise removal and smoothing methods, including Gaussian blur, median filtering, and bilateral filtering.
