# Maize Tassel Detection from UAV Imagery

Deep learning models for detecting maize tassels in Unmanned Aerial Vehicle (UAV) imagery using **YOLOv5** and **Detectron2 (Faster R-CNN)**. Originally developed as a CSE499 Senior Design project, now refactored into a reproducible, production-style repository.

![Python](https://img.shields.io/badge/python-3.9%2B-blue)
![PyTorch](https://img.shields.io/badge/pytorch-1.10%2B-red)
![License](https://img.shields.io/badge/license-MIT-green)
![Status](https://img.shields.io/badge/status-research-orange)

---

## Table of Contents
- [Motivation](#motivation)
- [Dataset](#dataset)
- [Models](#models)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Roadmap](#roadmap)
- [Contributors](#contributors)
- [License](#license)
- [Citation](#citation)

---

## Motivation

Accurate tassel detection enables automated phenotyping, yield estimation, and growth-stage monitoring in maize fields. Manual counting is labor-intensive and error-prone; UAV imagery combined with object detection makes it scalable.

## Dataset

- **Source:** UAV-captured RGB imagery of maize fields  
- **Split:** Train = 733 · Validation = 205 · Test = 30  
- **Annotations:** Bounding boxes in YOLO format (`.txt`) and COCO format (`.json`)

> Dataset is not bundled. See [`data/README.md`](data/README.md) for download and preparation instructions.

## Models

| Model | Framework | Backbone | Notebook |
|-------|-----------|----------|----------|
| YOLOv5 | Ultralytics / PyTorch | CSPDarknet53 | [`notebooks/YOLOV5_MAIZE_TASSEL.ipynb`](notebooks/YOLOV5_MAIZE_TASSEL.ipynb) |
| Faster R-CNN | Detectron2 | ResNet-50 FPN | [`notebooks/Maize_Tassel_Detectron2.ipynb`](notebooks/Maize_Tassel_Detectron2.ipynb) |

## Project Structure

```
.
├── data/
│   ├── raw/                 # Original UAV images (gitignored)
│   ├── processed/           # Resized / augmented images (gitignored)
│   └── README.md            # Dataset documentation
├── notebooks/               # Training & evaluation notebooks
│   ├── YOLOV5_MAIZE_TASSEL.ipynb
│   └── Maize_Tassel_Detectron2.ipynb
├── src/
│   ├── data/                # Dataset loaders & conversion utilities
│   ├── models/              # Model wrappers (yolo, detectron2)
│   ├── training/            # Train loops & config
│   ├── inference/           # Predict / visualize
│   └── evaluation/          # mAP, precision, recall
├── configs/                 # YAML config files
├── scripts/                 # CLI entry points (train.sh, infer.sh)
├── results/                 # Saved metrics, plots, sample outputs
├── tests/                   # Unit tests
├── requirements.txt
├── environment.yml          # Optional conda env
├── .gitignore
├── LICENSE
└── README.md
```

## Installation

### Option 1 — pip
```bash
git clone https://github.com/<your-username>/maize-tassel-detection-uav.git
cd maize-tassel-detection-uav
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
```

### Option 2 — conda
```bash
conda env create -f environment.yml
conda activate maize-tassel
```

### Detectron2 (separate install)
```bash
python -m pip install 'git+https://github.com/facebookresearch/detectron2.git'
```

## Usage

### Train YOLOv5
```bash
python src/training/train_yolo.py --data configs/maize.yaml --epochs 100 --img 640 --weights yolov5s.pt
```

### Train Detectron2
```bash
python src/training/train_detectron2.py --config configs/detectron2_faster_rcnn.yaml
```

### Inference
```bash
python src/inference/predict.py --model runs/train/exp/weights/best.pt --source data/test/
```

## Results

| Model | mAP@0.5 | Precision | Recall | Inference (ms/img) |
|-------|---------|-----------|--------|---------------------|
| YOLOv5s     | _TBD_ | _TBD_ | _TBD_ | _TBD_ |
| Faster R-CNN (D2) | _TBD_ | _TBD_ | _TBD_ | _TBD_ |

> Fill in the table after re-running training. Sample predictions are saved under [`results/`](results/).

## Roadmap

- [ ] Add YOLOv8 baseline
- [ ] Convert notebooks into reproducible scripts under `src/`
- [ ] Add Dockerfile for one-command setup
- [ ] CI: lint + unit tests via GitHub Actions
- [ ] Release pretrained weights via GitHub Releases
- [ ] Streamlit demo for live tassel counting

## Contributors

- **Sadiqun Nur Ayan** — [@ayan978](https://github.com/ayan978)
- *(add co-authors here)*

## License

Released under the [MIT License](LICENSE).

## Citation

If you use this work, please cite:

```bibtex
@misc{ayan2022maizetassel,
  title  = {Deep Learning with UAV Imagery for Maize Tassel Detection},
  author = {Ayan, Sadiqun Nur and others},
  year   = {2022},
  note   = {CSE499 Senior Design Project, North South University},
  url    = {https://github.com/ayan978/Deep-Learning-with-Unmanned-Aerial-Vehicle-Imagery-in-the-Detection-of-Tassels-in-Maize}
}
```
