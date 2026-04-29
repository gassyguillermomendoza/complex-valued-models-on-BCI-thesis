# Complex-Valued EEG Decoding (CSP vs TIMBRE)

![Python](https://img.shields.io/badge/python-3.10+-blue)
![Status](https://img.shields.io/badge/status-research-green)
![License](https://img.shields.io/badge/license-MIT-lightgrey)

---

## TL;DR

- Use **complex-valued signals (Hilbert transform)** for EEG decoding  
- **cCSP consistently beats rCSP**  
- **TIMBRE ≈ cCSP**, with subject-specific gains  
- Models exploit **mu (8–13 Hz)** and **beta (13–30 Hz)** rhythms  

---

## Models

| Model   | Type            | Projection        |
|--------|-----------------|------------------|
| rCSP   | Real-valued     | Closed-form      |
| cCSP   | Complex-valued  | Closed-form      |
| TIMBRE | Complex-valued  | Learned (NN)     |

---

## Data

- BCI Competition III — Dataset IVa  
- 118-channel EEG  
- Binary task: **hand vs foot imagery**  
- 100 Hz, 3.5s trials  

---

## Pipeline

```text
EEG → Filter → Hilbert → Whitening → Projection → Magnitude → Classifier
```

* 5-fold CV (per subject)
* Logistic regression / softmax output

---

## Spectral Insight

* Analyze **FFT of model activations**
* Compare class-wise power
* Reveals what frequencies drive decoding (not just accuracy)

---

## Run

```bash
pip install -r requirements.txt
python main.py
```

*or run the notebook directly*

---

## Notes

* Hyperparameter search via **Optuna (nested CV)**
* **cCSP is near-optimal analytically**
* **TIMBRE gains are data-dependent**

---

## Repo

[https://github.com/gassyguillermomendoza/complex-valued-models-on-BCI-thesis](https://github.com/gassyguillermomendoza/complex-valued-models-on-BCI-thesis)

---

## Citation

```bibtex
@thesis{mendoza2026complex,
  title={Complex-Valued Models Improve EEG Behavior Decoding},
  author={Mendoza Franco, Guillermo A.},
  year={2026},
  school={Claremont Colleges}
}
```

```

If you want one step further (more “viral repo” style), I can add:
- a **one-line hook**
- example figures (your spectra plots)
- or a **demo GIF-style workflow**

But this is already in that sweet spot: clean + technical + readable.
```

