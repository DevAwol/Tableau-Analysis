# Bigger companies on the Inc. 5000 grow slower but run leaner

Growth rate on this list mostly tracks how small a company started. Larger
companies grow slower but convert revenue into headcount far more
efficiently.

**[Interactive dashboard →](https://public.tableau.com/app/profile/awol.ler/viz/Viz2PersonalPractice/Dashboard1#1)**

![dashboard](dashboard.png)

## Data

2014 Inc. 5000: 5,000 privately held US companies ranked by revenue growth.
Revenue and headcount are self-reported. The file carries final-year revenue
and a growth percentage; base-year revenue is derived. The measurement
window isn't stated in the data — Inc's methodology for this edition
describes 2010–2013.

## Findings

1. Median growth falls from 2,281% to 90% as starting revenue rises from
   under $250K to over $25M.
2. Median revenue per employee rises from $142K to $644K across revenue
   tiers. Larger companies scaled without proportional hiring.
3. Energy adds the most revenue per company. IT Services contributes the
   most companies but ranks 16th of 25 per company.

## Limitations

Growth is measured against base-year revenue, so plotting the two together
produces negative correlation regardless of any real effect (Pearson, 1897).

Companies were selected for high growth, so these figures describe variation
within an already-filtered group.

Headcount is point-in-time — revenue per employee measures current
efficiency, not change in efficiency. Growth is nominal.

## Recommendation

Rank by revenue added, not growth percentage. Percentage growth is largely a
function of starting size.

## Files

- `calculations.md` — Tableau calculated fields
- `dashboard.png` — static export
