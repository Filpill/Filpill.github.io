---
title: "Python Web Scraping"
description: "Showcasing webscraping and data analysis of a product website on Python"
date: 2023-10-03
hideSummary: true
ShowWordCount: true
ShowReadingTime: true
ShowToC: true
draft: false

cover:
  image: /img/scrape/scrape_thumbnail.png
  alt: Scraping thumbnail

categories: [Data]
---

# Summary

Extracting data from public facing websites is a challenging, yet rewarding prospect. 

The data contained inside each website holds information that could help leverage better decision making: *e.g. comparing various products and services with various metrics such as price and ratings.*

Modern website designs are increasingly making it more challenging to extract data due to:
- The stress put on the server with rate of requests being made.
- Cutting into their profit margins by using the collected data against them.

The web scraping approach always needs to be tailored to the website your are visiting. But from my current experience, it will usually fall into these categories:
- Using some web-automation framework like Selenium or Playwright and then parsing the HTML (loaded via the browser automation) using something like Selectolax.
- If the data is being loaded dynamically with JavaScript, then I'm also searching the browser for the *"hidden API"* which is calling the back-end to fetch into the front-end.

The benefit of searching for that so called *"Hidden API"* is that the retrieved data is already organised into a neat little JSON file. 

Preferably you will probably want the data directly from the back-end to retrieve a dataset. Transforming a JSON is much easier than trying to parse through the front matter for HTML tags and containers.

In the example shown below, I've scraped the Pimoroni.com website by making requests to the back-end API to retrieve the JSON data. I've analysed a sample of the data here for reference:


Link to the project here: [Python Web Scraping](https://github.com/Filpill/web_scraper)


### Analytics Process Flow | Pimoroni Data

Flowchart below denotes my process for making requests to Pimoroni.com:

{{<mermaid>}}

graph TD;

    subgraph Process Initiation
    0([Python Notebook Executed])--> A1[Select Product Collection]
    A1-->A2[Request JSON Data via API]
    end

    subgraph Data Extraction
    A2-->B[Return Number of Hits <br>on Product Page]
    B-->C[Modify Request To <br>Return All Hits <br>in a Single Page Request]
    C-->D[Unpack Products from JSON<br>into Dataframe]
    D-->E[Prune Unnecessary data from Dataframe]
    E-->F[Loop for every <br>Collection on Website]
    F-->F1{Are all Product <br>Collections Retrieved?}
    F1-->F1y[Yes]
    F1-->F1n[No]--Concat Results <br> to Existing DF-->A1
    end

    subgraph Data Visualization
    F1y-->V1[Drop Duplicate Product ID's]
    V1-->V2[Groupby and Count Datapoints]
    V2-->V3([Create Charts and Save Files])
    end

{{</mermaid>}}

### Data Visualisations | Pimoroni Data

The following images are served directly from my github repository:

![Product Types](https://raw.githubusercontent.com/Filpill/web_scraper/main/pimoroni/charts/product_type.png)
![Vendors](https://raw.githubusercontent.com/Filpill/web_scraper/main/pimoroni/charts/vendor.png)
