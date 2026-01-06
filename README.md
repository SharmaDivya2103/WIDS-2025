# Midterm Submission - Predicting Stock Volatility Using Financial News Sentiment Analysis
The task was to work with real financial data and create a complete data pipeline, from data collection to basic analysis.

## Approach

### 1. Financial News Collection
I began by gathering financial news from various RSS feeds like Yahoo Finance, CNBC, and MarketWatch. The news data came in XML format, so I parsed the RSS feeds to pull out important details such as the source, headline, and publication date. I saved the collected data in a raw CSV file for further processing.

**Output file:**  
`news_raw.csv`

### 2. Understanding XML Structure
As I worked with the RSS feeds, I examined the XML structure and identified key tags such as `<item>`, `<title>`, and `<pubDate>`. I added a Markdown section in the notebook explaining how these tags are used and how RSS feeds differ from typical HTML web pages.

### 3. News Data Cleaning and Standardization
After gathering the raw news data, I cleaned and standardized it by converting the publication timestamps to UTC format. I extracted only the date part from the timestamps and added new columns for the date and the length of each headline. I saved the cleaned dataset separately for later use.

**Output file:**  
`news_cleaned.csv`

### 4. Stock Price Data Collection
Next, I selected a US-listed stock and used the `yfinance` API to download historical stock price data. I made sure the dataset included at least 10 trading days and contained only the necessary columns: Open, High, Low, Close, and Volume.

### 5. Market Calendar Awareness
When comparing news dates with stock market dates, I realized that some news articles were published on non-trading days, like weekends and holidays. I identified these non-trading days, counted the number of news articles published then, and explained the reasons for market closures in a Markdown section.

### 6. Data Merging
I merged the cleaned news data with the stock price data using the date column. To make sure no news data was lost, I performed a left join and kept rows even when stock data was missing. I also added a boolean column to indicate whether a date was a trading day.

**Output file:**  
`merged_midterm_data.csv`

### 7. Exploratory Analysis
Finally, I conducted basic exploratory analysis on the merged dataset. This included assessing the number of news articles per day, the distribution of news from different sources, and the differences in news frequency on trading versus non-trading days. I visualized these findings with simple plots.

## Challenges Faced
During the assignment, I encountered some problems like dealing with RSS feeds that blocked requests and mismatches between news dates and stock market trading days. These challenges helped me better understand real-world data inconsistencies and how to manage them programmatically.

## Files in This Repository

- `midterm_submission.ipynb` – Jupyter notebook containing all code and explanations  
- `news_raw.csv` – Raw news data collected from RSS feeds  
- `news_cleaned.csv` – Cleaned and standardized news data  
- `merged_midterm_data.csv` – Final merged dataset used for analysis  
