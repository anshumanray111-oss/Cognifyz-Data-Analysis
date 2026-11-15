# Cognifyz Data Analysis Internship Project

**Intern:** Anshuman Ray  
**Role:** Data Analysis Intern  
**Organization:** Cognifyz IT Solutions Pvt. Ltd.  
**Track:** Data Analysis  
**Selected Levels:** Level 1 + Level 2  

---
## 1. Project Overview

This project explores a multi-country restaurant dataset using Python and data analysis techniques to identify patterns in restaurant cuisines, pricing, ratings, service availability, and geographical distribution.

The project covers two levels of the Cognifyz Data Analysis Internship, implemented in two separate Jupyter Notebooks.

**Level 1 – Core Restaurant Analysis**
- Top Cuisines
- City Analysis
- Price Range Distribution
- Online Delivery Analysis

**Level 2 – Advanced Restaurant Analysis**
- Restaurant Ratings
- Cuisine Combinations
- Geographic Analysis
- Restaurant Chains

The analysis uses data cleaning, exploratory data analysis (EDA), statistical summaries, data aggregation, and visualization to identify meaningful patterns and develop data-driven business insights.

The project also considers analytical limitations, including sample sizes, missing values, and the distinction between correlation and causation.

## 2. Internship Information

- **Company:** Cognifyz IT Solutions Pvt. Ltd.
- **Position:** Data Analysis Intern
- **Focus Areas:** Python, pandas, data cleaning, exploratory data analysis, statistical analysis, data visualization, business insight extraction

---

## 3. Objectives

The primary goals of this project are:

1. **Clean and preprocess** raw restaurant data with transparency (no silent row drops).
2. **Characterize restaurant listing patterns** through cuisine frequencies, city-level restaurant distributions, and price range distributions (Level 1).

3. **Explore restaurant rating patterns and characteristics** by examining online delivery availability and its association with ratings, aggregate rating distributions, cuisine combinations, geographic distribution, and repeated restaurant names across multiple locations (Level 2).
4. **Translate quantitative findings** into structured business implications using an *Observation → Interpretation → Business Implication* framework.
5. **Uphold analytical integrity** by respecting sample sizes, avoiding false causal claims, and computing every number directly from data.

---

## 4. Dataset Description

The dataset represents restaurant listings from a global food aggregation platform.

- **Total records:** 9,551 restaurant listings
- **Total features:** 21 columns
- **Local dataset file:** `data/Dataset_real.csv`
- **GitHub availability:** The raw CSV is excluded from this repository through `.gitignore`. Obtain the dataset separately and place it in the `data/` folder before running the notebooks.

### Key Column Groups

| Category | Columns |
|---|---|
| **Identity & Geography** | `Restaurant ID`, `Restaurant Name`, `Country Code`, `City`, `Address`, `Locality`, `Locality Verbose`, `Longitude`, `Latitude` |
| **Cuisine & Cost** | `Cuisines`, `Average Cost for two`, `Currency`, `Price range` |
| **Platform Capabilities** | `Has Table booking`, `Has Online delivery`, `Is delivering now`, `Switch to order menu` |
| **Ratings & Engagement** | `Aggregate rating`, `Rating color`, `Rating text`, `Votes` |

---

## 5. Levels Completed

### Level 1 — Core Market Characterization
Implemented in `Level_1/Cognifyz_Level_1_Data_Analysis.ipynb`

1. **Task 1: Top Cuisines**
   - Correctly split comma-separated multi-cuisine cells (e.g., `"French, Japanese, Desserts"` counted individually).
   - Identified the top 3 most common cuisines and computed the percentage of restaurants serving each.
   - Visualized frequency with annotated horizontal bar charts.

2. **Task 2: City Analysis**
   - Identified the city with the highest number of restaurant listings.
   - Computed average rating per city (excluding unrated restaurants).
   - Determined the city with the highest average rating (raw calculation) and supplemented it with a sample-size filtered view ($n \ge 10$) to prevent single-restaurant cities from skewing conclusions.

3. **Task 3: Price Range Distribution**
   - Analyzed the distribution across 4 ordinal price categories (1 to 4).
   - Calculated exact counts and percentages for each tier.
   - Visualized with percentage-labeled bar charts.

4. **Task 4: Online Delivery**
   - Calculated the percentage of restaurants offering vs. not offering online delivery.
   - Compared the average aggregate ratings of delivery-enabled vs. non-delivery restaurants.
   - Emphasized association over causation in all interpretations.

---

### Level 2 — Deep-Dive & Relationship Analysis
Implemented in `Level_2/Cognifyz_Level_2_Data_Analysis.ipynb`

1. **Task 1: Restaurant Ratings**
   - Analyzed the distribution of `Aggregate rating` among rated restaurants using binned categories.
- Found that the 3.0–4.0 rating band was the largest group, accounting for 59.27% of rated restaurants.
   - Computed mean, median, and distribution of `Votes` (highlighting heavy right-skew where a few popular restaurants pull the mean upward).

2. **Task 2: Cuisine Combinations**
   - Treated cuisine combinations as distinct units.
   - Normalized combinations into canonical forms (alphabetical sorting of items) so `"North Indian, Chinese"` and `"Chinese, North Indian"` are unified.
   - Identified most frequent combinations and analyzed average ratings among combinations meeting a minimum sample size threshold ($n \ge 5$).

3. **Task 3: Geographic Analysis**
   - Excluded records where longitude or latitude was equal to zero before geographic visualization.
- Visualized restaurant coordinates using static scatter plots.
- Observed geographic concentration patterns across countries and cities.

4. **Task 4: Restaurant Chains**
   - Identified potential chains by detecting `Restaurant Name` values appearing at multiple distinct locations.
   - Computed chain-level metrics: location count, average rating (rated locations only), total votes, and average votes per location.
   - Analyzed the top chains by reach, popularity, and quality.

---

## 6. Technologies Used

- **Language:** Python 3.10+
- **Data Manipulation:** `pandas`, `numpy`
- **Visualization:** `matplotlib`, `seaborn`
- **Geographic Visualization:** Static scatter plots using  `matplotlib`
- **Environment:** Jupyter Notebook

---

## 7. Data Cleaning & Preprocessing

Cleaning was kept conservative, transparent, and reproducible:

1. **Encoding Handling:** Level 1 loads the dataset using UTF-8 encoding, while Level 2 includes a fallback to Latin-1 if a Unicode decoding error occurs.
2. **Zero-Rating Separation:** Restaurants with `Aggregate rating == 0.0` and `Rating text == 'Not rated'` are flagged with an `is_rated` boolean rather than deleted. All rating calculations use `is_rated == True` to avoid dragging averages down with unrated placeholders.
3. **Whitespace Normalization:** Stripped leading/trailing whitespace across `Cuisines`, `City`, `Has Online delivery`, and `Restaurant Name`.
4. **Missing Values:** Only `Cuisines` has missing values (9 rows). These are preserved in the main dataframe and handled explicitly inside cuisine tasks.
5. **Coordinate Validation:** Rows with zero longitude or zero latitude are excluded from `geo_df` for geographic visualization.
6. **No Silent Drops:** The main dataframe preserves all 9,551 original dataset rows. Geographic filtering is applied separately for visualization.

---

## 8. Methodology Principles

- **No Hardcoded Results:** Every metric, ranking, average, and percentage is computed directly from the dataframe.
- **Multi-Valued Data Handling:** Exploded comma-separated cuisines for individual frequency (L1T1); normalized canonical strings for combination analysis (L2T2).
- **Sample Size Context:** Every "highest average rating" metric is accompanied by the sample count ($n$) to prevent small-sample distortions.
- **Correlation $\ne$ Causation:** Observational differences (e.g., delivery vs. non-delivery ratings) are framed strictly as associations.

---

## 9. Key Findings

1. **Cuisine Distribution:** A few popular cuisines account for a substantial share of restaurant listings, with North Indian cuisine appearing most frequently.

2. **Geographic Concentration:** Restaurant listings are heavily concentrated in New Delhi compared with other cities in the dataset.

3. **Budget Focus:** Price Ranges 1 and 2 account for approximately 79.1% of all restaurant listings, indicating a strong representation of budget-to-mid-range establishments.

4. **Online Delivery Association:** Online delivery is available at 25.66% of restaurant listings. Restaurants without online delivery have a slightly higher average rating (3.467) than those offering it (3.381). This is an observed association, not evidence of causation.

5. **Rating Distribution:** The 3.0–4.0 rating band contains the largest share of rated restaurants (59.27%), followed by the 2.0–3.0 band (25.54%) and the 4.0–5.0 band (15.05%).

6. **Vote Distribution:** Vote counts are right-skewed, with a mean of approximately 156 and a median of 31, indicating that a relatively small number of restaurants receive substantially more votes.

7. **Potential Restaurant Chains:** Several restaurant names appear across multiple locations. Comparing location counts and engagement metrics helps identify potential multi-location chains, although repeated names do not confirm common ownership.

---

## 10. Business Insights

| Focus Area | Observation | Interpretation | Business Implication |
|---|---|---|---|
| **Cuisine Strategy** | North Indian, Chinese, and Fast Food are among the most frequently listed cuisines. | These cuisine categories have a strong presence in the dataset. | Restaurants can evaluate menu positioning around popular cuisines while differentiating through specialty offerings. |
| **Market Distribution** | Restaurant listings are heavily concentrated in New Delhi compared with other cities. | The dataset reflects an uneven geographical distribution of restaurant listings. | Platforms can investigate listing coverage in other cities before making expansion decisions. |
| **Pricing Strategy** | Price Ranges 1 and 2 account for the majority of restaurant listings. | Budget and mid-range restaurants dominate the dataset. | Businesses can evaluate affordable pricing, value-focused promotions, and offerings suited to these price segments. |
| **Delivery Strategy** | Online delivery is offered by a minority of restaurants. Non-delivery restaurants have a higher average rating (3.467) than delivery-enabled restaurants (3.381). | Delivery availability and average ratings show an observational difference, not a causal relationship. | Restaurants can evaluate delivery adoption based on operational capacity, customer needs, and service quality rather than assuming it improves ratings. |
| **Restaurant Chains** | Some repeated restaurant names have multiple locations and substantial total vote counts. | These names represent potential multi-location brands with varying listing reach and customer engagement. | Platforms can investigate partnerships with multi-location restaurant groups while evaluating each brand's actual performance. |

---

## 11. Project Structure

```
Cognifyz-Data-Analysis/
│
├── data/
│   └── Dataset_real.csv       # Original dataset (9,551 rows)
│
├── Level_1/
│   └── Cognifyz_Level_1_Data_Analysis.ipynb
│
├── Level_2/
│   └── Cognifyz_Level_2_Data_Analysis.ipynb
│
├── outputs/
│   ├── Demo_Video_Script.md
│   └── LinkedIn_Post.md
│
├── README.md
├── requirements.txt
└── .gitignore
```

---

## 12. How to Run

### 1. Clone the repository

```bash
git clone https://github.com/your-username/Cognifyz-Data-Analysis.git
cd Cognifyz-Data-Analysis
```

Replace `your-username` with your actual GitHub username after publishing the repository.

### 2. Set up a virtual environment

```bash
python -m venv venv
```

**Windows:**
```bash
venv\Scripts\activate
```

**macOS/Linux:**
```bash
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Add the dataset

The original CSV file is excluded from this repository.

- Obtain the restaurant dataset separately.
- Create a `data/` folder in the project root if it does not already exist.
- Place the file inside it with the exact name `Dataset_real.csv`.

Expected location:

```text
Cognifyz-Data-Analysis/
└── data/
    └── Dataset_real.csv
```

### 5. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open the following notebooks and run all cells:

- `Level_1/Cognifyz_Level_1_Data_Analysis.ipynb`
- `Level_2/Cognifyz_Level_2_Data_Analysis.ipynb`

Make sure the required dataset is present before running either notebook.
---

## 13. Conclusion

This project presents an end-to-end analysis of a global restaurant dataset through the selected **Level 1 and Level 2 tasks** of the Cognifyz IT Solutions Data Analysis Internship.

Using Python, Pandas, NumPy, Matplotlib, and Seaborn, the project explores restaurant cuisines, city-level distribution, pricing patterns, online delivery, rating behaviour, cuisine combinations, geographic distribution, and potential multi-location restaurant chains.

The analysis emphasizes reproducible workflows, transparent data cleaning, appropriate sample-size considerations, and responsible interpretation of observational results.

Overall, this project demonstrates practical skills in data analysis, exploratory data analysis (EDA), data visualization, and translating quantitative findings into meaningful business insights..
