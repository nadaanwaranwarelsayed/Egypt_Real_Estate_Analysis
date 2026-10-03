# Data

`cleaned_data.csv`: cleaned listings (19,752 rows), output of `notebooks/egypt_real_estate_analysis.ipynb`.
The raw dataset is not included; download it from [Kaggle](https://www.kaggle.com/datasets/hassankhaled21/egyptian-real-estate-listings).
`url` and `description` were removed (the description text can contain phone numbers).

Key columns: `type`, `price`, `size_sqm`, `price_per_sqm`, `city`, `region`, `compound`,
`down_payment_pct`, `is_outlier` (rows flagged as invalid; filter them out for price analysis).
