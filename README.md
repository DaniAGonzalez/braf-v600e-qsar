# BRAF V600E QSAR Analysis

Machine learning pipeline for predicting BRAF V600E kinase inhibitors using ChEMBL bioactivity data and interpretable AI.

## Overview

End-to-end chemoinformatics workflow that combines molecular featurization, ensemble machine learning, and SHAP-based interpretation to identify drug-like BRAF V600E inhibitors. Achieves R² = 0.73 on test set with 100% true positive rate in top 50 ranked candidates.

**Target:** BRAF V600E mutant kinase (ChEMBL5145)  
**Dataset:** 5,381 compounds with IC50 measurements  
**Best Model:** Random Forest (RMSE = 0.65 pIC50 units)

## Key Results

### Model Performance
- **Test R²:** 0.733
- **Test RMSE:** 0.652 pIC50 units
- **Top 50 TPR:** 100%
- **Features:** 2,060 (2,048 fingerprint bits + 12 descriptors)

### Drug-likeness Assessment
- **Lipinski pass:** 79.6% (4,284/5,381)
- **Veber pass:** 93.7% (5,043/5,381)
- **PAINS clean:** 96.1% (5,171/5,381)
- **Overall drug-like:** 72.3% (3,889/5,381)

### Chemical Space
- **Unique Murcko scaffolds:** 1,901
- **Scaffold diversity ratio:** 0.353
- Active compounds form distinct clusters in UMAP projection

### Key Predictive Features (SHAP)
1. **FractionCSP3** - Higher sp3 carbon content correlates with activity
2. **MolWt** - Optimal molecular weight range identified
3. **LogP** - Lipophilicity positively impacts binding

## Workflow
```
ChEMBL Data Acquisition
         ↓
Data Cleaning & pIC50 Conversion
         ↓
Molecular Featurization (Morgan FPs + Descriptors)
         ↓
Model Training (RF, XGBoost, LightGBM)
         ↓
SHAP Interpretation
         ↓
ADMET Filtering (Lipinski, Veber, PAINS)
         ↓
UMAP Chemical Space Analysis
         ↓
Candidate Ranking & Validation
```

## Quick Start

### Prerequisites
```bash
conda env create -f environment.yml
conda activate braf-qsar
```

### Run Analysis
```bash
jupyter notebook main_notebook.ipynb
```

Executes complete pipeline: data download → modeling → interpretation → ranking.

## Project Structure
```
braf_qsar/
├── data/
│   ├── raw/                      # ChEMBL downloads
│   └── processed/                # Feature matrices, train/test splits
├── models/                       # Trained models (.pkl)
├── results/
│   ├── figures/                  # 8 visualization outputs
│   └── metrics/                  # Performance metrics, ranked candidates
├── main_notebook.ipynb           # Complete analysis pipeline
├── environment.yml               # Conda dependencies
└── README.md
```

## Key Outputs

### Visualizations
- Activity distribution (pIC50 histogram)
- Model predictions vs actual values
- Residual analysis
- SHAP summary and dependence plots
- UMAP chemical space projections
- ADMET filter cascade
- Top candidate validation

### Data Files
- `ranked_candidates.csv` - All test compounds ranked by composite score
- `model_performance.csv` - Comprehensive metrics summary
- `PROJECT_SUMMARY.txt` - Human-readable results summary

## Technologies

- **Cheminformatics:** RDKit
- **Data Source:** ChEMBL Web Resource Client
- **ML Framework:** scikit-learn, XGBoost, LightGBM
- **Interpretability:** SHAP
- **Dimensionality Reduction:** UMAP
- **Visualization:** Matplotlib, Seaborn, Plotly

## Reproducibility

All random seeds fixed (random_state=42). Complete pipeline runs in ~10 minutes on standard laptop.

## Limitations

- Model trained on binding assay data only (no cellular/in vivo)
- ADMET predictions are rule-based (not experimental)
- Applicability limited to compounds within training chemical space
- Educational project - predictions require experimental validation

## Future Enhancements

- Hyperparameter optimization (GridSearchCV)
- Virtual screening of commercial libraries
- Molecular generation for de novo design
- Multi-target selectivity analysis

## References

- ChEMBL Database: [https://www.ebi.ac.uk/chembl/](https://www.ebi.ac.uk/chembl/)
- RDKit: [https://www.rdkit.org/](https://www.rdkit.org/)
- BRAF V600E Mutation: [https://www.mycancergenome.org/content/disease/melanoma/braf/](https://www.mycancergenome.org/content/disease/melanoma/braf/)

## License

MIT License - Free to use for educational and research purposes.

## Author

[Tu nombre]  
[LinkedIn/Email]  
[GitHub: @tu-username]

---

**Note:** This project demonstrates chemoinformatics workflow design and ML interpretability. Predictions are not validated experimentally and should not be used for clinical decisions.
---
Author: Dr. Daniela A. Gonzalez
