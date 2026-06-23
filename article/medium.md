# We gave 72 AI models one Sudoku to build — and the cheapest one won

*Ten vendors, one lazy sentence, and a great deal of confidence — some of it earned, some of it pure bluff. The cheapest model that actually worked turned out to be free. Here is who can turn a prompt into a working game, and who only looks the part.*

Every AI lab will tell you its models can code. Of course they will. The more interesting question is what happens when the rubber meets the road: hand a model a vague human request and ask it for something that actually runs. Most benchmarks won't tell you, because they're either invisible — you get a score, not the work — or so abstract they look nothing like building a thing a person would use. So we ran a small, slightly mischievous experiment instead. We gave seventy-two models, from ten vendors, the same throwaway sentence — *create a sudoku game with jazz music.* — and watched to see who came back with a real, playable game and who came back with something that only looked the part.

Sudoku is a wonderful instrument for this, precisely because it's so unglamorous. Everyone knows it, it has no graphics or physics to hide behind, and "correct" isn't a matter of taste: a grid either holds a valid puzzle you can solve to a genuine win, or it doesn't. That clean line lets us pull apart two things that usually travel together — *does it look like a Sudoku* and *is it a working Sudoku* — and the gap between them turned out to be the best part of the whole exercise.

## The field

Here is everyone who showed up, and the model classes each vendor brought to the table:

- **Anthropic (Claude).** A large, reasoning-heavy Opus tier and a small, quick Haiku tier. Famous for careful code; sits near the top of the price list.
- **OpenAI (GPT).** The GPT-5 family, from a heavyweight "pro" down to mini and nano sizes, plus a codex variant built for programming. The household name, and pricey at the top.
- **Google (Gemini).** A Pro flagship next to the Flash and Flash-Lite tiers, engineered for speed and a tiny bill.
- **xAI (Grok).** The Grok-4 reasoning models — the youngest line in the room.
- **DeepSeek.** The V4 family: cheap, widely available, and a quiet overachiever on code.
- **Mistral.** A Large flagship, two coding specialists (Codestral and Devstral), and small Ministral models. The lean European entry.
- **MiniMax.** The M-series, built around long context windows and low prices.
- **Alibaba (Qwen).** The biggest, cheapest spread of the lot: a Max flagship, Plus and Flash tiers, and a dedicated Coder line.
- **Zhipu (GLM).** China's GLM line — a GLM-5 flagship, a mid-size Air, and, unusually, a genuinely *free* Flash tier.
- **Moonshot (Kimi).** The Kimi K2 reasoning models, plus an older Moonshot-v1 chat family.

The obvious bet is that a coding task rewards the biggest, most expensive, most capable models. It's a reasonable bet. It's also, as it turns out, wrong — and watching it fall apart is the fun of this.

## The test

Every model got the identical prompt under identical conditions; the only thing that changed from run to run was the model. Then each result was loaded in a real browser and put through three checks: does it draw a 9×9 grid, is the puzzle it builds actually valid, and can you fill it in and have the game recognise a win? We logged the time and the cost for every one.

## What the results show

Of the seventy-two models, fifty-one returned a working game, and twenty-nine produced a Sudoku that was both correct and cleanly rendered. One built a perfectly valid but shrunken 4×4 board; the rest were unsolvable, broken, or — in a few memorable cases — not Sudoku at all. So a little over a third nailed it cold, on the first try. Three things in that result are worth lingering on.

**Looking right and working right are different skills, and models flunk them independently.** My favourite failure of the whole study: one model wrote a flawless solver and a flawless win-check, and then drew absolutely nothing — the page loaded with no grid on it at all. Inspect only the code or the program's internal state and it sails through; one screenshot and the illusion collapses. The opposite was just as common, a crisp, well-styled grid wrapped around a puzzle with repeated digits and no solution. The takeaway is unglamorous but important: if you're shipping AI-written software, reading the code or trusting the model's own summary won't save you. You have to run it and look at it.

![Sudoku Swing, from one of Qwen's coding-tuned models — correct, polished, and one of the cheapest results in the test.](https://anselmotalotta.github.io/sudoku-llm-study/article/img-1.png)

**Price and prestige barely mattered — and that's the genuinely fun part.** The fast, cheap, correct games came overwhelmingly from the smaller tiers and the coding-specialised models, not the flagships. The single most expensive run in the study confidently handed back an invalid puzzle. And the cheapest correct game of the entire field came from a model that costs nothing at all — Z.ai's free GLM-4.5-Flash built a clean, valid board for $0. None of this means the big models are weak; it means that for a clear, bounded job like this one, the extra money simply didn't buy a better answer.

**Reading the room counts too.** Handed a deliberately vague sentence, a few flagships quietly built a baby 4×4 instead of a real 9×9. It's a defensible reading — but it's not what a person asking for "a sudoku" pictures, and it's a neat reminder that good generation isn't just valid syntax. It's guessing what the human actually meant.

## So who would I reach for?

After seventy-two attempts, the honest shortlist:

- **Best overall — `gemini-2.5-flash-lite`.** A clean, complete 9×9 in about 36 seconds for a fraction of a cent — the best all-round package, and it's hard not to be a little charmed by it.
- **Best value — `glm-4.5-flash` (Z.ai).** A genuinely *free* model that still produced a clean, valid 9×9. You can't beat free, and it worked — with Google's `gemini-2.5-flash-lite` ($0.004) and Qwen's coder models close behind.
- **Fastest — `gemini-3-flash-preview`,** a playable board in 35 seconds flat.
- **Most complete — `gpt-5.4`,** which turned up with the deepest feature set: difficulty levels, notes, hints, the works.
- **Most dependable — Anthropic, Google and DeepSeek,** whose models almost always rendered correctly when they delivered; Zhipu's GLM line was close, at four clean games from five.

![Jazz Sudoku Squares, from gemini-2.5-flash-lite — a correct, playable 9×9 for roughly $0.004.](https://anselmotalotta.github.io/sudoku-llm-study/article/img-2.png)

The practical upshot writes itself. For everyday, well-specified generation — which is most of the work most of us do — the cheap, fast tier is the smart default, and the coding-tuned models are an outright steal. Save the expensive flagships for the genuinely hard, genuinely novel problems where their reasoning earns its keep. On a job like this, that premium mostly buys you a longer wait and the occasional wrong answer.

## The fine print

This is one prompt, run once per model, on one day. Line-ups shift fast, the same model can answer differently next time, and Sudoku is well-worn ground in training data — so think of this as how reliably a familiar program gets built and rendered, not a test of fresh reasoning. A snapshot, not a scoreboard.

## See for yourself

Every one of these runs in your browser right now:

- [Sudoku Swing](https://anselmotalotta.github.io/sudoku-llm-study/games/qwen3-coder-next.html) — the coding-tuned standout
- [Jazz Sudoku Squares](https://anselmotalotta.github.io/sudoku-llm-study/games/gemini-gemini-2-5-flash-lite.html) — the four-tenths-of-a-cent winner
- [glm-4.5-flash](https://anselmotalotta.github.io/sudoku-llm-study/games/glm-4-5-flash.html) — the free model that still delivered a clean board
- [gpt-5.4](https://anselmotalotta.github.io/sudoku-llm-study/games/gpt-5-4.html) — the most feature-complete
- [grok-4.3](https://anselmotalotta.github.io/sudoku-llm-study/games/xai-grok-4-3.html) — the one that proudly renders nothing

The full methodology, the per-model data, and all forty games are in the study: **https://anselmotalotta.github.io/sudoku-llm-study/**

---

*This study was produced by [PlayPrompt](https://playprompt.org), which builds games from natural-language prompts using third-party models. We ran it to decide which models to use, we have no model of our own in the comparison, and every generated game is published so the results can be checked. Model names are trademarks of their respective owners and are used to identify the systems tested.*
