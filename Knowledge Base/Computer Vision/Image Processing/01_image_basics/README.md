````markdown
# 01 Image Basics

This notebook documents the basic image representation concepts required before learning filtering, thresholding, morphology, edge detection, and defect inspection.

The focus is not on memorizing API calls.  
The focus is on understanding what an image actually is in code.

## Purpose

In image processing, many errors do not come from advanced algorithms.  
They come from basic misunderstandings:

- confusing RGB and BGR channel order
- displaying grayscale images with the wrong colormap
- processing an image without checking its `shape`, `dtype`, and value range
- assuming all images use the same pixel scale
- using HSV without understanding what each channel means

This notebook builds the minimum foundation needed to avoid those mistakes.

## What This Notebook Covers

### 1. Image as Array

An image is essentially a NumPy array.

- Grayscale image: `height × width`
- Color image: `height × width × channels`

In practice:

```text
image processing = array processing
pixel = number
color pixel = usually three numbers
```
````

### 2. Basic Image Inspection

Before processing any image, inspect:

```python
image.shape
image.dtype
image.min()
image.max()
```

These values tell us:

| Item              | Meaning                                |
| ----------------- | -------------------------------------- |
| `shape`           | Image dimension and number of channels |
| `dtype`           | How pixel values are stored            |
| `min()` / `max()` | Pixel value range                      |

A common image format is:

```text
dtype: uint8
range: 0 ~ 255
```

This means each pixel is stored as an 8-bit unsigned integer.

### 3. RGB Channel Structure

A normal RGB image contains three channels:

```text
R channel
G channel
B channel
```

Each channel is still a 2D intensity image.
The only difference is what that intensity represents.

The key idea:

```text
A color image is not a mysterious object.
It is three grayscale-like maps stacked together.
```

### 4. RGB to Grayscale

Grayscale conversion compresses color information into one intensity value.

Conceptually:

```text
RGB pixel  = [R, G, B]
Gray pixel = one brightness value
```

This is useful when the task depends more on structure, shape, edge, or intensity than color.

Examples:

- edge detection
- thresholding
- contour detection
- defect spot detection
- document processing

### 5. Matplotlib Grayscale Display

When displaying a 2D grayscale image with Matplotlib, use:

```python
plt.imshow(image, cmap="gray", vmin=0, vmax=255)
```

Without `cmap="gray"`, Matplotlib may display the image using a pseudocolor map.

The practical rule:

```text
If the image is 2D grayscale, explicitly set cmap="gray".
```

### 6. RGB vs BGR

This is one of the most common OpenCV mistakes.

- `skimage.data` images are usually RGB.
- `matplotlib.pyplot.imshow()` expects RGB for color images.
- `cv2.imread()` reads color images as BGR.

So if an image is loaded by OpenCV and displayed directly with Matplotlib, the colors may look wrong.

Correct workflow:

```python
img_bgr = cv2.imread("image.jpg")
img_rgb = cv2.cvtColor(img_bgr, cv2.COLOR_BGR2RGB)

plt.imshow(img_rgb)
```

The practical rule:

```text
OpenCV reads BGR.
Matplotlib displays RGB.
Convert before displaying.
```

### 7. HSV Color Space

HSV separates color into:

| Channel | Meaning                    |
| ------- | -------------------------- |
| H       | Hue: color type            |
| S       | Saturation: color strength |
| V       | Value: brightness          |

RGB describes color by mixing red, green, and blue.
HSV describes color in a way that is closer to how humans describe color.

For example:

```text
What color is it?
How strong is the color?
How bright is it?
```

This makes HSV useful for color-based segmentation.

Examples:

- extracting colorful regions
- detecting specific object colors
- separating brightness from color information
- creating simple masks based on saturation or brightness

### 8. Simple HSV-Based Mask

The notebook includes a small example using the Saturation channel.

The idea:

```text
High saturation = strong color
Low saturation  = closer to gray, white, or black
```

A simple threshold on the Saturation channel can already produce a useful mask.

This is not a complete detection system, but it shows the basic logic behind many classical image processing pipelines:

```text
convert color space
select useful channel
threshold
create mask
apply mask to original image
```

## Files

```text
01_image_basics/
│
├── image_basics.ipynb
├── README.md
└── outputs/
    └── 01_image_basics/
```

## Output Images

The notebook saves several intermediate results:

```text
01_original_rgb_saved_by_cv2.png
02_grayscale.png
03_saturation_mask.png
04_high_saturation_regions.png
```

Saving intermediate results is intentional.

In real image processing projects, when the final result is wrong, intermediate outputs help identify which step broke.

## Required Packages

```bash
pip install opencv-python scikit-image matplotlib numpy jupyterlab ipykernel
```

Main libraries used in this notebook:

| Library      | Usage                                            |
| ------------ | ------------------------------------------------ |
| OpenCV       | Color conversion, image processing, image saving |
| scikit-image | Built-in sample image                            |
| NumPy        | Array inspection and mask creation               |
| Matplotlib   | Image visualization                              |
| pathlib      | Output folder management                         |

## How to Run

Open the notebook in VSCode:

```text
image_basics.ipynb
```

Then run all cells from top to bottom.

Before running, make sure the Python environment has the required packages installed.

## Key Takeaways

The most important points from this notebook:

- An image is just an array.
- A grayscale image is usually `H × W`.
- A color image is usually `H × W × 3`.
- `shape`, `dtype`, and value range should be checked before processing.
- RGB and BGR are not the same.
- OpenCV uses BGR when reading images with `cv2.imread()`.
- Matplotlib expects RGB for color display.
- Grayscale images should be displayed with `cmap="gray"`.
- HSV is useful because it separates color type, color strength, and brightness.
- A mask is simply an image that marks which pixels should be kept or ignored.

## Engineering Note

The first habit in image processing should not be applying algorithms immediately.

The first habit should be:

```text
inspect the image
understand the data format
display it correctly
save intermediate results
```

If these basics are wrong, every later method becomes unreliable.

## Next Notebook

Next topic:

```text
02_filtering_and_denoising/filtering_and_denoising.ipynb
```

Recommended focus:

- Gaussian blur
- Median filter
- Bilateral filter
- Salt-and-pepper noise
- Gaussian noise
- Effect of filtering on edges

Core question for the next notebook:

```text
When we remove noise, what image details are we also damaging?
```

```
::contentReference[oaicite:1]{index=1}
```

[1]: https://scikit-image.org/docs/stable/user_guide/numpy_images.html?utm_source=chatgpt.com "4. A crash course on NumPy for images"
