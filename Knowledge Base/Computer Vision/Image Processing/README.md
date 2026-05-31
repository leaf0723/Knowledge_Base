# Image Processing

This directory contains a portfolio-oriented image processing learning series built with Python, OpenCV, scikit-image, NumPy, Matplotlib, and Jupyter notebooks.

The purpose of this series is not only to demonstrate how to call image processing APIs. Each notebook focuses on a specific part of the traditional computer vision workflow and records what the method does, what problem it solves, what information it may damage, and how the result should be judged from an engineering perspective.

English notebooks are used as the main GitHub-facing version. Traditional Chinese notebooks are provided in parallel for detailed learning and review.

---

## Directory Structure

```text
Image Processing/
├── README.md
├── 01_image_basics/
│   ├── README.md
│   ├── README_zh.md
│   ├── image_basics.ipynb
│   ├── image_basics_zh.ipynb
│   └── outputs/
│       └── 01_image_basics/
├── 02_filtering_and_denoising/
│   ├── README.md
│   ├── README_zh.md
│   ├── filtering_and_denoising.ipynb
│   ├── filtering_and_denoising_zh.ipynb
│   └── outputs/
│       └── 02_filtering_and_denoising/
├── 03_thresholding_and_morphlogy/
│   ├── README.md
│   ├── README_zh.md
│   ├── thresholding_and_morphology.ipynb
│   ├── thresholding_and_morphology_zh.ipynb
│   └── outputs/
│       └── 03_thresholding_and_morphology/
├── 04_edge_detection/
│   ├── README.md
│   ├── README_zh.md
│   ├── edge_detection.ipynb
│   ├── edge_detection_zh.ipynb
│   └── outputs/
│       └── 04_edge_detection/
└── 05_contours_and_components/
    ├── README.md
    ├── README_zh.md
    ├── contours_and_components.ipynb
    ├── contours_and_components_zh.ipynb
    └── outputs/
        └── 05_contours_and_components/
```

---

## Learning Path

| Part | Topic | Main Notebook | Core Focus |
|---|---|---|---|
| 01 | Image Basics | `01_image_basics/image_basics.ipynb` | Image arrays, shape, dtype, value range, color spaces, channel inspection, and image saving |
| 02 | Filtering and Denoising | `02_filtering_and_denoising/filtering_and_denoising.ipynb` | Noise removal, detail preservation, filter comparison, zoomed inspection, difference maps, and PSNR reference |
| 03 | Thresholding and Morphology | `03_thresholding_and_morphlogy/thresholding_and_morphology.ipynb` | Binary masks, threshold sensitivity, Otsu, adaptive thresholding, morphology, kernel effects, and inspection-style mask refinement |
| 04 | Edge Detection | `04_edge_detection/edge_detection.ipynb` | First-order and second-order edge logic, Sobel, Scharr, Laplacian, Canny, threshold sensitivity, and edge-to-contour transition |
| 05 | Contours and Components | `05_contours_and_components/contours_and_components.ipynb` | Mask cleanup, contour extraction, connected components, object measurement, shape filtering, and region-based inspection logic |

Traditional Chinese versions are available by adding `_zh` to each notebook filename.

---

## What This Series Demonstrates

This series follows a practical image processing pipeline:

```text
Image representation
→ filtering and denoising
→ thresholding and mask generation
→ morphology and mask refinement
→ edge detection
→ contour or component-based measurement
```

The key idea is that traditional image processing is not a collection of isolated functions. Each step changes the information available to the next step.

For example, filtering can suppress noise, but it may also weaken edges or remove small details. Thresholding can produce a binary mask, but the mask may be unstable under uneven illumination. Morphology can clean the mask, but it can also shrink, expand, merge, or remove structures. Edge detection can reveal local intensity changes, but a dense edge map is not necessarily useful unless it supports the next task.

The notebooks are designed around this practical chain of decisions.

---

## Engineering Focus

The main engineering focus is result-based judgment.

Each notebook emphasizes:

- checking image format before processing
- comparing methods visually instead of trusting API names
- saving intermediate outputs for debugging and portfolio presentation
- using real or realistic images rather than only simplified examples
- inspecting local detail damage through zoomed regions
- using difference maps when visual comparison alone is not enough
- explaining the trade-off behind each method
- connecting each processing step to downstream tasks such as segmentation, measurement, or inspection

The core mindset is:

> A good image processing result is not the one that looks the cleanest. It is the one that preserves the information required by the next step.

---

## Main Dependencies

Install the common packages used across the notebooks:

```bash
pip install opencv-python scikit-image matplotlib numpy pandas jupyterlab ipykernel
```

Some notebooks may not use every package, but this environment covers the current image processing series.

---

## How to Run

Clone the repository and open the `Image Processing` directory:

```bash
git clone https://github.com/leaf0723/Knowledge_Base.git
cd "Knowledge_Base/Knowledge Base/Computer Vision/Image Processing"
```

Open the notebooks in VS Code, JupyterLab, or Jupyter Notebook.

Example:

```bash
jupyter lab
```

Then run each notebook from top to bottom.

Recommended order:

```text
01_image_basics/image_basics.ipynb
02_filtering_and_denoising/filtering_and_denoising.ipynb
03_thresholding_and_morphlogy/thresholding_and_morphology.ipynb
04_edge_detection/edge_detection.ipynb
05_contours_and_components/contours_and_components.ipynb
```

---

## Expected Outputs

Each notebook saves generated images, comparison figures, and related outputs under its own `outputs/` folder.

```text
01_image_basics/outputs/01_image_basics/
02_filtering_and_denoising/outputs/02_filtering_and_denoising/
03_thresholding_and_morphlogy/outputs/03_thresholding_and_morphology/
04_edge_detection/outputs/04_edge_detection/
05_contours_and_components/outputs/05_contours_and_components/
```

These outputs are part of the learning record. They make the result easier to inspect without relying only on notebook cell outputs.

---

## Portfolio Value

This section of the knowledge base is intended to support computer vision and image processing portfolio presentation.

It shows the ability to:

- build reproducible image processing notebooks
- explain basic computer vision methods clearly
- analyze visual results instead of only reporting that a method was applied
- compare method behavior under different image conditions
- reason about trade-offs such as noise removal versus detail preservation
- convert image processing results into measurable evidence
- organize bilingual technical material for GitHub presentation

This is especially relevant to tasks such as AOI, defect inspection, preprocessing pipelines, rule-based vision systems, and classical computer vision analysis before or alongside deep learning methods.

---

## Notes on Language Versions

The English files are the main GitHub-facing version.

The Traditional Chinese files are provided for detailed explanation and review:

```text
README_zh.md
*_zh.ipynb
```

Both versions are intended to describe the same workflow and technical content. When one version is updated, the corresponding version should be updated as well.

---

## Current Coverage

Current completed sections:

```text
01 Image Basics
02 Filtering and Denoising
03 Thresholding and Morphology
04 Edge Detection
05 Contours and Components
```

Potential next directions:

```text
06 Localization and Matching
07 Feature Extraction and Matching
08 Classical Defect Inspection Pipeline
09 Image Processing for AOI-style Applications
```

The current foundation already covers the core path from image representation to measurable object-level evidence.
