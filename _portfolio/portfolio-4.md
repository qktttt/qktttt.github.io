---
title: "Automatic PBR Texture Reconstruction for Window Images"
excerpt: "Developed an unsupervised framework to estimate PBR texture maps (depth, normal, albedo) from real-world window images using viewpoint estimation and differentiable rendering. <br/><img src='/images/pbr_teaser.png'>"
collection: portfolio
---

Advised by Prof. John Femiani (Miami University， Department of Computer Science)


## Problem Statement

The goal of this project is to estimate Physically Based Rendering (PBR) materials from window images. Specifically, we aim to generate three canonical texture maps:
- **Depth Map**: Captures the distance of each part of the window from the camera.
- **Normal Map**: Represents surface orientations.
- **Albedo Map**: Encodes surface colors without lighting effects.

The challenge is to achieve this without using ground truth PBR textures, making it an unsupervised learning problem.

![Alt text](/images/pbr_teaser.png)

---

## Challenges

1. **Lack of Ground Truth**: Supervised methods require simulated datasets that are time-consuming and resource-intensive to create. Moreover, the domain gap between simulated and real images reduces accuracy.
2. **Complex Window Structures**: Unlike symmetrical objects like human faces, windows lack consistent bilateral symmetry, which adds complexity to viewpoint estimation.
3. **Data Quality Issues**: The collected dataset contains some out-of-domain images, affecting model performance.

![Alt text](/images/window_imgs_complex.png)
---

## Prior Arts

1. **Supervised Methods**: Use Blender simulations for creating ground truth PBR textures. However, these are computationally expensive and don't generalize well to real-world images.
2. **Unsup3D**: An unsupervised framework effective for symmetrical objects like human faces but poorly suited for windows due to its reliance on bilateral symmetry assumptions.
3. **NeRF and EG3D**: Advanced 3D modeling methods that lack the ability to output detailed PBR textures.

---

## Methodology

### Data Collection
- Collected **115,855** high-resolution window images from Flickr.
- Applied corner-point detection to extract and center individual windows.

![Alt text](/images/window_dta.png)

---

### Model Components
1. **Viewpoint Estimator**: A modified ResNet-50 pretrained on canonical images to predict rotation and translation.
2. **Texture Map Estimators**: Autoencoders used to generate depth, normal, and albedo maps.
3. **Uncertainty Map Estimator**: Autoencoder estimating pixel-wise aleatoric uncertainty to make the model robust to outliers.
4. **Differentiable Renderer**: Combines outputs to reconstruct the original image.

---

### Training
- Pretrained the ResNet-50 for viewpoint estimation using 500 canonical images with random rotations and translations.
- Optimized the entire network using multiple loss functions:
  - **Photometric Loss**: Compares reconstructed images with input images.
  - **Perceptual Loss**: Captures higher-level feature differences using a pretrained VGG16.
  - **Flip Loss**: Enforces bilateral symmetry for textures.
  - **Smoothness Loss**: Ensures adjacent pixels have similar depth and albedo values.

![Alt text](/images/network.png)
---

## Results

### Quantitative Metrics
1. **Viewpoint Estimation**:
   - RMSE for rotations and translations shows acceptable accuracy.

| Metric                 | RMSE ↓          |
|------------------------|-----------------|
| X-axis Rotation (°)    | 3.339           |
| Y-axis Rotation (°)    | 3.446           |
| Z-axis Rotation (°)    | 0.652           |
| X-axis Translation (unit of width) | 0.008 |
| Y-axis Translation (unit of width) | 0.006 |

2. **Depth Reconstruction** (on Blender-simulated windows):
   - Mean Absolute Error (MAE): 0.036 (18%)
   - Scale Invariant Depth Error (SIDE): 0.0316
   - Normal Error (MAD): 18.686°

---

### Qualitative Results
The model successfully reconstructs canonical textures for most windows. However, limitations are observed under extreme viewpoints and complex structures.

![Alt text](/images/good_output_1.png)

---

## Limitations
1. **Out-of-Domain Data**: Presence of non-window images reduces model robustness. During the training process, outlier images will negatively affect the fitted model's performance.
2. **Viewpoint Accuracy**: Errors in viewpoint estimation affects the unsupervised learning of PBR textures from window images.
3. **Limited Texture Detail**: Despite improvements, the resolution remains at 128x128, which is not sufficient for detailed PBR textures and higher resolutions such as 256x256 may be considered.

---

## Future Work
- Annotate more images to improve viewpoint estimation.
- Develop methods for filtering out-of-domain samples during preprocessing.
- Explore advanced differentiable renderers and generative models for enhanced texture reconstruction.

---

Thank you for exploring this project! If you'd like to see more, check out my [portfolio page](/portfolio).