# Signal to Insight

**Portfolio:** https://kceniab.github.io/signal-to-insight/

Data science portfolio exploring biosignals, wearable devices, sports performance, and AI. 

---

## Live Projects

### NB01 · MMASH: Activity, Sleep & HRV Exploration
Exploratory analysis of the [MMASH dataset](https://physionet.org/content/mmash/1.0.0/) (Multilevel Monitoring of Activity and Sleep in Healthy People, PhysioNet). Covers behavior distributions, RR interval dynamics, RMSSD-based HRV, and multi-day physiological patterns across 22 subjects.

**Tools:** pandas, numpy, matplotlib, seaborn, scipy

### NB08 · Sport Biomechanics Literature Navigator
AI-powered research assistant that fetches real PubMed abstracts, builds a knowledge graph, and uses RAG + LLM synthesis to answer biomechanics questions with cited evidence.

**Pipeline:** PubMed E-utilities API → overlapping chunk windows → `all-MiniLM-L6-v2` embeddings → NetworkX knowledge graph → cosine similarity retrieval → LLaMA 3.3 70B via Groq API

**Tools:** sentence-transformers, NetworkX, Groq API, pandas

#### Running NB08
The repo includes pre-computed files so you can skip the PubMed fetch:
- `notebooks/data/chunks.csv` — chunked abstracts
- `notebooks/data/embeddings.npy` — pre-computed sentence embeddings

The only API key required is **Groq** (free at [console.groq.com](https://console.groq.com)) for the LLM synthesis step. Create a `.env` file in the `notebooks/` folder:
```
GROQ_API_KEY=your_key_here
```

(add the `.env` file in the .gitignore) 

Install dependencies:
```bash
pip install groq sentence-transformers==2.7.0 transformers==4.40.0 "numpy<2" networkx requests python-dotenv
```

---

## Interactive Tools

- **Running Training Planner** — pace zones, weekly load, taper planning, 400m lap times calculator
- **From Beat to Pace** — music BPM to running cadence matcher


---

## Project Building (In Progress)

| # | Title | Domain |
|---|-------|--------|
| NB02 | Activity Detection: Supervised vs Unsupervised | ML · Wearables |
| NB03 | ECG & PPG Signal Processing | Biosignals · DSP |
| NB04 | Sleep Staging & Cardiac Dynamics | Sleep · HRV |
| NB06 | Running Shoe Drop vs Race Performance (1975–2024) | Sports · Biomechanics |
| NB07 | Music BPM × Running Pace | Audio · Sports |
| NB09 | Banking Churn & Customer Lifetime Value | Consulting · ML |


---

## Repository Structure

```
notebooks/          # analysis notebooks
notebooks/figures/  # generated plots
notebooks/data/     # cached data (chunks, embeddings)
figures/            # portfolio site figures
index.html          # portfolio website (GitHub Pages)
running_training_planner.html
session_builder.html
```

---

## Stack

Python 3.11 · pandas · numpy · scikit-learn · matplotlib · sentence-transformers · NetworkX · Groq API · Plotly
