# Mission 02 — Pet Breed Classifier (37 classes)

**End model:** an image classifier that identifies which of 37 cat/dog breeds is in a photo — built three ways (from scratch, frozen pretrained, fine-tuned) so you *feel* why transfer learning owns applied vision.

**Why this mission:** it's your cats-vs-dogs project grown up. Same domain, but 37 fine-grained classes instead of 2, modern PyTorch instead of whatever you used years ago, and a deliberate from-scratch-vs-pretrained comparison that teaches the most important lesson in practical deep learning.

## Dataset

Oxford-IIIT Pet — 7,349 images, 37 breeds, ~200 images each. torchvision downloads and splits it for you (~800 MB into the shared datacenter):

```python
from torchvision.datasets import OxfordIIITPet
train = OxfordIIITPet(root="../../datacenter/oxford-pets", split="trainval", download=True)
test  = OxfordIIITPet(root="../../datacenter/oxford-pets", split="test", download=True)
```

Or download directly (note: the old `/~vgg/data/pets/` URLs now redirect):

```bash
mkdir -p ../../datacenter/oxford-pets/oxford-iiit-pet
cd ../../datacenter/oxford-pets/oxford-iiit-pet
curl -sSL -O https://thor.robots.ox.ac.uk/pets/images.tar.gz
curl -sSL -O https://thor.robots.ox.ac.uk/pets/annotations.tar.gz
tar xzf images.tar.gz && tar xzf annotations.tar.gz
```

## Success criteria

- All three approaches scored on the same test split, in one comparison table.
- Fine-tuned model ≥ 90% test accuracy.
- Confusion-matrix analysis: name the most-confused breed pairs and *why* (look at the images).
- `WRITEUP.md` framed as if a client asked "can you build us an image classifier with only ~200 examples per class?"

## Rules

Protocol in `../README.md`. Predictions before every training run are especially valuable in this mission — the gaps between the three approaches are the lesson. Create `LEARNINGS.md` at stage 1. Training runs use your Mac's GPU (`device="mps"`).

## Stages

### Stage 1 — Data in, eyes on
**Build:** download via torchvision; visualize a grid of samples per breed; build `DataLoader`s with resize + normalization (ImageNet mean/std).
**Learn:** tensors, batches, normalization — `02-deep-learning/GUIDE.md` keywords block.
**Checkpoint:** What shape is one batch tensor and what does each dimension mean? Why normalize with ImageNet's statistics rather than this dataset's?

### Stage 2 — Small CNN from scratch (the humbling)
**Build:** a small CNN written layer by layer, and the training loop written **by hand** (forward → loss → backward → step) with train/val loss curves. Train ~15 epochs.
**Learn:** the whole of `02-deep-learning/GUIDE.md` plus CNN basics in `03-computer-vision/GUIDE.md`.
**Checkpoint:** *Predict test accuracy before running* (random guessing = 2.7%). Walk through the four lines of the training loop and say what each does. Is the model over- or underfitting, per the loss curves?

### Stage 3 — Transfer learning, frozen (the revelation)
**Build:** pretrained ResNet-18, all layers frozen, final layer replaced with a 37-class head; train just that head, same epochs budget.
**Learn:** transfer learning, feature extraction — `03-computer-vision/GUIDE.md`.
**Checkpoint:** *Predict the accuracy jump first.* Explain to an imaginary client, in plain words, what the frozen layers "know" and where they learned it.

### Stage 4 — Fine-tune (the polish)
**Build:** unfreeze; fine-tune everything at a low learning rate; add data augmentation (flips, crops, color jitter); early stopping on val accuracy.
**Learn:** fine-tuning vs feature extraction, augmentation, learning-rate intuition.
**Checkpoint:** Why must the learning rate be lower when fine-tuning than when training the head? What would a too-high rate destroy?

### Stage 5 — Autopsy
**Build:** confusion matrix over 37 classes; per-class accuracy; a gallery of the worst-confused pairs with actual images side by side.
**Learn:** confusion matrix reading — `03-computer-vision/GUIDE.md`.
**Checkpoint:** Which pairs are confused and would a human confuse them too? What would you tell a client who demands those last few percent?

### Stage 6 — Case study
**Build:** `WRITEUP.md` — the three-approach comparison table, cost/effort per approach, the "200 images per class is enough *if* you use transfer learning" argument, and when you'd instead recommend a zero-shot API (CLIP) with no training at all.
**Learn:** advisor lens sections of `03-computer-vision/GUIDE.md` and `07-advisory/GUIDE.md`.
**Checkpoint:** Two-sentence CFO version of this whole mission.
