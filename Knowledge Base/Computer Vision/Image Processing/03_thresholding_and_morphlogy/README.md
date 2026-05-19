# 03 — Thresholding and Morphology

This folder contains the third part of the Computer Vision / Image Processing learning series.

This section focuses on binary segmentation using thresholding and mask refinement using morphological operations.  
The goal is to build a practical image processing workflow that can convert a grayscale image into measurable regions for inspection-style tasks.

## Files

```text
03_thresholding_and_morphology/
├── README.md
├── README_zh.md
├── thresholding_and_morphology.ipynb
└── thresholding_and_morphology_zh.ipynb
```

## Main Notebook

Use the English notebook as the main GitHub-facing version:

```text
thresholding_and_morphology.ipynb
```

The Traditional Chinese version is provided as:

```text
thresholding_and_morphology_zh.ipynb
```

## Topics Covered

This section covers:

- Global thresholding
- Threshold sensitivity comparison
- Otsu's thresholding
- Adaptive thresholding
- Morphological erosion and dilation
- Morphological opening and closing
- Kernel size comparison
- Connected component analysis
- Inspection-style pipeline visualization
- Output image saving for portfolio presentation

## How to Run

Install the required packages if they are not already available:

```bash
pip install opencv-python numpy matplotlib jupyter
```

Then open the notebook:

```bash
jupyter notebook thresholding_and_morphology.ipynb
```

or run it in JupyterLab / VS Code.

## Expected Outputs

After running the notebook, output images will be saved under:

```text
outputs/03_thresholding_and_morphology/
```

The generated outputs include:

- synthetic inspection image
- grayscale histogram
- global threshold mask
- threshold sensitivity comparison
- Otsu threshold mask
- adaptive threshold mask
- thresholding method comparison
- morphology operation results
- opening and closing kernel-size comparisons
- connected component detection result
- pipeline summary report image

## Learning Goals

After completing this part, the reader should understand:

1. How thresholding converts grayscale images into binary masks.
2. Why fixed thresholds are sensitive to lighting and contrast.
3. When Otsu's method is useful and when it may fail.
4. Why adaptive thresholding can help with uneven illumination.
5. How morphology cleans or repairs binary masks.
6. How kernel size affects false positives and false negatives.
7. How connected component analysis converts a binary mask into measurable regions.

## Engineering Notes

The key practical idea is:

> Thresholding creates the candidate mask. Morphology improves the mask. Component analysis turns the mask into measurable evidence.

This workflow is especially useful for traditional computer vision tasks such as AOI, defect detection, simple object segmentation, and rule-based inspection.

## Next Step

The next section can naturally move toward edge-based processing, such as Sobel, Laplacian, Canny edge detection, and contour extraction.