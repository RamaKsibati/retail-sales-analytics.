# Retail Sales Analytics | Python, SQL & Business Intelligence

**Portfolio case study | Historical online retail data (2010–2011)**

## Business question
How did sales change toward the end of 2011, which products contributed to growth, and where was revenue concentrated?

## Dataset and approach
Source: [UCI Online Retail](https://archive.ics.uci.edu/dataset/352/online-retail), 541,909 transaction-line records. Analysis performed in Google Colab with Python, pandas, Matplotlib, and SQLite SQL. Initial gross-sales analysis retained 530,104 rows with positive quantity and unit price, excluding cancellation invoices. Merchandise-focused analysis additionally excluded selected non-merchandise stock codes (DOT, POST, M, D, C2, BANK CHARGES). These exclusions are preliminary and should be reviewed before operational use.

**Metric definition:** Gross sales = quantity × unit price on filtered positive-sale rows. Figures are **not net revenue** and do not account for returns, tax, or shipping economics. Identical rows were flagged but not automatically removed.

## Key findings

| Metric | Finding |
|---|---:|
| Initial filtered gross sales (includes some charges) | £10,666,684.54 |
| Initial filtered unique orders | 19,960 |
| Identified customers | 4,338 |
| Merchandise gross sales growth, Aug–Nov 2011 | 97.88% |
| Merchandise order-count growth, Aug–Nov 2011 | 105.30% |
| Merchandise units growth, Aug–Nov 2011 | 77.98% |
| Average merchandise order value change | −3.61% |
| Christmas-labeled products' share of Aug–Nov merchandise sales growth | 18.60% |
| Unusual single transaction (invoice 581483) | £168,469.60 |
| Effect of excluding that invoice on merchandise gross sales | 1.64% |

### Monthly merchandise comparison

| Metric | August 2011 | November 2011 |
|---|---:|---:|
| Gross sales | £736,667.22 | £1,457,745.53 |
| Unique orders | 1,340 | 2,751 |
| Units sold | 421,452 | 750,082 |
| Average order value | £549.75 | £529.90 |

Sales nearly doubled while average order value decreased slightly. The increase was primarily associated with higher order volume, not larger average orders.

### Christmas-labeled merchandise

| Month | Christmas-labeled sales | Other merchandise sales |
|---|---:|---:|
| August 2011 | £24,021.48 | £712,645.74 |
| November 2011 | £158,163.06 | £1,299,582.47 |

Christmas-labeled products contributed £134,141.58 of the £721,078.31 increase in merchandise gross sales. This is an association, not proof that holidays caused the change. Only one full year is available, so recurring seasonality cannot be established.

### Top geographic markets (merchandise gross sales)

| Country | Sales |
|---|---:|
| United Kingdom | £8,773,136.22 |
| Netherlands | £283,889.34 |
| EIRE (Ireland) | £271,164.30 |
| Germany | £205,569.89 |
| France | £184,582.74 |

### Data quality and outlier investigation
- 135,080 missing Customer IDs; retained for aggregate sales analysis, excluded from identified-customer counts.
- 1,454 missing descriptions; 5,268 exact duplicate rows flagged for review.
- 10,624 negative-quantity rows, 2,515 zero-price rows, 2 negative-price rows, and 9,288 cancellation-invoice rows in the source data.
- A single invoice (581483) contained 80,995 units of PAPER CRAFT, LITTLE BIRDIE at £2.08 each, totaling £168,469.60. Excluding this invoice changes product rankings and lowers merchandise gross sales by 1.64%. A matching-return investigation is still pending; do not label it an error or permanently exclude it without verification.

## Business recommendations
1. Prepare order processing and inventory for possible late-year volume spikes, while validating the pattern against additional years.
2. Review demand for Christmas-themed products, especially paper-chain kits and seasonal bags.
3. Separate merchandise from postage and manual charges in product-performance reporting.
4. Investigate high-value invoices and returns before publishing net-revenue or top-product claims.
5. Evaluate international markets with profitability and customer metrics, not sales alone.

## Reproduce
Open `retail_sales_portfolio.ipynb` in [Google Colab](https://colab.research.google.com/). The notebook downloads the publicly available UCI dataset into the Colab runtime, creates charts, and runs SQL in an in-memory SQLite database. No local Python installation is required.

## Limitations
Historical 2010–2011 data; December 2011 is incomplete. Gross merchandise sales are not net revenue. Product-type filtering is heuristic. Duplicate rows and returns have not been fully reconciled. The user-reported summary metrics above are preserved as initial analysis results and should be compared with the notebook's reproducible outputs.

## Skills demonstrated
Python · pandas · data cleaning · exploratory data analysis · SQL (SQLite) · aggregation · KPI design · Matplotlib · business storytelling · sensitivity analysis
