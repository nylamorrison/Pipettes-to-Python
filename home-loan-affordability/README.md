# Housing Buyer Experience Analysis

Data visualization project in R looking at how neighborhood rating, connectivity, and buyer satisfaction relate to each other and to property type.

## Data

International House Sales and Buyer Loan Records, Eman Fatima (2025), Kaggle:
https://www.kaggle.com/datasets/emanfatima2025/international-house-sales-and-buyerloan-records

200,000 home purchase records from 13 countries, 25 variables. I used these:

- `neighbourhood_rating` – buyer's rating of the neighborhood (1–10)
- `connectivity_score` – how accessible the property is (1–10)
- `satisfaction_score` – buyer's satisfaction (1–10)
- `property_type` – apartment, farmhouse, independent house, studio, townhouse, villa
- `country`

The dataset isn't included here. To run the code, download `global_house_purchase_dataset.csv` from Kaggle and put it in a `data/` folder.

## Questions

1. Are buyers in better-rated neighborhoods more satisfied?
2. Do neighborhood rating, connectivity, and satisfaction differ by property type?

## Analysis

### 1. Satisfaction by neighborhood rating (line plot)

I averaged satisfaction score for each neighborhood rating from 1 to 10. There was no trend. Average satisfaction stayed between 5.47 and 5.52 across all ratings and moved up and down with no pattern.

### 2. Neighborhood rating vs. satisfaction categories (mosaic plot)

I grouped both variables into Low (1–3), Medium (4–6), and High (7–10) and made a contingency table and mosaic plot. The proportions of low, medium, and high satisfaction were about the same in every neighborhood group, which matched the line plot. Because the plot didn't show much difference, I moved on to looking at property type.

### 3. Lifestyle metrics by property type (heatmap)

I calculated the average neighborhood rating, connectivity, and satisfaction for each property type, reshaped the data to long format, and plotted it as a heatmap (Bertin matrix) with the average written in each tile.

The differences were small, with every average between 5.47 and 5.53:

- Townhouses had the highest neighborhood rating (5.53)
- Apartments had the highest satisfaction (5.52)
- Studios and farmhouses had the highest connectivity (5.51)

I made a few versions while working on this one:
- a first version with a single-color scale and no labels
- a z-score version with a diverging color scale, to show which property types were above or below the average for each metric
- versions split by country, and one by country instead of property type

The final version uses a white-to-blue scale with the exact values labeled, since the raw differences were small enough that labels made it much easier to read than color alone.

## Takeaways

- Neighborhood rating did not predict satisfaction in this data.
- Property type also had very little effect on any of the three metrics.
- All three scores average close to 5.5 on a 1–10 scale with almost no variation between groups. That suggests the ratings may be close to evenly distributed in this dataset, so it may not be a good source for studying buyer satisfaction. Real buyer survey data would be needed to say more.

## Files

- `DATAVIZFINAL.Rmd` – all code, including the earlier drafts of the heatmap

## Running the code

```r
install.packages(c("tidyverse", "vcd"))
```

Open `DATAVIZFINAL.Rmd` in RStudio, update the file path in the first chunk to point to `data/global_house_purchase_dataset.csv`, and run the chunks.

## Tools

R, tidyverse (dplyr, tidyr, ggplot2), base R `mosaicplot`
