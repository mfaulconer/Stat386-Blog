---
layout: post
title:  "Bigger, Better, Stronger, Power: Do NBA Combine Stats REALLY Have an Effect on Draft Order?"
description: After more EDA and statistical analysis, it is time to answer the question in my latest blog post, "Which metrics stand out as the deciders of the next best players?" And for any doubters, further exploration can be done on my dataset using my streamlit app!
display_image: false
---

## There's More to Basketball than Running and Jumping

While that may sound obvious to many, the conclusion opens the door to a whole new question in sports analytics, what really does matter?

While I don't have that answer, I do have further evidence to support my claim. My inital question at hand can be summarized as "What are the differences between NBA draftees?". Each player who declares for the NBA draft AND is further invited by the NBA, has the opportunity to participate in the NBA Draft Combine. The Combine consists of skills assessments, scrimmages, interviews, and other measurements that teams can use to solidify their decisions of who to draft.

Each year, 78 players are invited to the combine, but only 60 can be drafted into the NBA. Knowing this, I was interested in finding out what aspects of the draft, if any, can change the fate of combine players. Looking at assessments from the Strength and Agility portion of the combine, I found that there is really no "stand-out" differences between performances of player who get drafted first round, second round, or not at all.

## Diving Deeper

Across all the years in my dataset, I found there to be little to no difference in the average performance of skill assessments between players who end up being drafted in first and second rounds, and not at all. To visualize this difference, I have plotted the average performance for each group across the four years in my dataset.

<div style="display: flex; justify-content: center;">
<iframe src="https://mfaulconer.github.io/Stat386-Blog/assets/plots/Lane_Agility_Comparison.html" width="600" height="400"></iframe>

<iframe src="https://mfaulconer.github.io/Stat386-Blog/assets/plots/Shuttle_Run_Comparison.html" width="600" height="400"></iframe>

<iframe src="https://mfaulconer.github.io/Stat386-Blog/assets/plots/Three_Q_Comparison.html" width="600" height="400"></iframe>

<iframe src="https://mfaulconer.github.io/Stat386-Blog/assets/plots/Standing_Bar_Comparison.html" width="600" height="400"></iframe>

<iframe src="https://mfaulconer.github.io/Stat386-Blog/assets/plots/Approach_Bar_Comparison.html" width="600" height="400"></iframe>
<div>

Across all four years and all three groups of draftees, there is no noticeable differences between the average performances. There is a small outlier for first round picks in 2021 jump tests, but that is the only difference. To further confirm this observation, I conducted a simple test to compare the means of players drafted in the first and second rounds. Across all four years, the only significant difference was found to be in the Lane Agility Test, where round one picks were an average of 0.144 seconds faster than round two picks. Each other test had no significant difference.

| Strength and Agility Assessment | Average Difference | Significant? |
|-----------|------| 
| Lane Agility Time (seconds) | -0.144 seconds | Yes |
| Shuttle Run (seconds) | -0.0585 seconds | No |
| Three Quarter Sprint (seconds) | -0.008 seconds | No |
| Standing Vertical Leap (inches) | 0.620 inches| No |
| Max Vertical Leap (inches) | 0.804 inches | No |

Note: For running tests (Lane Agility, Shuttle Run, and Three Quarter Sprint, a negative difference shows a faster, and therefore better, time)

## EDA DIY - Look at my App!

While I have provided some plots to visualize the data, I have also created an app using streamlit! 



## Wrapping Up

Like I said at the beginning, there really is more to basketball than running and jumping. If performances are the same amongst almost all combine participamts, NBA General Managers and front office teams must have different strategies for choosing their next star players. Whether that is college performances, wingspan, or private interviews, there is something missing in our analysis. If I had the opportunity to dive deeper into this question, I would love to include college in-game statistics, and create a more in-depth model that can calculate player efficiency. Hopefully, such a model would provide deeper insight into the draft decisions made across the league. 

If you are interested to explore the question deeper, feel free to use <a href="https://github.com/mfaulconer/Stat386ProjCode" target="_blank">my final dataset</a>, which can be found on my github!

Thank you again to the NBA for the public data that has made this project possible!
