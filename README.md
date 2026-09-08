# Bigger companies on the Inc. 5000 grow slower but run leaner

Tableau analysis of the 2014 Inc. 5000. Growth rate on this list mostly
tracks how small a company started — but larger companies convert revenue
into headcount far more efficiently.

**[Interactive dashboard →](https://public.tableau.com/app/profile/awol.ler/viz/Viz2PersonalPractice/Dashboard1#1)**

## Data

2014 Inc. 5000 — privately held US companies ranked by revenue growth over
a multi-year period. The dataset does not state the period explicitly;
Inc.'s published methodology for this edition describes three-year growth
(2010–2013), and the derived base-year figures are consistent with that,
but the file itself carries only start and end revenue. Revenue and
headcount are self-reported.

## Findings

1. Median growth falls from 2281% to 90% as starting revenue rises from
   under $250K to over $25M.
2. Median revenue per employee rises from roughly $142k to $644k across
   revenue tiers — larger companies scaled without proportional hiring.
3. Energy Companies adds the most revenue per company; IT services contributes the
   most companies but ranks 16th per company out of 25.

## Limitations

Growth is defined relative to base-year revenue, so plotting it against
base-year revenue induces negative correlation independent of any real
effect (Pearson, 1897).

The sample is truncated on the outcome variable — companies were selected
for high growth — so estimates describe variation within an already-selected
group.

Headcount is point-in-time, so revenue per employee measures current
efficiency, not change in efficiency. Growth is nominal, not deflated.

The measurement window is not specified in the source file, so the
base-year figures reconstructed here are dated by inference rather than
by the data.

## Recommendation

Rank by revenue added rather than growth percentage when using this list to
screen companies. Percentage growth is a function of starting size.

## Files

- `calculations.md` — Tableau calculated fields
- `dashboard.png` — static export
