# GitHub Topic Repository Scraper

A Python web scraping project that explores GitHub's topic directory and
collects repository information from each listed topic. Starting from
the [GitHub Topics](https://github.com/topics) page, the scraper
extracts topic links, visits each topic page, and gathers details for up
to 320 repository entries , including the author's name,
repository title, author profile URL, repository URL, and star count.
The results are organized into a Pandas DataFrame for inspection and
further analysis.

## Project Workflow

1.  Send an HTTP request to the GitHub Topics page.
2.  Parse the returned HTML with Beautiful Soup.
3.  Extract the topic-page URLs listed on the page.
4.  Visit each topic page and locate repository cards.
5.  Extract author names, repository titles, profile links, repository
    links, and star counts.
6.  Convert star counts into numeric values where possible.
7.  Store the collected records in a Pandas DataFrame.

## Data Collected

  Column              Description
  ------------------- ------------------------------------------------------
  `author_name`      Name or username displayed for the repository author

  `repository`        Repository title

  `author_account`    Link to the author's GitHub profile

  `repository_link`   Direct link to the repository

  `star`              Repository star count converted to a number
 
## Technologies Used

-   **Python** --- scraping logic and data processing
-   **Requests** --- sends HTTP requests and retrieves page content
-   **Beautiful Soup** --- parses HTML and selects page elements
-   **Pandas** --- stores the extracted data in a DataFrame

## Getting Started

### 1. Clone the repository

``` bash
git clone https://github.com/<your-username>/github-topic-repository-scraper.git
cd github-topic-repository-scraper
```

Replace `<your-username>` with your GitHub username.

### 2. Install dependencies

``` bash
python -m pip install requests beautifulsoup4 pandas
```

### 3. Run the scraper

Save the scraping code in a Python file, such as `scraper.py`, then run:

``` bash
python scraper.py
```

The script returns a Pandas DataFrame named `complete_df`. 

Inspect it with `complete_df.head()` or export it for later analysis
with `complete_df.to_csv("github_repositories.csv", index=False)`.

## Error Handling and Reliability

The scraper can check HTTP response status and use request timeouts to
avoid waiting indefinitely. GitHub may change its HTML structure, so
selectors can require maintenance. Requests may also fail because of
network issues or rate limiting. Consider adding request pacing,
logging, and retry logic before running large scraping jobs.

## Attached Output File

I have also attached the `Top_Repository.csv` file to show how the final scraped dataset looks. Refer to this file to understand the output structure and the extracted data.

## Project Scope

This project collects repository metadata displayed on GitHub topic
pages. It does not scrape repository source code, issues, pull requests,
or commit histories.
