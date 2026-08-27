# Deep Learning

Neural networks: stacks of simple math units that learn their own features. Use when the input is unstructured — images, text, audio — where hand-crafting features is hopeless.

## Keywords decoded

- **Neuron / layer** — a neuron is `output = activation(weights · inputs + bias)`. A layer is many neurons in parallel; a network is layers stacked so each learns increasingly abstract patterns.
- **Activation function (ReLU etc.)** — the non-linearity between layers. Without it, a 100-layer network collapses into one linear equation.
- **Backpropagation** — the algorithm that computes, for every weight, "which direction should I nudge this to reduce the loss?" (calculus chain rule, automated).
- **Gradient descent / optimizer (SGD, Adam)** — the nudging strategy. **Learning rate** = nudge size; the single most important hyperparameter. Too big → training explodes; too small → takes forever.
- **Epoch** — one full pass over the training data. **Batch** — the chunk of examples processed per nudge (you don't fit all data in memory at once).
- **Training loop** — the PyTorch ritual: forward pass → compute loss → `loss.backward()` → `optimizer.step()`. You will write this by hand in Mission 02; after that it's boilerplate.
- **Dropout / weight decay / early stopping** — anti-overfitting tools: randomly silence neurons / penalize big weights / stop when validation loss stops improving.
- **GPU / CUDA / MPS** — training is matrix math; GPUs do it 10–100× faster. On your Mac, PyTorch uses **MPS** (Apple's GPU backend) via `device = "mps"`.
- **Tensor** — n-dimensional array, PyTorch's basic object. A batch of images is a 4-D tensor: (batch, channels, height, width).

## PyTorch vs TensorFlow vs Keras

Learn **PyTorch**. It won research and most of industry; job posts and modern tutorials assume it. Recognize the other names, don't invest in them.

## What to master

1. Write a training loop from scratch once — then understand what libraries automate.
2. Read a loss curve: is it converging, overfitting (val loss rising while train falls), or is the learning rate wrong?
3. Know when deep learning is the *wrong* tool (small tabular datasets — see `01-classical-ml`).

## Advisor lens

Deep learning needs data volume and compute budget. Client has 2,000 rows of sales data? Recommending a neural net is malpractice. Client has 100k product photos? Now we're talking — and transfer learning (see `03-computer-vision`) cuts the data requirement by 10×.
