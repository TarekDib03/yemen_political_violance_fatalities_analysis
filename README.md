# Spatial-Temporal Dynamics of Conflict Mortality in Yemen (2015–2026)

Data repository, analytical pipeline, and scientific findings tracking the geographic concentration and temporal volatility of conflict-related fatalities across Yemen. This project maps macro-level (Governorate) and micro-level (District) spatial inequalities utilizing mathematical Lorenz Curves and high-frequency monthly timelines.

## 📊 Core Findings & Analytics
* **The Scale Shift:** Refining spatial resolution from the Governorate scale to the District scale exposes a classic *Modifiable Areal Unit Problem (MAUP)*—causing the calculated **Gini Coefficient of fatality concentration to leap from 0.5684 to an extreme 0.7906**.
* **Micro-Level Enclaves:** The data proves that **10% of Yemen's municipal districts absorbed roughly 68% of all national conflict fatalities**, while 75% of local districts remained heavily insulated from direct kinetic combat (accounting for just ~10% of deaths).
* **The Truce Cliff:** High-frequency monthly tracking flags late 2018 as the absolute zenith of the war (~3,500 deaths/month during the Battle of Al Hudaydah). It maps a structural breaking point in April 2022, where a UN-brokered truce permanently dropped and flattened the fatality baseline below 250 deaths/month through 2026.

## 🛠️ Installation & Quickstart

### Prerequisites
Ensure you have Python 3.8+ installed along with the required scientific computing dependencies:
```bash
pip install pandas numpy matplotlib
```

### Running the Analysis
To compute the exact Gini indexes and output the analytical charts directly from your local dataset, clone this repository and execute the analytical core:

```bash
# Clone the repository
git clone [https://github.com/TarekDib03/yemen_political_violance_fatalities_analysis](https://github.com/TarekDib03/yemen_political_violance_fatalities_analysis)
cd yemen_political_violance_fatalities_analysis

# Execute the spatial and temporal aggregation notebook
yemen_political_violence.ipynb
```

---

## 🧮 Mathematical Pipeline

The script uses a localized integration loop utilizing the **Trapezoidal Rule** to calculate the area under the empirical curve ($A_{lorenz}$), determining the explicit geographic concentration index:

$$
\text{Gini} = \frac{0.5 - \int_{0}^{1} L(x) \, dx}{0.5}
$$

```python
# Snippet from src/lorenz_spatial_analysis.py
area_under_lorenz = 0
for i in range(total_units):
    dx = 1 / total_units
    y1 = cum_fatalities_pct[i] / 100
    y2 = cum_fatalities_pct[i+1] / 100
    area_under_lorenz += 0.5 * (y1 + y2) * dx

gini_coefficient = (0.5 - area_under_lorenz) / 0.5
```

---

## 📈 Visualizations Catalog

### 1. District-Level Spatial Inequality
The micro-level Lorenz Curve demonstrates a massive "sag" away from the Line of Perfect Equality, resulting in a **Gini index of 0.7906**. This visually asserts that lethality was restricted to explicit strategic enclaves.

### 2. High-Frequency Campaign Timeline
The monthly trend visualization reveals the immediate micro-shocks of tactical maneuvers, explicitly isolating the 2018 Al Hudaydah urban offensive and the rigid structural floor created by the mid-2022 truce.

---

## 📜 Data Attribution & Academic Citation

### 1. Primary Data Source
The raw chronological and geospatial data utilized in this repository is sourced entirely from the **Armed Conflict Location & Event Data Project (ACLED)**. ACLED is widely recognized as the industry-standard disaggregated conflict registry for researchers, geopolitical analysts, and humanitarian operators.

* **Data Provider:** ACLED (Armed Conflict Location & Event Data)
* **Official Website:** [acleddata.com](https://acleddata.com/)
* **Dataset Used:** Yemen Conflict Events Registry (2015–2026)
* **Data Access Date:** July 2026

### 2. Dataset Query & Filtering Parameters
To ensure research transparency and mathematical reproducibility, the data was extracted from the ACLED API / Data Export Tool using the following structural filters:
* `Country` == `Yemen`
* `Timeframe` == `01 January 2015` to `Current Extent (2026)`
* `Disorder Type` == `Political Violence`
* `Event Types Included` == `Battles`, `Explosions/Remote Violence`, `Violence Against Civilians`
* `Target Variables Extracted` == `event_date`, `year`, `governorate` (Admin1), `district` (Admin2), `fatalities`

### 3. Formal Academic Citations
When utilizing this repository's analytical methodology, Lorenz plotting pipeline, or aggregated data insights for academic research, policy briefs, or portfolio reviews, please cite the primary data author and the foundational methodology text as follows:

#### Standard Dataset Citation (APA 7th Edition)
> Armed Conflict Location & Event Data Project (ACLED). (2026). *Yemen Conflict Events Dataset (2015-2026)* [Data file]. Retrieved from https://acleddata.com/conflict-data/.

#### Methodological Codebook Citation (Chicago/Turabian)
> ACLED. "Armed Conflict Location & Event Data (ACLED) Codebook." Last modified October 3, 2024. Accessed March 15, 2026. www.acleddata.com.

### 4. Terms of Use & Disclaimer
This repository is an independent data analysis portfolio developed for non-commercial research, educational valuation, and skill demonstration purposes. All original data manipulation, spatial grouping, Lorenz calculus, and temporal trend visualization remain under the authorship of this project, while the underlying source telemetry belongs exclusively to ACLED. Users must abide by the [ACLED Terms of Use](https://acleddata.com/attributionpolicy) when republishing or redistributing downstream data subsets.


---
