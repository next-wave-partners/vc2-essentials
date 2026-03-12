# Simulate Fund Portfolio Prompt

This prompt is for use with AI assistants that support code execution to run the Safer Fund Monte Carlo Simulator.

## Instructions

Upload `engines/safer_monte_carlo.py` and `engines/requirements.txt` to your AI session, then use this prompt:

```
Run the Safer Fund Monte Carlo Simulator (safer_monte_carlo.py) to model portfolio-level returns.

Install dependencies first: pip install numpy pandas matplotlib

Available modes:

1. Default simulation (10,000 iterations):
   python safer_monte_carlo.py

2. Scenario presets from the VC 2.0 book:
   python safer_monte_carlo.py --scenario standard
   python safer_monte_carlo.py --scenario revenue-focused
   python safer_monte_carlo.py --scenario all-scenarios

3. Sensitivity analysis:
   python safer_monte_carlo.py --sensitivity

4. Unicorn-free stress test (caps exits at $50M):
   python safer_monte_carlo.py --unicorn-free

5. Custom fund parameters:
   python safer_monte_carlo.py \
       --fund-size [size] \
       --portfolio-size [companies] \
       --investment [per-company] \
       --valuation-cap [cap] \
       --revenue-share [rate] \
       --target-multiple [multiple]

Present:
- Median and percentile TVPI/DPI/IRR
- Return attribution (yield vs. equity)
- Probability of achieving 1x, 2x, 3x returns
- Time to 1x DPI
```

## Usage Without Code Execution

Run locally and share the output with your AI:

```bash
cd engines
pip install -r requirements.txt
python safer_monte_carlo.py --scenario all-scenarios
```

The simulator generates PNG charts and terminal output that any AI can analyze.
