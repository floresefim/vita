# Vita - Advanced Image Pixelization Algorithm

## Description
**Vita** is an advanced image pixelization algorithm that combines gradient processing, adaptive smoothing, and contrast enhancement techniques to achieve high-quality results. The algorithm enhances edge sharpness and smoothness of the image while minimizing pixelation artifacts.

## Formulas and Mathematical Foundations

### 1. **Pixelization Algorithm**

The main goal of pixelization is to replace each block of pixels with the averaged color of that block. We apply the following methods and mathematical formulas to enhance the quality of pixelization:

#### 1.1. **Gradients**

To improve sharpness and clarity in pixelization, gradients are used. The formula for calculating the gradient is as follows:

\[
G = G_x^2 + G_y^2
\]
where:
- \( G \) — gradient of the image,
- \( G_x \) — gradient along the x-axis,
- \( G_y \) — gradient along the y-axis.

**Where it's used**: In the `APA::process` method to improve edge sharpness.

**Purpose**: It helps to enhance edge sharpness and clarity, preventing blurring at the borders during pixelization.

#### 1.2. **Contrast**

For better image processing in low-contrast areas, we use the following formula to determine the contrast range of a pixel block:

\[
C = \max(P) - \min(P)
\]
where:
- \( C \) — contrast of the block,
- \( P \) — set of pixels in the block.

**Where it's used**: In the `APA::process` method to determine where aggressive smoothing is needed.

**Purpose**: Helps identify low-contrast areas and apply more aggressive filtering to avoid excessive blurring.

#### 1.3. **Adaptive Smoothing**

To improve averaging in low-contrast blocks, adaptive smoothing is applied to preserve smooth transitions between pixels:

\[
P' = (1 - \alpha) P_{\text{center}} + \alpha \times \text{avg}(P_{\text{neighbors}})
\]
where:
- \( P' \) — new pixel,
- \( P_{\text{center}} \) — central pixel of the block,
- \( P_{\text{neighbors}} \) — neighboring pixels,
- \( \alpha \) — adaptive smoothing coefficient,
- \( \text{avg}(P_{\text{neighbors}}) \) — average value of neighboring pixels.

**Where it's used**: In the `APA::process` method for smooth and high-quality averaging of low-contrast pixels.

**Purpose**: Allows smooth and high-quality averaging of pixels in blocks with low contrast, avoiding sharp transitions and improving image smoothness.

### 2. **Advantages of Vita**

**Vita** provides significantly better image quality compared to traditional algorithms for the following reasons:

- **Gradient Processing**: Using gradients to enhance sharpness and clarity at the edges prevents edge blurring that occurs in traditional pixelization methods and makes the image clearer.

- **Adaptive Smoothing**: Unlike classical methods that do not consider contrast differences across the image, **Vita** adapts the smoothing level based on the contrast, preserving more details in high-contrast areas while smoothing low-contrast blocks.

- **Contrast Enhancement**: Unlike classical pixelization algorithms that simply reduce the pixel count, **Vita** analyzes contrast between pixels and applies filtering where necessary, improving image details.

### 3. **Why Vita is Better Than Other Algorithms**

**Vita** is better than other pixelization algorithms like bilinear or bicubic interpolation for the following reasons:

- **Gradients for Edge Enhancement**: Traditional methods often blur the edges of the image, resulting in loss of detail. **Vita** uses gradients to preserve edge sharpness, significantly improving the visual appearance of the image.

- **Adaptive Smoothing**: Classical pixelization algorithms do not take contrast into account when processing pixel blocks. **Vita** adapts smoothing based on contrast, which helps retain more details in high-contrast areas and smoothly averages low-contrast blocks.

- **Optimization**: **Vita** uses optimizations, such as pre-calculating gradients and contrast for pixel blocks, allowing us to reduce processing time without sacrificing quality.

---

## How to Run

### 1. Clone the Repository

First, clone the repository:

```bash
git clone https://github.com/yourusername/vita.git
cd vita
```bash


### 2. Install Dependencies
Before running, you need to install all dependencies. Specifically, you need to install the SFML (Simple and Fast Multimedia Library) for graphics and user interface handling.

Linux (Ubuntu/Debian):

```bash
sudo apt-get update
sudo apt-get install libsfml-dev

Windows:
Download SFML from the official website: https://www.sfml-dev.org/download.php

macOS:

```bash
brew install sfml

### 3. Build Using Makefile
The project supports cross-platform build using the Makefile. To compile the project, use the following commands:

For Linux/macOS:

```bash
make

For Windows (using MinGW):

```bash
mingw32-make

### 4. Running the Application
After building, run the application with:

```bash
./vita

This will open a window where you can select an image, apply the pixelization algorithm, view progress, and save the result.
