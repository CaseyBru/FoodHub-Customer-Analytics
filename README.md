# FoodHub Customer Analytics

## Overview

FoodHub is a New York food-ordering aggregator that connects customers with restaurants and coordinates delivery. This exploratory analysis examines 1,898 orders across nine variables to identify demand patterns, high-value customers, restaurant performance, order economics, customer-feedback gaps, and fulfillment-time risks.

The work originated as an academic data-analysis project and has been refined into a concise portfolio case study. Results are descriptive and apply to the observed orders; the dataset does not specify its collection period or sampling method.

## Business questions

- Which restaurants, cuisines, and customers generate the most orders?
- How are order cost, preparation time, and delivery time distributed?
- Which restaurants satisfy defined promotion criteria based on rating volume and average score?
- What revenue is produced by the stated commission rules?
- How do weekday and weekend delivery performance compare?

## Analysis performed

The notebook uses pandas and NumPy for inspection, aggregation, and business-rule calculations. Matplotlib and seaborn support univariate and multivariate exploration through histograms, box plots, bar charts, scatter plots, a correlation heatmap, and pair plots. The workflow covers data structure and completeness, demand rankings, ratings, order costs, preparation and delivery performance, promotion eligibility, and estimated platform revenue.

## Key findings

- The dataset contains 1,898 orders with no null values, but 736 orders (38.78%) are explicitly marked `Not given` for rating.
- Food preparation averages 27.37 minutes, while delivery averages 24.16 minutes.
- Shake Shack leads restaurant demand with 219 orders. The Meatball Shop, Blue Ribbon Sushi, Blue Ribbon Fried Chicken, and Parm complete the top five.
- American is the most frequently ordered weekend cuisine, with 415 orders.
- Orders above $20 represent 29.24% of the dataset. Applying the stated commission rules produces estimated revenue of $6,166.30.
- Blue Ribbon Fried Chicken, Blue Ribbon Sushi, Shake Shack, and The Meatball Shop meet the promotion thresholds of more than 50 rated orders and an average rating above 4.
- Mean delivery time is 28.34 minutes on weekdays and 22.47 minutes on weekends. Overall, 10.54% of orders take more than 60 minutes from placement through delivery.

## Recommendations

- Investigate weekday delivery operations, where average delivery is 5.87 minutes slower than on weekends.
- Monitor orders exceeding 60 minutes and look for recurring restaurant, cuisine, or delivery patterns.
- Feature qualifying high-rated restaurants in promotions and emphasize American cuisine in weekend campaigns.
- Use targeted retention offers for the three most frequent customers.
- Improve post-delivery feedback collection to reduce the large share of unrated orders.

## Technologies

Python, Jupyter Notebook, NumPy, pandas, Matplotlib, and seaborn. Exact package versions are listed in `requirements.txt`.

## Data-access note

`foodhub_order.csv` is excluded because redistribution permission is unknown. To run the analysis, obtain an authorized copy, place it beside `foodhub_customer_analytics.ipynb`, install the packages in `requirements.txt`, and open the notebook in Jupyter or Google Colab.
