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
- Area sizes are converted from sqft to sqm (sqft / 10.764).
- Chalets are analyzed separately from residential units, since they are mostly coastal/vacation properties.
