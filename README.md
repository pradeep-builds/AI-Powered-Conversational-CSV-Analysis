# AI-Powered Conversational CSV Data Analyst

A Python-based conversational data analysis tool that enables users to explore any CSV dataset using natural language. The application combines **Pandas** for deterministic statistical computation with the **Google Gemini API** for contextual interpretation, ensuring that numerical results are calculated locally while AI is used only to explain the analytics.

## Overview

This project provides an interactive command-line interface where users can load a CSV file and ask questions such as averages, maximum values, group-by aggregations, missing value analysis, and trend-related queries.

Unlike traditional AI chatbots that rely on sampled data, this application first computes the dataset statistics using Pandas and then grounds Gemini's responses in those computed analytics.

## Features

- Load and analyze any CSV dataset
- Natural language querying through a command-line interface
- Direct computation of averages, sums, minimum, maximum, median, and standard deviation
- Group-by aggregations and top-N value analysis using Pandas
- Automatic dataset profiling with:
  - Missing value analysis
  - Data type detection
  - Statistical summaries
  - Correlation matrix
- AI-generated contextual insights powered by Google Gemini
- Secure API key management using environment variables

## Project Structure

```text
AI-Powered-CSV-Data-Analyst/
│
├── CSV_AI_Assistant.ipynb
├── .env
├── .gitignore
├── requirements.txt
└── sample_data.csv
```

## Tech Stack

- Python 3.10+
- Pandas
- Google Gemini API (`google-genai`)
- python-dotenv
- Jupyter Notebook

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/your-username/AI-Powered-CSV-Data-Analyst.git
cd AI-Powered-CSV-Data-Analyst
```

### 2. Create a virtual environment (recommended)

**Windows**

```bash
python -m venv venv
venv\Scripts\activate
```

**macOS/Linux**

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

Or install manually:

```bash
pip install pandas google-genai python-dotenv
```

## Gemini API Configuration

Create a file named `.env` in the project root.

```text
GEMINI_API_KEY=YOUR_GEMINI_API_KEY
```

The application automatically loads the API key using `python-dotenv`.

**Never hardcode your API key into the source code or commit the `.env` file to GitHub.**

## How to Run

1. Open `CSV_AI_Assistant.ipynb` in Jupyter Notebook.
2. Run all cells.
3. When prompted, enter the path to your CSV file.

Example:

```text
Enter the path to your CSV file:
C:\Users\Pradeep\Downloads\housepricedata.csv
```

4. Ask questions about the dataset.
5. Type `exit` to close the application.

## Example Questions

### Statistical Questions

- What is the average LotArea?
- What is the maximum GarageArea?
- What is the median OverallQual?
- How many unique values are in OverallCond?

### Aggregation Questions

- Total GarageArea by OverallQual
- Average LotArea by OverallCond
- Top values in BedroomAbvGr

### Insight Questions

- What trends do you observe in this dataset?
- Which features appear to be strongly correlated?
- Summarize the overall characteristics of the dataset.

## Example Output

```text
CSV loaded successfully: 1460 rows, 11 columns.

Computing dataset profile...
Profile ready.

Ask a question:
> What is the average LotArea?

[Computed directly from the data]

The average LotArea is 10516.83.
```

For open-ended questions:

```text
> What trends do you see?

[AI-interpreted from computed statistics]

The dataset suggests that OverallQual has a strong positive relationship with the target variable, while GarageArea and TotalBsmtSF also contribute significantly to higher-valued properties.
```

## Architecture

```text
        CSV Dataset
             │
             ▼
      Pandas DataFrame
             │
             ▼
   Statistical Profiling
 (EDA + Missing + Correlation)
             │
      ┌──────┴──────┐
      │             │
      ▼             ▼
Direct Pandas    Gemini API
 Computation     Interpretation
      │             │
      └──────┬──────┘
             ▼
      Natural Language Answer
```

## Supported Operations

| Category | Operations |
|----------|------------|
| Numerical | Average, Sum, Max, Min, Median, Standard Deviation |
| Categorical | Unique values, Counts, Top-N frequencies |
| Aggregation | Group-by Mean, Sum, Count |
| Profiling | Missing values, Data types, Correlations, Statistical Summary |
| AI Insights | Dataset interpretation and trend analysis |

## Security

- API keys are stored in `.env`
- `.env` should be included in `.gitignore`
- No credentials are stored inside the notebook

Example `.gitignore`:

```text
.env
__pycache__/
.ipynb_checkpoints/
```

## Future Improvements

- Support Excel (`.xlsx`) files
- Interactive visualizations using Matplotlib and Seaborn
- Automatic chart generation from natural language
- Support for large-scale datasets using Apache Spark or Dask
- Web interface using Streamlit

## Author

**Pradeep Rajkumar**
contact: pradeeprajkumar025@gmail.com
