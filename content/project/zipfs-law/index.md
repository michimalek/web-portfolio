---
title: Zipf's Law applied to city population in Europe
summary: Scraped city population data from DBPedia and statistically compared to Zipf's Law
tags:
- Analysis
date: "2021-12-18T00:00:00Z"

# Optional external URL for project (replaces project detail page).
external_link: ""

image:
  caption: Polands city populations compared to Zipf's distribution
  focal_point: Smart

links:
- icon: github
  icon_pack: fab
  name: GitHub
  url: https://github.com/michimalek/zipfs-law-analysis
url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

# Script to compare Zipf's Law to country population

### Description

This Script's origin is based on an university project concerning Central Place Theory.
The purpose is to scrap population data from [DBpedia](https://www.dbpedia.org/) and to compare those to the by Zipf's Law defined Distribution.
DBpedia is a tool to query trough available Wikipedia data with the use of their query language SPARql.
If you wanna learn more about Zipf's Law feel free to read trough [here](https://en.wikipedia.org/wiki/Zipf%27s_law).

To compare the Zipf's distribution to the population frequency distribution of the cities of each country, we used two probability distribution comparison tools namely [Hellinger Distance](https://en.wikipedia.org/wiki/Hellinger_distance) and [Kullback-Leibler Divergence](https://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence). Those indicate how similar two distributions are from each other.
When the script is run it prints out some indication of what is going on and at the end prints the results of Hellinger Distance and KL Divergence. The script also creates a logarithmic coordinate system to visually compare the two distributions.

Short summary of how to understand the resulting values:
- **Hellinger Distance** describes the degree of similarity between two different probability distributions. It is calculated as a scale between 0 and 1, where 0 being that the two distribution are identical to each other and 1 that
they are the furthest apart from each other.
- **Kullback-Leibler Divergence** focuses on information loss
between two distributions. This is indicated by first mapping the real data to
the zipf data and afterwards mapping the zipf data to the real data and comparing both results with each other. If the results are close to each other, there is
almost no information loss and therefore no similarity between the distributions
and contrarily if the results are far away from each other there is significant
information loss and therefore the distributions are not similar. 

### Structure

The script consists of three .py files: 
- *query_graphql.py* prepares the queries and scraps the population data from DBpedia 
- *zipfs_script.py* prepares the DataFrames and does the statistical calculations to compare both distributions by Hellinger Distance and Kullbeck Divergence.
- *pipeline.py* combines all steps into one pipeline. This script should be run.

So far the script only receives data from two european countries Poland and Netherlands. Maybe I will be able to add more countries in the future, otherwise an experienced programmer should be able to expand on the code I wrote.