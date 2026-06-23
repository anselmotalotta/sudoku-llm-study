*(Draft for LinkedIn / Medium. Links point to the live study and playable games.)*

# I asked 60 AI models to build the same game. 23 of them actually could.

**One prompt — “create a sudoku game with jazz music.” — sent to 60 language models. Then I played every game they wrote to see which ones actually worked.**

There’s a lot of noise about which AI model is “best at coding.” Most of it is benchmark scores you can’t see or poke at. So we tried something concrete and a little stubborn: give 60 models from 8 vendors the *exact same* one-line request, have each one generate a complete, self-contained browser game, and then **machine-test every single output** — does it render a real Sudoku grid, is the puzzle actually valid, and can you play it all the way to a win?

Every game is published and playable. You can click any of them below.

👉 **Full study, data, and all 30 playable games:** https://anselmotalotta.github.io/sudoku-llm-study/

## The funnel

- **60** models got the prompt.
- **41** returned a working game.
- **23** produced a Sudoku that was *both* logically correct *and* cleanly rendered.
- 1 built a valid-but-shrunken 4×4 variant; the rest were flawed, broken, or — in a couple of cases — not Sudoku at all.

That gap between “returned something” and “actually works” is the whole story.

## Four things that surprised us

**1. Looking right and working right are different problems.**
The sharpest lesson came from a single model that passed every logic check we threw at it — valid solver, correct win detection — and then rendered **a blank screen with no grid at all**. If we’d graded on code and internal state alone (as a lot of evaluations do), it would have “passed.” A screenshot caught it instantly. The reverse happened too: models that drew a beautiful grid around a puzzle with duplicate digits — impossible to solve. You have to *both* run it and look at it.
[See the broken render →](https://anselmotalotta.github.io/sudoku-llm-study/games/xai-grok-4-3.html)

**2. Spending more didn’t buy more.**
The single most expensive generation in the study produced an **invalid** puzzle. Meanwhile the cheapest clean, fully-playable game cost a fraction of a cent.
[Play the best-value game →](https://anselmotalotta.github.io/sudoku-llm-study/games/gemini-gemini-2-5-flash-lite.html)

**3. The “coder” models punched above their weight.**
Underneath the jazz theme, this is a code-generation task — and the vendors’ coding-tuned models repeatedly delivered fast, cheap, correct boards.
[Play a coder-model build →](https://anselmotalotta.github.io/sudoku-llm-study/games/qwen3-coder-next.html)

**4. One sentence leaves a lot of room.**
Given the same vague request, some models built a standard 9×9 grid and others quietly built a simpler **4×4**. Both are “Sudoku.” Neither is wrong. But it’s a reminder of how much a one-line prompt leaves to interpretation.

## Try a few yourself

- ⚡ Fastest clean build: [gemini-3-flash-preview](https://anselmotalotta.github.io/sudoku-llm-study/games/gemini-gemini-3-flash-preview.html)
- 🧩 Most features: [gpt-5.4](https://anselmotalotta.github.io/sudoku-llm-study/games/gpt-5-4.html)
- 💸 Best value: [gemini-2.5-flash-lite](https://anselmotalotta.github.io/sudoku-llm-study/games/gemini-gemini-2-5-flash-lite.html)

(Yes — the jazz soundtrack is AI-generated too.)

## How we kept it honest

Full disclosure: this study comes from **[PlayPrompt](https://playprompt.org)**, which builds an AI platform that turns a prompt into a playable game. That’s a conflict of interest, so we ran it the only way that’s fair:

- **No home-team advantage.** PlayPrompt has no model of its own in the comparison — it orchestrates third-party models — and no fixed favorite. We ran this partly *to decide* which models to use, so our incentive is an accurate answer, not a flattering one.
- **Identical conditions for all 60.** Same prompt, same setup; only the model changed.
- **Everything is published** — every generated game, every screenshot, the per-model data, and the rubric — so anyone can re-run or re-score it.
- **We even disclose the grader.** The harness (and this analysis) was run with Claude Code; logic verdicts are decided by execution, not opinion, and every screenshot is public so the visual calls can be re-checked.

And the honest caveats: it’s **one prompt, one run per model, on one date**. Sudoku is well-represented in training data, so this measures *building and rendering* a familiar thing, not novel reasoning. Treat it as a relative snapshot, not a definitive ranking.

## Read the whole thing

The full write-up has the complete methodology, the per-model results table, the failure breakdown, threats-to-validity, and all 30 games:

📄 **Study (and PDF):** https://anselmotalotta.github.io/sudoku-llm-study/

If you build with these models, the takeaway is simple: **don’t trust the demo — run it and look at it.** That’s the only way to tell the 23 that work from the 18 that just look like they do.

---

*Independent, point-in-time study · single prompt, single run per model · 2026-06-23. Model names are trademarks of their respective owners, used to identify the systems tested; PlayPrompt is not affiliated with or endorsed by any of them.*
