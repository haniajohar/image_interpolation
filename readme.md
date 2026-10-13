# Spatial-Domain Image Processing Lab

This repository/notebook contains a comprehensive exploration of digital image processing techniques in the spatial domain using Python, OpenCV, NumPy, and Matplotlib. The practical laboratory is divided into four principal processing domains spanning nine distinct tasks.

## 📋 Table of Contents
1. [Pixel Count, Dimensionality, and Data Types](#task-1)
2. [Color Space Transformations (RGB to Grayscale)](#task-2)
3. [Image Binarization (Thresholding)](#task-3)
4. [Spatial Low-Pass Filtering (Gaussian Blur)](#task-4)
5. [Dynamic Range Adjustments (Logarithmic Transformations)](#task-5)
6. [Spatial Resizing and Interpolation](#task-6)
7. [Histogram Analysis & Equalization](#task-7)
8. [Affine Transformations & Interpolation Comparisons](#task-8)
9. [Change Detection, Connected-Component Analysis & ROI Masking](#task-9)

---

## 🛠️ Tasks & Methodologies

### <a name="task-1"></a>Task 1: Pixel Count, Dimensionality, and Data Types
* **Methodology**: Read uncompressed raster images using OpenCV, unpacking `img.shape` and `img.size` to understand multi-dimensional matrix dimensions and spatial memory layouts.
* **Learning Outcome**: Mastered how digital image representations function as continuous 3D matrices in memory (`H x W x C`), verifying how channels dictate overall byte size.

### <a name="task-2"></a>Task 2: Color Space Transformations
* **Methodology**: Implement standard weighted luminance conversion ($	ext{ITU-R Equation: } Y = 0.299R + 0.587G + 0.114B$) to map chromatic information into a single 2D grayscale intensity channel.
* **Learning Outcome**: Learned how human photoreceptor sensitivity (highest for green wavelengths) drives conversion coefficients, resulting in $66.7\%$ reduction in memory footprint while preserving perceptual structure.

### <a name="task-3"></a>Task 3: Image Binarization
* **Methodology**: Apply global thresholding ($T=127$) to convert continuous-tone grayscale images into 1-bit binary representations ($\{0, 255\}$).
* **Learning Outcome**: Understood the trade-offs of global thresholding and how binarization strips textures to isolate structural contours and object silhouettes.

### <a name="task-4"></a>Task 4: Spatial Low-Pass Filtering
* **Methodology**: Apply Gaussian filters with varying kernel sizes ($5\times5$ and $15\times15$) and standard deviations ($\sigma$) to perform 2D spatial convolutions.
* **Learning Outcome**: Discovered how spatial low-pass filtering attenuates high-frequency details (textures, noise, sharp borders) to achieve smooth local pixel transitions.

### <a name="task-5"></a>Task 5: Dynamic Range Adjustments
* **Methodology**: Implement logarithmic transformations ($s = c \cdot \ln(1 + r)$) to expand low-intensity dark gray tones while compressing high-intensity highlights.
* **Learning Outcome**: Learned to apply non-linear point-processing techniques to enhance dynamic range and reveal hidden features in dark shadows.

### <a name="task-6"></a>Task 6: Spatial Resizing and Interpolation
* **Methodology**: Downsample an image by $50\%$, then upsample it back to original dimensions using Bilinear interpolation.
* **Learning Outcome**: Demonstrated the irreversibility of spatial downsampling (loss of high-frequency data) and analyzed interpolation-induced softening.

### <a name="task-7"></a>Task 7: Histogram Analysis & Equalization
* **Methodology**: Linearize the cumulative distribution function (CDF) across the entire intensity range $[0, 255]$ to equalize global image contrast.
* **Learning Outcome**: Mastered intensity histogram evaluation. Examined how contrast enhancement can aid or hinder object segmentation due to noise amplification.

### <a name="task-8"></a>Task 8: Affine Transformations
* **Methodology**: Chain downscaling ($75\%$), rotation ($25^\circ$), and translation ($dx=+40, dy=+20$) into a single 2D warp-affine matrix. Evaluate Nearest-Neighbor (`INTER_NEAREST`), Bilinear (`INTER_LINEAR`), and Bicubic (`INTER_CUBIC`) interpolations.
* **Learning Outcome**: Gained structural insight into compound geometric transforms, analyzing spatial aliasing (staircasing) versus mathematical smooth fitting.

### <a name="task-9"></a>Task 9: Change Detection & ROI Masking
* **Methodology**: Perform pixel-wise absolute frame difference subtraction ($|I_1 - I_2|$), apply morphological opening, isolate change with 8-way connected-component labeling, and gate the resulting detection using a bitwise AND Region of Interest (ROI) mask.
* **Learning Outcome**: Built a complete motion-tracking and change-detection pipeline, incorporating differential masking, spatial grouping, and logical ROI isolation.

---

## 💻 Tech Stack
* **Language**: Python 3
* **Libraries**: OpenCV (`opencv-python`), NumPy, Matplotlib
