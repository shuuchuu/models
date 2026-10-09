# models

Trained model weights used by shuuchuu's training labs (the Colab notebooks of
https://github.com/shuuchuu/labs), one model per directory. Each directory's
`README.md` gives the model, how it was trained, and the license of its weights.
Datasets live in https://github.com/shuuchuu/datasets.

## Getting a model

To get a single file, e.g. in Colab:

```
!wget -q -P RIAD_models https://github.com/shuuchuu/models/raw/refs/heads/main/riad-unet-mvtec/best_model_carpet.pt
```

## Models

| Directory | Model | License |
| --- | --- | --- |
| [`riad-unet-mvtec`](riad-unet-mvtec) | RIAD U-Net for visual anomaly detection, trained on MVTec AD | CC BY-NC-SA 4.0 |
