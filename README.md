# Can a language model build a working game from one sentence?

An **independent, reproducible benchmark**: 60 large language models across 8 vendors, each given the *same* one-line prompt — `create a sudoku game with jazz music.` — and asked to generate a complete, playable **Sudoku** game. Every game was then machine-tested in a real browser for whether it actually **renders**, encodes a **valid puzzle**, and can be **played to a recognized win**.

**▶ Read the study:** https://anselmotalotta.github.io/sudoku-llm-study/

- **60** models · **8** vendors · **41** delivered a working game · **23** were correct *and* cleanly rendered.
- Every generated game is published in [`/games/`](games/) and is playable in your browser (jazz soundtrack included).
- Screenshots of every evaluated game are in [`/assets/`](assets/).

Games were created with **[PlayPrompt](https://playprompt.org)** — an agentic AI platform that turns a single prompt into a complete, ready-to-play browser game, generating the gameplay, the music, and (when needed) the visual assets. In this study only the underlying text model was swapped.

---

*Single prompt, single run per model, 2026-06-23. Independent benchmark for informational purposes; not affiliated with, sponsored by, or endorsed by any model vendor. All product and model names are trademarks of their respective owners and are used solely to identify the models tested. Costs are estimates from published list prices. Results may not reproduce exactly due to model non-determinism.*
