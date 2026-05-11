# legal-rag-eval

**Open evaluation framework for legal RAG and citation verification systems.**

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE)
[![Status: alpha](https://img.shields.io/badge/Status-alpha-orange)](#status)

Reproducible benchmarks for legal AI tools — Verbatim, Westlaw, CoCounsel, LlamaParse, GPT-5.5, and any system you want to add. Methodology builds on [Stanford RegLab's 2025 hallucination paper](https://dho.stanford.edu/wp-content/uploads/Legal_RAG_Hallucinations.pdf).

Live results: **[apertis.ai/verbatim/leaderboard](https://apertis.ai/verbatim/leaderboard)** (refreshed weekly)

---

## Why this exists

Two independent academic studies measured leading legal AI tools — and disagreed substantially. **The disagreement is the opportunity.**

### Stanford RegLab (May 2024)

[arXiv:2405.20362](https://arxiv.org/abs/2405.20362) — attorney-validated query test sets.

| System | Citation accuracy | Hallucination rate |
|---|---|---|
| Lexis+ AI | 83% | 17% |
| Westlaw AI-Assisted Research | 66% | 34% |
| CoCounsel (Thomson Reuters) | 51% | 49% |

### VLAIR (Feb 2025)

[Vals Legal AI Report](https://www.vals.ai/benchmarks/vlair-02-25-2025) — task-completion benchmark across 8 legal task types.

| System | Accuracy |
|---|---|
| Harvey | 94.8% |
| CoCounsel | 89.6% |
| Westlaw | 67% |

Same systems, different methodologies, different numbers. Neither result is reproducible without re-purchasing the underlying tools. **Both source studies are static snapshots — there is no live, open, continuously-updated benchmark.**

This project fills that gap: public methodology, reproducible runs, live dashboard updated weekly.

## Status

🟠 **Alpha (2026-05-09)** — methodology stub + dataset references in place. First public run targets **Verbatim GA day, 2026-06-09**.

Roadmap to v0.1.0:
- [ ] Dataset adapter for Stanford RegLab corpus
- [ ] Runner skeleton for Verbatim, Westlaw API, CoCounsel API, LlamaParse, GPT-5.5-direct
- [ ] Citation accuracy scorer (Bluebook-aware)
- [ ] Hallucination detector (LLM-judge with calibration)
- [ ] Multi-jurisdiction adapter (US anchor + Korean legal systems)
- [ ] Live dashboard publisher (writes to apertis.ai/verbatim/leaderboard)
- [ ] CI for weekly auto-run

## Quick start

```bash
git clone https://github.com/apertis-ai/legal-rag-eval.git
cd legal-rag-eval
pip install -e .
legal-rag-eval run --suite reglab-2025 --systems verbatim,gpt4o,westlaw
```

(coming with v0.1.0)

## Methodology

See [METHODOLOGY.md](METHODOLOGY.md) for full details. Highlights:

- **Test categories** mirror Stanford 2025 paper: case retrieval, statutory interpretation, regulatory analysis, multi-jurisdictional, brief drafting
- **Citation accuracy** scored against verified ground truth using Bluebook-format normalisation
- **Hallucination rate** measured via fact-grounding LLM-judge with human-calibrated samples
- **Reproducibility** — every run logs model versions, dataset hashes, prompt templates

## Contributing

PRs welcome. See [CONTRIBUTING.md](CONTRIBUTING.md). Most-wanted contributions:

1. New jurisdiction adapters (Korean legal systems are v1 scope; additional jurisdictions welcome as community research)
2. Additional system runners (LegalMation, Spellbook, Irys, Briefpoint, etc.)
3. Methodology critique — open an issue
4. Bluebook citation normaliser improvements

## Citation

If you use this framework in research:

```bibtex
@software{legal_rag_eval_2026,
  title = {legal-rag-eval: Open Evaluation Framework for Legal RAG Systems},
  author = {Apertis},
  year = {2026},
  url = {https://github.com/apertis-ai/legal-rag-eval}
}
```

## License

Apache License 2.0 — see [LICENSE](LICENSE).

## Maintainers

Maintained by [Apertis](https://apertis.ai). Built alongside [Verbatim](https://apertis.ai/verbatim), our open legal AI infrastructure.

Questions, methodology critique, or want to add a system to the leaderboard? **hi@apertis.ai** or open an issue.
