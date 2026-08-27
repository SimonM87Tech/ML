# Computer Vision

Models that understand images. Your cats-vs-dogs project lived here; Mission 02 upgrades it to modern practice.

## Keywords decoded

- **CNN (convolutional neural network)** — network whose layers slide small filters across the image, learning edges → textures → shapes → objects. The classic image architecture.
- **Vision Transformer (ViT)** — newer architecture treating an image as a sequence of patches. State of the art at scale; CNNs (ResNet) remain excellent and cheaper for most practical jobs.
- **ResNet** — the workhorse CNN family (ResNet-18/34/50 = depth). "Residual connections" let very deep networks train. Your default starting point.
- **Transfer learning** — take a model pretrained on millions of images (ImageNet) and adapt it to your task. **This is the single highest-leverage technique in applied vision.** Nobody trains from scratch anymore.
- **Fine-tuning vs feature extraction** — retrain all layers on your data (more power, more data needed) vs freeze the pretrained layers and retrain only the final classifier (fast, works with hundreds of images).
- **Pretrained weights / ImageNet** — the learned parameters from that big prior training; ImageNet is the 1.2M-image dataset they came from.
- **Data augmentation** — random flips/crops/color shifts applied during training so the model sees "more" data and generalizes better. Cheap accuracy, always use it.
- **Normalization** — scaling pixel values to the ranges pretrained models expect (their published mean/std). Forgetting this silently degrades everything.
- **Tasks beyond classification**: **object detection** (draw boxes: YOLO), **segmentation** (label every pixel), **OCR** (read text). Recognize the names; learn on demand.

## The modern recipe (Mission 02 walks it)

1. Load pretrained ResNet
2. Replace final layer with one sized to your classes
3. Feature-extract first (frozen) → score
4. Unfreeze and fine-tune at low learning rate → score
5. Augmentation + a confusion matrix to see *which* classes it confuses

## What to master

The recipe above, reading a confusion matrix, and the intuition for "how many images per class do I need" (with transfer learning: often just hundreds).

## Advisor lens

Vision projects fail on data, not models: inconsistent lighting, mislabeled images, classes the client forgot to mention. Scope a labeling/data-audit phase into every vision proposal. Also know that for common objects, an API call (or zero-shot model like CLIP) may solve it with no training — check that *before* proposing a custom model.
