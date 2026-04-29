# Complex-Valued Models for EEG Motor Imagery (BCI Competition IVa)

This repository contains an end-to-end notebook pipeline for benchmarking **real-valued** and **complex-valued** decoding methods on EEG motor-imagery data from **BCI Competition III, Dataset IVa**.

The core comparison is between:
- **rCSP** (real-valued Common Spatial Patterns) + logistic regression,
- **cCSP** (complex-valued CSP on analytic signals) + logistic regression,
- **TIMBRE** (a complex-valued neural model), including tuned and untuned variants.

The implementation is provided in a single, user-oriented Jupyter notebook.

---

## Repository Contents

- `user_friendly_notebook.ipynb` — full workflow: data loading, preprocessing, model definitions, hyperparameter search, evaluation, spectral analysis, and sanity checks.
- `README.md` — project overview and usage notes.

---

## What the Notebook Does

The notebook is organized into the following sections:

1. **Imports and setup**
   - Installs dependencies and prepares the environment.
2. **Data loading**
   - Loads subject-level IVa `.mat` files and builds trial metadata.
3. **Preprocessing**
   - Filtering, Hilbert transform / analytic-signal construction, whitening, and fold-safe train/test handling.
4. **Model definitions**
   - Implements TIMBRE variants and CSP-based pipelines.
5. **Analysis utilities**
   - Helper functions for visualization and diagnostics.
6. **Hyperparameter search (TIMBRE)**
   - Optuna-based tuning loop.
7. **Hyperparameter search (CSP)**
   - Optuna-based tuning for cCSP/rCSP-related settings.
8. **Model comparison**
   - Sweeps model configurations and compares accuracies.
9. **Spectral analysis**
   - Frequency-domain analysis of learned activations/projections.
10. **Sanity checks**
   - Leakage checks and additional validation diagnostics.

---

## Data Requirements

The notebook expects BCI IVa subject files named like:

- `data_set_IVa_aa.mat`
- `data_set_IVa_al.mat`
- `data_set_IVa_aw.mat`

In the current notebook code, files are referenced using a `/content/...` style path (Colab-style layout). If you run locally, update those paths to your local dataset location.

---

## Environment and Dependencies

The notebook installs packages inline, including (at minimum):
- `mne`
- `optuna`
- `tensorflow`
- `scikit-learn`
- `scipy`
- `numpy`

It also clones the TIMBRE repository in-notebook. For reproducibility, consider pinning package versions and using a dedicated virtual environment.

---

## How to Run

1. Open `user_friendly_notebook.ipynb` in Jupyter or Google Colab.
2. Update dataset paths to where IVa files live on your machine/runtime.
3. Run cells in order from top to bottom.
4. Inspect outputs from:
   - model-comparison section (accuracy trends),
sdd   - spectral analysis plots.

---

## Notes

- This repo is notebook-centric (not yet packaged as a Python module).
- Some sections are computationally heavy (especially Optuna loops).
- Results are subject-dependent and rely on fold-wise evaluation strategy defined in the notebook.

---

## Suggested Next Improvements

- Extract reusable functions into `src/` Python modules.
- Add a `requirements.txt` / `environment.yml` for deterministic setup.
- Add a small configuration block for dataset paths and subject selection.
- Save key outputs (metrics/tables/figures) to versioned artifacts.
- Add CI checks for notebook execution (or a lightweight smoke test script).


