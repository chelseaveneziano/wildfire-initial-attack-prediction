# Predicting Large Wildfires at Initial Attack

Can we tell which California wildfires are likely to escape initial attack, using only what is known when the fire is first reported?

This project uses 183,622 California wildfires (2000–2020) from the public FPA FOD-Attributes dataset to predict whether a new fire will grow past 10 acres (escape initial attack) or reach 100+ acres (a large fire).

**Author:** Chelsea Veneziano
**Course:** DSC 680 Applied Data Science, Bellevue University

## Key results (test years 2017–2020)

| Model | ROC-AUC | PR-AUC |
| --- | --- | --- |
| Logistic regression | 0.758 | 0.186 |
| Random forest | 0.778 | 0.214 |
| **Gradient boosting** | **0.793** | **0.230** |

- At a 0.49 cutoff, gradient boosting flagged about 1 in 5 new fires and caught 60% of the fires that escaped.
- The large-fire model reached a ROC-AUC of 0.821.
- How remote and undeveloped an area is (population, land development, nearby fire stations) mattered about 3 times more than weather.
- Fairness check: the model caught fewer escapes in the most socially vulnerable areas (48% vs. about 62% elsewhere).

## How to run

1. Install Python 3 with pandas, numpy, matplotlib, seaborn, and scikit-learn (Anaconda includes all of them).
2. Create a `data/` folder next to the notebook.
3. Open `wildfire-analysis.ipynb` and run all cells from top to bottom.
   - The notebook downloads the 29 yearly data files (about 5 GB) from Zenodo automatically.
   - All models use `random_state=42`, so results are reproducible.

The raw data is not stored in this repository because of its size.

## Data sources

- Pourmohamad, Y., et al. (2023). *Physical, social, and biological attributes for improved understanding and prediction of wildfires: FPA FOD-Attributes dataset* (Version 1.0) [Data set]. Zenodo. https://doi.org/10.5281/zenodo.8381129
- Short, K. C. (2022). *Spatial wildfire occurrence data for the United States, 1992–2020 [FPA_FOD_20221014]* (6th ed.) [Data set]. Forest Service Research Data Archive. https://doi.org/10.2737/RDS-2013-0009.6

## Files

- `wildfire_analysis.ipynb`: all data preparation, charts, models, and evaluation
- `fig_*.png`: charts used in the white paper
