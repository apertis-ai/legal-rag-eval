# legal-rag-eval

**Open evaluation framework for legal RAG and citation verification systems.**

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE)
[![Status: alpha](https://img.shields.io/badge/Status-alpha-orange)](#status)

Reproducible benchmarks for legal AI tools — Verbatim, Westlaw, CoCounsel, LlamaParse, GPT-4o, and any system you want to add. Methodology builds on [Stanford RegLab's 2025 hallucination paper](https://dho.stanford.edu/wp-content/uploads/Legal_RAG_Hallucinations.pdf).

Live results: **[apertis.ai/verbatim/leaderboard](https://apertis.ai/verbatim/leaderboard)** (refreshed weekly)

---

## Why this exists

Stanford benchmarked the major legal AI tools in 2025:

| System | Citation accuracy | Hallucination rate |
|---|---|---|
| Lexis+ AI | 65% | <3% |
| CoCounsel (Thomson Reuters) | 49% | — |
| Westlaw AI-Assisted Research | 42% | 5-6% |

None of these systems publish their benchmark numbers. Most don't expose APIs to reproduce them.

This project does both — open methodology, reproducible runs, public live dashboard.

## Status

🟠 **Alpha (2026-05-09)** — methodology stub + dataset references in place. First public run targets **Verbatim GA day, 2026-06-09**.

Roadmap to v0.1.0:
- [ ] Dataset adapter for Stanford RegLab corpus
- [ ] Runner skeleton for Verbatim, Westlaw API, CoCounsel API, LlamaParse, GPT-4o-direct
- [ ] Citation accuracy scorer (Bluebook-aware)
- [ ] Hallucination detector (LLM-judge with calibration)
- [ ] Multi-jurisdiction adapter (US, KR, TW, JP, EU)
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

1. New jurisdiction adapters (especially KR, JP, EU member states)
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
