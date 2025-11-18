# BRAF V600E QSAR Analysis

Machine learning models to predict BRAF V600E kinase inhibitors using ChEMBL bioactivity data.

## What it does

- Downloads bioactivity data for BRAF V600E from ChEMBL
- Trains ML models (Random Forest, XGBoost, LightGBM) to predict IC50 values
- Identifies key structural features using SHAP
- Filters compounds by drug-likeness (Lipinski, Veber, PAINS)
- Visualizes chemical space with UMAP
- Ranks potential inhibitor candidates

## Tech stack

- **Cheminformatics:** RDKit
- **Data:** ChEMBL Web Resource Client  
- **ML:** scikit-learn, XGBoost, LightGBM
- **Interpretation:** SHAP
- **Viz:** Matplotlib, Seaborn, Plotly

## Quick start
```bash
# Clone and setup
git clone https://github.com/YOUR_USERNAME/braf-v600e-qsar.git
cd braf-v600e-qsar
conda env create -f environment.yml
conda activate braf-qsar

# Run analysis
jupyter notebook main_notebook.ipynb
```

## Project structure
```
braf-v600e-qsar/
├── data/                 # Raw and processed datasets
├── models/               # Trained models
├── results/              # Figures and metrics
├── main_notebook.ipynb   # Complete pipeline
└── environment.yml       # Dependencies
```

## Results

*Coming soon - analysis in progress*

## Reference

Target: BRAF V600E (ChEMBL5145)  
Benchmark: Vemurafenib (approved melanoma drug)

---
Author: Dr. Daniela A. Gonzalez
