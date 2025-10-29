# Mountain Bike Brand Recommender Demo

A demonstration of collaborative filtering for mountain bike brand recommendations using matrix factorization (SVD). This project shows how to build a recommender system that suggests mountain bike brands based on user preferences, simulating real-world recommendation scenarios with synthetic data.

## Overview

This repository contains a Jupyter notebook that:

- Creates a synthetic dataset of mountain bike brand ratings
  - Simulates 500 users rating 3-5 brands each
  - Incorporates realistic brand popularity weights
  - Adds controlled random noise for natural variation
- Trains an SVD recommender using `scikit-surprise`
  - Uses matrix factorization to learn latent user-brand preferences
  - Handles sparse ratings (users only rate some brands)
  - Provides personalized top-K recommendations
- Evaluates recommendation quality
  - RMSE for rating prediction accuracy
  - nDCG for ranking quality
  - Qualitative analysis of brand associations

## Quick Start Options

### Option 1: Binder (No Setup Required)

1. Launch the notebook on mybinder.org (or another working Jupyter environment).

   [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/4a4c/mtb-recommender-demo/HEAD?urlpath=%2Fdoc%2Ftree%2Frecommender.ipynb)

2. Open the `recommender.ipynb` notebook (this should open automatically if launching the binder from above link).
3. Run cells in order from top to bottom. If the first cell installs packages, restart the kernel after it finishes and re-run that cell.

### Option 2: Dev Container (Recommended for Development)

If you have Docker and VS Code with the Dev Containers extension:

1. Clone this repository
2. Open in VS Code
3. When prompted, click "Reopen in Container" (or use Command Palette → "Dev Containers: Reopen in Container")
4. The devcontainer will automatically install all dependencies from `requirements.txt`
5. Open `recommender.ipynb` and run the cells

This provides a consistent, isolated development environment with all dependencies pre-configured.

## Cell by cell (what to run and why)

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

## Understanding the Results

The model's performance is evaluated using two key metrics:

1. **RMSE (Root Mean Square Error)**
   - Measures rating prediction accuracy
   - Range: 0 (perfect) to 4 (worst) for 5-star ratings
   - Target: < 1.2 indicates good performance
   - Typical values: 0.8-1.2 for production recommenders

2. **nDCG (Normalized Discounted Cumulative Gain)**
   - Measures recommendation ranking quality
   - Range: 0 to 1 (1 = perfect ranking)
   - Target: > 0.5 indicates useful recommendations
   - We report both overall nDCG and nDCG@3 (for top-3 recommendations)

## Requirements

### Manual Installation

- Python 3.8+
- Jupyter Notebook or JupyterLab
- Key packages:
  - `pandas` for data handling
  - `numpy` (<2.0 for compatibility)
  - `scikit-surprise` for recommendation algorithms
  - `scikit-learn` for evaluation metrics

### Automated Installation

Dependencies are automatically managed via:
- `requirements.txt` (for pip/devcontainer)
- `environment.yml` (for conda/Binder)

If installing manually: `pip install -r requirements.txt` or `conda env create -f environment.yml`

## Acknowledgments

- Brand popularity weights based on hypothetical market research data
- Evaluation methodology follows recommender systems best practices
- Synthetic dataset is based off of **2024 Pinkbike Community Survey**
   - [2024 Survey](https://www.pinkbike.com/news/pinkbikes-2024-community-survey-what-bikes-do-pinkbike-readers-ride.html)
   - [Comparisons to 2021 Survey](https://www.pinkbike.com/news/pinkbikes-2024-community-survey-key-comparisons-from-our-2021-dataset.html)