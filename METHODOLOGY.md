# Methodology

Builds on [Stanford RegLab's 2025 hallucination paper](https://dho.stanford.edu/wp-content/uploads/Legal_RAG_Hallucinations.pdf). Public, reproducible, PR-able.

## Test categories

Adapted from Stanford 2025:

| Category | What it measures | Sample size target |
|---|---|---|
| **Case retrieval** | Does the system surface the most relevant case for a fact pattern? | 500 queries |
| **Statutory interpretation** | Does the system correctly cite the controlling statute and recent amendments? | 500 queries |
| **Regulatory analysis** | Does the system trace authority correctly across agency rules? | 300 queries |
| **Multi-jurisdictional** | Does the system distinguish jurisdictional differences when asked? | 300 queries |
| **Brief drafting assistance** | Are facts and citations grounded in the cited sources? | 200 queries |

## Scoring

### Citation accuracy

Each cited authority is normalised to Bluebook canonical form, then matched against ground truth:

- **Exact match** — full citation matches (case, reporter, page, year)
- **Partial match** — case name + year correct, reporter ambiguity allowed
- **Wrong** — citation refers to a different case or doesn't exist

Score = (exact + 0.5 × partial) / total citations.

### Hallucination rate

Each fact statement in the response is scored against the cited authority:

- **Grounded** — fact is supported by the cited source
- **Contradicted** — fact is contradicted by the cited source
- **Unsupported** — cited source doesn't address the fact
- **Fabricated** — citation refers to non-existent authority

Hallucination rate = (contradicted + unsupported + fabricated) / total facts.

LLM-judge: GPT-4o + Claude Opus 4.7 ensemble, human-calibrated on 200-sample stratified subset (target inter-rater agreement κ ≥ 0.8).

## Datasets

### Primary
- **Stanford RegLab legal hallucination corpus** — public dataset, ground truth verified by Stanford team
- **Harvard Caselaw Access Project (CAP)** — 6.7M US case law records, public
- **CourtListener** — federal case law + audio, public

### Multi-jurisdictional
- **Korea**: Korean Law Information Center (law.go.kr) — public statutes, judgments
- **Taiwan**: Judicial Yuan Law Database (judicial.gov.tw) — public judgments
- **Japan**: Japan Courts Case Search (courts.go.jp) — public court decisions
- **EU**: EUR-Lex — public regulations and case law

## Reproducibility

Every run logs:
- Dataset hash (SHA-256 of normalized corpus)
- Model versions and parameters
- Prompt templates
- Random seeds
- System adapter version

Results are deterministic given the same inputs. CI runs hash-comparison against locked baselines on every PR.

## Statistical reporting

- Confidence intervals via bootstrap (1000 resamples, 95% CI)
- Per-category and aggregate scores reported
- Sample size justification per category in `evals/<category>/SAMPLES.md`

## Known limitations

1. **Bluebook normalisation is imperfect** — edge cases (parallel citations, supplements) tracked in `evals/citation/EDGE_CASES.md`
2. **LLM-judge has bias** — calibration set is reported per release; humans label new samples on every methodology change
3. **English-language bias** — ground truth quality varies across jurisdictions; CJK and EU corpora are alpha quality at v0.1

## Versioning

Methodology version is tagged on every release (e.g., `v0.1.0-methodology`). Score comparisons across methodology versions are not directly comparable — see `CHANGELOG.md`.

## Get involved

- Critique methodology: open an issue tagged `methodology`
- Add jurisdiction: see [CONTRIBUTING.md](CONTRIBUTING.md)
- Cite issues: tag `citation-edge-case`
