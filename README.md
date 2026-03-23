# VC 2.0 Essentials

Free, open-source venture analysis tools from *Venture Capital 2.0: Building, Funding, and Scaling Startups in the Post-Power Law Era* by John Cowan.

**Works with any AI platform.** Use with ChatGPT, Claude, Gemini, Copilot, or any other AI assistant.

**Powered by the EPAC framework** - every scorecard passes through an Expert-Planner-Actor-Critic validation loop that checks for internal consistency, evidence quality, hallucination risk, and analytical rigor before returning results.

---

## What's Inside

### AI-Ready Prompts

Four pre-built prompts you can copy into any AI assistant. Open the file, copy the contents, and paste into your AI of choice.

| Prompt | Purpose |
|--------|---------|
| [score-opportunity](prompts/score-opportunity.md) | Run the EPAC-enhanced 10-dimension scorecard on a venture opportunity |
| [generate-safer](prompts/generate-safer.md) | Generate a Safer instrument term sheet with VREC provisions |
| [simulate-safer](prompts/simulate-safer.md) | Model a Safer investment scenario |
| [simulate-fund](prompts/simulate-fund.md) | Run a Monte Carlo fund simulation |

### Enhanced Scorecard

The 10-dimension weighted scorecard evaluates venture opportunities across market size, customer urgency, competition, founder-market fit, timing, and six other dimensions using t-shirt sizing (S/M/L/XL/XXL) with critical pattern rules.

The Enhanced framework adds four validation phases:

1. **Expert Capture** - Gathers your specification, restates assumptions, confirms scope
2. **Planner** - Builds a structured analytical plan before any scoring begins
3. **Actor** - Executes the plan: analyzes documents, conducts web research, scores dimensions
4. **Critic** - Validates all outputs: internal consistency, evidence quality, hallucination detection, analytical rigor, completeness, and audit trail

### Claude Desktop Plugin

The `claude-plugin/` folder contains a pre-built `.plugin` file that adds slash commands to Claude Desktop with Cowork: `/score-opportunity`, `/generate-safer`, `/simulate-safer`, and `/simulate-fund`.

See [claude-plugin/README.md](claude-plugin/README.md) for installation instructions.

---

## Quick Start

### Option 1: Use with any AI (ChatGPT, Gemini, Copilot, Claude, etc.)

1. Open the [prompts/](prompts/) folder above
2. Click on the prompt you want (e.g., `score-opportunity.md`)
3. Copy the full contents of the file
4. Paste it into your AI assistant
5. Provide your venture details - pitch deck, one-pager, or description

That's it. The prompt contains all the instructions the AI needs.

### Option 2: Claude Desktop plugin

1. Download `vc2-essentials.plugin` from the [claude-plugin/](claude-plugin/) folder
2. Open Claude Desktop and switch to **Cowork**
3. Click **Customize** in the left sidebar
4. Click **Browse plugins**, then upload the `.plugin` file
5. Type `/score-opportunity` to get started

---

## Privacy

Everything runs in your AI session. Nothing is sent to us. Nothing leaves your machine.

---

## About

Created by [Next Wave Partners](https://nextwave.partners). Based on the book by John Cowan.

## License

Prompts and methodology are licensed under [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/).
