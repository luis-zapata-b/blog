---
title: "Using Python, SerpAPI, and GPT to Build a Smart Web Search Analyzer"
author: "Luis Jose Zapata Bobadilla"
date: "2025-03-12"
slug: "openai-gpt-web-search-analyzer"
categories: Machine Learning
tags:
- OpenAI
- Machine_Learning
subtitle: "Using Open AI GPT to build a smart web search analyzer"
summary: "In this blog post, we provide an accessible introduction to using APIs like Open Ai and SerpAPI to build a smart web search analyzer. We will walk you through the process of setting up your environment, making API calls, and analyzing the results using Python."
authors: []
lastmod: ''
featured: true
image:
  caption: RD
  focal_point: ''
  preview_only: false
projects: []
---





# Introduction

In this blog post, I'll walk through how to use modern tools like Python, SerpAPI, and OpenAI's GPT models to build a modular search pipeline. The idea is to scrape Google Search results programmatically, analyze them using LLMs, and extract structured insights.

## What Are APIs, and Why Are We Using Them?

APIs (Application Programming Interfaces) are like bridges that allow one software to talk to another in a standardized way. Instead of building a search engine or a language model from scratch, developers can connect to existing services using APIs to request data, process information, or trigger tasks.

In this project, we rely on two APIs:

-   **SerpAPI**: This is a powerful tool that lets us programmatically fetch Google search results. Instead of scraping raw HTML and fighting with unpredictable webpage structures, SerpAPI gives us clean, structured JSON data for any Google query --- including titles, URLs, and summaries.
-   **OpenAI API**: This allows us to access large language models (like GPT-4o) via code. By sending a structured prompt and some example text to OpenAI's API, we receive intelligent summaries, classifications, or decisions in return --- perfect for analyzing search results at scale.

Together, these APIs let us build a small but powerful pipeline: search → filter → analyze --- all from Python.

To keep things simple and general, our example will revolve around analyzing search results related to **shoes**, rather than any specialized domain, but this project can easily be adapted to any other complex topic.

We'll break the process into four key parts:

1.  Fetching Google results using SerpAPI
2.  Cleaning and organizing the raw data
3.  Using GPT to extract structured insight from results
4.  Putting everything together in one function

## Step 1: Fetch Google Results Using SerpAPI

We'll start by querying SerpAPI. **SerpAPI** is a commercial API that allows developers to access real-time, structured Google search results without the hassle of traditional web scraping. In this blog, SerpAPI is used to automate the collection of search result data for a given keyword or product --- for example, "shoes with waterproof soles" or "trail running sneakers." Instead of manually performing searches and copying links, we send queries through SerpAPI and receive a JSON response containing the search titles, URLs, summaries, and even metadata like the publication date. This structured output is the foundation of our analysis pipeline, feeding directly into the next steps where we clean the data and evaluate relevance using language models.

First, we'll need a [SerpAPI API key](https://serpapi.com/).


``` python
import requests

def fetch_google_results(query, api_key, start=0, num=10):
    params = {
        "q": query,
        "location": "Los Angeles, California, United States",
        "start": start,
        "num": num,
        "hl": "en",
        "gl": "us",
        "engine": "google",
        "api_key": api_key
    }

    response = requests.get("https://serpapi.com/search", params=params)
    results = response.json().get("organic_results", [])
    return results
```

Example:


``` python
import pandas as pd 
serpapi_key = serapi_code
results = fetch_google_results("best running shoes 2024", serpapi_key)
print(pd.DataFrame(results).head())
```

```
##    position  ... rich_snippet
## 0         1  ...          NaN
## 1         2  ...          NaN
## 2         3  ...          NaN
## 3         4  ...          NaN
## 4         5  ...          NaN
## 
## [5 rows x 13 columns]
```

Keep in mind that SerpAPI offers 100 free requests per month. If your project requires more extensive usage, you'll need to upgrade to a paid plan. Additionally, SerpAPI supports other search engines (like Bing, DuckDuckGo, YouTube, and more), so you can adapt the same API logic to different platforms if needed.

## Step 2: Clean and Organize the Raw Data

Once we have the raw search results, we want to extract important fields and handle possible issues like missing data.


``` python
import pandas as pd
import datetime

def clean_results(raw_results):
    df = pd.DataFrame(raw_results)
    df = df[["position", "title", "link", "snippet"]].rename(
        columns={
            "position": "Rank",
            "title": "Title",
            "link": "URL",
            "snippet": "Summary"
        }
    )
    df["Scrape Date"] = datetime.date.today().strftime("%Y-%m-%d")
    return df
```

Example:


``` python
df_cleaned = clean_results(results)
df_cleaned.head()
```

```
##    Rank  ... Scrape Date
## 0     1  ...  2025-04-12
## 1     2  ...  2025-04-12
## 2     3  ...  2025-04-12
## 3     4  ...  2025-04-12
## 4     5  ...  2025-04-12
## 
## [5 rows x 5 columns]
```

## Step 3: Use GPT to Analyze the Results

**OpenAI's API** provides access to advanced language models like GPT-4, which can process and understand natural language. In this project, we use the **Chat Completion API** to enhance our search pipeline by analyzing each result retrieved from Google. For every link found, we prompt GPT to generate a **brief summary** of the content and assign a **probability score** that estimates how likely the link is to contain **useful shopping-related information** --- such as detailed product reviews, buying guides, or comparisons. This allows us to automatically prioritize the most informative links without manual filtering, making it easier to identify high-value content in large batches of search results.


``` python
from openai import OpenAI
import json
import time

client = OpenAI(api_key=openai_code)

def query_openai(df, keyword):
    json_data = df[["Rank", "Title", "URL", "Summary"]].to_dict(orient="records")
    prompt = f""" You are an AI assistant helping to analyze search engine results for consumer products. Analyze the following JSON search results from Google. For each result, please:
      1. Provide a short summary (max 150 characters) of the result.
      2. Estimate the probability (from 0 to 1) that the result contains useful information such as reviews, comparisons, product specs, or guides relevant to the keyword '{keyword}'.
      Return a JSON list under the key "results" with these fields:
      - Rank
      - URL
      - Probability
      - GPT_Summary
      
    Ensure that the number of output rows matches the number of input rows. If any row has no relevant information, still return it with a low Probability.
    ####
    
    Data:
    {json.dumps(json_data, indent=2)}
    ####
    """
    response = client.chat.completions.create(
        model="gpt-4o",
        messages=[
            {"role": "system", "content": "You are an AI summarizer and classifier of search engine results."},
            {"role": "user", "content": prompt}
        ],
        response_format={
            "type": "json_schema",
            "json_schema": {
                "name": "SearchEvaluation",
                "schema": {
                    "type": "object",
                    "properties": {
                        "Rank": {"type": "integer"},
                        "URL": {"type": "string"},
                        "Probability": {"type": "number"},
                        "GPT_Summary": {"type": "string"}
                    },
                    "required": [
                        "Rank",
                        "URL",
                        "Probability",
                        "GPT_Summary"
                    ]
                }
            }
        }
    )
    
    return json.loads(response.choices[0].message.content)["results"]
```

We use the response_format option to ensure the output is returned as a structured JSON object, making parsing and downstream processing much easier. Be aware that the OpenAI API has usage quotas and token limits that depend on your subscription tier and the model in use. Occasionally, the API may experience outages or degraded performance --- always check OpenAI's status page or the official documentation if things go wrong. For this project, we use the gpt-4o model, which offers faster responses and lower cost per token. Keep in mind that token limits and output behavior can vary across different models and versions.

## Step 4: Full Pipeline Example

Now let's combine everything into one pipeline and try it out:


``` python
query = "best waterproof trail running shoes"
raw = fetch_google_results(query, serpapi_key)
df = clean_results(raw)

response = query_openai(df, keyword="trail running shoes")
print(pd.DataFrame(response).head())
```

```
##    Rank  ...                                        GPT_Summary
## 0     1  ...       Guide on top waterproof trail running shoes.
## 1     2  ...  Listing of waterproof trail running shoes at REI.
## 2     3  ...  Reddit discussion on waterproof trail running ...
## 3     4  ...  Review of best waterproof trail running shoes ...
## 4     5  ...  Tested reviews of top trail running shoes for ...
## 
## [5 rows x 4 columns]
```

``` python
if response:
    df_scores = pd.DataFrame(response)
    final_df = pd.merge(df, df_scores, on=["Rank", "URL"],how="inner")
    print(final_df[["Rank", "Title", "Probability","GPT_Summary"]].head())
else:
    print("GPT analysis failed.")
```

```
##    Rank  ...                                        GPT_Summary
## 0     1  ...       Guide on top waterproof trail running shoes.
## 1     2  ...  Listing of waterproof trail running shoes at REI.
## 2     3  ...  Reddit discussion on waterproof trail running ...
## 3     4  ...  Review of best waterproof trail running shoes ...
## 4     5  ...  Tested reviews of top trail running shoes for ...
## 
## [5 rows x 4 columns]
```

Im only going to use R for the final table, but you can use any other language to do it.

``` r
knitr::kable(
  py$final_df[, c("Rank", "URL","Title", "Probability", "GPT_Summary")],
  format = "html",
  caption = "GPT Analysis of Search Results"
)
```

<table>
<caption><span id="tab:unnamed-chunk-7"></span>Table 1: GPT Analysis of Search Results</caption>
 <thead>
  <tr>
   <th style="text-align:right;"> Rank </th>
   <th style="text-align:left;"> URL </th>
   <th style="text-align:left;"> Title </th>
   <th style="text-align:right;"> Probability </th>
   <th style="text-align:left;"> GPT_Summary </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> https://runrepeat.com/guides/best-trail-waterproof-running-shoes </td>
   <td style="text-align:left;"> 7 Best Waterproof Trail Running Shoes in 2025 </td>
   <td style="text-align:right;"> 0.95 </td>
   <td style="text-align:left;"> Guide on top waterproof trail running shoes. </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 2 </td>
   <td style="text-align:left;"> https://www.rei.com/c/trail-running-shoes/f/f-waterproof </td>
   <td style="text-align:left;"> Waterproof Trail-Running Shoes | REI Co-op </td>
   <td style="text-align:right;"> 0.90 </td>
   <td style="text-align:left;"> Listing of waterproof trail running shoes at REI. </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 3 </td>
   <td style="text-align:left;"> https://www.reddit.com/r/trailrunning/comments/1adsza0/need_some_recommendations_for_waterproof_running/ </td>
   <td style="text-align:left;"> Need some recommendations for waterproof running ... </td>
   <td style="text-align:right;"> 0.75 </td>
   <td style="text-align:left;"> Reddit discussion on waterproof trail running shoe recommendations. </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> https://www.livefortheoutdoors.com/trail-running/shoes/best-waterproof-trail-running-shoes/ </td>
   <td style="text-align:left;"> Best waterproof trail running shoes for 2025 | Tested and ... </td>
   <td style="text-align:right;"> 0.95 </td>
   <td style="text-align:left;"> Review of best waterproof trail running shoes for 2025. </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 5 </td>
   <td style="text-align:left;"> https://www.outdoorgearlab.com/topics/shoes-and-boots/best-trail-running-shoes-womens </td>
   <td style="text-align:left;"> The 9 Best Trail Running Shoes for Women | Tested </td>
   <td style="text-align:right;"> 0.85 </td>
   <td style="text-align:left;"> Tested reviews of top trail running shoes for women. </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 6 </td>
   <td style="text-align:left;"> https://www.brooksrunning.com/en_us/mens/shoes/trail-shoes/?srsltid=AfmBOoow-beP7iwwQgxtcrDarJJkMzB4EGLSRJQnxacCDaeJa8C2rU-a </td>
   <td style="text-align:left;"> Men's Trail Running Shoes </td>
   <td style="text-align:right;"> 0.80 </td>
   <td style="text-align:left;"> Brooks' men's trail shoes with GORE-TEX options. </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 7 </td>
   <td style="text-align:left;"> https://www.rei.com/learn/expert-advice/should-you-get-waterproof-trail-running-shoes.html </td>
   <td style="text-align:left;"> Should I Get Waterproof Trail-Running Shoes </td>
   <td style="text-align:right;"> 0.90 </td>
   <td style="text-align:left;"> Guide on deciding to purchase waterproof trail running shoes. </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> https://www.trailandkale.com/roundups/best-trail-running-shoes-buyers-guide/ </td>
   <td style="text-align:left;"> The Best Trail Running Shoes In 2025 [Tried And Tested] </td>
   <td style="text-align:right;"> 0.95 </td>
   <td style="text-align:left;"> Comprehensive guide to best trail running shoes. </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 9 </td>
   <td style="text-align:left;"> https://singletrackworld.com/forum/off-topic/waterproof-trail-running-shoes-yay-or-nay/ </td>
   <td style="text-align:left;"> Waterproof trail running shoes – Yay or nay? – Chat Forum </td>
   <td style="text-align:right;"> 0.70 </td>
   <td style="text-align:left;"> User opinions on waterproof trail shoes in forum. </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> https://lifehacker.com/health/waterproof-running-shoes-are-game-changer </td>
   <td style="text-align:left;"> I'm a Runner, and These Water-Resistant Running Shoes ... </td>
   <td style="text-align:right;"> 0.80 </td>
   <td style="text-align:left;"> Review of water-resistant running shoes for runners. </td>
  </tr>
</tbody>
</table>

# Conclusion

In this post, we built a modular and extensible web search analyzer using Python, SerpAPI, and OpenAI's GPT. We demonstrated how to automatically retrieve search results, clean and structure the data, and use a large language model to generate useful summaries and rank the most relevant links based on probabilistic reasoning.

This framework is highly adaptable:

-   You can modify the **SerpAPI parameters** to target different locations, languages, or result depths.
-   You can enhance the **GPT prompt** to fit specific domains --- whether it's shopping, education, or scientific research.
-   The structured outputs can be stored in CSVs, Excel files, or databases for further visualization or batch processing.
-   You can even integrate this pipeline into larger workflows, such as product monitoring, competitive analysis, or content recommendation engines.

By abstracting complexity through APIs and combining them with thoughtful logic in Python, we enable powerful automation with very little code. This project is a good example of how language models and APIs can work together to extract meaning and prioritize knowledge at scale --- without writing a single web scraper.

Happy exploring!
