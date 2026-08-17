<h1 align="center">
  <strong>Music Research Corpus</strong>
</h1>
<h3 align="center">Agentic literature review of music research — generation, MIR, perception & cognition, AI music systems, evaluation</h3>

### 🔗 Links

- **GitHub**: https://github.com/tobias-weiss-ai-xr/music-research
- **License**: https://github.com/tobias-weiss-ai-xr/music-research/blob/main/LICENSE
- **CI**: https://github.com/tobias-weiss-ai-xr/music-research/actions/workflows/validate.yml
- **Agent Learning**: https://github.com/tobias-weiss-ai-xr/agent-learning-research
- **Learning**: https://github.com/tobias-weiss-ai-xr/learning-research


> 🎵 **Music research corpus:** music generation, music information retrieval,
> perception & cognition, AI music systems, and evaluation — analyzed with the
> same pipeline as the other `*-research` corpus repos.

<p align="center">
  <img src="https://raw.githubusercontent.com/tobias-weiss-ai-xr/music-research/main/assets/visualizations/category_distribution.png" alt="Teaser" width="600" />
</p>

---

## What you get

| Capability | How |
|------------|-----|
| 📄 **Curated corpus** | `papers.yaml` is the source of truth — one structured entry per paper |
| ✅ **Auto-validation** | `scripts/validate_papers.py` checks schema, duplicates, URL normalization, LaTeX artifacts |
| 🧾 **Auto-generated README** | `scripts/generate_readme.py` renders the paper list grouped by your taxonomy |
| 📊 **Statistics & trends** | `scripts/standard_stats.py` → `statistics.json` (momentum, gaps, bursts, venues, authors) |
| 🔍 **Literature review report** | `scripts/analysis/generate_reports.py` → `docs/research/literature_review.md` + `trends.md` |
| 🧭 **Topic planning** | `tools/topic_planner.py`, `tools/trend_scanner.py`, `tools/landscape_analyzer.py`, `tools/brief_generator.py` |
| 🔎 **New paper discovery** | `scripts/fetch/fetch_new_papers.py` (arXiv), `fetch_other_sources.py` (dblp/crossref/europepmc), `fetch_openalex_bulk.py` |
| 🐙 **GitHub repos discovery** | `scripts/fetch/fetch_github_repos.py` (config-driven via `github_queries` in taxonomy.yaml) |
| 🖥️ **GitHub Pages site** | `docs/index.html` — searchable, filterable paper browser |
| 🤖 **Agentic workflow** | `AGENTS.md` + `config/taxonomy.yaml` make this repo agent-friendly by design |

## 🚀 Quick Start

```bash
# 1. Clone
git clone https://github.com/tobias-weiss-ai-xr/music-research.git
cd music-research

# 2. Install dependencies
pip install -r requirements.txt

# 3. Validate + generate
python3 scripts/validate_papers.py
python3 scripts/generate_readme.py
python3 scripts/standard_stats.py
python3 scripts/analysis/generate_reports.py
```

## 📖 How it works

```
config/taxonomy.yaml ──► papers.yaml ──► validate_papers.py
                          │   ▲              │
                          ▼   └── fetch_* ───┘
                   generate_readme.py ──► README.md (auto)
                          │
                          ▼
                  standard_stats.py ──► statistics.json, docs/papers.json
                          │
                          ▼
              analysis/generate_reports.py ──► docs/research/*.md
```

- **Never edit README.md directly** — it is generated from `papers.yaml`.
- The **taxonomy lives in one place** (`config/taxonomy.yaml`); every script reads it via `scripts/research_config.py`.
- **CI (validate.yml)** runs on every push/PR and weekly to discover new papers.

## 🧪 Local pipeline (all in one)

```bash
# Full pipeline (validate → README → stats → reports)
python3 scripts/validate_papers.py && \
python3 scripts/generate_readme.py && \
python3 scripts/standard_stats.py && \
python3 scripts/analysis/generate_reports.py
```

## 🤖 Agentic workflow (AGENTS.md)

This repo is designed to be driven by coding agents (OpenCode, Claude Code, …):

- **Spec-style guardrails** in `AGENTS.md` — agents know the pipeline, never edit README, always re-validate.
- **One config file** to change → one re-run to verify (low context cost for agents).
- **Auto-validation** gives agents an objective pass/fail signal.
- **Weekly discovery** keeps the corpus fresh without human babysitting.

## 📊 Corpus Statistics

**51 papers** across **6 categories**.  
Sources: **arXiv** 51 (100%).  
Full paper list: [GitHub Pages site](https://tobias-weiss-ai-xr.github.io/music-research).

### Top categories

| Category | Papers | Recent | |
|----------|--------|--------|-|
| analysis | **13** | 0 | ████████████ |
| generation | **12** | 0 | ███████████░ |
| evaluation | **9** | 0 | ████████░░░░ |
| cognition | **6** | 0 | █████░░░░░░░ |
| survey | **6** | 0 | █████░░░░░░░ |
| systems | **5** | 0 | ████░░░░░░░░ |


### By year

| Year | Papers | |
|------|--------|-|
| 2024 | 1 | ░░░░░░░░░░░░ |
| 2025 | 23 | ████████████ |
| 2026 | 18 | █████████░░░ |


### Momentum (hottest categories)

| Category | Total | Rate | Recent | Score |
|----------|-------|------|--------|-------|
| Cognition | 6 | 0.5/mo | 100% | 100 |
| Evaluation | 9 | 0.8/mo | 100% | 100 |
| Systems | 5 | 0.3/mo | 80% | 80 |
| Analysis | 13 | 0.8/mo | 69% | 69 |
| Generation | 12 | 0.6/mo | 58% | 58 |


### Trending keywords

| Keyword | Papers | Burst |
|---------|--------|-------|
| agent | 4 | 1.34 |
| skill | 4 | 1.34 |
| diffusion | 3 | 1.34 |
| reinforcement | 2 | 1.34 |
| multi-agent | 2 | 1.34 |
| planning | 2 | 1.34 |
| imitation | 2 | 1.34 |
| reward | 1 | 1.34 |


### Top venues

| Venue | Papers |
|-------|--------|
| NeurIPS 2023 | 1 |
| ICLR 2019 | 1 |
| ACM Multimedia 2020 | 1 |
| NeurIPS 2022 | 1 |
| ICLR 2022 | 1 |
| IJCNN 2024 | 1 |
| ISMIR 2023 | 1 |
| ACL 2024 | 1 |


### Research gaps (thinnest cells)

| Cell | Papers |
|------|--------|
| `systems/multimodal` | 1 |
| `cognition/audio` | 2 |
| `cognition/multimodal` | 2 |
| `cognition/agentic` | 2 |
| `survey/multimodal` | 3 |



*Generated 2026-08 by `scripts/standard_stats.py`.*

## 📖 Citation

If you use this research corpus, please cite:

```bibtex
@misc{music-research,
  author = {Weiß, Tobias},
  title = {Music Research Corpus: Data-Driven Agentic Literature Review},
  year = {2026},
  publisher = {GitHub},
  url = {https://github.com/tobias-weiss-ai-xr/music-research}
}
```

## 📄 License

MIT — see [LICENSE](LICENSE).
