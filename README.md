# distributed-web-crawler

## File Descriptions:

`README.md`: The README file for the project. This is where you should include a brief introduction to the project, installation instructions, usage instructions, and other relevant information about the project.<br />
`app.py`: The main script for the project. This script allows the user to interact with the command-line interface and choose between scraping or crawling.<br />
`generate_urls.py`: A module that generates a list of URLs for the crawler to use.<br />
`scraper.py`: A module that contains functions for scraping a website.<br />
`content.py`: A module that contains a function to check if a file exists and print its content.<br />
`node.py`: A module that defines a Flask app and serves as the endpoint for the scraper and crawler.<br />
`crawler.py`: A module that contains functions for crawling a website.<br />
`storage/`: A directory where the scraped data is stored.<br />
`requirements`.txt: A file that lists the required packages for the project.

## Installation:
To install the required packages for this project, run the following command:<br />
`pip install -r requirements.txt
`
## Usage:
To start the web scraper, run the following command:<br />
`
python app.py
`
<br />The program will prompt you to choose between crawling or scraping. If you choose to crawl, you will be prompted to enter a website and the number of levels to crawl. If you choose to scrape, you will be prompted to enter a website and a filename to save the scraped data to.
