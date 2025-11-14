# Movie Analysis: Data-Driven Insights for Film Production Strategy

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-1.x-green.svg)](https://pandas.pydata.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## Project Overview

This data science project analyzes box office performance data to provide actionable insights for a new movie studio venture. By examining the relationship between various factors—including genre, production budget, ratings, and release timing—we identify key drivers of commercial success in the film industry.

**Group 6 - Full Time Hybrid**  
**Instructor:** Diana Mongina

---

## Business Problem

Our company is entering the original video content market by launching a new movie studio. However, the organization lacks experience in film production. This project addresses that knowledge gap by analyzing current box office trends to determine:

- Which genres generate the highest revenue
- The relationship between production budget and profitability
- How ratings influence box office performance
- Optimal release timing for maximizing returns

The insights from this analysis will guide strategic decisions on what types of films to produce.

---

## Objectives

1. **Identify high-revenue genres** — Determine which film genres consistently generate strong box office returns
2. **Analyze top-performing movies** — Examine characteristics of the highest-grossing films
3. **Evaluate rating-revenue correlation** — Test whether highly-rated films generate higher revenue
4. **Assess budget impact on profits** — Quantify the relationship between production budget and financial returns
5. **Determine seasonal effects** — Analyze whether release month affects ratings and revenue

---

## Dataset

### Data Sources

The analysis integrates data from multiple sources:

- **IMDb Database** (`im.db`) - SQLite database containing:
  - `movie_basics` — Movie titles, runtime, genres
  - `movie_ratings` — Average ratings and vote counts
  - Additional tables for directors, writers, and cast information

- **The Numbers** (`tn.movie_budgets.csv`) — Financial data including:
  - Production budgets
  - Domestic gross revenue
  - Worldwide gross revenue
  - Release dates

### Final Dataset

After merging and cleaning, the analysis uses **2,752 movies** with complete information across all relevant dimensions.

**Key Features:**
- Movie metadata (title, year, runtime, genre)
- Ratings (average rating, number of votes)
- Financial data (production budget, domestic gross, worldwide gross)
- Temporal data (release date, release month)

---

## Methodology

### Data Preprocessing

1. **Database Integration** — Connected to SQLite database and joined `movie_basics` with `movie_ratings` tables
2. **Data Cleaning** — Removed null values and handled missing data (65,720 entries retained initially)
3. **Data Transformation**:
   - Converted currency strings to integers (removed `$` and `,` characters)
   - Converted release dates to datetime format
   - Extracted month from release dates for temporal analysis
4. **Dataset Merging** — Merged IMDb data with financial data using movie titles as the join key

### Analytical Approach

- **Descriptive Statistics** — Calculated mean revenues by genre, rating, and release month
- **Correlation Analysis** — Examined relationships between budget, ratings, runtime, and revenue
- **Hypothesis Testing**:
  - T-test to compare revenue between high-rated (≥7.0) and low-rated (<7.0) movies
  - ANOVA to test the effect of release month on worldwide gross
- **Visualization** — Created bar plots, scatter plots, line charts, and heatmaps to communicate findings

---

## Key Findings

### 1. Genre Performance

**Top Revenue-Generating Genre Combinations:**
- Family, Fantasy, Musical — Avg. domestic: $440M, worldwide: $934M
- Action, Adventure, Sci-Fi — Avg. domestic: $220M, worldwide: $599M
- Adventure, Fantasy — Avg. domestic: $193M, worldwide: $701M

**Insight:** Genre mixing, particularly combining adventure elements with fantasy or sci-fi, drives the highest revenues.

### 2. Budget-Revenue Relationship

- **Correlation:** Strong positive correlation (r > 0.6) between production budget and both domestic and worldwide revenue
- **Profitability Probability:**
  - 61% chance of worldwide gross exceeding production budget
  - 41% chance of domestic gross exceeding production budget

**Insight:** Higher budgets generally lead to higher revenues, but ROI is not guaranteed—strategic investment is crucial.

### 3. Rating Impact on Revenue

**Statistical Analysis:**
- High-rated movies (≥7.0) show significantly higher mean worldwide revenue
- T-test result: p-value = 2.05e-13 (highly significant at α = 0.05)

**Top-Rated Revenue Performance:**
- Movies rated 8.5: Avg. worldwide gross $331M
- Movies rated 7.8-8.3: Avg. worldwide gross $213M-$257M

**Insight:** Quality matters. Higher audience satisfaction directly translates to box office success.

### 4. Seasonal Release Patterns

**Peak Revenue Months:**
- June: $173M average worldwide gross
- May: $158M average worldwide gross
- November: $156M average worldwide gross

**Statistical Significance:**
- ANOVA p-value = 5.83e-18, confirming release month significantly affects revenue

**Insight:** Summer releases (May-July) and holiday season (November-December) generate the highest returns.

### 5. Highest-Grossing Films

**Top Performers:**
1. Avatar — $2.78B worldwide
2. Avengers: Endgame — $1.52B+ worldwide
3. Jurassic World — $1.50B+ worldwide
4. Furious 7 — $1.51B+ worldwide

**Common Characteristics:** High production values, franchise potential, action/adventure elements, visual spectacle.

---

## Recommendations

### 1. Invest in Quality Production — Ratings Drive Revenue
Movies rated between 7.5-8.5 consistently outperform lower-rated films. Focus resources on:
- Strong, well-developed scripts
- High production standards
- Quality casting and direction

**Action:** Prioritize pre-production development and script refinement over rushing to production.

### 2. Adopt a Tiered Budget Strategy
While higher budgets correlate with higher revenues, the relationship isn't proportional. Implement a portfolio approach:
- **Flagship Films:** 2-3 high-budget ($150M+) blockbusters per year
- **Mid-Tier Films:** 4-6 medium-budget ($50M-$100M) films with strong scripts
- **Strategic Bets:** 2-3 low-budget (<$30M) films targeting niche markets

**Action:** Diversify investment to balance risk while maximizing potential returns.

### 3. Optimize Release Timing
Schedule major releases during peak revenue months:
- **Summer Season (May-July):** Blockbusters and action films
- **Holiday Season (November-December):** Family films and tentpoles
- **Off-Peak Months:** Lower-budget or niche films to reduce competition

**Action:** Develop a strategic release calendar 12-18 months in advance.

### 4. Focus on High-Revenue Genre Combinations
Prioritize genre mixes that historically perform well:
- Action + Adventure + Sci-Fi
- Adventure + Fantasy
- Family + Fantasy + Musical

**Action:** Balance commercial genres (for revenue) with critically-acclaimed genres (for brand reputation).

---

## Technical Stack

### Programming Language
- **Python 3.8+**

### Core Libraries
- **pandas** — Data manipulation and analysis
- **numpy** — Numerical computing
- **matplotlib** — Data visualization
- **seaborn** — Statistical data visualization
- **scipy** — Statistical testing
- **sqlite3** — Database connectivity
- **pandasql** — SQL queries on pandas DataFrames

### Environment
```
pandas>=1.3.0
numpy>=1.21.0
matplotlib>=3.4.0
seaborn>=0.11.0
scipy>=1.7.0
pandasql>=0.7.3
```

---

## Project Structure

```
Phase2-project/
│
├── datasets/
│   ├── im.db                          # IMDb SQLite database
│   └── tn.movie_budgets.csv           # Financial data from The Numbers
│
├── notebooks/
│   └── movie_analysis.ipynb           # Main analysis notebook
│
├── presentations/
│   └── Group 6 presentationn.edited.pptx.pdf
│
├── README.md                          # Project documentation
└── requirements.txt                   # Python dependencies
```

---

## Installation & Usage

### Prerequisites
- Python 3.8 or higher
- pip package manager

### Setup Instructions

1. **Clone the repository:**
```bash
git clone https://github.com/Graham-49/Phase2-project.git
cd Phase2-project
```

2. **Install dependencies:**
```bash
pip install -r requirements.txt
```

3. **Launch Jupyter Notebook:**
```bash
jupyter notebook
```

4. **Run the analysis:**
Open the notebook and execute cells sequentially to reproduce the analysis.

---

## Statistical Methods

### Hypothesis Tests Conducted

**Test 1: Rating vs. Revenue**
- **H₀:** Mean worldwide revenue for high-rated movies ≤ low-rated movies
- **H₁:** Mean worldwide revenue for high-rated movies > low-rated movies
- **Method:** Independent samples t-test (unequal variances)
- **Result:** p = 2.05e-13, reject H₀ at α = 0.05

**Test 2: Release Month Effect**
- **H₀:** Release month has no significant effect on worldwide gross
- **H₁:** Release month has a significant effect on worldwide gross
- **Method:** One-way ANOVA
- **Result:** p = 5.83e-18, reject H₀ at α = 0.05

---

## Visualizations

The project includes comprehensive visualizations:
- Bar charts for genre revenue comparison
- Correlation heatmaps for budget-revenue relationships
- Scatter plots showing budget vs. gross revenue
- Line charts depicting seasonal revenue patterns
- Horizontal bar charts of top-performing movies

All visualizations are generated dynamically from the data and can be customized.

---

## Limitations & Future Work

### Current Limitations
- Dataset limited to 2,752 movies with complete financial data
- No adjustment for inflation in revenue figures
- Genre categorization uses broad combinations rather than granular sub-genres
- Does not account for marketing spend or international market variations

### Future Enhancements
- Incorporate marketing budget data for comprehensive ROI analysis
- Add sentiment analysis from reviews and social media
- Develop predictive models for box office forecasting
- Analyze streaming platform performance metrics
- Include talent (director/actor) impact analysis

---

## Contributors

**Group 6 Members:**
- Project analysis conducted as part of Data Science coursework
- Full Time Hybrid program

---

## License

This project is available for educational and reference purposes.

---

## Contact

For questions or collaboration opportunities, please open an issue in the GitHub repository.

---

## Acknowledgments

- Data provided by IMDb and The Numbers
- Analysis conducted under the guidance of Instructor Diana Mongina
- Special thanks to the Data Science program for project support
