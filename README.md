# Generating Sudoku with 60 language models

An **independent, reproducible generation study**: 60 LLMs across 8 vendors received one identical prompt — `create a sudoku game with jazz music.` — and each output was rendered, validated, **played to a win** in a real browser, and **published here**.

**▶ Read the study:** https://anselmotalotta.github.io/sudoku-llm-study/

- 60 models · 8 vendors · 41 delivered · 23 correct **and** cleanly rendered.
- Every generated game is in [`/games/`](games/) (playable), every screenshot in [`/assets/`](assets/), the per-model data in [`/data/`](data/).
- The **exact prompt** sent to every model — the end-user sentence *and* the full system instruction — is disclosed in Appendix B of the study.

**Conflict of interest, stated up front:** this study is produced by **[PlayPrompt](https://playprompt.org)**, which sells an AI game-generation platform. PlayPrompt has no model of its own in the comparison (it orchestrates third-party models), its own production-default model was among the weakest here, and all artifacts are published so anyone can re-run or re-score. See the study's Disclosure and Threats-to-Validity sections.

---

*v1.0 · run date 2026-06-23 · single prompt, single run per model. Independent, point-in-time study; not affiliated with, sponsored by, or endorsed by any model vendor. All product/model names are trademarks of their owners, used nominatively. Costs are estimates from published list prices. Results may not reproduce exactly due to model non-determinism.*
