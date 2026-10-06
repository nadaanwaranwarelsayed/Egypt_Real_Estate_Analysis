# Egypt Real Estate Market Analysis

End-to-end analysis of ~20,000 property listings from PropertyFinder Egypt: data exploration in Excel, cleaning and analysis in Python, and an interactive Power BI dashboard.

**Data:** [Egyptian Real Estate Listings (Kaggle)](https://www.kaggle.com/datasets/hassankhaled21/egyptian-real-estate-listings), asking prices, mostly dated Aug-Sep 2025.
**Tools:** Excel, Python (pandas, matplotlib, seaborn), Power BI.

## Dashboard
![Dashboard](powerbi/dashboard.png)

## Key findings
Based on 15,096 residential listings after cleaning (median values; asking prices, not sale prices).

1. **Location drives price per sqm.** The median ranges from about 9.7K EGP in Badr City to about 130.8K in Sidi Abdel Rahman. By region: North Coast 104.2K, Red Sea 77.8K, Cairo 57.1K, Giza 42.4K, Alexandria 35.9K. The overall residential median is 58.2K. Coastal figures include vacation homes.
2. **Villas cost more per sqm than apartments in all 11 cities compared** (3% to 102% more). Across all cities the median villa is about twice the size of the median apartment (321 vs. 155 sqm).
3. **Larger units are cheaper per sqm within each property type.** Overall the pattern looks reversed because units above 300 sqm are mostly villas, which cost more per sqm.
4. **Installment-labelled listings are priced about 27% higher** than cash-labelled listings of the same type in the same city, but their down payments are the same (median 10%). The Cash/Installments label is unreliable: many "Cash" listings report a down payment or mention payment plans.
5. **Typical advertised down payment is 10%** (3,592 listings report it). It is highest in Noor City, Madinaty, and Shorouk City (26-30%) and lowest (about 5%) in North Coast cities and New Heliopolis.
6. **About 2% of listings (292 of 14,305) are priced unusually** for their city and type; the unusually low ones look like data errors or partial prices.
7. **Chalets** (3,918 listings, mostly coastal) have a median of 86.8K EGP per sqm, about 49% above residential units.

## Data cleaning
19,924 raw rows became 19,752: 77 blank rows and 95 duplicate listings removed. Price, down payment, and size were parsed from text; location was split into compound, city, and region; bedrooms and bathrooms were converted to numbers (with a maid-room flag). 48 listings with impossible sizes or extreme prices per sqm were flagged and excluded from price analysis, down payments under 1,000 EGP (percentages typed as EGP) were treated as missing, and rare property types were grouped as "Other".

## Project structure
| Folder | Content |
|---|---|
| `excel/` | Excel exploration: validation checks, pivot tables, data issues |
| `notebooks/` | Python notebook: cleaning and analysis of all business questions |
| `data/` | `cleaned_data.csv` (cleaned listings; `url` and `description` removed) |
| `powerbi/` | Power BI dashboard (`.pbix` and screenshot) |
| `questions.md` | Business questions and scope notes |

## How to reproduce
1. Download the raw CSV from Kaggle.
2. Open the notebook in Google Colab, upload the CSV, and run all cells (the notebook reads `/content/egypt_real_estate_listings.csv`).
3. The notebook produces `cleaned_data.csv`, which feeds the Power BI dashboard.

## Limitations
- Asking prices, not sale prices; most listings are dated Aug-Sep 2025.
- Comparisons are at city level; compound-level differences are not controlled.
- Down payment is reported in only about 26% of listings.
- Outlier thresholds are judgment calls, documented in the notebook.
