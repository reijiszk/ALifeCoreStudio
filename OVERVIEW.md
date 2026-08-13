# ALifeCoreStudio

**A browser-based environment for building and running complex-systems and artificial-life models**

*One-page overview*

**What it is.** Three single-file, browser-only apps: no install, no build step, no
server. Just open an HTML file.

| Studio | Question it answers | Built-in models |
|---|---|---|
| **ABM Studio** | What global pattern emerges from simple local agent rules? | elementary cellular automata, Conway's Life, Schelling segregation, flocking (boids), ant pheromone trails, spatial Prisoner's Dilemma, SIR epidemic, Social Particle Swarm (8) |
| **EVO Studio** | What does an evolutionary algorithm converge on? | bit-string GA / function optimization, mass-spring creatures, soft-body voxel creatures, knapsack problem, traveling salesman (5) |
| **IEC Studio** | What happens when *you* are the fitness function? Click the one you like best and it becomes the next generation's parent. | branching shapes, flocking (animated), face evolution, stained glass, math art, soft-body creatures, sound/melody evolution (7) |

---

## What's inside

```
ABM_Studio.html                  ─┐
Evo_Studio.html                   ├─ the 3 apps, just double-click to run
IEC_Studio.html                  ─┘

ABM_Studio_FirstSteps.html       ─┐
Evo_Studio_FirstSteps.html        ├─ "first steps" guides, one per app
IEC_Studio_FirstSteps.html       ─┘   → read this first if you're new

ABM_Studio_Manual.html           ─┐
Evo_Studio_Manual.html            ├─ detailed / advanced manuals
IEC_Studio_Manual.html           ─┘   → parameter-by-parameter reference

index.html                 landing page linking to every studio and document
ALifeCoreStudio_Viewer.html   replay viewer for exported experiment data
README.md                  English README (full)
OVERVIEW.md                this file
LICENSE                    MIT License

ja/                        Japanese versions of all 9 apps, guides, and manuals
```

Each app/guide/manual is a **single self-contained HTML file**: no external JS libraries,
nothing to build. Only the fonts are fetched from Google Fonts at runtime.

---

## How to use it

1. **Open an app.** Double-click e.g. `ABM_Studio.html`, and it opens in your browser and
   runs immediately with a default model.
2. **Pick a model** from the dropdown, hit ▶ Run, and drag the parameter sliders to see the
   simulation change live.
3. **Change or create a model with AI.** Each app's code panel has buttons to:
   - copy a ready-made prompt ("modify this model" / "write a new model") to paste into
     ChatGPT / Gemini / Claude, then paste the AI's code back in and run it, or
   - call an OpenAI-compatible API directly (local, e.g. LM Studio, or cloud, e.g.
     OpenRouter/OpenAI) and have the generated code dropped straight into the runner.
   You don't need to know how to code. You need to know how to *ask*.
4. **Read the code.** The current model's JavaScript is always visible in the code panel, so
   you can see exactly what's driving the simulation, not just a black-box binary.
5. **Go deeper.** The First Steps guide explains the UI and walks through examples; the
   Manual documents every parameter and built-in model in detail. Japanese versions of
   everything are in [`ja/`](ja/).

---

## Who it's for

Students and teachers of agent-based modeling / artificial life / complex systems who want a
zero-setup sandbox; anyone curious what "evolution," "emergence," or "self-organization" look
like when you can nudge the parameters yourself.

---

## Status & license

**v1.0**, three studios, 8 + 5 + 7 built-in models. Japanese versions of all applications,
guides, and manuals are in [`ja/`](ja/).

**MIT License** (`LICENSE`). Soft-body models are independent implementations inspired by
Evolution Gym's concept. The Social Particle Swarm model has an associated paper. See the
Citation section of the README.

The code and documentation of the applications themselves were written with the help of
[Claude Code](https://claude.com/claude-code).

For the full picture see [README.md](README.md) (English) or [ja/README.md](ja/README.md)
(Japanese).
