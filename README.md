# VC 2.0 Essentials

Free, open-source venture analysis tools from *[Venture Capital 2.0: Building, Funding, and Scaling Startups in the Post-Power Law Era](https://johncowan.io)* by John Cowan.

**Works with any AI platform.** Use with ChatGPT, Claude, Gemini, Copilot, open-source models, or run standalone.

**Now powered by the EPAC framework** — every scorecard passes through an Expert-Planner-Actor-Critic validation loop that checks for internal consistency, evidence quality, hallucination risk, and analytical rigor before returning results.

---

## What's Inside

### Financial Engines (Python)

Two standalone simulation tools for modeling the Safer instrument — a venture financing structure designed to produce predictable returns without requiring unicorn outcomes.

| Engine | What it does |
|--------|-------------|
| **Safer Scenario Simulator** | Models individual investment outcomes with quarterly cash flows, IRR, and return waterfall analysis |
| **Safer Fund Monte Carlo** | 10,000-path portfolio simulation with TVPI/DPI distributions, return attribution, and LP waterfall |

```bash
cd engines
pip install -r requirements.txt

# Model a single investment
python safer.py --scenario steady-growth-acquisition --output report.html

# Simulate an entire fund
python safer_monte_carlo.py --scenario all-scenarios
```

### EPAC-Enhanced Scorecard

The 10-dimension weighted scorecard for evaluating venture opportunities, now with EPAC (Expert-Planner-Actor-Critic) validation. Covers market size, customer urgency, competition, founder-market fit, timing, and six other dimensions with t-shirt sizing (S/M/L/XL/XXL) and critical pattern rules.

The EPAC framework adds four phases to every scorecard:

1. **Expert Capture** — Gathers your specification, restates assumptions, confirms scope
2. **Planner** — Builds a structured analytical plan before any scoring begins
3. **Actor** — Executes the plan: analyzes documents, conducts web research, scores dimensions
4. **Critic** — Validates all outputs: internal consistency, evidence quality, hallucination detection, analytical rigor, completeness, and audit trail

See [`methodology/scorecard.md`](methodology/scorecard.md) for the complete framework.

### AI-Ready Prompts

Pre-built prompts you can copy into any AI assistant:

| Prompt | Purpose |
|--------|---------|
| [`score-opportunity`](prompts/score-opportunity.md) | Run the EPAC-enhanced 10-dimension scorecard on a venture |
| [`generate-safer`](prompts/generate-safer.md) | Generate a Safer term sheet with VREC provisions |
| [`simulate-safer`](prompts/simulate-safer.md) | Model a Safer investment scenario |
| [`simulate-fund`](prompts/simulate-fund.md) | Run Monte Carlo fund simulation |

### Claude Desktop Plugin (Cowork)

If you use Claude Desktop with Cowork, download the pre-built `.plugin` file from [Releases](https://github.com/nextwave-partners/vc2-essentials/releases) and install it to get slash commands (`/score-opportunity`, `/generate-safer`, `/simulate-safer`, `/simulate-fund`).

To install:
1. Download `vc2-essentials.plugin` from [Releases](https://github.com/nextwave-partners/vc2-essentials/releases)
2. Open Claude Desktop and switch to the **Cowork** tab
3. Click **Customize** in the left sidebar
4. Upload the `.plugin` file

The plugin is saved locally to your machine and works fully offline.

---

## Quick Start

### Option 1: Use with any AI

1. Open your preferred AI assistant
2. Copy the relevant prompt from [`prompts/`](prompts/)
3. Paste it as a system prompt or into the conversation
4. Provide your venture documents or parameters

### Option 2: Run the engines directly

```bash
git clone https://github.com/nextwave-partners/vc2-essentials.git
cd vc2-essentials/engines
pip install -r requirements.txt

# Quick Safer scenario
python safer.py --scenario steady-growth-acquisition --output report.html

# Full Monte Carlo fund simulation
python safer_monte_carlo.py --scenario revenue-focused
```

### Option 3: Claude Desktop plugin (Cowork)

1. Download `vc2-essentials.plugin` from [Releases](https://github.com/nextwave-partners/vc2-essentials/releases)
2. Open Claude Desktop and switch to **Cowork**
3. Click **Customize** in the left sidebar and upload the `.plugin` file
4. Type `/score-opportunity` to get started

---

## Privacy

Fully private. Nothing leaves your machine.

---

## About

Created by [Next Wave Partners](https://nextwave.partners). Based on the book by John Cowan.

EPAC framework by James Thomason. Financial engines by James Thomason, licensed under BSD terms (see [`engines/LICENSE`](engines/LICENSE)).

## License

The methodology documentation and prompts are licensed under [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/). The Python financial engines are licensed under BSD terms. See individual LICENSE files for details.
