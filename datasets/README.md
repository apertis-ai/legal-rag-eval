# datasets/

Test corpora and ground truth. Large files are not committed; fetcher scripts pull from public sources on demand.

| Source | Coverage | License |
|---|---|---|
| Stanford RegLab 2025 | US legal hallucination corpus | Stanford terms (research) |
| Harvard CAP | 6.7M US case law records | CC0 / public |
| CourtListener | Federal cases + audio | CC BY-SA |
| 國家法令資訊中心 (KR) | Korean statutes + judgments | Public |
| 司法院法學資料 (TW) | Taiwan judgments | Public |
| 裁判所判例検索 (JP) | Japan court decisions | Public |
| EUR-Lex | EU regulations + case law | EU public |

## community/

Hand-verified test queries from the community. Include `query`, `ground_truth`, `verifier_notes`, `submitter_handle`.

See [CONTRIBUTING.md](../CONTRIBUTING.md) for submission format.
