# SF-GANet

## Dataset

The Beijing 2001–2020 LCZ map series is available at:
https://drive.google.com/drive/folders/115iLU2r2hl-T30uB6udfRTbGaPyV1aYD

## Repository structure

```text
code/
├── config.py
├── model/
│   └── model.py
├── train/
│   ├── training.py
│   └── losses.py
└── evaluation/
    └── metrics.py
```

## Requirements

- Python 3.10
- NumPy 1.26.4
- PyTorch (CUDA 11.8 build)
- pandas 2.3.1
- GDAL 3.10.3
- GeoPandas 1.1.1
- scikit-learn
- SciPy
- Matplotlib
- Rasterio
- torchvision
- tqdm
- einops

## Experimental protocol

- Spatial folds are assigned at parcel level before patch extraction, keeping overlapping and neighboring samples within the same fold.
- Accuracy evaluation uses nested spatial five-fold validation. Each outer fold is held out for final evaluation; epoch selection uses an inner validation fold.
- After epoch selection, models are refit on all four outer-training folds and evaluated on the held-out fold.
- Model-comparison, ablation, and training-strategy experiments use five random seeds (40–44).
- Final annual-map generation uses the default seed 42.
