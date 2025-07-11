# DataQueryAssistant
Dataquery-Bigquery-GCP-dataAnalysis-report generation

===============================
DataQuery Assistant - README
===============================

Overview:
---------
DataQuery Assistant is an AI-powered CLI tool that allows business users to query payment-related data using natural language. 
It translates queries into SQL using Gemini, fetches data from Google BigQuery, and generates Word reports with summaries, key insights, and charts.

Environment Requirements:
--------------------------
- Platform: Google Colab (recommended for easy setup)
- Python version: 3.8+

Required Packages:
-------------------
Install these packages before running the program:

!pip install -q google-cloud-bigquery
!pip install -q google-generativeai
!pip install -q pandas matplotlib seaborn python-docx

Python Libraries Used:
-----------------------
- google.colab.auth
- google.cloud.bigquery
- google.generativeai (Gemini API)
- pandas
- matplotlib
- seaborn
- docx (python-docx)
- datetime, os, re

Google Cloud Requirements:
---------------------------
1. BigQuery Enabled in your Google Cloud project
2. Cloud project ID (used: `testdatapayment`)
3. Required IAM permissions for BigQuery:
   - bigquery.jobs.create
   - bigquery.tables.getData
   - bigquery.datasets.get
4. Enable the following APIs:
   - BigQuery API
   - Generative Language API (for Gemini)

Authentication:
----------------
- Authenticate in Colab using:
  `from google.colab import auth`
  `auth.authenticate_user()`

Data Source & Storage:
-----------------------
BigQuery Tables Used:
- `testdatapayment.payment_data_colab.transactions_colab`
- `testdatapayment.payment_data_colab.daily_summary_by_country`
- `testdatapayment.payment_data_colab.daily_summary_by_region`

These tables contain:
- transaction_timestamp, status, amount, currency, payment_method, card_type
- transaction_date, country/region, successful_transactions, failed_transactions

Gemini API:
------------
- Used to convert natural language to SQL
- Also generates summaries and insights based on result data
- Requires API key for: models/gemini-1.5-flash

Security Features:
-------------------
- User query is filtered to reject destructive intents (e.g., delete, drop, truncate)
- Generated SQL is checked to only allow SELECT statements

Output:
--------
- Word reports with:
  - Query summary
  - Story insights
  - Key business takeaways
  - Line/bar chart visualizations
- Saved with timestamp and query keyword in `/content/sample_data/`

How to Run:
------------
1. Open the notebook in Google Colab
2. Install required packages
3. Authenticate to Google Cloud
4. Enter your payment-related query in natural language
5. View generated report in DOCX format from the output folder

Example Queries:
----------------
- Show failed transactions month-wise in 2024
- Compare payment methods for March and April 2024
- Provide success vs failure breakdown by country

