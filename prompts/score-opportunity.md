---
description: Run the VC 2.0 10-dimension scorecard on a venture opportunity
allowed-tools: Read, Write, Edit, WebSearch, WebFetch
---

Run the full VC 2.0 10-Dimension Scorecard evaluation on a venture opportunity.

First, load the studio-os skill's scorecard framework by reading `${CLAUDE_PLUGIN_ROOT}/skills/studio-os/SKILL.md`.

## AUTONOMOUS ANALYSIS MODE

This scorecard agent operates **autonomously**. When the user provides documents (pitch decks, business plans, one-pagers, technical docs, governance docs), the agent should:

1. **Analyze all provided documents thoroughly** — Extract every relevant data point for scoring
2. **Use web search to verify claims and fill gaps** — Research the company, market, competitors, founders, and industry trends
3. **Score conservatively when data is uncertain** — If information for a dimension is missing or unverifiable, score conservatively (lower for standard dimensions, higher for inverted dimensions)
4. **Request additional documents when needed** — If critical information is missing, tell the user what additional documents would improve scoring accuracy
5. **Produce a complete score report** without requiring interactive Q&A for each dimension

Do NOT walk through dimensions interactively asking the user to rate each one. Instead, the agent analyzes everything available and produces the complete scorecard.

## SCORING FRAMEWORK

### The 10 Dimensions with T-Shirt Sizing

**Standard Dimensions** (higher is better): S=1, M=2, L=3, XL=5, XXL=8
**Inverted Dimensions** (lower resource/cost/time intensity is better): S=8, M=5, L=3, XL=2, XXL=1

| # | Dimension | Direction | S | M | L | XL | XXL |
|---|-----------|-----------|---|---|---|----|----|
| 1 | Founder-Market Fit | STANDARD | 1 | 2 | 3 | 5 | 8 |
| 2 | Market Size | STANDARD | 1 | 2 | 3 | 5 | 8 |
| 3 | Customer Urgency | STANDARD | 1 | 2 | 3 | 5 | 8 |
| 4 | Competition | INVERTED | 8 | 5 | 3 | 2 | 1 |
| 5 | Novelty | STANDARD | 1 | 2 | 3 | 5 | 8 |
| 6 | Resources Required | INVERTED | 8 | 5 | 3 | 2 | 1 |
| 7 | Time to Market | INVERTED | 8 | 5 | 3 | 2 | 1 |
| 8 | Cost of Sales | INVERTED | 8 | 5 | 3 | 2 | 1 |
| 9 | Profitability | STANDARD (avg of 2 sub-scores) | 1 | 2 | 3 | 5 | 8 |
| 10 | Market Timing | STANDARD | 1 | 2 | 3 | 5 | 8 |

### Profitability Sub-Dimensions (averaged to produce dimension 9 score)
- **Profit Margin Potential** [STANDARD]: S=1, M=2, L=3, XL=5, XXL=8
- **Time to Profitability** [INVERTED]: S=8, M=5, L=3, XL=2, XXL=1

### Dimension Scoring Criteria

**1. Founder-Market Fit** — How well the team's skills and experience align with the target market.
- S(1): No relevant experience, skills, or network in the target domain
- M(2): Some transferable skills but limited domain-specific experience
- L(3): Solid relevant experience with some industry connections
- XL(5): Deep domain expertise with strong industry network and track record
- XXL(8): Exceptional domain mastery with unique unfair advantages and proven success

**2. Market Size** — The potential addressable market for the product or service.
- S(1): Very small niche market (<$100M TAM), limited growth potential
- M(2): Moderate market ($100M-$500M TAM) with some growth
- L(3): Large market ($500M-$1B TAM) with solid growth trajectory
- XL(5): Very large market ($1B-$10B TAM) with strong growth drivers
- XXL(8): Massive market ($10B+ TAM) with explosive growth potential

**3. Customer Urgency** — How badly target customers need the problem solved.
- S(1): Nice-to-have; customers rarely think about this problem
- M(2): Moderate pain point; customers have workarounds they tolerate
- L(3): Significant pain; customers actively seek solutions
- XL(5): Critical problem; customers urgently need a solution and will pay premium
- XXL(8): Hair-on-fire problem; customers desperate for a solution, massive willingness to pay

**4. Competition** [INVERTED] — How crowded the competitive landscape is.
- S(8): Virtually no direct competitors; blue ocean opportunity
- M(5): Few competitors with significant gaps in their offerings
- L(3): Moderate competition with room for differentiation
- XL(2): Crowded market with strong incumbents and limited differentiation
- XXL(1): Hyper-competitive market dominated by well-funded incumbents

**5. Novelty** — How unique and differentiated the solution is.
- S(1): Virtually indistinguishable from existing offerings; competing on minor features or price
- M(2): Some unique features or improvements but still largely similar to what exists
- L(3): Distinctive approach with clear differentiation, but core use case is familiar
- XL(5): Pioneers a new category or way of doing things; requires some customer education but value prop is clear
- XXL(8): Completely new-to-the-world innovation creating an entirely new market; transformative but requires significant customer education

**6. Resources Required** [INVERTED] — How much capital, people, and effort needed.
- S(8): Minimal resources; solo founder or small team with bootstrap funding and off-the-shelf tools
- M(5): Moderate resources; small dedicated team, seed funding, some custom development
- L(3): Significant resources; larger team, Series A/B funding, extensive development or infrastructure
- XL(2): Major resources; dozens/hundreds of employees, nine-figure funding, years of R&D
- XXL(1): Massive resources; hundreds/thousands of employees, billions in capital, major infrastructure or regulatory hurdles

**7. Time to Market** [INVERTED] — How long to develop and launch MVP.
- S(8): Under 3 months; simple product, experienced team, clear requirements
- M(5): 3-6 months; some complexity but manageable
- L(3): 6-12 months; fairly complex with technical unknowns
- XL(2): 12-18 months; complex and novel with regulatory, partnership, or integration challenges
- XXL(1): 18+ months; massive, ambitious project with fundamental technology or scientific breakthroughs needed

**8. Cost of Sales** [INVERTED] — How much it costs to acquire and serve each customer.
- S(8): Very low; transactional, self-service product with easy-to-reach audience
- M(5): Moderate; some human touch and targeted marketing needed
- L(3): Significant; high-touch, relationship-driven sales with sophisticated buyers
- XL(2): Very high; complex, expensive product for hard-to-reach, skeptical audience
- XXL(1): Astronomical; entrenched industry relationships, extremely long sales cycles, massive investment per customer

**9. Profitability** — Expected unit economics and path to profitability. Average of two sub-scores:
- **Profit Margin Potential**: S(1)=structurally low-margin, M(2)=moderate margins with constraints, L(3)=high margins at scale, XL(5)=exceptionally high margins with near-zero marginal costs, XXL(8)=industry-leading margin potential
- **Time to Profitability**: S(8)=profitable within 0-6 months, M(5)=6-18 months, L(3)=18-36 months, XL(2)=3-5 years, XXL(1)=5+ years

**10. Market Timing** — How well the venture aligns with current macro trends.
- S(1): Unfavorable macro environment; significant headwinds and little momentum
- M(2): Mixed environment; some positive trends but also significant challenges or uncertainties
- L(3): Generally favorable; several positive trends with few major headwinds
- XL(5): Highly favorable; strong and clear tailwinds across multiple dimensions
- XXL(8): Exceptionally favorable; perfect storm of positive trends and momentum building

## SCORE INTERPRETATION

- **70-80 points**: Exceptional idea with strong potential across all key dimensions. Rare and valuable find warranting serious consideration and investment.
- **60-69 points**: Very good idea with more strengths than weaknesses. Some areas may need improvement but overall foundation is solid.
- **50-59 points**: Mixed bag with significant potential but also notable risks or challenges. Worth pursuing but will likely require substantial refinement and de-risking.
- **40-49 points**: Weak idea with more red flags than green lights. Overall picture is not compelling. Should probably be set aside in favor of better options.
- **Below 40 points**: Very poor idea unlikely to succeed in current form. Fundamentals and execution ability are questionable. Should almost certainly not be pursued.

## CRITICAL PATTERN RULES (Override Mechanical Scoring)

- **Customer Urgency below 3** = failure predictor regardless of other scores. Recommend repositioning problem or passing.
- **High Market Timing (5+) compensates** for moderate scores elsewhere. Prioritize market window exploitation.
- **Founder-Market Fit below 4** = requires team augmentation, recruitment, or partnership.
- **Resources Required score <3 AND Time to Market score <3** = dangerous capital exposure. Scope reduction or partnership required.
- **Competition score >6 AND Customer Urgency >5** = potential market creation opportunity. Premium weighting.

## REPORT FORMAT

Produce a comprehensive scorecard report as a markdown file with these sections:

### 1. Executive Summary
Brief overview of the opportunity, key findings, and overall recommendation.

### 2. Scorecard Table
| Dimension | T-Shirt | Score | Confidence | Notes |
With a Total Score row and Max Possible (80).

### 3. Dimension-by-Dimension Analysis
For each of the 10 dimensions, provide:
- The assigned rating and score with justification
- Key evidence from documents and research
- Confidence level (High/Medium/Low based on available data)
- Risk factors or uncertainties

### 4. Pattern Rule Flags
Any critical pattern rules triggered and their implications.

### 5. Structural Analysis
- Key strengths (dimensions scoring 5+)
- Key weaknesses (dimensions scoring 2 or below)
- Structural misalignments (e.g., high market + low founder fit, strong problem + weak sales model)

### 6. Data Gaps and Recommendations
- What information was missing or unverifiable
- What additional documents would improve scoring accuracy
- Specific questions the founders should address

### 7. Overall Assessment and Recommendation
- Score interpretation
- Go/No-Go recommendation
- Recommended engagement mode (Internal Origination, Asset Transformation, Strategic Partnership, Structured Support, or Pass)
- Key conditions or milestones for engagement

### 8. Appendix: Research Notes
Key findings from web research used in the analysis.

Save the scorecard report as a markdown file in the user's workspace with filename format: `[CompanyName]-Scorecard-[Date].md`

**Note:** This scorecard is a diagnostic tool, not a definitive verdict. It provides structured analysis to inform investment decisions, not replace human judgment.
