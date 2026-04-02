# 📊 BI Platform

<div align="center">

![Python](https://img.shields.io/badge/Python-3.11+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-1.35+-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.0+-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-5.20+-3F4F75?style=for-the-badge&logo=plotly&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-10B981?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Live-22C55E?style=for-the-badge)

### 🚀 A fully interactive, browser-based Business Intelligence platform
### built entirely in Python — no expensive tools, no coding required.

**[🌐 Live Demo](https://bimlplatform-8aqd7my7y6xhlz8egwv6pl.streamlit.app)** &nbsp;|&nbsp;

</div>

## 🎯 What Is This?

> **Upload any CSV or Excel file → get a full BI dashboard, forecasts, and business insights in seconds.**

The **BI & Forecasting Platform** is an open-source, web-based analytics tool that lets anyone — regardless of technical background — go from raw data to actionable business insights without writing a single line of code.

Think of it as a **lightweight, free alternative to Power BI or Tableau**, with built-in data cleaning, time-series forecasting, and auto-generated business recommendations — all running locally or in the cloud.


## ✨ Key Features

| Feature                      | Description                                                            |
| ---------------------------- | ---------------------------------------------------------------------- |
| 📂 Smart Data Upload         | Upload CSV or Excel files with automatic encoding detection            |
| 🧹 Auto Data Cleaning        | Handles missing values, duplicates, and outliers automatically         |
| 🔍 Exploratory Data Analysis | Visual charts including distributions, scatter plots, and correlations |
| 📈 BI Dashboard              | Displays KPIs, trends, and segment comparisons                         |
| 📉 Forecasting               | Time-series forecasting using ARIMA or Linear Trend                    |
| 💡 Insights Engine           | Automatically generates business insights from the dataset             |
| ⚡ Performance Optimization   | Uses Streamlit caching to improve speed                                |
| ☁️ Cloud Deployment          | Hosted on Streamlit Community Cloud                                    |



---

## 🖥️ Live Demo

> **Try it right now — no sign-up, no installation:**
> ### 👉 [https://bimlplatform-8aqd7my7y6xhlz8egwv6pl.streamlit.app](https://bimlplatform-8aqd7my7y6xhlz8egwv6pl.streamlit.app)

---

## 🗺️ Platform Workflow

```
┌─────────────┐     ┌──────────────┐     ┌─────────────┐     ┌──────────────┐
│  📂 Upload  │────▶│  🧹 Clean    │────▶│  🔍 Explore │────▶│  📈 BI Dash  │
│  CSV/Excel  │     │  Auto-fix    │     │  EDA Charts │     │  KPI Trends  │
└─────────────┘     └──────────────┘     └─────────────┘     └──────────────┘
                                                                      │
                    ┌──────────────┐     ┌─────────────┐             ▼
                    │  💡 Insights │◀────│  📉 Forecast│◀────────────┘
                    │  Auto Report │     │  ARIMA/ML   │
                    └──────────────┘     └─────────────┘
```

---

## 📁 Project Structure

```
bi_ml_platform/
│
├── 📄 main.py                    # App entry point — routing & sidebar navigation
├── 📄 requirements.txt           # All Python dependencies
│
├── 📂 dashboard/                 # UI layer — one file per page
│   ├── 🏠 home.py               # Landing page with session KPIs
│   ├── 📂 upload.py             # File uploader + sample dataset
│   ├── 🧹 cleaning.py           # Auto-cleaning pipeline & report
│   ├── 🔍 eda.py                # EDA: distributions, scatter, heatmap
│   ├── 📈 bi.py                 # BI dashboard: KPIs, trends, segments
│   ├── 📉 forecasting.py        # ARIMA/linear forecasting page
│   └── 💡 insights.py           # Auto-generated insights report
│
└── 📂 utils/
    └── 🧠 data_manager.py        # ALL logic: loading, cleaning, EDA,
                                  #             forecasting, insights, cache
```

> **Architecture principle:** Dashboard pages handle display only. All computation lives in `data_manager.py`. Pages never calculate — they only call and show.

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                        BROWSER (User)                           │
└────────────────────────────┬────────────────────────────────────┘
                             │ HTTP
┌────────────────────────────▼────────────────────────────────────┐
│                    main.py  (Entry Point)                       │
│   Sets page config │ Renders sidebar │ Routes to page module    │
└────────────────────────────┬────────────────────────────────────┘
                             │ imports & calls render()
┌────────────────────────────▼────────────────────────────────────┐
│              dashboard/  (Presentation Layer)                   │
│  home │ upload │ cleaning │ eda │ bi │ forecasting │ insights   │
│                 ↕ reads/writes session_state                    │
│                 ↕ calls functions from data_manager             │
└────────────────────────────┬────────────────────────────────────┘
                             │ function calls
┌────────────────────────────▼────────────────────────────────────┐
│            utils/data_manager.py  (Logic Layer)                 │
│                                                                  │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────────┐   │
│  │  Loading │  │ Cleaning │  │   EDA    │  │  Forecasting │   │
│  │ CSV/XLSX │  │ 6-steps  │  │ Stats    │  │ ARIMA/Linear │   │
│  └──────────┘  └──────────┘  └──────────┘  └──────────────┘   │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │              Streamlit Cache Layer                        │  │
│  │  @st.cache_data  ·  @st.cache_resource                  │  │
│  └──────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📄 Page-by-Page Guide

### 🏠 Home
- Displays live session KPIs: dataset rows, columns, models trained, best accuracy
- Workflow guide showing the 7-step analytics journey
- No computation — purely informational

### 📂 Upload Data
- Drag & drop CSV or Excel upload with multi-encoding support
- Built-in sample dataset (1,200-row synthetic sales/churn data)
- Instant preview: row count, column count, missing cells, duplicates
- Column type inspector with null percentages

### 🧹 Data Cleaning
The auto-cleaning pipeline runs **6 sequential steps**:

```
Step 1 → Drop fully empty rows
Step 2 → Impute missing values  (median for numeric, mode for categorical)
Step 3 → Remove duplicate rows
Step 4 → Cap outliers           (IQR method: clip at Q1-1.5×IQR and Q3+1.5×IQR)
Step 5 → Encode categoricals    (LabelEncoder → adds *_enc columns)
Step 6 → Engineer date features (month, day-of-week, quarter)
```

Reports: missing values fixed, duplicates removed, outliers capped, quality score (0–100%)

### 🔍 EDA Analysis
- **Distribution chart** — histogram + marginal box plot for any numeric column
- **Scatter plot** — X vs Y with optional colour-coding by category
- **Box plot** — spread comparison across segments
- **Correlation heatmap** — Pearson r matrix for all numeric features
- **Top correlations table** — ranked by absolute correlation value

### 📈 BI Dashboard
- **KPI cards** — sum and average for top numeric columns
- **Time-series area chart** — daily / weekly / monthly frequency toggle
- **Category bar chart** — any metric broken down by any category
- **Segment donut chart** — proportional share visualisation
- **CSV export** — download the full dataset

### 📉 Forecasting

```
Input: date column + value column + periods ahead + method

         Historical Data
              │
              ▼
    ┌─────────────────┐     Success    ┌───────────────────┐
    │  ARIMA (1,1,1)  │────────────▶  │  Forecast + 95%CI │
    │  statsmodels    │               └───────────────────┘
    └─────────────────┘
              │ Failure (short series / non-convergence)
              ▼
    ┌─────────────────┐               ┌───────────────────┐
    │  Linear Trend   │────────────▶  │  Forecast + 95%CI │
    │  numpy polyfit  │               └───────────────────┘
    └─────────────────┘

Output: forecast line + confidence band + MAPE score + CSV download
```

### 💡 Insights Report
Auto-generated findings using **6 statistical rules**:

| Rule Name       | Condition                                                                  | Priority |
| --------------- | -------------------------------------------------------------------------- | -------- |
| Skewness Check  | Any column with absolute skewness value greater than 2                     | Medium   |
| Pareto Analysis | Top 20% of rows contribute more than 60% of revenue                        | High     |
| Target Rate     | Positive rate exceeds the 20% industry benchmark                           | High     |
| Top Driver      | Feature with the highest Pearson correlation with target                   | High     |
| Segment Gap     | Best performing segment generates 1.5× more revenue than the worst segment | Medium   |
| Trend Detection | Change between first half and second half exceeds 10%                      | Medium   |


Each finding is colour-coded: 🔴 High &nbsp; 🟡 Medium &nbsp; 🟢 Low

---

## ⚡ Quick Start

### Option 1: Use the Live App (No Setup)
👉 Visit **[https://bimlplatform-8aqd7my7y6xhlz8egwv6pl.streamlit.app](https://bimlplatform-8aqd7my7y6xlz8egwv6pl.streamlit.app)**

### Option 2: Run Locally

**Prerequisites:** Python 3.10+ and Git

```bash
# 1. Clone the repository
git clone https://github.com/YOUR_USERNAME/bi-ml-platform.git
cd bi-ml-platform

# 2. Create a virtual environment
python -m venv venv

# 3. Activate it
# Windows:
venv\Scripts\activate
# Mac / Linux:
source venv/bin/activate

# 4. Install dependencies
pip install -r requirements.txt

# 5. Launch the app
streamlit run main.py


## 🧰 Technology Stack

| Technology       | Version | Purpose                                           |
| ---------------- | ------- | ------------------------------------------------- |
| **Streamlit**    | ≥ 1.35  | Web application framework and UI rendering        |
| **Pandas**       | ≥ 2.0   | Data manipulation and analysis                    |
| **NumPy**        | ≥ 1.26  | Numerical operations and forecasting calculations |
| **Plotly**       | ≥ 5.20  | Interactive charts and visualizations             |
| **scikit-learn** | ≥ 1.4   | Machine learning utilities and encoding           |
| **statsmodels**  | ≥ 0.14  | ARIMA time-series forecasting                     |
| **openpyxl**     | ≥ 3.1   | Reading Excel `.xlsx` files                       |
| **xlrd**         | ≥ 2.0   | Reading legacy Excel `.xls` files                 |


---

## 🚀 Performance & Caching

The platform uses Streamlit's caching system so heavy operations run **only once**:

```python
@st.cache_data          # For data (DataFrames, dicts, lists)
def clean_dataframe(df): ...

@st.cache_data
def run_forecast(_df, date_col, value_col, ...): ...

@st.cache_resource      # For objects (ML models, pipelines)
def train_all_classifiers(_df, feature_cols, target): ...
```

| Function                   | Cache Type   | Purpose                     | Performance Benefit                |
| -------------------------- | ------------ | --------------------------- | ---------------------------------- |
| `generate_sample_data()`   | `cache_data` | Generates demo dataset      | Runs only once per session         |
| `clean_dataframe()`        | `cache_data` | Data cleaning pipeline      | Prevents repeated cleaning         |
| `get_summary_stats()`      | `cache_data` | Computes dataset statistics | Instant results for large datasets |
| `get_correlation_matrix()` | `cache_data` | Correlation calculations    | Saves ~2 seconds                   |
| `run_forecast()`           | `cache_data` | Time-series forecasting     | Avoids repeated ARIMA training     |
| `generate_insights()`      | `cache_data` | Insight generation          | Faster report creation             |

> **Result:** After the first load, switching between pages is near-instant.

---

## 📦 requirements.txt

```txt
streamlit>=1.35.0
pandas>=2.0.0
numpy>=1.26.0
scikit-learn>=1.4.0
plotly>=5.20.0
statsmodels>=0.14.0
openpyxl>=3.1.0
xlrd>=2.0.1
```

---

## ☁️ Deployment Guide

### Deploy to Streamlit Community Cloud (Free)

```
1. Push your code to a public GitHub repository
2. Go to → https://share.streamlit.io
3. Sign in with GitHub
4. Click "New app"
5. Select your repo, branch: main, file: main.py
6. Click "Deploy!" — live in ~3 minutes
```

### Auto-Deploy on Every Push

```bash
# Make any change, then:
git add .
git commit -m "Update dashboard"
git push

# Streamlit Cloud detects the push and redeploys automatically (~60 seconds)
```

---

## 🗂️ Data Format Guide

The platform works with **any structured tabular data**. For best results:

| Data Type         | Example                        | Role in Analysis                                         |
| ----------------- | ------------------------------ | -------------------------------------------------------- |
| **Date**          | `order_date`, `created_at`     | Enables time-based trends and forecasting                |
| **Numeric**       | `revenue`, `units`, `cost`     | Calculates KPIs and supports statistical analysis        |
| **Categorical**   | `region`, `product`, `segment` | Enables grouping, segmentation, and comparison           |
| **Binary Target** | `churn`, `converted`           | Used for identifying key drivers and generating insights |


> **Tip:** Name your date column with "date" in it (e.g. `sale_date`) for automatic detection.

---

## 💡 Sample Dataset

No data? No problem. The built-in sample generates a **synthetic sales & churn dataset**:

```
Columns:  date | product | region | units | revenue | cost | tenure_months | churn
Rows:     1,200 (adjustable 200–5,000)
Purpose:  Explore all 7 platform features end-to-end
```

---

## 🎓 How ARIMA Forecasting Works

```
ARIMA = AutoRegressive (AR) + Integrated (I) + Moving Average (MA)

AR(1) → This month's revenue depends on last month's revenue
I(1)  → Differencing removes trend (makes series stationary)
MA(1) → Corrects for past prediction errors

              Past Data               Future Forecast
              ──────────────          ──────────────────────
              ████████████████        ░░░░░░░░░░░░
              ████████████████    ┌─  ░░░░░░░░░░░░  ─┐ 95% CI
              ████████████████  ──┘   ────────────   └──
              Jan  Feb  Mar  Apr  May  Jun  Jul  Aug  Sep

Fallback: If ARIMA fails, NumPy polyfit linear trend is used automatically.
```

---

## 🧪 Testing the Platform

### Recommended Demo Flow

```
Step 1 → Upload Data      → Click "Load sample dataset"
Step 2 → Data Cleaning    → Click "Run auto-cleaning pipeline"
                            → Note quality score (should be ~99%)
Step 3 → EDA Analysis     → View correlation heatmap
                            → Check which features correlate with "churn"
Step 4 → BI Dashboard     → Switch frequency: Monthly → Weekly
                            → Change "Group by" to "product"
Step 5 → Forecasting      → Select "date" + "revenue" + 12 periods
                            → Compare ARIMA vs Linear method
Step 6 → Insights Report  → Select "churn" as target variable
                            → Read top high-priority findings
```

---

## 📊 Project Stats

```
📁 Total files          :  12
📝 Lines of code        :  ~900
📋 Dashboard pages      :  7
⚡ Cached functions     :  7
📦 Dependencies         :  8
🌐 Deployment           :  Streamlit Community Cloud (Free)
🔄 CI/CD                :  Auto-deploy on git push
```

---

## 🗺️ Roadmap

- [x] Data upload (CSV + Excel)
- [x] Auto data cleaning pipeline
- [x] Interactive EDA charts
- [x] BI dashboard with KPIs
- [x] ARIMA forecasting with confidence intervals
- [x] Auto-generated insights report
- [x] Performance caching
- [x] Cloud deployment
- [ ] ML model training (Random Forest, Gradient Boosting)
- [ ] Real-time predictions page
- [ ] PDF report export
- [ ] User authentication
- [ ] Prophet seasonal forecasting
- [ ] Database backend (SQLite)
- [ ] Multi-dataset comparison

---

## 🤝 Contributing

Contributions are welcome! Here's how to get started:

```bash
# 1. Fork the repository on GitHub

# 2. Clone your fork
git clone https://github.com/YOUR_USERNAME/bi-ml-platform.git

# 3. Create a feature branch
git checkout -b feature/your-feature-name

# 4. Make your changes, then commit
git add .
git commit -m "Add: description of your feature"

# 5. Push and open a Pull Request
git push origin feature/your-feature-name
```

---

## 📬 Contact

**Khushbir Kaur Bamrah**

[![Email](https://img.shields.io/badge/Email-khushbir36%40gmail.com-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:khushbir36@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Khushbir_Kaur_Bamrah-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/khushbir-kaur-bamrah-178aa4269)
[![GitHub](https://img.shields.io/badge/GitHub-khushbirkaur-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/khushbirkaur)

---

<div align="center">

*Built with ❤️ using Python + Streamlit*

</div>
Author
KHUSHBIR KAUR BAMRAH
