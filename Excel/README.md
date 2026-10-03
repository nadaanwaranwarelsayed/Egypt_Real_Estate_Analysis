# Step 1: Excel Exploration

Quick exploratory review of the raw dataset in Excel before cleaning it in Python.

**Dataset:** [Egyptian Real Estate Listings](https://www.kaggle.com/datasets/hassankhaled21/egyptian-real-estate-listings) (PropertyFinder Egypt, ~20,000 listings, Aug-Sep 2025).
The raw CSV is not included in this repo; download it from Kaggle.

## What I did
- Loaded the CSV with UTF-8 encoding and saved a working copy as `.xlsx` (the original file was never modified).
- Hid the `url` and `description` columns to make the sheet readable, since they are long text columns.
- Built validation checks, two Pivot Tables, and a list of data issues.

## 1. Validation checks
| Check | Result |
|---|---|
| Number of listings | 19,924 |
| Missing `price` | 539 (2.7%) |
| Missing `down_payment` | 14,479 (72.7%) |
| Min price | 186,900 EGP |
| Max price | 840,000,000 EGP |

<img width="1182" height="770" alt="Checks" src="https://github.com/user-attachments/assets/2fd12b32-6ff2-4177-88e2-7ce738ab165f" />


## 2. Listings by property type
<img width="888" height="783" alt="Pivot type" src="https://github.com/user-attachments/assets/f8834384-381e-464c-b85a-0d0014f63dc1" />

- Apartments are the largest group (41.9%), followed by Chalets (20.3%) and Villas (17.9%).
- The top 3 types cover about 80% of all listings.
- 8 rare types (Land, Cabin, Palace, Whole Building, Roof, Full Floor, Bulk Sale Unit, Bungalow) total only 152 listings (~0.8%). Plan: group them into "Other".
- 77 listings have no type. A later check in Python showed these rows are completely blank (only a URL), so they were removed during cleaning.
  
## 3. Listings by payment method
<img width="863" height="765" alt="Pivot payment" src="https://github.com/user-attachments/assets/e57ab7c8-7a2e-4d91-a221-f1839a4ef146" />

- Cash: 15,521 (77.9%), Installments: 3,862 (19.4%), Missing: 541 (2.7%).
- The groups are imbalanced, so Cash vs. Installments comparisons need care (medians, not just averages).

## 4. Data issues found
<img width="954" height="783" alt="Data Issues" src="https://github.com/user-attachments/assets/d787a43d-a70f-451d-8d87-e0a89e84ba3a" />

> The screenshot above was taken during the Excel step. In Python, `governorate` became `region`, because the North Coast is not a governorate.

| Issue | Column(s) | Planned fix (Python) |
|---|---|---|
| Numbers stored as text | price, down_payment | Remove commas and "EGP", convert to numeric |
| Number embedded in text | size | Extract the sqm value with regex |
| Multiple levels in one cell | location | Split into compound, city, region || Mixed values (e.g. "3+ Maid", "studio") | bedrooms | Create `bedrooms_num` and `has_maid_room` |
| Mixed values (e.g. "7+", "none") | bathrooms | Convert to numeric |
| High missing rate (72.7%) | down_payment | Keep, analyze only listings that report it (see "What changed later" below) || Invalid values | price, size | Flag outliers via price per sqm, review before removing |
| Duplicate listings | all columns | Drop rows identical except for url |
| Rare categories | type | Group into "Other" |
| Personal data in text | description | Exclude from analysis and published files |

## What changed later in Python
- The 77 listings without a type were fully blank rows and were removed.
- In the raw data, 343 `down_payment` values were under 1,000 EGP. They were percentages typed as EGP (for example "5 EGP" for a 5% down payment) and were set to missing.
- `available_from` mixes dates from Aug-Sep 2025 (about 87% of the dated rows) with a few later dates, so it is not used in the analysis.

## Next step
Data cleaning and EDA in Python
