Overview:
This project, developed in a Jupyter Notebook, involves scraping data from a Wikipedia page listing the largest companies in the United States by revenue. The goal was to extract relevant data, organize it into a structured format, and save it as a CSV file for further analysis or use. This project demonstrates how to use web scraping techniques within an interactive environment to collect and process data.

Objective:
To extract and organize data about the largest U.S. companies by revenue from a Wikipedia page and store it in a CSV file for easy access and analysis.

Problem Statement:
The challenge was to automate the extraction of structured data from a Wikipedia page, which is formatted as an HTML table, and convert it into a clean, usable dataset for further processing.

Tools & Technologies Used

Languages: Python

Libraries/Frameworks:

BeautifulSoup (for parsing HTML)
Requests (for making HTTP requests)
Pandas (for data manipulation)

Tools:
Jupyter Notebook (for development and visualization)
Wikipedia (as the data source)


Process & Methodology

Fetching the Webpage:
Used the requests library to send an HTTP request to the Wikipedia page.

import requests

url = 'https://en.wikipedia.org/wiki/List_of_largest_companies_in_the_United_States_by_revenue'
page = requests.get(url)

Parsing the HTML:
Employed BeautifulSoup to parse the HTML content of the page and locate the specific table containing the desired data.

from bs4 import BeautifulSoup

soup = BeautifulSoup(page.text, 'html.parser')
tables = soup.find_all('table', class_='wikitable sortable')
table = tables[1]  # Selecting the correct table

Extracting Data:
Extracted the relevant data (company name, industry, revenue, etc.) from the table rows and columns.

import pandas as pd

headers = [header.text.strip() for header in table.find_all('th')]
df = pd.DataFrame(columns=headers)

rows = table.find_all('tr')[1:]  # Skipping the header row
for row in rows:
    columns = row.find_all('td')
    row_data = [column.text.strip() for column in columns]
    df.loc[len(df)] = row_data

Data Storage:
Organized the extracted data into a Pandas DataFrame and saved it as a CSV file.
codedf.to_csv('/Users/aqsa/Desktop/File Sorter/Companies.csv', index=False)


Challenges:
Navigating HTML Structure: The page contained multiple tables, so locating the correct one required careful inspection of the HTML structure.
Data Cleaning: Ensuring that the extracted data was clean and correctly formatted for storage in a CSV file.

Innovation:
Utilizing Jupyter Notebook allowed for an interactive and iterative approach to developing the web scraping code, making it easier to debug and visualize data throughout the process.


Outcomes:
Successfully extracted data from the Wikipedia page, creating a CSV file containing information on the largest companies in the U.S. by revenue. The dataset includes company rank, name, industry, revenue, growth, number of employees, and headquarters location.

Impact:
This project demonstrates the ability to automate the extraction of structured data from a webpage, which can be applied in various fields for data collection, research, and analysis.


Lessons Learned:
Gained a deeper understanding of how to navigate and parse HTML structures using BeautifulSoup.
Improved skills in data extraction and cleaning, which are essential for preparing data for analysis.
Enhanced familiarity with Jupyter Notebook as a tool for data science projects, benefiting from its interactive environment.

Future Work:
Expand the project to include data from multiple years to analyze trends over time.
Implement error handling and logging to make the web scraping process more robust and reliable.


Links:
GitHub Repository (Include link to the project repository)
Wikipedia Page 


Personal Growth:
This project enhanced my web scraping and data processing skills within the Jupyter Notebook environment, which is valuable for data-intensive tasks. It also provided a practical application of Python libraries like BeautifulSoup and Pandas in a real-world scenario.

Relevance:
The ability to efficiently collect and process data from online sources aligns with my broader career goals in data science and analytics. This project also deepened my understanding of how to handle and manipulate large datasets, a skill crucial for my future endeavors in this field.
