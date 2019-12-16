---
title: "Purpose of this Project"
date: 2019-12-16
published: true
tags: [dataviz, folium]
excerpt: "Background on how this data is accessed now."
folium-loader:
  folium-chart-1: ["charts/foliumChart.html", "400"]
  folium-chart-2: ["charts/percent_no_internet.html", "400"]
custom-css-list:
  - "assets/css/leaflet.timedimension.control.min.css"
toc: true
toc_sticky: true
---

### Purpose
Jim Kenney is in his second term in office as mayor of Philadelphia. He was sworn in as mayor on January 4, 2016, and re-elected this year, for a running total of 1,423 days in office. In a professional capacity, where does Mayor Kenney spend his time? Where in the city does his work take him? Does his movement as mayor reflect the commitments made by his administration? 

In this project, I used web scraping to present information about where Mayor Kenney travels most often within the city. This project required complex web scraping, from a website that includes a significant interactive component. Location information from the Mayor’s schedule is published online daily in the City of Philadelphia online archive; the locations the Mayor plans to visit each day can be accessed by clicking on a link to that day’s schedule. 
My web scraping allowed me to analyze the over 2,000 locations included in the Mayor’s public schedules and determine what locations the Mayor visits most often, something that would be incredibly tedious and time consuming without the web scraping process. 

While the web scraping portion of my analysis was successful, building an interactive map to visualize the locations the Mayor visits regularly proved more challenging. 
