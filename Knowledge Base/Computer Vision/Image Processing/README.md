# Image Processing

This directory contains a hands-on Image Processing learning series for building practical Computer Vision foundations with Python, OpenCV, NumPy, Matplotlib, and scikit-image.

The focus of this series is not only to call image-processing APIs, but to understand what each operation changes in the image, what information may be damaged, and how the result can support later inspection, segmentation, localization, or measurement tasks.

## Directory Position

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

> Note: the folder name `03_thresholding_and_morphlogy` follows the current repository path.

## Series Structure

| Part | Folder | Main Notebook | Traditional Chinese Notebook | Focus |
|---|---|---|---|---|
| 01 | `01_image_basics/` | `image_basics.ipynb` | `image_basics_zh.ipynb` | Image array structure, color spaces, channel inspection, RGB/BGR handling, and basic result saving |
| 02 | `02_filtering_and_denoising/` | `filtering_and_denoising.ipynb` | `filtering_and_denoising_zh.ipynb` | Noise simulation, filtering methods, denoising trade-offs, zoomed comparison, difference maps, and PSNR reference |
| 03 | `03_thresholding_and_morphlogy/` | `thresholding_and_morphology.ipynb` | `thresholding_and_morphology_zh.ipynb` | Thresholding, binary masks, morphology, kernel-size effects, and inspection-style mask refinement |
| 04 | `04_edge_detection/` | `edge_detection.ipynb` | `edge_detection_zh.ipynb` | First- and second-derivative edge detection, Sobel, Scharr, Laplacian, Canny, and edge-map interpretation |
| 05 | `05_contours_and_components/` | `contours_and_components.ipynb` | `contours_and_components_zh.ipynb` | Mask cleanup, contours, connected components, geometric measurements, and shape-based filtering |
| 06 | `06_localization_and_matching/` | `localization_and_matching.ipynb` | `localization_and_matching_zh.ipynb` | Object localization, ROI extraction, template matching, multi-scale matching, ORB feature matching, homography, and reliability analysis |

## How to Use This Series

Open the notebooks in order from Part 01 to Part 06.

The sequence is designed to move from image representation to practical object localization:

```text
01 Image Basics
→ 02 Filtering and Denoising
→ 03 Thresholding and Morphology
→ 04 Edge Detection
→ 05 Contours and Components
→ 06 Localization and Matching
```

This order matters because later topics depend on earlier outputs. For example, contour extraction depends on mask quality, and localization becomes more reliable when the candidate region, boundary, or feature evidence is already understood.

## Environment Setup

Install the common packages used across the series:

```bash
pip install opencv-python scikit-image matplotlib numpy pandas jupyterlab ipykernel
```

Then open the target notebook in VS Code, JupyterLab, or Jupyter Notebook.

Example:

```bash
jupyter notebook 01_image_basics/image_basics.ipynb
```

or, for the Traditional Chinese version:

```bash
jupyter notebook 01_image_basics/image_basics_zh.ipynb
```

## Expected Outputs

Each notebook saves generated figures or analysis results under its own `outputs/` directory.

Typical output structure:

```text
01_image_basics/outputs/01_image_basics/
02_filtering_and_denoising/outputs/02_filtering_and_denoising/
03_thresholding_and_morphlogy/outputs/03_thresholding_and_morphology/
04_edge_detection/outputs/04_edge_detection/
05_contours_and_components/outputs/05_contours_and_components/
06_localization_and_matching/outputs/06_localization_and_matching/
```

The output images are part of the learning record. They are used to compare methods, inspect local differences, verify intermediate results, and support engineering-style observations.

## Engineering Focus

The key idea behind this directory is that image processing should be judged by evidence, not by function names.

A useful result is not simply the cleanest-looking image. A useful result is one that preserves the information needed for the next step.

Examples:

- A denoising filter may remove noise, but it may also damage edges or small structures.
- A threshold mask may look simple, but its reliability depends on illumination, contrast, and preprocessing.
- A morphology operation may clean false positives, but it may also remove thin or weak foreground regions.
- An edge map with many edges is not necessarily better; it may contain texture noise that makes later contour extraction harder.
- A localization result should be supported by visual alignment, geometric consistency, or a measurable response score.

This series therefore emphasizes comparison, intermediate outputs, and practical judgment instead of only showing final results.

## Portfolio Value

This directory is intended to demonstrate practical Computer Vision fundamentals for portfolio presentation.

It shows the ability to:

- inspect image data before processing;
- design reproducible image-processing workflows;
- compare multiple methods visually and numerically;
- save intermediate and final outputs for review;
- explain method trade-offs clearly;
- connect low-level image operations to inspection, segmentation, measurement, and localization tasks.

The notebooks are the main technical content. This README only provides the directory-level entry point and learning route.

## Language Versions

Each topic provides both English and Traditional Chinese versions.

- `README.md`: English entry document
- `README_zh.md`: Traditional Chinese entry document
- `*.ipynb`: English notebook
- `*_zh.ipynb`: Traditional Chinese notebook

The English version is used as the main GitHub-facing version, while the Traditional Chinese version is kept for parallel review and learning.
