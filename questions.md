# Business Questions

This project analyzes ~20,000 property listings from PropertyFinder Egypt
(19,752 after cleaning; asking prices, not actual sale prices) to answer the following questions:

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
- "Area" refers to the city level (e.g., New Cairo City, 6 October City). Area-level comparisons include only areas with at least 30 listings.
- Residential units = Apartment, Villa, Townhouse, Twin House, Duplex, Penthouse, iVilla. Chalets are analyzed separately (city level only). Hotel Apartments and rare types ("Other": Land, Cabin, Palace, etc.) are excluded from price analysis.
- Invalid listings are flagged (`is_outlier`), kept in the data, and excluded from price analysis: impossible sizes (under 20 or over 5,000 sqm), extreme price per sqm within a property type (3 x IQR on a log scale), or above 1M EGP per sqm.
- Question 5 compares each listing with others of the same type in the same city (1.5 x IQR on a log scale, at least 30 listings per city and type).
- Question 7 is analyzed overall and within each property type, because larger units are mostly villas.
- Down payment is reported in only ~26% of listings; Questions 4 and 8 use only those listings. Values under 1,000 EGP were percentages typed as EGP and are treated as missing.
- The Cash/Installments label is not fully reliable: many "Cash" listings report a down payment or mention payment plans. Questions 3 and 8 compare labels, not confirmed payment terms.
- Prices are asking prices from PropertyFinder listings, mostly dated Aug-Sep 2025, not actual sale prices.
