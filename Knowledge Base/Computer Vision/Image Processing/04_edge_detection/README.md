# 04 Edge Detection

This folder contains the fourth part of the Computer Vision / Image Processing learning series.

This section records the learning and implementation notes for edge detection from an engineering perspective.  
The focus is not only on applying OpenCV functions, but also on understanding what each method is measuring, what kind of result it produces, and how that result can be used in a practical image-processing pipeline.

The notebook uses real example images from `skimage.data` and includes pre-generated output images for inspection.

## Files

```text
04_edge_detection/
├── README.md
├── README_zh.md
├── edge_detection.ipynb
├── edge_detection_zh.ipynb
└── outputs/
    └── 04_edge_detection/
```

## Main Notebook

Use the English notebook as the main GitHub-facing version:

```text
edge_detection.ipynb
```

The Traditional Chinese version is provided as:

```text
edge_detection_zh.ipynb
```

## Topics Covered

- What an edge represents in image processing
- First derivative vs. second derivative intuition
- How kernel design affects convolution-based edge detectors
- Sobel as a directional gradient operator with built-in smoothing
- Scharr as an improved 3x3 gradient operator
- Difference-map comparison between Sobel and Scharr
- Laplacian as second-order local-change detection
- Why Laplacian is sensitive to noise and texture
- Canny as a full edge-detection pipeline
- Canny threshold sensitivity using real coin images
- Edge map to contour extraction
- Engineering notes for selecting edge detection methods

## How to Run

Install the required packages:

```bash
pip install opencv-python scikit-image matplotlib numpy jupyter
```

Open the notebook:

```bash
jupyter notebook edge_detection.ipynb
```

or run it in JupyterLab / VS Code.

## Expected Outputs

The notebook saves output images under:

```text
outputs/04_edge_detection/
```

The ZIP already includes generated output images so the results can be reviewed directly.

## Engineering Focus

Different edge detectors are not just different function names.

For convolution-based methods, the kernel defines what kind of local change is measured.  
For Canny, the algorithm is a multi-stage pipeline that uses gradient information, thinning, double thresholds, and edge-linking logic.

A good edge map is not the one with the most edges.  
A good edge map is the one that preserves useful boundaries for the next step.
