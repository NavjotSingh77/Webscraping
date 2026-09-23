# Web Scraping & API Data Analysis

A hands-on Python project covering two practical data collection and analysis workflows: scraping technology-company and job-posting data from web pages, and retrieving weather data through a web API.

## Project Overview

This Jupyter Notebook contains two modules:

### Module 1 — Tech Industry Companies & Job Postings

The first module simulates a technology recruitment analytics workflow. It collects information about large technology companies, cleans the scraped data, extracts location information, and parses job listings from a job-search results page.

### Module 2 — Weather Data Using an API

The second module demonstrates how to consume weather data from a JSON-based API, convert nested response data into a Pandas DataFrame, inspect the returned fields, and visualize temperature trends.

## Module 1: Tech Industry Analysis

### 1. Scraping Company Data

The notebook retrieves an HTML page containing a table of large technology companies and uses `pandas.read_html()` to extract the available tables.

Source used by the notebook:

`https://dlai-lc-dag.s3.us-east-2.amazonaws.com/list_of_largest_companies.html`

The extracted company dataset contains information including:

* Company name
* Revenue in USD billions
* Employee count
* Country of origin
* Headquarters

The executed notebook output contains a 25-company table including Amazon, Apple, Alphabet, Microsoft, Meta, Nvidia, IBM, and other large technology companies.

### 2. Data Cleaning

The company table is transformed into a cleaner structure with standardized column names:

```text
company
revenue_usd_billions
employee_count
country
headquarters
```

The revenue field is cleaned by removing the `$` symbol and converting the values to numeric `float` values.

### 3. Revenue Analysis

The notebook creates a revenue distribution visualization to examine how revenue varies across the companies in the scraped dataset.

### 4. Job Posting Scraping

The notebook uses `requests` and `BeautifulSoup` to retrieve HTML from a job-search page and locate job listing containers.

Job listing elements are selected using the page's HTML structure, including the `base-search-card_info` container and job-title elements.

The extracted job records are assembled into a Pandas DataFrame with the following fields:

```text
job_title
company
location
list_date
```

This demonstrates a practical HTML parsing workflow for converting webpage markup into structured recruitment data.

## Module 2: Weather API Analysis

The second module demonstrates API-based data collection using `requests`.

The notebook uses `wttr.in` to request weather data for a specified city and parses the JSON response.

Example city used in the notebook:

`Sydney`

The response is navigated through the JSON structure and the daily weather records are loaded into Pandas.

The weather DataFrame contains fields such as:

* Date
* Average temperature (°C / °F)
* Minimum temperature (°C / °F)
* Maximum temperature (°C / °F)
* Astronomy-related information
* Hourly weather information
* Sun hours
* Snowfall
* UV index

### Temperature Visualization

The notebook plots minimum and maximum temperature over the returned dates to visualize temperature variation through time.

## Technologies Used

| Area                | Technology           |
| ------------------- | -------------------- |
| Programming         | Python               |
| Web Requests        | `requests`           |
| HTML Parsing        | BeautifulSoup        |
| Table Extraction    | Pandas `read_html()` |
| Data Analysis       | Pandas               |
| Regular Expressions | Python `re`          |
| Visualization       | Matplotlib, Seaborn  |
| API Data            | wttr.in JSON API     |
| Environment         | Jupyter Notebook     |

## Repository Structure

```text
Webscraping/
│
├── webscraping.ipynb    # Web scraping, job analysis and weather API analysis
├── LICENSE              # Project license
└── README.md            # Project documentation
```

## Workflow

```text
Web Pages / APIs
       │
       ├── Company HTML table
       │       ↓
       │   pandas.read_html()
       │       ↓
       │   Data Cleaning
       │       ↓
       │   Company Analysis
       │
       ├── Job Search HTML
       │       ↓
       │   Requests + BeautifulSoup
       │       ↓
       │   Structured Job Data
       │       ↓
       │   Pandas Analysis
       │
       └── Weather JSON API
               ↓
           requests
               ↓
           JSON Parsing
               ↓
           Pandas DataFrame
               ↓
           Temperature Visualization
```

## How to Run

### 1. Clone the repository

```bash
git clone https://github.com/NavjotSingh77/Webscraping.git
cd Webscraping
```

### 2. Install dependencies

```bash
pip install pandas requests beautifulsoup4 matplotlib seaborn jupyter
```

### 3. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open `webscraping.ipynb` and run the cells sequentially.

## What This Project Demonstrates

* Extracting HTML tables with Pandas
* Sending HTTP requests with Python
* Parsing webpage structure with BeautifulSoup
* Selecting and extracting information from HTML elements
* Cleaning scraped data into analysis-ready columns
* Converting textual numeric fields into usable numeric types
* Building structured datasets from job listings
* Consuming JSON APIs
* Working with nested API responses
* Creating visualizations from collected data

## Key Learning Outcomes

This project provides practical experience in the complete path from **web data acquisition to analysis**:

**Extract → Parse → Clean → Structure → Analyze → Visualize**

It also demonstrates the difference between two common data acquisition approaches:

* **Web scraping:** extracting information from HTML pages
* **API consumption:** retrieving structured JSON data directly from an API

## Notes

The notebook relies on external webpages and an external weather service. Because web pages and APIs can change over time, the exact returned data may differ from the notebook's previously executed outputs.

For production use, it would be useful to add request error handling, timeout settings, validation for missing HTML elements, and API response checks.

## Future Improvements

* Add robust exception handling for failed HTTP requests.
* Add request timeouts and retry logic.
* Store scraped job/company datasets as CSV files.
* Add filtering by company, location, or job title.
* Perform job-location and posting-date analysis.
* Extract additional job attributes such as seniority or employment type where available.
* Flatten hourly weather data for deeper time-series analysis.
* Turn the notebook into reusable Python scraping/API modules.
* Add automated scheduled data collection.

## Author

**Navjot Singh**
---

⭐ If you find this project useful, consider starring the repository.
