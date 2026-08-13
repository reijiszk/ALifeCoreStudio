# ALifeCoreStudio

**A browser-based environment for building and running complex-systems and artificial-life models**

*[日本語版 / Japanese](ja/README.md) · [1-page project overview](OVERVIEW.md)*

Three studios: **ABM** (agent-based modeling), **EVO** (evolutionary computation), and
**IEC** (interactive evolutionary computation).

Each studio is a **single self-contained HTML file**: no installation, no build step, no
server. Double-click it and it runs in any modern browser, on desktop or mobile.

Describe a model in plain language, let a generative AI write the code, paste it in, and run
it. No programming knowledge is required to get started.

---

## Why this exists

The constructive (synthetic) approach, understanding complex and living systems by building
them, proceeds as a cycle: design → implement → run → visualize → analyze → design again.
Implementation has traditionally been the bottleneck. ALifeCoreStudio keeps the framework for
model construction, visualization, and analysis **fixed**, and lets a generative AI supply
only a model's **essential logic**. Because the conventions are always the same, whatever the
AI returns arrives as a live, adjustable model with sliders and charts.

---

## Quick start

1. Download or clone this repository:

   ```bash
   git clone https://github.com/reijiszk/ALifeCoreStudio.git
   ```

2. **Double-click** the studio you want to try, and it opens in your browser.
3. First time? Open the matching **First Steps** guide first.

**Requirements:** any modern browser (Chrome, Firefox, Safari, or Edge). No installation, no
dependencies, no server, no internet connection needed to run a model.

> 💡 Model code runs via `new Function`, and AI generation makes network calls. Both are
> blocked under a restrictive Content Security Policy. If something doesn't work, open the
> HTML directly (`file://`) or serve it locally (e.g. `python3 -m http.server`).

---

## Repository contents

All applications and documents are unified at **v1.0**.

| File | Description |
|---|---|
| `ABM_Studio.html` | **ABM Studio**: agent-based models (flocking, epidemics, segregation, …) |
| `Evo_Studio.html` | **EVO Studio**: evolutionary computation (genetic algorithms, evolving virtual creatures) |
| `IEC_Studio.html` | **IEC Studio**: interactive evolutionary computation (evolve shapes by picking your favorites) |
| `ABM_Studio_FirstSteps.html` | ABM Studio First Steps guide |
| `Evo_Studio_FirstSteps.html` | EVO Studio First Steps guide |
| `IEC_Studio_FirstSteps.html` | IEC Studio First Steps guide |
| `ABM_Studio_Manual.html` | ABM Studio detailed manual (advanced) |
| `Evo_Studio_Manual.html` | EVO Studio detailed manual (advanced) |
| `IEC_Studio_Manual.html` | IEC Studio detailed manual (advanced) |
| `index.html` | Landing page listing every studio and document (also the GitHub Pages entry point) |
| `ALifeCoreStudio_Viewer.html` | Experiment-data replay viewer (loads a studio's exported ZIP and replays each recorded step/generation) |
| `OVERVIEW.md` | The project in one page |
| `LICENSE` | MIT License |
| `ja/` | Japanese versions of all nine applications, guides, and manuals |

Every studio and document is fully self-contained in one HTML file (no external JavaScript
libraries; only web fonts are fetched at runtime from Google Fonts).

---

## Authoring and understanding models with generative AI

Each studio's code bar provides:

- **✏️ Modify prompt / ✨ New-model prompt**: copies a fully-specified, ready-to-paste
  prompt to your clipboard for ChatGPT / Gemini / Claude or any chat-based LLM. One
  **Paste & apply** click brings the answer back into the running model.
- **📖 Explain prompt**: asks the AI to describe, in plain language and pseudocode, what the
  current model does, so you can understand it without reading the JavaScript.
- **🐍 Python-conversion prompt** (ABM / EVO): converts the current model into an equivalent
  self-contained Python (`matplotlib`) script.
- **🤖 AI Generate**: calls an OpenAI-compatible endpoint directly from the page (a local
  server such as LM Studio, or a cloud provider) and inserts the generated code automatically.

Generating, running, modifying, and explaining all happen on the same page, so the whole
modeling cycle stays in one tight loop.

---

## Built-in models

- **ABM Studio**: elementary cellular automata (ECA), Conway's Game of Life, Schelling
  segregation, flocking (boids), ant-pheromone foraging, spatial Prisoner's Dilemma, SIR
  epidemic, Social Particle Swarm (SPS)
- **EVO Studio**: bit-string GA (function optimization), mass-spring creatures, soft-body
  voxel creatures, the knapsack problem, the traveling salesman problem (TSP)
- **IEC Studio**: branching shapes, flocking (animated), face evolution, stained glass,
  mathematical art, soft-body creatures, sound/melody evolution

The original sources each model draws on are listed in the **References** section at the end
of each First Steps guide.

---

## Record & replay

**📦 Download ZIP** exports everything since initialization (`model.js`, parameters,
experiment settings, the random seed, chart CSVs, and a full JSON). Two complementary
mechanisms make each step/generation reproducible:

- **Method A, deterministic seed.** The engine seeds all randomness and records the seed, so
  a run can be reproduced from `model.js` + settings + seed. This works for AI-modified and
  newly created models too, with no per-model changes.
- **Method B, recorded state.** For ABM / EVO, **Record states** writes the state at each
  step/generation to `frames.jsonl` (IEC always records all nine individuals per generation).
  This is what the in-app timeline replays, so anything you notice while a run is going can be
  revisited. It is **on by default on a computer and off on phones and tablets**, where memory
  is tighter; switch it either way at any time.

Drop an exported ZIP onto **`ALifeCoreStudio_Viewer.html`** to replay each recorded
step/generation along a timeline, rendered by the model's own drawing code, for built-in and
AI-generated models alike.

---

## Documentation

- **First Steps guides**: start here; the shortest path to a running, modified model.
- **Detailed manuals**: every feature, the model contract, prompt writing, LLM endpoint
  setup, and data export.

Japanese versions of all applications, guides, and manuals are in [`ja/`](ja/).

---

## Project status

ALifeCoreStudio is developed by a single author. The repository is public so that anyone can
use, study, and fork it under the MIT License, but pull requests are not being accepted at
this time: each studio is one self-contained HTML file of several thousand lines, which does
not lend itself to merging external patches.

Bug reports and questions are welcome in
[Issues](https://github.com/reijiszk/ALifeCoreStudio/issues), and forks are entirely fine.

---

## License

MIT License. See [`LICENSE`](LICENSE).

---

## Citation

If you use the **Social Particle Swarm (SPS)** model included in this tool, please cite:

> Nishimoto, K., Suzuki, R., & Arita, T. (2023).
> Social Particle Swarm model for investigating the complex dynamics of social relationships.
> *Psychologia*, 65(2), 185–210. https://doi.org/10.2117/psysoc.2023-B039

---

## Using this in teaching

If you use ALifeCoreStudio in a class, seminar, or workshop, I would be glad to hear about it
(<reiji@nagoya-u.jp>). This is **not a condition of the license**, simply a request: knowing
how the tool is actually used helps me decide what to improve, and I am always interested in
hearing what people have built with it.

---

## Acknowledgements

This project is strongly influenced by [NetLogo](https://www.netlogo.org/)
(Wilensky, U., 1999, Center for Connected Learning and Computer-Based Modeling, Northwestern
University), which the author has used extensively in his own teaching and research, and
which we gratefully acknowledge. Several ABM Studio models cover classic topics that also have
well-known counterparts in the NetLogo Models Library; ABM Studio's versions are independent
implementations of the same classic algorithms.

The soft-body voxel creature models are likewise independent implementations inspired by the
concept of evolving voxel soft robots introduced by **Evolution Gym**; the physics
(position-based dynamics) and the rest of the code were written independently.

- Evolution Gym: Bhatia, J., Jackson, H., Tian, Y., Xu, J., & Matusik, W. (2021).
  *Evolution Gym: A Large-Scale Benchmark for Evolving Soft Robots.* NeurIPS 2021.
  https://github.com/EvolutionGym/evogym

The code and documentation of the applications themselves were written with the help of
[Claude Code](https://claude.com/claude-code).

Web fonts (IBM Plex Mono / Syne / Noto Sans JP, all SIL OFL 1.1) are not bundled and are
loaded from Google Fonts at runtime.

---

## Author

Reiji Suzuki (Nagoya University), <reiji@nagoya-u.jp>
