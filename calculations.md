# Calculated fields

Built in Tableau Public against the 2014 Inc. 5000 CSV.

### Growth %

    [growth]/100

Source column stores growth as a whole-number percentage (158957 =
158,957%). Dividing by 100 and applying percentage formatting displays it
correctly — Tableau's percent format multiplies by 100 on render.

### Pre-growth Revenue

    [revenue] / (1 + [growth]/100)

Reconstructs 2010 revenue, which is not in the source file. The `revenue`
column is post-growth (2013). Validated against Fuhu: $195.6M ÷ 1590.57
≈ $123K.

### Nominal Growth

    [revenue] - [Pre-growth Revenue]

Absolute dollars added over the period. Used to rank companies
independently of starting size.

### Revenue Per Employee

    [revenue] / [workers]

Row-level ratio. Requires a dimension at company grain in the view —
aggregating it across companies sums ratios and is meaningless.

### Average Revenue Per Employee

    SUM([revenue]) / SUM([workers])

Aggregate version for industry- and tier-level comparison. Weights by
company size rather than treating each company equally.

### Revenue Buckets

    IF [revenue] < 2500000 THEN "1. $1.5–2.5M"
    ELSEIF [revenue] < 5000000 THEN "2. $2.5–5M"
    ELSEIF [revenue] < 10000000 THEN "3. $5–10M"
    ELSEIF [revenue] < 20000000 THEN "4. $10–20M"
    ELSEIF [revenue] < 40000000 THEN "5. $20–40M"
    ELSEIF [revenue] < 80000000 THEN "6. $40–80M"
    ELSEIF [revenue] < 160000000 THEN "7. $80–160M"
    ELSE "8. $160M+"
    END

Log-spaced tiers. Equal-width bins put ~90% of companies in the first
bucket. Numeric prefixes force correct sort order — Tableau sorts these
alphabetically.

### Pre-growth Revenue Buckets

    IF [Pre-growth Revenue] < 250000 THEN "1. < $250k"
    ELSEIF [Pre-growth Revenue] < 500000 THEN "2. $250k–$500k"
    ELSEIF [Pre-growth Revenue] < 1000000 THEN "3. $500k–$1M"
    ELSEIF [Pre-growth Revenue] < 2500000 THEN "4. $1M–$2.5M"
    ELSEIF [Pre-growth Revenue] < 5000000 THEN "5. $2.5M–$5M"
    ELSEIF [Pre-growth Revenue] < 10000000 THEN "6. $5M–$10M"
    ELSEIF [Pre-growth Revenue] < 25000000 THEN "7. $10M–$25M"
    ELSE "8. $25M+"
    END

### Number of Companies

    ZN(COUNTD([company]))

Distinct company count. ZN returns 0 rather than null for empty
partitions.

## Aggregation notes

Industry and state measures use MEDIAN rather than SUM. Summed dollar
growth ranks groups by how many companies they contain — IT Services leads
on total dollars with ~735 companies while Energy reaches a comparable
total with ~115.

## Validation

Fuhu (rank 1, $195.6M revenue, 158,957% growth) hand-checked against the
published Inc. 5000 listing. Derived base-year revenue of ~$123K is
consistent with the reported figures.