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

`python node.py 5000`<br />
`python node.py 5001`<br />
`python node.py 5002`<br />
`python node.py 5003`

Then, in another terminal window, you can run the app.py file to interact with the distributed web crawler:
`python app.py
`
## app.py
This is the main module of the project which serves as the entry point to the application. It contains a loop that waits for user input to either crawl or scrape a website.

### Functions

- `make_urls(number_of_ports)`: This function takes in the number of ports and returns a list of URLs based on the number of ports.
- `get_random_url(list_of_urls)`: This function takes in a list of URLs and returns a random URL from the list.
- `scrape_website(url, params)`: This function takes in a URL and a dictionary of parameters and returns the scraped data as a dictionary.
- `crawl_website(url, params)`: This function takes in a URL and a dictionary of parameters and crawls the website, storing the HTML content and returning a list of child URLs.
- `main()`: This function is the entry point to the application. It contains a loop that waits for user input to either crawl or scrape a website.

## content.py
This module contains a function to check if a file exists and print its HTML content.
### Functions
`check_if_exists_and_print_html(name)`: This function takes in a file name and checks if the file exists. If it exists, it prints its HTML content. If it does not exist, it prints a message saying that the file is not accessible.

## crawler.py
This module contains functions to crawl a given URL and extract text content from its HTML.
### Functions
- `validate_url(url): This function takes in a URL and returns True if the URL is valid and False otherwise.
- `extract_text(html)`: This function takes in an HTML string and extracts the title and text content from it.
- `hard_disk_store(html, url)`: This function takes in an HTML string and a URL, and stores the HTML content on disk with a filename based on the URL.
- `crawl(url)`: This function

