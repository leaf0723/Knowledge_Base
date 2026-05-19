# 05 Contours and Components

This folder contains the fifth part of the Computer Vision / Image Processing learning series.

This section records how binary masks can be converted into measurable objects using two common approaches:

- contour extraction
- connected component analysis

The main idea is:

> A mask describes which pixels belong to the foreground region.  
> A boundary describes the outline around that region.  
> Contours and connected components convert the mask into measurable evidence.

## Files

```text
05_contours_and_components/
├── README.md
├── README_zh.md
├── contours_and_components.ipynb
├── contours_and_components_zh.ipynb
└── outputs/
    └── 05_contours_and_components/
```

## Main Notebook

Use the English notebook as the main GitHub-facing version:

```text
contours_and_components.ipynb
```

The Traditional Chinese version is provided as:

```text
contours_and_components_zh.ipynb
```

## Topics Covered

- Mask and boundary concepts
- Binary mask as the input to object measurement
- Progressive mask cleanup before measurement
- Contour extraction using `cv2.findContours`
- Connected component analysis using `cv2.connectedComponentsWithStats`
- Difference between boundary-based and region-based analysis
- Contour retrieval modes and hierarchy
- Contour approximation and point reduction
- Bounding boxes, centroids, area, perimeter, and circularity
- Shape filtering from measured features
- Practical inspection-style pipeline summary

## How to Run

Install the required packages:

```bash
pip install opencv-python scikit-image matplotlib numpy pandas jupyter
```

Open the notebook:

```bash
jupyter notebook contours_and_components.ipynb
```

or run it in JupyterLab / VS Code.

## Expected Outputs

The notebook saves output images and CSV tables under:

```text
outputs/05_contours_and_components/
```

The ZIP already includes generated output files for direct inspection.

## Engineering Focus

Contours are boundary-oriented.  
Connected components are region-oriented.

Both are useful, but they answer different questions.

A practical rule is:

- Use connected components when the task is mainly to count and measure separated foreground regions.
- Use contours when boundary geometry, perimeter, shape, hierarchy, or approximation matters.
