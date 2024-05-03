---
title: "Sports Stats Analysis in Python"
excerpt: "A fun personal project analyzing volleyball players' stats"
categories:
  - portfolio
tags:
  - data science
  - python

---
![volley-stats](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS27An_e6dBdQI1LuwWrlgIgZZtFl5FBEtH_Ew-PuVWVw&s) 

## Volleyball players' stats analysis  
In this fun project, I scraped data from volleyservice.ru website for top players and compared their stats to see how my favorite player Zhang compares to other players as an outside hitter. 

## Data collection
- Query: I used the `BeautifulSoup` library to query the player stats website to get their player stats. 
- Translate: Since the data are in Russian, I then used Google Translator api to translate them into English for further analysis
- Save: I saved the cleaned data for further analysis and visualization

## Data visualization
-  Prep: I transformed raw stats into each player's ranking to make different variables comparable in terms of each player's relative strengths/weaknesses
-  Radar chart: I used a radar chart to visualize my favorite player Zhang's performance in comparison to others


[Code](https://github.com/chaix026/volley-zjy){: .btn .btn--success .btn--large}

