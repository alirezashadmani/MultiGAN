# Multi-GAN

A structured Python package (`multi_gan`) for exploring Generative Adversarial Networks across distinct environmental profiles including synthesized multi-modal clusters and complex grid imagery (e.g. `mnist`, `cifar10`).

## Overview
This repository utilizes PyTorch to run modular experiments comparing standalone and multiple Generator/Discriminator couplings (Multi-GAN). Deep network variations like `GeneratorDCGAN28` and `DiscriminatorResNet32` are exposed dynamically via Sacred experiments depending on the dataset provided.

## Architecture
This project was initially coupled tightly to Google Colab environments via hardcoded outputs (e.g. `/content/drive/...`). It has been explicitly decoupled to establish dynamic local resolution, protecting execution flows across standalone PCs and generalized Cloud Virtual Machines.

- **Removed `Run.ipynb`**: The Google environment orchestrator has been purged.
- **Added `run_pipeline.ipynb`**: Integrates the library organically (via `pip install -e .`) and fires the Sacred orchestration experiment `run_training.py` sequentially without reliance on specialized magic commands. Large artifacts will neatly dump to a generated `data/output/multi_gan/` structure securely nestled within your filesystem.

## Getting Started

### 1. Requirements
Ensure your Python environment meets the dependencies defined in `setup.py` and standard deep learning requisites:
- Torch
- Torchvision
- Sacred
- Joblib

### 2. Installation
To register `multi_gan` as a module and fulfill `setup.py`:
```bash
pip install -e .
```

### 3. Usage
Run the default pipeline via the new Orchestrator notebook (`run_pipeline.ipynb`) or invoke the Python script directly via CLI:
```bash
python run_training.py
```

### 4. Configuration Modifications
`run_training.py` provides several `@exp.named_config` decorators (e.g., `synthetic()`, `cifar()`, `mnist()`). You can override the default parameters at runtime via Sacred CLI conventions:
```bash
python run_training.py with cifar batch_size=64 G_lr=1e-4
```
