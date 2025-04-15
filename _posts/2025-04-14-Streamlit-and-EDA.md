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

<iframe src="https://mfaulconer.github.io/Stat386-Blog/assets/plots/Lane_Agility_Comparison" width="600" height="400"></iframe>

<iframe src="https://mfaulconer.github.io/Stat386-Blog/assets/plots/Shuttle_Run_Comparison" width="600" height="400"></iframe>

<iframe src="https://mfaulconer.github.io/Stat386-Blog/assets/plots/Three_Q_Comparison" width="600" height="400"></iframe>

<iframe src="https://mfaulconer.github.io/Stat386-Blog/assets/plots/Standing_Bar_Comparison" width="600" height="400"></iframe>

<iframe src="https://mfaulconer.github.io/Stat386-Blog/assets/plots/Approach_Bar_Comparison" width="600" height="400"></iframe>

| Strength and Agility Assessment | Average Difference | Significant? |
|-----------|------| 
| Lane Agility Time (seconds) | -0.144 seconds | Yes |
| Shuttle Run (seconds) | -0.0585 seconds | No |
| Three Quarter Sprint (seconds) | -0.008 | No |
| Standing Vertical Leap (inches) | 0.620 | No |
| Max Vertical Leap (inches) | 0.804 | No |
