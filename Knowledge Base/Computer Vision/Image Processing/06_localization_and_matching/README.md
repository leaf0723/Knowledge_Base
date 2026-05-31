# 06 Localization and Matching

This folder contains the sixth part of the Computer Vision / Image Processing learning series.

This section focuses on object localization in industrial-style inspection images. The notebook emphasizes not only how to produce a location, but also how to judge whether that location is supported by reliable visual, geometric, or numerical evidence.

## Files

```text
06_localization_and_matching/
├── README.md
├── README_zh.md
├── localization_and_matching.ipynb
├── localization_and_matching_zh.ipynb
└── outputs/
    └── 06_localization_and_matching/
```

## Main Notebook

Use the English notebook as the main GitHub-facing version:

```text
localization_and_matching.ipynb
```

The Traditional Chinese version is provided as:

```text
localization_and_matching_zh.ipynb
```

## Topics Covered

- Localization concept and image coordinates
- Bounding boxes, center points, and ROI cropping
- Mask-based localization
- Contour-based localization
- Template matching and response maps
- Multi-scale template matching
- ORB feature-based matching
- Homography-based localization
- Reliability analysis
- Failure case analysis
- Method selection guide
- Final engineering pipeline

## How to Run

```bash
pip install opencv-python matplotlib numpy pandas jupyter
jupyter notebook localization_and_matching.ipynb
```

## Expected Outputs

Generated figures are saved under:

```text
outputs/06_localization_and_matching/
```

The ZIP already includes generated output images for direct inspection.
