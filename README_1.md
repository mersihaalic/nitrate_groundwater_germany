# Trend and Variability Analysis of Nitrate Levels in German Groundwater

**Where is groundwater nitrate improving, where is it not, and where should authorities act first?**

Final project of the Data Analytics bootcamp (October 2026), by **Mersiha Alic** (M.Sc. Geology | Data Analyst).
This project combines domain knowledge in hydrogeology with statistical, spatial and machine learning analysis of public monitoring data.

<!-- Add one strong image here, e.g. the hotspot map or the dashboard:
![Nitrate hotspots in Germany](figures/YOUR_IMAGE.png)
-->

---

## Motivation

Fertilizers applied to farmland can leach into groundwater as nitrate (NO₃⁻). The EU limit for nitrate in drinking water is **50 mg/L** (Directive (EU) 2020/2184). Elevated concentrations put pressure on drinking water supply, human health and ecosystems.

**Potential users of the insights:** water suppliers (e.g. Stadtwerke), water authorities, environmental agencies and policy makers.

## Research questions

1. **Trend:** Is nitrate declining, and does the decline reach individual stations?
2. **Regional variability:** Which federal states carry the highest nitrate burden?
3. **Risk patterns:** Where do exceedances of 50 mg/L persist, and where do hotspots cluster?
4. **Drivers and prediction:** Does depth matter, and can location predict nitrate at new stations?

## Data

| | |
|---|---|
| **Source** | GovData / Umweltbundesamt (UBA), Nitrate Report (EU Nitrates Directive), groundwater subset |
| **Period** | 2012–2022 (11 years) |
| **Size** | 7,311 observations, 767 monitoring stations, 15 federal states, 14 variables |
| **Key variables** | nitrate concentration, status and category; year; federal state, station, latitude/longitude; sampling depth; groundwater body |

The dataset is not included in this repository. It is publicly available via [GovData](https://www.govdata.de) / [Umweltbundesamt](https://www.umweltbundesamt.de).

## Methods

- **Data preparation:** cleaning and preparing the groundwater dataset
- **Exploratory data analysis:** distributions, trends, first patterns
- **Statistical tests:** linear trend test, Mann-Kendall test with Sen's slope (per station, FDR 10%), Kruskal-Wallis test, Spearman correlation
- **Spatial analysis:** persistent hotspot definition, Getis-Ord Gi* hot spot analysis (10 nearest stations)
- **Machine learning:** Linear Regression vs. Random Forest, validated both by observation and by station
- **Visualization:** Python (Matplotlib, Seaborn, Plotly) and an interactive Power BI dashboard

## Key findings

| Question | Result |
|---|---|
| **Trend** | Mean nitrate decreases by **−0.669 mg/L per year** (p < 0.001). The share of observations above 50 mg/L fell from **30.3% to 24.6%**. |
| **Station level** | Among stations with significant trends, decreases outnumber increases about **3 to 1** (113 decreasing, 36 increasing, 486 not significant). |
| **Federal states** | Nitrate differs significantly between states (Kruskal-Wallis H = 713.4, p < 0.001). Highest median: Bremen (101.6 mg/L, only 12 observations); lowest: Hamburg (0.2 mg/L). |
| **Depth** | Nitrate decreases with sampling depth (Spearman ρ = −0.169, p < 0.001): median 28.8 mg/L at 0–10 m vs. 0.2 mg/L below 100 m. |
| **Persistent hotspots** | **157 stations (20.5%)** exceed 50 mg/L in at least 80% of their observed years (minimum 5 years of data). |
| **Spatial clusters** | 52 stations in hot spots (mainly Saxony and Rhineland-Palatinate), 71 in cold spots (mainly Brandenburg and Mecklenburg-Western Pomerania). Exploratory, not adjusted for multiple testing. |
| **Machine learning** | Random Forest reaches R² = 0.879 on a random split (vs. 0.032 for Linear Regression), but **R² = −0.251 on unseen stations**. Location (lat/long) accounts for about 71% of feature importance, so the model memorises locations rather than generalising. |

## Interactive dashboard

The Power BI dashboard lets users filter by federal state and switch between trend and hot spot views.

![Power BI dashboard: persistent nitrate hotspots](figures/dashboard_hotspots.png)

## Recommendations

1. **Prioritise persistent hotspots:** focus monitoring and investigation on the 157 stations with persistent exceedances.
2. **Use region-specific strategies:** federal states show very different nitrate patterns.
3. **Continue long-term monitoring:** the trend is encouraging, but about a quarter of observations still exceed 50 mg/L.
4. **Improve predictive modelling:** add land use, agricultural intensity, hydrogeology, precipitation and soil data, and validate on unseen stations.

## Repository structure

```
├── notebooks/     # Jupyter notebooks: cleaning, EDA, statistics, spatial analysis, ML
├── figures/       # charts, maps and dashboard screenshots
└── README.md
```

## Tools

Python (Pandas, NumPy, SciPy, scikit-learn, Matplotlib, Seaborn, Plotly) · Jupyter · Power BI · Git/GitHub

## Author

**Mersiha Alic**, M.Sc. Geology | Data Analyst
Focus: water supply, groundwater protection and environmental data
[GitHub](https://github.com/mersihaalic) · [XING](https://www.xing.com/profile/Mersiha_Alic)
