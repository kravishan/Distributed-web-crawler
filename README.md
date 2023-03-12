# Distributed Web Crawler

## Project Structure:

├── app.py<br />
├── content.py<br />
├── crawler.py<br />
├── generate_urls.py<br />
├── node.py<br />
└── README.md<br />

`app.py`: The main script for the project. This script allows the user to interact with the command-line interface and choose between scraping or crawling.<br />
`generate_urls.py`: A module that generates a list of URLs for the crawler to use.<br />
`scraper.py`: A module that contains functions for scraping a website.<br />
`content.py`: A module that contains a function to check if a file exists and print its content.<br />
`node.py`: A module that defines a Flask app and serves as the endpoint for the scraper and crawler.<br />
`crawler.py`: A module that contains functions for crawling a website.<br />
`storage/`: A directory where the scraped data is stored.<br />
`requirements`.txt: A file that lists the required packages for the project.

## Requirements:
Before running the application, you need to have the following packages installed:

- `requests`
- `beautifulsoup4`
- `flask`
- `prometheus_client`
- `validators`
- `aiohttp`
- `asyncio`

You can install these packages by running the following command:
`pip install -r requirements.txt
`

## How to Run:

To run the distributed web crawler, you need to run multiple instances of the `node.py` file in separate terminal windows. For example, to run four instances, you can run the following commands in four separate terminal windows:

`python node.py 5000<br />
python node.py 5001<br />
python node.py 5002<br />
python node.py 5003`

Then, in another terminal window, you can run the app.py file to interact with the distributed web crawler:
`python app.py
`
## app.py
This is the main module of the project which serves as the entry point to the application. It contains a loop that waits for user input to either crawl or scrape a website.
