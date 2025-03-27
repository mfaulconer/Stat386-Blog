---
layout: post
title:  "Anything is Possible! Scraping NBA Combine Data Like a MVP"
description: Using public data on the NBA official website, I've created a championship data set that can be used to find which performance metrics determine the top draft picks.
display_image: false
---

## And with the first pick in the 2025 NBA Draft...
Every year, 60 players are drafted to the NBA from colleges, G-League teams, and overseas. However, there can only 560 active players in the NBA at any time. The league is not retiring and finding 60 new players each year, and with such limited roster space, choosing the best prospects for your team is one of the hardest challenges in basketball.

The question every GM is asking, "Who do I draft to build the best team?" Unfortunately, I don't have the answer. With bust picks and underrated legends being drafted each year, it appears the league hasn't figured it out either. 

I want to dive into the mind of an NBA General Manager and see how they act to build the best team possible, so how DO teams determine their draft picks? I have set out to answer that question using data from the NBA Combine Strength and Agility testing, which can be found on the <a href="https://www.nba.com/stats/draft/combine-strength-agility" target="_blank">NBA Website</a>.

Using the performance metrics from the NBA combine, I hope to determine which metrics differentiate first and second round picks, as well as players who go undrafted. Which metrics stand out as the deciders of the next best players?

## Don't Foul Out: Ethical Webscraping
Before moving forward with any project, it is important to understand where your data is coming from, and if you're even "allowed" to collect it. Some companies have very specific rules about what data you can and cannot take from their websites and resources. 

A good first place to look is the Terms of Use. When I looked at the NBA.com Terms of Use, I found a section specifically about NBA Statistics! You can read this section of the terms of use <a href="https://www.nba.com/termsofuse#nba-statistics" target="_blank">here</a>. In summary, NBA statistics can be used as long as it is VERY CLEAR that your data came from the NBA, the data is used for non-commerical purposes, and that you aren't using the data for gambling activity. I seem to fit in all those categories!

Another place to double check for scraping is on a websites 'robots.txt' file. Every website has a robots.txt file that tells web crawlers what parts of the website are off-limits. I checked the NBA's robots.txt, the draft statistics path is allowed to be scraped by User-Agents GPTBot and Google-Extended. Great! Everything is all set!

## Time to Jam (Scrape)
To replicate my epic webscraping, you will first need to download the correct packages. The NBA website has their Combine and Draft History data separated by year, and you have to go in and click the pages you want and adjust the filters to see all the data in one page. This caused a real pain for my simple HTML requests. After much consultation with a good friend named Generative AI, I learned that I needed to use a package called Selenium.

Selenium helps scrape dynamic content that is often displayed by JavaScript. The nature of the tables I was extracting was in fact dynamic, so Selenium helped me to grab all that I needed! Here are all the packages I used.
![Packages](https://mfaulconer.github.io/Stat386-Blog/assets/img/packages.png)

Once I had Selenium to help me set up my drivers for the JavaScript based website, I could use the same HTML skills that we practiced in class. It wasn't too different at all! I collected data from 2021-2024 for both the NBA Combine tests, and the NBA Draft History. I grabbed all the data from each table and saved it as a dataframe. 
![Webdriver](https://mfaulconer.github.io/Stat386-Blog/assets/img/webdriver.png)


Once I had everything I needed, I combined all the frames into my one big frame! I did this by using concat to stack the similar datasets (NBA Combine, NBA Draft). Once I had 2021-2024 NBA Combine and 2021-2024 NBA Draft in their two seperate dataframes, I made sure the variable types were what I needed, and merged the frames based on "Player Name" and "Year". That's it!

## Final Dataset
 My final dataset can be found on my github <a href="https://github.com/mfaulconer/Stat386ProjCode" target="_blank">here</a>!

The final dataset I am working with includes all combine participants from 2021-2024, regardless of whether or not they were drafted. I used a left join draft results to those players who were selected in the NBA Draft.

There are a total of 237 observations and 13 variables in the dataset.

| Variables | Type |
|-----------|------|
| Player | object | 
| POS | object | 
| Lane Agility Time (seconds) | float64 |
| Shuttle Run (seconds) | float64 |
| Three Quarter Sprint (seconds) | float64 |
| Standing Vertical Leap (inches) | float64 |
| Max Vertical Leap (inches) float64 |
| Year | int64 |
| Team | object |
| Affiliation | object |
| RoundNumber | float64 |
| RoundPick | float64 |
| OverallPick | float64 |

In various observations, there are some missing values. Not everyone opts in to participate in every strength test, but I do not want to remove those observations from the dataset, as their other results are relevant to my analysis. These missing at random values are currently left as N/A. For variables that came from the draft history, the objects (Team, Affiliation) were left as N/A, and the numeric variables (RoundNumber, RoundPick, OverallPick) were filled in with "0".

## Quick EDA
To start exploring the data, I wanted to look at boxplots of the five NBA Strength Combine testing seperated by draft round pick. "0" is undrafted, "1" is first round, and "2" is second round!

<iframe src="https://mfaulconer.github.io/Stat386-Blog/assets/plots/LaneAgility.html" width="600" height="400"></iframe>

<iframe src="https://mfaulconer.github.io/Stat386-Blog/assets/plots/ShuttleRun.html" width="600" height="400"></iframe>

<iframe src="https://mfaulconer.github.io/Stat386-Blog/assets/plots/3QSprint.html" width="600" height="400"></iframe>

<iframe src="https://mfaulconer.github.io/Stat386-Blog/assets/plots/ApproachJump.html" width="600" height="400"></iframe>

<iframe src="https://mfaulconer.github.io/Stat386-Blog/assets/plots/StandJump.html" width="600" height="400"></iframe>

Each of the graphs shows that there is not an obvious difference in performance amongst the first and second round picks or those who were undrafted. Lane Agility and Shuttle Run tests actually do see a slight higher median than either draft groups. The second round picks are slightly higher in the Three Quarter Sprint, and both the first and second round picks are higher than undrafted players in the jump categories, but practically the same.

## Conclusion
This brief EDA does bring some interesting questions. If many of the performances between drafted and undrafted players are similar, then they may not have any impact on draft decisions at all. If you have two identical performers, and one player is drafted while the other isn't, there are likely other confounding variables that GMs are using to determine which players will be added to their team each year.

## THANK YOU NBA FOR LETTING ME USE YOUR DATA!
Like in the Terms of Use, HERE IS A VERY OBVIOUS AND CLEAR INDICATOR that I could not have this data without the NBA! Thank you!
