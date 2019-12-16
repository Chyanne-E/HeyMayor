---
title: "Where this data came from"
date: 2019-12-16
published: true
tags: [webscraping,opendata]
excerpt: "It's easy to find the mayor's daily schedule online, but aggregating those daily schedules over time required web scraping and data transformation. "
toc: true
toc_sticky: true
---

# Mayor Kenney's Public Schedule

Mayor Kenney's administration makes his daily public schedule available online in the form of press releases on the Philadelphia city government website, https://www.phila.gov/the-latest/archives/#/?templates=press_release. You can click through individual press releases to see what public events, like speeches and award ceremonies, the mayor attends. 

To get a more holistic view of where the mayor's job takes him, I collected data from these press releases using web scraping. 

## Web Scraping Process 

#### Collect links to each press release: 
The website I scraped includes a significant interactive component: there is a table that contains a link for each press release.  The table is populated dynamically and pulls its content from a database on the server. As a result, I webscraped for the individual links to each press release not from the table, but from the URL that shows up as an XHR request: https://www.phila.gov/wp-json/the-latest/v1/archives?count=-1

#### Test web scraping on one press release: 
I knew that each press release included a date and also an address of a location the mayor would be visitin. Using the web scraper, I determined what HTML code was related to each element. Each date was part of a title, denoted by 'div',{'class': 'cell medium-18 post-title'}. Each address was inside a paragraph, denoted by 'p'. I successfully web scraped an individual press release before moving on. 

#### Build a dataframe: 

I webscraped the URL XHR request and put all of that HTML code into a dataframe (including a column for each press release link). I was then able to filter for only links related to press releases that had the words "Public Schedule for" in their name. 

To scrape for titles and paragraphs in all of the links, I built a for loop. That for loop instructed Python to take a link (from the column 'this_link') from the dataframe (sched), request the link's cont
ent, and apply BeautifulSoup. Python would then go on to return any content from that one link tagged as 'p' (paragraph) or 'div',{'class': 'cell medium-18 post-title'} (title). All the paragraphs were entered into a column (named 'Paragraph') of a dataframe and all of the titles were entered into another column (named 'Titles'). Some press releases has multiple paragraphs and each of those paragraphs needed the same title. To do this, I multiplied the title returned for a press release by the number of paragraphs (using the len function). 

The result was a dataframe with paragraphs and titles for each press release, all of which were then concatonated into one dataframe. 

#### About the data: 
This process resulted in 2,036 records of public appearances made by the mayor between October 5, 2016 and December 16, 2019. In the "Visual Summary" post, I've included charts that highlight a few simple themes about these appearances (spoiler alert: many of them occur at City Hall!) 

![example-chart]({{ site.url }}{{ site.baseurl }}/assets/images/MUSA620_sn.PNG)

#### Geocoding: 
Process to geocode
