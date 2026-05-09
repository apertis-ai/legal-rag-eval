# runners/

System adapters. Each file implements the `Runner` protocol and routes a query to a target legal AI system.

| File | System | Status |
|---|---|---|
| `verbatim.py` | Verbatim API (apertis.ai/verbatim) | 🟠 stub |
| `westlaw.py` | Westlaw AI-Assisted Research API | 🟠 stub |
| `cocounsel.py` | CoCounsel (Thomson Reuters) API | 🟠 stub |
| `lexis.py` | Lexis+ AI API | 🟠 stub |
| `llamaparse.py` | LlamaParse + downstream LLM | 🟠 stub |
| `gpt4o_direct.py` | GPT-4o direct (no RAG, baseline) | 🟠 stub |

To add a system: implement `runners/systems/<name>.py` matching the `Runner` protocol. See [CONTRIBUTING.md](../CONTRIBUTING.md).

Implementation lands at v0.1.0 (target: 2026-06-09).
