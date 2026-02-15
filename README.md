# LatentHide : Deep Image Steganography using Stable Diffusion
An efficient image steganography system implementing alpha blending techniques with Stable Diffusion infrastructure to embed secret images within cover images while maintaining high visual fidelity.

This project implements a practical steganography framework that uses mathematical alpha blending to hide secret images within cover images. Leveraging Stable Diffusion's preprocessing pipeline and PyTorch tensor operations, the system achieves near-perfect reconstruction with SSIM scores ranging from 0.9644 to 0.9982, demonstrating robust performance while maintaining computational efficiency.

## Key Features:

- **Advanced Steganography**: Custom alpha-blending encoding/decoding algorithm
- **High Visual Fidelity**: Achieves SSIM scores up to 0.9982 (near-perfect retention)
- **Diffusion Models**: Leverages Stable Diffusion v1-5 for robust embedding
- **Comprehensive Evaluation**: SSIM and MSE metrics for performance validation


## Output
<img width="1768" height="618" alt="Output" src="https://github.com/user-attachments/assets/9b9c4fff-ec4f-441f-a4ff-aba8b2d07a39" />

## Technologies
**Deep Learning & Framework**
- PyTorch
- Stable Diffusion (runwayml/stable-diffusion-v1-5)
- Diffusion Probabilistic Models (DDPM)

**Computer Vision**
- OpenCV
- scikit-image (SSIM, MSE metrics)
- PIL/Pillow
- Matplotlib

**Data & Evaluation**
- Flickr8k Dataset
- Custom PyTorch Dataset/DataLoader
- Structural Similarity Index (SSIM)
- Mean Squared Error (MSE)


## Architecture
The system implements a streamlined steganography framework with two core components:

1. **Image Encoding Pipeline**
- **Direct Alpha Blending**: Employs weighted combination of cover and secret images using parameterized alpha value
- **Tensor Operations:** Uses PyTorch tensor arithmetic for efficient image blending: (1 - alpha) * cover + alpha * secret
- **Preprocessing**: Implements image resizing (512×512) and tensor conversion for model compatibility

 2. **Stable Diffusion Integration**
- **Pretrained Model**: Leverages _runwayml/stable-diffusion-v1-5_ for latent space understanding
- **Device Optimization**: Configures model for CPU/GPU deployment
- **Pipeline Setup:** Initializes complete Stable Diffusion pipeline for potential generative enhancements

3. **Decoding & Recovery System**
- **Inverse Blending**: Mathematical extraction using: (encoded - (1 - alpha) * cover) / alpha
- **Value Clamping**: Applies torch.clamp(0, 1) to ensure valid pixel ranges
- **Lossless Recovery**: Perfect mathematical reconstruction when using identical alpha parameters

4. **Evaluation Framework**
- **Multi-Metric Analysis**: Implements SSIM (Structural Similarity) and MSE (Mean Squared Error) metrics
- **Visualization Tools**: Provides side-by-side comparison of cover, secret, encoded, and decoded images
- **Data Pipeline:** Custom Flickr8k dataset loader with batch processing capabilities

### Dataset
Flickr-8k - https://paperswithcode.com/dataset/flickr-8k
