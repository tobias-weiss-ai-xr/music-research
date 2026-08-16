<h1 align="center">
  <strong>Music Research Corpus</strong>
</h1>
<h3 align="center">Agentic literature review of music research — generation, MIR, cognition, evaluation</h3>

<div align="center">

[![License](https://img.shields.io/badge/License-MIT-yellow.svg?)](LICENSE)
[![CI](https://img.shields.io/github/actions/workflow/status/tobias-weiss-ai-xr/music-research/validate.yml?label=CI&logo=github)](https://github.com/tobias-weiss-ai-xr/music-research/actions/workflows/validate.yml)
[![GitHub Pages](https://img.shields.io/badge/Demo-GitHub%20Pages-brightgreen.svg?logo=github)](https://tobias-weiss-ai-xr.github.io/music-research/)

</div>

> 🎵 **All sorts of music research, one corpus.** Data-driven, auto-validated,
> agentic literature review built from the `skeleton-research` template —
> papers live in `papers.yaml`, everything else is generated.

## Scope

The corpus covers music research across symbolic, audio, multimodal and
agentic lines of work:

| Category | What lives here |
|----------|-----------------|
| 🎼 **Music Generation & Composition** | text-to-music, symbolic generation, long-form structure |
| 🔬 **Music Analysis & Understanding** | MIR: transcription, source separation, embeddings, captioning |
| 🧠 **Music Perception & Cognition** | music psychology, neuroscience, emotion, cognition |
| 🤖 **AI Music Systems & Agents** | LLM-based music systems, agentic composition frameworks |
| 📏 **Evaluation & Benchmarks** | metrics, datasets, benchmarking protocols |
| 📚 **Surveys & Taxonomies** | reviews and taxonomies of the field |

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

## 🚀 Jump-start (5 steps)

```bash
# 1. Clone
git clone https://github.com/tobias-weiss-ai-xr/music-research.git
cd music-research

# 2. (Re)define the topic & taxonomy
#    Edit config/taxonomy.yaml: topic name, categories, subcategories, queries
vim config/taxonomy.yaml

# 3. Seed/extend your corpus (start small — 5-10 papers is fine)
#    Either hand-curate papers.yaml, or auto-discover:
python3 scripts/fetch/fetch_new_papers.py --months 12 --dry-run   # preview arXiv hits
python3 scripts/fetch/fetch_new_papers.py --local                 # append to papers.yaml

# 4. Validate + generate
python3 scripts/validate_papers.py
python3 scripts/generate_readme.py
python3 scripts/standard_stats.py
python3 scripts/analysis/generate_reports.py

# 5. Commit & let CI keep it healthy
git add -A && git commit -m "update music corpus"
git push
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

## 📚 Paper list

- [📚 Music Generation & Composition](#music-generation-&-composition)
  - [Audio](#audio)
  - [Symbolic](#symbolic)
- [📚 Music Analysis & Understanding](#music-analysis-&-understanding)
  - [Audio](#audio)
  - [Multimodal & Text](#multimodal-&-text)
- [📚 Music Perception & Cognition](#music-perception-&-cognition)
  - [Audio](#audio)
  - [Multimodal & Text](#multimodal-&-text)
  - [Agentic & LLM](#agentic-&-llm)
- [📚 AI Music Systems & Agents](#ai-music-systems-&-agents)
  - [Multimodal & Text](#multimodal-&-text)
  - [Agentic & LLM](#agentic-&-llm)
- [📚 Evaluation & Benchmarks](#evaluation-&-benchmarks)
  - [Audio](#audio)
  - [Agentic & LLM](#agentic-&-llm)
- [📚 Surveys & Taxonomies](#surveys-&-taxonomies)
  - [Audio](#audio)
  - [Multimodal & Text](#multimodal-&-text)

### Music Generation & Composition

#### Audio

##### 2026

- [2026] **MusicLayout: Explicit Structural Planning for Controllable Text-to-Music Generation** [[paper](https://arxiv.org/abs/2608.09035)]
- [2026] **Pushing the Frontier of Full-Song Generation: Hierarchical Autoregressive Planning Meets Flow-Matching Rendering** [[paper](https://arxiv.org/abs/2607.20253)]
- [2026] **Shao: Scaling Acoustic Token Language Models Toward High-Fidelity Music Generation** [[paper](https://arxiv.org/abs/2605.01790)]

##### 2023

- [2023] **Simple and Controllable Music Generation** *NeurIPS 2023* [[paper](https://arxiv.org/abs/2306.05284)] [[code](https://github.com/facebookresearch/audiocraft)]
- [2023] **MusicLM: Generating Music From Text** [[paper](https://arxiv.org/abs/2301.11325)]

[⬆ Back to top](#paper-list)

#### Symbolic

##### 2026

- [2026] **Diff-Symbo: Text-Controlled Long-Duration Symbolic Music Generation Using Autoregressive Latent Diffusion Model** [[paper](https://arxiv.org/abs/2608.05222)]
- [2026] **BeatEdit: Symbolic Music Generation as Explicit Editing** [[paper](https://arxiv.org/abs/2607.11124)] [[code](https://github.com/Haoyu-Gu/BeatEdit-code)]
- [2026] **MIDI-RAE-JEPA: Hierarchical Representation Learning and Generation for Symbolic Music** [[paper](https://arxiv.org/abs/2607.14537)]

##### 2025

- [2025] **SAGE-Music: Low-Latency Symbolic Music Generation via Attribute-Specialized Key-Value Head Sharing** [[paper](https://arxiv.org/abs/2510.00395)]

##### 2022

- [2022] **Museformer: Transformer with Fine- and Coarse-Grained Attention for Music Generation** *NeurIPS 2022* [[paper](https://arxiv.org/abs/2210.10349)] [[code](https://github.com/microsoft/muzic/tree/main/museformer)]

##### 2020

- [2020] **Pop Music Transformer: Beat-based Modeling and Generation of Expressive Pop Piano Compositions** *ACM Multimedia 2020* [[paper](https://arxiv.org/abs/2002.00212)] [[code](https://github.com/sander-wood/pop-music-transformer)]

##### 2018

- [2018] **Music Transformer** *ICLR 2019* [[paper](https://arxiv.org/abs/1809.04281)] [[code](https://github.com/magenta/music-transformer)]

[⬆ Back to top](#paper-list)

### Music Analysis & Understanding

#### Audio

##### 2026

- [2026] **MuScriptor: An Open Model for Multi-Instrument Music Transcription** [[paper](https://arxiv.org/abs/2607.08168)]
- [2026] **Music-Source-Separation-Training (MSST): A Unified Framework for Training and Evaluating Music Demixing Models** [[paper](https://arxiv.org/abs/2607.23395)]

##### 2023

- [2023] **MERT: Acoustic Music Understanding Model with Large-Scale Self-supervised Training** *IJCNN 2024* [[paper](https://arxiv.org/abs/2306.00107)] [[code](https://github.com/yizhilll/MERT)]

##### 2021

- [2021] **MT3: Multi-Task Multitrack Music Transcription** *ICLR 2022* [[paper](https://arxiv.org/abs/2111.03017)] [[code](https://github.com/magenta/mt3)]

##### 2019

- [2019] **Music Source Separation in the Waveform Domain** [[paper](https://arxiv.org/abs/1911.13254)] [[code](https://github.com/facebookresearch/demucs)]

[⬆ Back to top](#paper-list)

#### Multimodal & Text

##### 2025

- [2025] **Music Flamingo: Scaling Music Understanding in Audio Language Models** [[paper](https://arxiv.org/abs/2511.10289)]
- [2025] **Enhancing Automatic Chord Recognition through LLM Chain-of-Thought Reasoning** [[paper](https://arxiv.org/abs/2509.18700)]

##### 2023

- [2023] **LP-MusicCaps: LLM-Based Pseudo Music Captioning** *ISMIR 2023* [[paper](https://arxiv.org/abs/2307.16372)] [[code](https://github.com/seungheondoh/LP-MusicCaps)]

[⬆ Back to top](#paper-list)

### Music Perception & Cognition

#### Audio

##### 2026

- [2026] **MindMelody: A Closed-Loop EEG-Driven System for Personalized Music Intervention** [[paper](https://arxiv.org/abs/2605.01235)]

[⬆ Back to top](#paper-list)

#### Multimodal & Text

##### 2026

- [2026] **Musical Training, but not Mere Exposure to Music, Drives the Emergence of Chroma Equivalence in Artificial Neural Networks** [[paper](https://arxiv.org/abs/2602.18635)]

[⬆ Back to top](#paper-list)

#### Agentic & LLM

##### 2025

- [2025] **The MUSE Benchmark: Probing Music Perception and Auditory Relational Reasoning in Audio LLMs** [[paper](https://arxiv.org/abs/2510.19055)]

[⬆ Back to top](#paper-list)

### AI Music Systems & Agents

#### Multimodal & Text

##### 2024

- [2024] **ChatMusician: Understanding and Generating Music Intrinsically with LLM** *ACL 2024* [[paper](https://arxiv.org/abs/2402.16153)] [[code](https://github.com/microsoft/muzic/tree/main/chatmusician)]

[⬆ Back to top](#paper-list)

#### Agentic & LLM

##### 2026

- [2026] **Libretto: Giving LLM Agents a Sense of Musical Structure** [[paper](https://arxiv.org/abs/2606.22708)]
- [2026] **MuseAgent-1: Interactive Grounded Multimodal Understanding of Music Scores and Performance Audio** [[paper](https://arxiv.org/abs/2601.11968)]

##### 2025

- [2025] **WeaveMuse: An Open Agentic System for Multimodal Music Understanding and Generation** [[paper](https://arxiv.org/abs/2509.11183)]
- [2025] **CompLex: Music Theory Lexicon Constructed by Autonomous Agents for Automatic Music Generation** [[paper](https://arxiv.org/abs/2508.19603)]

[⬆ Back to top](#paper-list)

### Evaluation & Benchmarks

#### Audio

##### 2026

- [2026] **SongBench: A Fine-Grained Multi-Aspect Benchmark for Song Quality Assessment** [[paper](https://arxiv.org/abs/2604.25937)]

##### 2025

- [2025] **MuseCPBench: an Empirical Study of Music Editing Methods through Music Context Preservation** [[paper](https://arxiv.org/abs/2512.14629)]

[⬆ Back to top](#paper-list)

#### Agentic & LLM

##### 2026

- [2026] **Music I Care About: Automated Multimodal Benchmarking of LLM Music Perception Skills on (Almost) Any Music** [[paper](https://arxiv.org/abs/2607.06015)]
- [2026] **Can LLMs understand LilyPond? A benchmark for symbolic music generation and understanding** [[paper](https://arxiv.org/abs/2606.08722)] [[code](https://github.com/CSCPadova/lilybench)]

##### 2025

- [2025] **ABC-Eval: Benchmarking Large Language Models on Symbolic Music Understanding and Instruction Following** [[paper](https://arxiv.org/abs/2509.23350)]

[⬆ Back to top](#paper-list)

### Surveys & Taxonomies

#### Audio

##### 2025

- [2025] **Aligning Generative Music AI with Human Preferences: Methods and Challenges** [[paper](https://arxiv.org/abs/2511.15038)]
- [2025] **Twenty-Five Years of MIR Research: Achievements, Practices, Evaluations, and Future Challenges** [[paper](https://arxiv.org/abs/2511.07205)]
- [2025] **A Survey on Evaluation Metrics for Music Generation** [[paper](https://arxiv.org/abs/2509.00051)]

[⬆ Back to top](#paper-list)

#### Multimodal & Text

##### 2025

- [2025] **A Survey on Music Generation from Single-Modal, Cross-Modal, and Multi-Modal Perspectives** [[paper](https://arxiv.org/abs/2504.00837)]
- [2025] **A Survey on Multimodal Music Emotion Recognition** [[paper](https://arxiv.org/abs/2504.18799)]
- [2025] **Vision-to-Music Generation: A Survey** [[paper](https://arxiv.org/abs/2503.21254)]

[⬆ Back to top](#paper-list)

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
