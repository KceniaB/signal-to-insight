# 09 — Expected Goals (xG) Model: World Cup 2022

**Sports Analytics · Machine Learning · Spatial Data**

A shot-quality model trained on full event and 360 freeze-frame data from the FIFA World
Cup 2022 (64 matches, 1,494 shots), built to estimate the probability that any given shot
becomes a goal — and benchmarked directly against StatsBomb's own published xG values.

## Why this project

Built as a focused extension of the predictive-modeling and time-series methods used
throughout the rest of this portfolio's neuroscience work, applied to a new domain:
football performance data. Same toolkit (feature engineering → classification → calibrated
evaluation), new signal.

## Result

| Model | AUC | LogLoss | Brier |
|---|---|---|---|
| Logistic Regression (geometry + context) | 0.799 | 0.298 | 0.085 |
| XGBoost (geometry + context) | 0.813 | 0.298 | 0.087 |
| **XGBoost + 360 freeze-frame** | **0.814** | **0.225** | **0.062** |
| StatsBomb xG (proprietary benchmark) | 0.887 | 0.218 | 0.065 |

The model lands within ~0.07 AUC of StatsBomb's commercial xG model, using only public
open data — no proprietary tracking feed, no ball/player speed — and is well-calibrated
(predicted probabilities track observed goal rates closely across the full range).

## Notebook

[`09_xg_model_worldcup2022.ipynb`](09_xg_model_worldcup2022.ipynb) — full pipeline,
data pull through evaluation, fully executed with outputs.

#### DATASET
FIFA World Cup 2022 — 64 matches · StatsBomb Open Data (CC BY-NC-SA 4.0)

#### FEATURES
Shot distance & angle, body part, shot type/technique, pressure, 360 freeze-frame
defenders-in-cone & goalkeeper distance

#### MODELS
Logistic Regression baseline, XGBoost (geometry-only and +360 variants)

#### EVALUATION
ROC-AUC, log-loss, Brier score, calibration curve — benchmarked against StatsBomb's
own xG

## A feature worth highlighting

Counting opposing players in the shooter's angular cone toward goal (derived from 360
freeze-frame data) produces a clean, monotonic relationship with scoring probability:

| Defenders in shot cone | Goal conversion rate | n shots |
|---|---|---|
| 0 | 35.0% | 117 |
| 1 | 12.4% | 688 |
| 2 | 5.3% | 419 |
| 3+ | 1.9% | 212 |

This single feature meaningfully improved both log-loss and calibration over geometry
alone — a direct, data-confirmed version of the basic football intuition that a blocked
shooting lane lowers scoring chances regardless of distance or angle.

## Stack

Python · pandas · NumPy · scikit-learn · XGBoost · statsbombpy · Matplotlib

## Next steps

- Possession-value / expected threat (xT) modeling — valuing all on-ball actions, not just shots
- Match outcome prediction from aggregated team-level xG
- Re-running this pipeline on World Cup 2026 shot data once open event data is released

---

Dataset: [StatsBomb Open Data ↗](https://github.com/statsbomb/open-data) (CC BY-NC-SA 4.0)
