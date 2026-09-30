# Business Questions

This project analyzes ~20,000 property listings from PropertyFinder Egypt
(asking prices, not actual sale prices) to answer the following questions:

1. What is the average price per sqm in each area/city?
2. How do apartment prices compare to villa prices within the same area?
3. Is there a price difference between Cash and Installments listings?
4. What is the typical down payment percentage of the price in each area?
5. Which listings are priced unusually high or low compared to their area (outliers)?
6. Which areas are the most and least expensive per sqm (with at least 30 listings)?
7. Does price per sqm decrease as unit size increases?
8. Do installment listings have lower down payments than cash listings?

## Scope notes
- Size is parsed from the listing's "sqm" value (already provided in the data).
- "Area" refers to the city/district level (e.g., New Cairo, 6th of October). Compound-level analysis is used only where there are enough listings.
- Area-level comparisons include only areas with at least 30 listings.
- Chalets are analyzed separately from residential units, since they are mostly coastal/vacation properties.
- Listings with clearly invalid price or size values are flagged and handled before analysis (see the cleaning section in the notebook).
- Down payment analysis is limited to listings that report it (~27% of the data).
- Question 8 compares only listings that report a down payment, in both payment groups.
- Prices are asking prices from PropertyFinder listings (Aug-Sep 2025), not actual sale prices.
