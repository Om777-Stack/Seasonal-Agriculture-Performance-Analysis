# Seasonal Agriculture Performance Analysis

Analysis of 4,000 farm records across three Indian growing seasons (Kharif, Rabi, Zaid) to find out how much yield and profit depend on season, and how much depend on crop and irrigation method.

Completed as the major project of the VOIS x AICTE Data Analytics internship (Edunet Foundation).

**Tools:** Python, Pandas, NumPy, Matplotlib, Seaborn, SciPy, Jupyter Notebook

## Problem

Raw agricultural data does not show how performance changes from one season to another. The task was to investigate seasonal differences in farm performance and identify which patterns hold up in the data.

## Dataset

- 4,000 farm records, 28 columns covering location, crop, season, weather, soil, inputs, yield, cost, revenue, profit, water use and disease risk
- 8 states, 10 districts, 8 crops, 3 seasons, 4 irrigation methods
- Supplied by the VOIS program as part of the project brief

## Key findings

| Season | Avg yield (t/ha) | Avg profit | Avg water efficiency | Farms making a loss |
|---|---|---|---|---|
| Kharif | 5.63 | ₹1.79 lakh | 5.89 | 42.2% |
| Rabi | 5.09 | ₹0.88 lakh | 5.19 | 51.1% |
| Zaid | 4.63 | -₹24,805 | 4.41 | 64.5% |

Averages are across all crops. Water efficiency is in tonnes per 1,000 m³.

1. **Kharif leads and Zaid trails, in every crop.** The Kharif > Rabi > Zaid order holds for both yield and profit in all 8 crops. The profit difference between seasons is statistically significant within each crop (Kruskal-Wallis, p < 0.01).
2. **Crop matters far more than season.** Crop explains about 81% of the variance in yield and 35% of the variance in profit. Season explains about 0.1% and 1.7%. Sugarcane yields 38-53 t/ha depending on season, while every other crop averages under 3 t/ha.
3. **Zaid is the only season with a negative average profit.** It has the lowest average rainfall (about 299 mm) and the highest average temperature (about 31°C). Disease and pest risk is lowest in Zaid (38.2%, against 54.5% in Kharif), so pest pressure does not explain the losses.
4. **Wheat, Maize and Rice lose money on average in every season.** Pulses only loses money in Rabi and Zaid. The positive overall average profit is carried by Sugarcane, Chilli and Cotton.
5. **Drip irrigation has the highest average yield (6.68 t/ha)** and leads within 6 of the 8 crops. Rainfed has the highest water efficiency (7.56) because it uses the least water, not because it yields more. Flood irrigation is the least efficient (3.44).
6. **Profit follows revenue (r = 0.89) more closely than yield (r = 0.49).** Price and cost matter as much as physical output.
7. **Punjab (₹1.36 lakh) and Maharashtra (₹1.35 lakh) have the highest average profit;** Andhra Pradesh (₹0.73 lakh) has the lowest. State averages mix different crops, so this is not a pure location effect.

## Approach

1. **Data quality.** Three columns had missing values (Rainfall 48, Soil Moisture 40, Yield 32; at most 1.2% of rows). There were no duplicates. Yield matches Production divided by Farm Area to within 0.01 in every recorded row, so missing yield was recomputed from those two columns. Rainfall and soil moisture differ strongly by season, so missing values were filled with the median of their own season.
2. **Outliers.** 267 records have yield above 20 t/ha. All are Sugarcane, which is agronomically normal, so they were kept and analysed by crop.
3. **Exploratory analysis.** Univariate, bivariate and multivariate plots, including season-by-crop and season-by-irrigation breakdowns and a correlation heatmap.
4. **Statistics.** Descriptive statistics by season, variance explained by each factor (eta squared), and Kruskal-Wallis tests for seasonal differences.
5. **Insights and recommendations.** Each insight states the observation, the evidence, the interpretation and the limitation.

## What the data suggests

- Compare yield and profit within a crop, not through blended season averages. Sugarcane's scale distorts every overall average.
- Look at crop and irrigation choices for Zaid specifically, since it has the worst economics and the lowest rainfall.
- Treat grain-crop profitability as a cost and price question. Yield is not what holds it back in this data.

## Limitations

- One cross-sectional dataset, so the results show association, not cause.
- Crop, state and irrigation method are not randomly assigned, so their effects are mixed with factors the data does not record (soil quality, farmer capacity).
- Each record has a single market price, so price movement within a season cannot be studied.

## Repository contents

| File | Description |
|---|---|
| `Seasonal_Agriculture_Performance_Analysis.ipynb` | Full analysis with code, outputs and written interpretation |
| `seasonal_agriculture_performance_dataset.csv` | Dataset (4,000 rows, 28 columns) |
| `Seasonal_Agriculture_Performance_Presentation.pdf` | Project presentation |
| `Problem_Statement.pdf` | Project brief from the program |

## How to run

```bash
pip install pandas numpy matplotlib seaborn scipy jupyter
jupyter notebook Seasonal_Agriculture_Performance_Analysis.ipynb
```

Keep the CSV in the same folder as the notebook.

## Author

Om Bagal, B.Tech Metallurgy and Materials Engineering, COEP Technological University, Pune
[LinkedIn](https://www.linkedin.com/in/om-bagal-3a7a28347) | [GitHub](https://github.com/Om777-Stack)
