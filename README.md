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

You also need to start a Prometheus server to collect and store metrics. You can start the server by running the following command in a separate terminal window:<br />
`python node.py 9000`

Then, in another terminal window, you can run the app.py file to interact with the distributed web crawler:

`python app.py
`
Note that the Prometheus server will be running on port 9000. You can access the Prometheus dashboard by visiting http://localhost:9000 in your web browser. The dashboard will show you health information about every node.

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
- `validate_url(url)`: This function takes in a URL and returns True if the URL is valid and False otherwise.
- `extract_text(html)`: This function takes in an HTML string and extracts the title and text content from it.
- `hard_disk_store(html, url)`: This function takes in an HTML string and a URL, and stores the HTML content on disk with a filename based on the URL.
- `crawl(url)`: This function takes in a URL, crawls the website, and returns a list of child URLs. It first checks if the URL is valid using `validate_url()`. Then, it requests the page using the requests library, and extracts the HTML content using the `extract_text()` function. The HTML content is then stored on disk using `hard_disk_store()`. Finally, the function uses `beautifulsoup4` to parse the HTML and extract all child URLs, which are returned as a list.

## generate_urls.py
This module generates a list of URLs for the crawler to use.

### Functions
`generate_urls(port)`: This function takes in a port number and generates a list of URLs based on that port number. It uses the validators library to ensure that the URLs are valid.

## node.py
This module defines a Flask app and serves as the endpoint for the scraper and crawler.
### Functions
`start_node(port)`: This function takes in a port number and starts a Flask app on that port. It defines two routes: `/scrape` and `/crawl`. Both routes accept a URL and a list of parameters as JSON in the request body. The `/scrape` route calls the `scraper.py` module to scrape the website, and returns the scraped data as JSON. The `/crawl` route calls the `crawler.py` module to crawl the website, and returns a list of child URLs as JSON.

## scraper.py
This module contains functions for scraping a website.
### Functions
`scrape_website(url, params)`: This function takes in a URL and a dictionary of parameters and returns the scraped data as a dictionary. It uses the requests library to `request` the page, and `beautifulsoup4` to extract the data.

## app.py
This is the main module of the project which serves as the entry point to the application. It contains a loop that waits for user input to either crawl or scrape a website.

### Functions
- `make_urls(number_of_ports)`: This function takes in the number of ports and returns a list of URLs based on the number of ports.
- `get_random_url(list_of_urls)`: This function takes in a list of URLs and returns a random URL from the list.
- `scrape_website(url, params)`: This function takes in a URL and a dictionary of parameters and returns the scraped data as a dictionary.
- `crawl_website(url, params)`: This function takes in a URL and a dictionary of parameters and crawls the website, storing the HTML content and returning a list of child URLs.
- `main()`: This function is the entry point to the application. It contains a loop that waits for user input to either crawl or scrape a website.

## storage/
The `storage/` directory is where the scraped data is stored. The `crawler.py` module stores the HTML content of each page it crawls in a file within the `storage/` directory. The name of the file is based on the URL of the page being crawled.

It is important to note that the storage directory should not be directly accessed by any other module of the project. The storage files are only accessed by the `crawler.py` module and should be accessed through the `content.py` module.
## content.py
This module contains functions to read the content of files stored in the `storage/` directory. The functions should be used to read the content of files stored in the `storage/` directory, as they handle file access errors and return useful messages to the user.
### Functions
- `read_content_from_file(url)`: This function takes in a URL, reads the content of the file associated with that URL in the `storage/` directory and returns the content as a string. If the file does not exist, the function returns a message indicating that the file could not be found.
- `check_if_file_exists(url)`: This function takes in a URL, checks if the file associated with that URL exists in the `storage/` directory, and returns True if the file exists and False otherwise.
## Conclusion
This project provides an example of a distributed web crawler that can be used to scrape or crawl websites. The crawler is designed to work on multiple nodes, with each node responsible for crawling a subset of the website. The scraped data is stored in the `storage/` directory, and can be accessed through the `content.py` module.

The project can be extended to include additional functionality, such as support for different types of data storage, integration with database systems, and more advanced crawling and scraping techniques.

