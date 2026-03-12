# Simulate Safer Scenario Prompt

This prompt is for use with AI assistants that support code execution (ChatGPT Code Interpreter, Claude with tool use, etc.) to run the Safer Scenario Simulator.

## Instructions

Upload `engines/safer.py` and `engines/requirements.txt` to your AI session, then use this prompt:

```
Run the Safer Scenario Simulator (safer.py) to model investment returns.

Install dependencies first: pip install numpy matplotlib

Then run the simulator with these parameters:
- Investment: [amount]
- Valuation cap: [cap]
- Target return multiple: [multiple, default 3.0]
- Revenue share: [rate, default 0.05]
- Honeymoon months: [months, default 12]

Available built-in scenarios:
- steady-growth-acquisition
- explosive-growth-ipo
- sustainable-complete-repurchase
- failure-low-revenue
- modest-growth-small-exit

Or provide custom revenue trajectory:
- Initial ARR: [starting revenue]
- Growth rates: [comma-separated annual rates]
- Exit year: [year]
- Exit valuation: [amount]

Run the simulation and present:
- Total return and MOIC
- IRR
- Whether payout was via Cash-Out or Conversion
- Key findings from the report
```

## Usage Without Code Execution

If your AI doesn't support code execution, run the simulator locally:

```bash
cd engines
pip install -r requirements.txt
python safer.py --scenario steady-growth-acquisition --output report.html
```

Then share the HTML report with your AI for analysis and interpretation.
