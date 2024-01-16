---
layout: single
title: "Is it true that long-term injuries comes from prior minior injuries?"
header:
categories:
  - Projects
author_profile: false
---
# A lense from a statistical point of view. Can we create a ML model to predicit the outcomes?

# Introduction

After watching sports for many years, I noticed non-contact injuries, especially in the NBA. I went on to examine it. Randomly, I clicked on a video where a popular YouTuber states, 'Look at KD; he had an ACL injury, and before that, he had a calf strain.' Is this really true? The YouTube channel mentioned is MPJPerformance, and the video link is [here!](https://www.youtube.com/watch?v=HnPjGpcTU8A&t=47s.)

# Retriving and Cleaning the data

## Firstly getting the data 

Luckly for me the raw data is already avaliable, big thanks to JaseZiv for the github repositry [click here!](https://github.com/JaseZiv/NBA_data/tree/main)

## How is the data currently structured? 

the file named "nba_injuries" has webcrawled various NBA sources and the origian files follow a JSON schema as follows:

- **Date:** 1947-08-05
- **Team:** Bombers (BAA)
- **Acquired:** 
- **Relinquished:** Jack Underman
- **Notes:** fractured legs (in auto accident) (out indefinitely) (date approximate)

## Creating a database and cleaning up the data 

Before we can clean the data to remove duplicates and unnessary/missing inputs we first need to create a database scehema appropriate to our queries and data retrival goals. 
 
- Identify all injured playes easily 
- Idenify length of injury easily
- Identify if this play has prior/future injury
- Proximity of next injury/prior injury

Based on these retrival goals we can take a view from a statisatical POV if "long term injuries are srouced from short term injuries". Where we can explore...


As pointed out by Chip Huyen in Chapter two of "Designing Machine Learning Systems" states the importance of Data Models "How you choose to represent data not only affects the way your systems are built, but also the problems your systems can solve". Using this chapter as a out Chip outlines "NoSQL" to follow a strict schema, therefore for time saving we will use a "Relational Database". 




# Let's start off by examing it from a statistics point of view?

building the story
