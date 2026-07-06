# NBA Player Stats Analysis & Dashboard

An end-to-end data project that scrapes NBA player and team statistics, cleans and analyzes the data, stores it in MongoDB, and presents the insights through an interactive Streamlit dashboard.

##  Project Overview

This project explores NBA player performance data to uncover trends in age, position, scoring, and team composition — from raw web scraping to a deployed interactive web app.

##  Data Collection & Preprocessing

### 1. Data Scraping
- Used Python's **requests** library to fetch HTML content from the NBA website (or a related statistics platform)
- Parsed the data using **BeautifulSoup (bs4)** to extract structured information (player stats, team rosters, performance metrics)

### 2. Data Cleaning
- Removed duplicate entries to ensure each player/team is represented once
- Handled null/missing values (filled numerical data with averages, dropped irrelevant rows)
- Applied **regex** to standardize text fields (player names, team abbreviations) and extract numerical values (percentages, ages)
- Converted column data types (e.g., strings to integers for Age/Points, cleaned FG% into float values)

### 3. Exploratory Data Analysis (EDA)
Processed the cleaned data to generate visualizations covering distributions, correlations, and positional trends.

##  Key Insights

- **Age Distribution:** Most players are between 22.5–30 years old, peaking around 25–27.5; few play past 35
- **Top Scorers:** Joel Embiid, Luka Dončić, and Damian Lillard lead in total points
- **Deepest Rosters:** SAS (Spurs) and DET (Pistons) have the most players (~50), suggesting rebuilding phases with younger talent
- **Position Distribution:** PG and SG make up the largest share (~18–19% each); Centers are least common (~17%)
- **Age vs. Points:** Peak scoring occurs between ages 25–30, with a slight decline after 30
- **Shooting Percentages:** FG% typically exceeds 3P%, since closer shots are more efficient; FT% varies widely
- **Assists vs. Rebounds by Position:** PGs lead in assists, Centers dominate rebounds
- **Top Scoring Teams:** TOR (Raptors) and PHI (76ers) rank highest in average points per game
- **Top 5 Player Shooting Profiles:** Giannis and Durant excel in 2P%; Curry and Dončić balance FG%, 3P%, and FT%
- **Correlation Heatmap:**
  - Points (PTS) strongly correlate with minutes played (MP) and field goal attempts
  - Assists (AST) and rebounds (TRB) correlate with position
  - Age shows a slight negative trend with steals (STL) and blocks (BLK)
  - 3P% is essentially independent of age

###  Key Takeaways
- **Prime Age:** NBA players peak offensively between 25–30 years old
- **Positional Trends:** Guards dominate ball-handling; Centers focus on rebounding
- **Team Strategies:** High-scoring teams (e.g., BOS, LAL) prioritize offensive firepower, while others (e.g., SAS) emphasize roster depth
- **Shooting Efficiency:** Top players maintain high 2P% and FT%, with 3P% differentiating guards

##  Storing Data in MongoDB

MongoDB was used as a NoSQL database to store both the cleaned dataset and generated visualizations:
- The cleaned CSV was imported into a dedicated collection for efficient retrieval within the Streamlit app
- Each visualization was saved as a **Base64-encoded image**, along with its title and description, in a separate collection
- This structure allowed dynamic retrieval and display of content without regenerating plots on each app load

##  Building the Streamlit App

1. **Connecting to MongoDB** – used `pymongo` to connect and retrieve both the cleaned dataset and stored visualizations
2. **Data Preparation** – converted data into a Pandas DataFrame, removed the `_id` column, and dropped duplicate rows
3. **Building the Dashboard** – built with Streamlit, featuring:
   - A sidebar for CSV file download
   - A KPIs section (total players, number of teams, top scorer)
   - Visualizations with accompanying insights and analysis
   - A selectbox for dynamically exploring teams and player details
4. **Displaying Visualizations** – pre-generated visualizations retrieved from MongoDB in Base64 format, decoded, and displayed alongside descriptive analysis

##  Deployment

The interactive dashboard was deployed using **Streamlit**, making it accessible as a standalone web app where users can explore NBA data, download the dataset, and view key statistics and visualizations.

##  Tech Stack
- **Python** – requests, BeautifulSoup (bs4), Pandas, regex
- **MongoDB** – NoSQL storage for cleaned data & visualizations (pymongo)
- **Streamlit** – interactive dashboard & deployment

## 🔗 Live Demo
You can try the live interactive dashboard here: [NBA Players Analysis App](https://nba-players-analysis-g2xxvsvngdmkumcxkzoh5d.streamlit.app/)

##  How to Use
1. Clone this repository
2. Install dependencies: `pip install -r requirements.txt`
3. Set up your MongoDB connection string
4. Run the app: `streamlit run app.py`

---
