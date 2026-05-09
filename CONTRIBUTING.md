# Contributing to legal-rag-eval

Thanks for considering. PRs welcome — this framework is meant to be community-owned.

## High-priority contributions

1. **New jurisdiction adapters** — KR, JP, EU member states especially. Pattern lives in `runners/jurisdictions/`.
2. **System runners** — add a new legal AI tool to the leaderboard. Implement `runners/systems/<system>.py` interface.
3. **Methodology critique** — open an issue tagged `methodology`. We respond within 7 days.
4. **Bluebook normaliser improvements** — `evals/citation/normalize.py` has edge cases catalogued.
5. **Test queries** — submit hand-verified query/ground-truth pairs in `datasets/community/`.

## Process

1. Fork → branch → PR
2. Tag your PR with the relevant area (`jurisdiction:KR`, `system:<name>`, `methodology`, `citation`, etc.)
3. CI runs the deterministic eval suite + hash check
4. Review SLA: 7 days for substantive PRs, 48 hours for typo / docs

## What we won't merge

- Closed-source system adapters (we're an open framework)
- Methodology that can't be reproduced from public sources
- Score-tweaking that hasn't been calibrated against humans
- Commercial promotion without methodology contribution

## Code style

- Python 3.10+, type-hinted, `ruff` formatted
- One adapter / runner per file
- Every public function has a docstring with example

## License & CLA

Apache 2.0. By contributing you agree your contributions are licensed under Apache 2.0. No CLA required.

## Communication

- Issues for bugs / methodology
- Discussions for design proposals
- Discord for chat: [discord.gg/apertis](https://discord.gg/apertis)
- Email for security: hi@apertis.ai
