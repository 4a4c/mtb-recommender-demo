# mtb-recommender-demo

Minimal guide to run the `recommender.ipynb` notebook in mybinder.org.

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/4a4c/mtb-recommender-demo/HEAD?urlpath=%2Fdoc%2Ftree%2Frecommender.ipynb)

This repository contains a Jupyter notebook that:

- creates a synthetic mountain-bike-brand ratings dataset,
- trains an SVD recommender using `scikit-surprise`, and
- evaluates recommendations (RMSE + mean nDCG).

## Quick binder-first workflow

1. Launch the notebook on mybinder.org (or another working Jupyter environment).
2. Open the recommender.ipynb notebook.
3. Run cells in order from top to bottom. If the first cell installs packages, restart the kernel after it finishes and re-run that cell.

## Cell-by-cell (what to run and why)

1. **Setup / imports (top cell)**
   - Verifies or installs packages in the running kernel and imports core libraries (`pandas`, `numpy`, `surprise`, `scikit-learn`).
   - Run first. If it performs installs, restart the kernel and re-run to ensure imports succeed.

2. **Data generation (brands + synthetic ratings)**
   - Generates a synthetic dataset of user-brand ratings and populates the DataFrame `df`.

3. **Export / summary (optional)**
   - Writes `mtb_ratings.csv` and prints dataset summaries (counts, distribution, ratings per brand).

4. **Train & recommend (modeling cell)**
   - Loads `df` into Surprise, splits train/test, trains SVD, and prints sample top‑k recommendations.

5. **Evaluation (evaluation cell)**
   - Computes RMSE and mean nDCG on the hold-out test set and prints results.