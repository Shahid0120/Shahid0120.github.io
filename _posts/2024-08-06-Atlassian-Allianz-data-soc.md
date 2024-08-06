---
layout: single
classes: wide
title: "Atlassian x Alliance Datathons! Lesson I've Learnt"
header:
categories:
  - Datathons
author_profile: True
---
Recently I've had the opportunity to to participate compete in the UNSW Atlassian Allianz Data Competition at their respective headquarters! This 3-day event required my team to classify fraudulent customers from insurance data collected by Allianz customers.

Luckily, we made it to the final round, comprising 4 teams, and ended up coming 3rd out of 75 teams! here's the (Project Link)[https://github.com/Shahid0120/atlassian-allianz-data-competition]

The objective of the task was to classify fraudulent insurance cases based on consumer history, profile, demographics, and geographics. This was my first time competing in an event like this, and although I was a little nervous, it was one of the best experiences I've had. Working together in a team to solve data problems, I can't wait until I get a job in the field! Anyways, I just wanted to share my insights and lessons learned from senior Allianz data scientists on our presentation and what I overall learned from the experience.

# 1. Interpretability is KING

"I've been recently looking at a lot of Kaggle competition winners and their solutions to problems. Additionally, I recently read a paper on the[M5 forcasting competition](https://www.sciencedirect.com/science/article/pii/S0169207021001874). What I found is that although traditional models like ARIMA were used, the majority used LightGBM and Neural Networks. The problem is that only one solution in the top 20 used classical statistics, so just by reading these Kaggle competitions, I was given false hope about learning these complex models, which are not really interpretable.

In the industry, you will always have to present your findings to a non-technical manager or employee. Thus, being able to accurately explain your model in depth is required, and you can't really do it if you're ensembling multiple models."

# 2. Simplicity is always the way to go forward

We focused on using decision trees, including CatBoost and LightGBM, and the other team focused on these models as well. Interestingly, the winner ended up using Lasso regression. Funny enough, I was talking to the group prior to the presentation, and when I heard Lasso regression, I thought, 'Hmm... that's more aimed at feature selection.' But the important thing is that it's a simple model that you can easily explain to non-technical managers!

# 3. Industrial standard are important, don't just use a methods without researching academic papers on its effectiveness and con's!

The label set was unbalanced, representing more non-fraudulent cases than fraudulent cases, which makes sense. Of course, we had to address this issue; if we didn't, we wouldn't get meaningful results. From all the blog posts and general discussions, the most popular method is SMOTE-N, so we thought, 'Great, easy,' and we did it.

During our presentation, a key criticism was that 'SMOTE doesn't really work in reality; it's not used in the industry since you are making artificial data points. You should have used Weighted Oversampling.' Now, of course, if I or the team had read about the industrial performance of oversampling methods, we could have identified this!

# Conclusion

This was an invaluable experience. I can't express my gratitude enough for the opportunity to participate in such an event. If one day I get the opportunity to be a judge at this event when I'm a senior data scientist, I will welcome it with open arms.