# Cognifyz Data Analysis Internship — Demo Video Presentation Script

**Project:** Data Analysis Internship Project  
**Presenter:** Anshuman Ray  
**Organization:** Cognifyz IT Solutions Pvt. Ltd.  
**Levels Presented:** Level 1 + Level 2  
**Target Duration:** ~5–7 minutes  

---

## Video Outline & Timestamps

- **[0:00 – 0:45]** Introduction & Internship Context
- **[0:45 – 1:30]** Dataset Overview & Data Quality Preparation
- **[1:30 – 3:15]** Level 1 Walkthrough: Core Market Characterization
- **[3:15 – 5:00]** Level 2 Walkthrough: Deep-Dive & Relationship Analysis
- **[5:00 – 6:00]** Business Insights & Practical Implications
- **[6:00 – 6:45]** Technical Takeaways & Conclusion

---

## Script

### [0:00 – 0:45] 1. Introduction & Internship Context

*(Screen shows title slide or GitHub repository overview with README.md visible)*

> **"Hello everyone! My name is Anshuman Ray, and in this video, I am excited to present my completed Data Analysis Internship project for Cognifyz IT Solutions Pvt. Ltd.**
>
> **As part of the Cognifyz internship guidelines, interns were given the opportunity to choose any two out of three levels. I chose Level 1 and Level 2, covering a total of eight comprehensive data analysis tasks.**
>
> **Throughout this project, I used Python, pandas, NumPy, Matplotlib, and Seaborn to perform end-to-end exploratory data analysis, clean real-world data, visualize distributions, and extract actionable business insights from a multi-country restaurant dataset."**

---

### [0:45 – 1:30] 2. Dataset Overview & Data Quality

*(Switch screen to `Level_1/Cognifyz_Level_1_Data_Analysis.ipynb` — scrolling down through the Initial Inspection and Data Cleaning sections)*

> **"Let's look at the dataset first.**
>
> **The dataset contains 9,557 restaurant records across 21 features, capturing details such as restaurant identity, city, geographic coordinates, cuisines served, price range, online delivery availability, aggregate ratings, and vote counts.**
>
> **Before jumping into analysis, I conducted a thorough data-quality audit:**
> - **First, I identified that the `Cuisines` column had 9 missing entries, which I preserved and handled explicitly inside the cuisine tasks rather than silently dropping rows.**
> - **Second, I discovered that restaurants with an aggregate rating of 0.0 correspond to unrated establishments labeled 'Not rated'. To prevent this from dragging down rating calculations, I created a boolean flag `is_rated` to evaluate rated restaurants accurately.**
> - **Third, I standardized string fields and identified invalid (0, 0) geographic coordinates for separate handling.**
>
> **This ensured that every number computed in both notebooks is reliable and completely free from silent data distortion."**

---

### [1:30 – 3:15] 3. Level 1 Walkthrough: Core Market Characterization

*(Screen focuses on Level 1 Tasks 1 through 4 with visualizations)*

> **"Now, moving into Level 1:**
>
> **In Task 1 — Top Cuisines:**
> *A critical analytical step here was recognizing that the `Cuisines` column contains multiple comma-separated values in a single cell, such as 'French, Japanese, Desserts'. Instead of treating the whole string as one cuisine, I split and exploded the values so every cuisine is counted individually. The analysis revealed that North Indian, Chinese, and Fast Food are the top three cuisines in the dataset, representing the largest restaurant coverage.*
>
> **In Task 2 — City Analysis:**
> *I evaluated restaurant density and average ratings across cities. New Delhi holds the highest number of listings by a massive margin. When calculating the city with the highest average rating, I included a crucial statistical check: a city with just one restaurant can artificially top the ranking. I presented the raw highest-average city as required, but also provided a supplementary ranking with a minimum threshold of 10 restaurants to show a statistically meaningful view.*
>
> **In Task 3 — Price Range Distribution:**
> *I visualized the four price tiers. The data clearly shows a heavy concentration in Price Range 1 and Price Range 2, confirming that the platform's supply is strongly budget-to-mid-market focused.*
>
> **In Task 4 — Online Delivery:**
> *I calculated that approximately 25.7% of restaurants offer online delivery. Comparing ratings, delivery-enabled restaurants showed a higher average rating than non-delivery ones. Importantly, I explicitly highlighted that this represents an observational association, not a causal proof that adding delivery increases ratings."**

---

### [3:15 – 5:00] 4. Level 2 Walkthrough: Deep-Dive & Relationships

*(Switch screen to `Level_2/Cognifyz_Level_2_Data_Analysis.ipynb` — scrolling through Tasks 1 to 4)*

> **"Next, in Level 2, we moved into deeper relationships:**
>
> **In Task 1 — Restaurant Ratings:**
> *I examined aggregate ratings and vote counts. Ratings are left-skewed, with the vast majority of rated restaurants clustering tightly in the 3.5 to 4.5 band. Vote counts, however, are heavily right-skewed: the median is much lower than the mean, meaning a small number of blockbuster restaurants pull total engagement.*
>
> **In Task 2 — Cuisine Combinations:**
> *Unlike Level 1 where cuisines were split, here I treated pairings as full combinations and normalized them into canonical alphabetical order to avoid counting 'North Indian, Chinese' separately from 'Chinese, North Indian'. Looking at combinations with at least 5 restaurants revealed which recurring pairings maintain high customer satisfaction.*
>
> **In Task 3 — Geographic Analysis:**
> *I filtered out invalid (0, 0) coordinates and visualized the spatial distribution of restaurants using scatter plots and interactive Folium maps. The visualization shows distinct clustering in major metropolitan hubs, reflecting platform penetration.*
>
> **In Task 4 — Restaurant Chains:**
> *I identified potential chains by tracking restaurant names appearing at multiple distinct locations. For brands with 3 or more locations, I calculated chain-level reach, average rating, total votes, and average votes per location, showing how brand popularity and customer perception vary across multi-unit operators."**

---

### [5:00 – 6:00] 5. Business Insights

*(Screen shows the Business Insights markdown summary table in either notebook or README)*

> **"Translating these analytical findings into business value, I framed four core insights using an Observation → Interpretation → Business Implication structure:**
>
> 1. **Cuisine Strategy:** Mainstream cuisines drive catalog breadth. New restaurants should anchor in proven categories while differentiating, and platforms should use them as primary search filters.
> 2. **Geographic Strategy:** Listing concentration in primary metros means platforms must defend dominant hubs while capturing under-served secondary cities.
> 3. **Pricing & Promotions:** Because volume sits in Price Ranges 1 and 2, mass-market discount campaigns and delivery subscription models should target value-tier diners.
> 4. **Chain Partnerships:** Multi-location chains drive disproportionate engagement and total votes, making them prime candidates for platform exclusivity and joint promotions."**

---

### [6:00 – 6:45] 6. Conclusion & Wrap-Up

*(Screen shows the GitHub README.md or closing slide)*

> **"In conclusion, this project demonstrates how clean data preprocessing, thoughtful metric design, and clear visualizations can turn raw restaurant data into meaningful strategic insights.**
>
> **Both Jupyter Notebooks are fully reproducible, well-documented, and contain zero hardcoded results. All code, documentation, requirements, and findings are available in the repository.**
>
> **I would like to thank Cognifyz IT Solutions for this fantastic learning opportunity and practical internship experience.**
>
> **Thank you for watching!"**
