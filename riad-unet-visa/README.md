# RIAD U-Net, VisA

Weights of the U-Net that the `visual-anomaly-detection-keras` and
`visual-anomaly-detection-lightning` labs train to detect visual anomalies by
inpainting (RIAD: *Reconstruction by Inpainting for Visual Anomaly Detection*), on
VisA's `chewinggum`, so the labs can show that category without training on it (they
train on `pcb4` themselves).

## Files

- `best_model_chewinggum.pt`: the `state_dict` of the Lightning lab's `RIAD` module
  (its U-Net with 5 steps, starting at 64 feature maps), the epoch with the lowest
  training loss kept. Load it with the lab's `unet(...)` function.
- `best_model_chewinggum.weights.h5`: the same U-Net in the Keras lab, its weights at
  the epoch with the lowest training loss (`ModelCheckpoint`). Load them with
  `unet().load_weights(...)`.

Both were trained on the 250 training images of `chewinggum` in
https://github.com/shuuchuu/datasets/tree/main/visa-subset (256×256, the labs'
preprocessing).

## Source

- Trained with each lab's own code (Adam at 1e-3, batches of 5, early stopping after
  20 epochs without improvement), on Colab's runtime image with an RTX 3090
  (2026-10-18):
  - Lightning: 74 epochs, the best one the 54th (training loss 1.035);
  - Keras: 207 epochs, the best one the 187th (training loss 0.986).
- Method: Vitjan Zavrtanik, Matej Kristan, Danijel Skočaj, "Reconstruction by
  inpainting for visual anomaly detection", Pattern Recognition 112 (2021).
- Data: VisA, https://github.com/amazon-science/spot-diff (Yang Zou, Jongheon Jeong,
  Latha Pemula, Dongqing Zhang and Onkar Dabeer, "SPot-the-Difference Self-Supervised
  Pre-training for Anomaly Detection and Segmentation", ECCV 2022), through
  shuuchuu/datasets' `visa-subset`.

## License

The weights are derived from VisA, licensed under CC BY 4.0: they are under the same
license, https://creativecommons.org/licenses/by/4.0/ (attribution: VisA, © Amazon.com,
Inc., and this repository).
