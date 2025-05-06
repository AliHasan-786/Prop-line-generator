# Prop-line-generator

A lightweight pipeline and notebook that turns full-season NBA box-score data into actionable OVER/UNDER prop lines, powered by a local Mistral LLM via Ollama.

## What It Does
1. **Data Ingestion**  
   Fetches every completed NBA game (2024–25 season) from ESPN’s public JSON API in parallel.  
2. **Statistical Processing**  
   Computes per-player distributions (mean, std, 25th/50th/75th percentiles) for key categories:  
   - Points  
   - Rebounds  
   - Assists  
   - 3-Point Makes  
   - Steals  
   - Blocks  
3. **AI-Driven Line Setting**  
   Feeds those distributions to a local Mistral-7B model (via Ollama), which produces one OVER/UNDER line per player+stat along with a concise, data-backed rationale.  
4. **Visualization**  
   Generates Plotly charts comparing median vs. 75th-percentile values for quick insight into how suggested lines relate to historical performance.

## Prerequisites
- Python 3.8+  
- Ollama CLI with the `mistral` model pulled  
- Libraries: `requests`, `pandas`, `tqdm`, `plotly`

## Getting Started
1. Open `DFS.ipynb` in Colab or Jupyter.  
2. Install Python dependencies:  
   ```bash
   pip install requests pandas tqdm plotly
3. Run all cells to:
   - Ingest and process ESPN box scores
   - Build your prompt.txt for the LLM
   - (Locally) pipe prompt.txt into Ollama to get your prop lines
   - View interactive charts of distributions vs. suggested lines

## Output
- `dist_df`: DataFrame of distribution metrics for top performers
- `prompt.txt`: JSON-based prompt for Mistral
- LLM output: A clean list of OVER/UNDER prop lines with one-sentence rationales
- Plotly charts: Visual comparison of historical percentiles vs. proposed lines
