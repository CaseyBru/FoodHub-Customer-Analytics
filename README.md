# FoodHub Customer Analytics

Exploratory analysis of 1,898 food-delivery orders to identify demand patterns, high-value customers and restaurants, service-time risks, and rule-based revenue opportunities.

This repository presents an academic analysis as a portfolio case study. The original notebook prompts, code, saved outputs, and conclusions are preserved; only academic point values were removed from question headings. Known analytical limitations are documented below rather than silently rewriting the original work.

## Project overview

FoodHub is a food-ordering aggregator that connects customers with multiple New York restaurants and coordinates delivery. The notebook examines historical orders to understand restaurant and cuisine demand, order economics, customer activity, ratings, and fulfillment time.

The project is descriptive and exploratory. It does not train a predictive machine-learning model.

## Business problem and objective

FoodHub wants to use order history to improve customer experience and commercial decision-making. The analysis addresses four practical areas:

- Which restaurants, cuisines, and customers account for the most demand?
- What do order cost, preparation time, and delivery time look like?
- Which restaurants meet specified rating-based promotion criteria?
- What revenue and service-level outcomes result from the business rules in the notebook?

## Dataset description

The notebook uses `foodhub_order.csv`, containing 1,898 rows and 9 columns. The dataset is not included in this repository because the notebook does not provide a license or otherwise confirm that redistribution is permitted.

| Field | Description |
| --- | --- |
| `order_id` | Unique order identifier |
| `customer_id` | Identifier for the customer placing the order |
| `restaurant_name` | Restaurant receiving the order |
| `cuisine_type` | Cuisine ordered |
| `cost_of_the_order` | Order cost in US dollars |
| `day_of_the_week` | Whether the order was placed on a weekday or weekend |
| `rating` | Customer rating from 1 to 5, or the text value `Not given` |
| `food_preparation_time` | Minutes from restaurant confirmation to delivery pickup |
| `delivery_time` | Minutes from pickup to customer drop-off |

The notebook reports no null values. However, missing ratings are represented by the string `Not given`, so a null-only check does not measure unrated orders.

## Analysis workflow

1. Install and import NumPy, pandas, Matplotlib, and seaborn.
2. Load the FoodHub order data and inspect its shape, types, completeness, and summary statistics.
3. Explore numerical and categorical variables with histograms, box plots, bar charts, and frequency tables.
4. Rank restaurants, cuisines, and customers by order count.
5. Explore relationships using a correlation heatmap, pair plot, scatter plots, and grouped box plots.
6. Apply the notebook's business rules for restaurant promotion eligibility and platform revenue.
7. Calculate the share of orders whose combined preparation and delivery time exceeds 60 minutes.

## Models and evaluation methods

No predictive model is fitted, and the notebook does not use a train/test split, cross-validation, or model-performance metrics. Evaluation is limited to descriptive statistics, grouped aggregations, visual exploratory analysis, and deterministic business-rule calculations.

## Key findings

The following results are taken directly from saved notebook outputs:

| Finding | Saved result |
| --- | --- |
| Dataset size | 1,898 orders and 9 variables |
| Food preparation time | 20-minute minimum, 27.37-minute mean, 35-minute maximum |
| Top five restaurants by orders | Shake Shack (219), The Meatball Shop (132), Blue Ribbon Sushi (119), Blue Ribbon Fried Chicken (96), and Parm (68) |
| Most ordered weekend cuisine | American, with 415 orders |
| Orders costing more than $20 | 29.24% |
| Mean delivery time | 24.16 minutes |
| Three most frequent customers | Customer 52832 (13 orders), 47440 (10), and 83287 (9) |
| Restaurants meeting the stated promotion rule | Blue Ribbon Fried Chicken (64 rated orders; 4.328 mean), Blue Ribbon Sushi (73; 4.219), Shake Shack (133; 4.278), and The Meatball Shop (84; 4.512) |
| Revenue under the notebook's commission rules | $6,166.303 |
| Orders taking more than 60 minutes from placement to delivery | 10.54% |

## Recommendations supported by the analysis

- Prioritize weekend campaigns featuring American cuisine, the highest-volume weekend cuisine in the saved results.
- Consider the four restaurants that satisfy the notebook's rating-count and mean-rating thresholds for the specified promotional offer.
- Use targeted retention offers for the three customers with the highest observed order frequency.
- Investigate the 10.54% of orders whose preparation-plus-delivery time exceeds 60 minutes and monitor that service-level measure over time.
- Normalize `Not given` ratings before measuring feedback participation or comparing ratings, then encourage feedback only after establishing a reliable baseline.

These are directional recommendations based on one descriptive dataset. The notebook does not establish causality or test the incremental effect of an intervention.

## Known limitations

- The dataset's period, collection method, provenance, and redistribution license are not supplied in the notebook.
- Question 5 checks `rating.isnull()` even though unrated orders use `Not given`. Its saved result of `0` therefore means there are no nulls, not that every order was rated.
- The weekday/weekend comparison creates a new category by testing for `Saturday` and `Sunday`, while the source field already contains `Weekday` and `Weekend`. The saved output consequently contains only one `Weekday` group and does not answer the intended comparison.
- The multivariate section provides visual exploration but no statistical significance tests or predictive evaluation.
- The revenue result is an estimate produced by the stated commission rules, not an audited accounting figure.

## Technologies used

- Python
- Jupyter Notebook / Google Colab
- NumPy 2.0.2
- pandas 2.2.2
- Matplotlib 3.10.0
- seaborn 0.13.2

## Running the notebook

1. Clone the repository and enter its directory.
2. Create and activate a virtual environment.
3. Install the imported libraries from `requirements.txt`.
4. Obtain `foodhub_order.csv` from an authorized source. Do not commit it unless you have confirmed redistribution rights.
5. Open `foodhub_customer_analytics.ipynb` in Jupyter or Google Colab.
6. Make the data-loading cell point to your authorized local copy. The preserved notebook currently expects `/content/foodhub_order.csv`, the standard Colab upload location.
7. Restart the kernel after the notebook's package-install cell, then run the remaining cells in order.

Example setup in Windows PowerShell:

~~~powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python -m pip install jupyterlab
jupyter lab foodhub_customer_analytics.ipynb
~~~

The notebook includes saved outputs, so its documented results can be reviewed without redistributing the source dataset. Re-execution requires the authorized CSV file.
