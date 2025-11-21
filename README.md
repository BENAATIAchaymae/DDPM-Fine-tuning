# DDPM Fine-Tuning for Custom Image Generation

This repository provides a complete pipeline for **fine-tuning a Denoising Diffusion Probabilistic Model (DDPM)** using the Hugging Face *diffusers* library. It allows you to train diffusion models on your own dataset and generate high‑quality images.

---

##  Features

* Fine‑tuning DDPM on custom datasets
* Configurable training through command-line arguments
* Automatic checkpoint saving and image generation
* Clean and modular repository structure
* Optional GitHub Actions CI integration

---

##  Repository Structure

```
ddpm-finetuning/
├─ .github/
│  └─ workflows/
│     └─ ci.yml
├─ data/
│  ├─ README.md
│  └─ (train/val/test directories)
├─ docs/
│  └─ usage.md
├─ models/             # saved checkpoints (ignored by git)
├─ notebooks/
│  └─ demo.ipynb
├─ outputs/            # generated images and logs
├─ src/
│  └─ train.py         # main training script
├─ tests/
│  └─ test_imports.py
├─ .gitignore
├─ README.md
├─ LICENSE
├─ requirements.txt
└─ setup.cfg
```

---

##  Installation

Install the dependencies:

```bash
pip install -r requirements.txt
```

---

## Training the Model

Run the training script with your dataset:

```bash
python src/train.py \
  --train_dir data/train \
  --output_dir outputs/my_ddpm \
  --epochs 50 \
  --batch_size 4 \
  --lr 1e-4
```

Your dataset must be located in:

```
data/train/
data/val/
```

Images will be automatically resized.

---

##  Generating Images

After training:

```bash
python src/train.py --generate --checkpoint models/latest.pth --output_dir outputs/samples
```

Generated images will be stored in `outputs/samples/`.

---

##  Requirements

```
torch
torchvision
diffusers
accelerate
tqdm
Pillow
matplotlib
transformers
```

---

##  GitHub CI Workflow

This repository includes an optional GitHub Actions workflow (`.github/workflows/ci.yml`):

```yaml
name: CI
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v4
        with:
          python-version: '3.10'
      - name: Install dependencies
        run: pip install -r requirements.txt
      - name: Run tests
        run: pytest -q
```
---

##  Contributing

Contributions are welcome! Feel free to submit pull requests or open issues.



## Contact

For questions or suggestions, open an issue on GitHub.



If you want, I can also generate:

* The `train.py` code
* A dataset README
* A usage guide in `/docs`

Just tell me!
