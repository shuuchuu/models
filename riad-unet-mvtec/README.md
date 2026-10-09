# RIAD U-Net, MVTec AD

Weights of the U-Net that the `visual-anomaly-detection-lightning` lab trains to detect
visual anomalies by inpainting (RIAD: *Reconstruction by Inpainting for Visual Anomaly
Detection*), one model per MVTec AD object category, so the lab can show a category
without training on it.

## Files

- `best_model_carpet.pt`: the `state_dict` of the lab's `RIAD` Lightning module (its
  U-Net with 5 steps, starting at 64 feature maps), trained on MVTec AD's `carpet`
  training images (256×256, the lab's preprocessing), the epoch with the lowest
  training loss kept. Load it with the lab's `unet(...)` function.

## Source

- Trained with the lab's own code (`lightning`, Adam at 1e-3, batches of 5, early
  stopping after 20 epochs without improvement), on Colab's runtime image with an RTX
  A4000: 93 epochs, the best one the 72nd (training loss 0.716).
- Method: Vitjan Zavrtanik, Matej Kristan, Danijel Skočaj, "Reconstruction by
  inpainting for visual anomaly detection", Pattern Recognition 112 (2021).
- Data: MVTec AD, https://www.mvtec.com/company/research/datasets/mvtec-ad (Paul
  Bergmann et al., "MVTec AD — A Comprehensive Real-World Dataset for Unsupervised
  Anomaly Detection", CVPR 2019).

## License

The weights are derived from MVTec AD, licensed under CC BY-NC-SA 4.0: they are under
the same license, https://creativecommons.org/licenses/by-nc-sa/4.0/ (non-commercial
use, attribution, share alike).
