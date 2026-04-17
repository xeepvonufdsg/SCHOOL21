# City life

## Taxi Routes and Neighborhoods

*Summary:* This project is an introduction to geospatial analytics: GeoPandas, clustering, making maps.

💡 [Tap here](https://new.oprosso.net/p/4cb31ec3f47a4596bc758ea1861fb624) **to leave your feedback on the project**. It's anonymous and will help our team make your educational experience better. We recommend completing the survey immediately after the project.

## Contents

1. [Chapter I](#chapter-i) \
   1.1. [Preamble](#preamble)
2. [Chapter II](#chapter-ii) \
   2.1. [Introduction](#introduction)
3. [Chapter III](#chapter-iii) \
   3.1. [Rules of project](#rules-of-project)
4. [Chapter IV](#chapter-iv) \
   4.1. [Instructions](#instructions)
5. [Chapter V](#chapter-v) \
   5.1. [Mandatory part](#mandatory-part)
6. [Chapter VI](#chapter-vi) \
   6.1. [Bonus part](#bonus-part)

## Chapter I

How to learn at “School 21”:

- Here, you’ll find a unique learning experience with a lot of freedom. You’re given a task and left to find your own way to solve it, using whatever resources work best for you — whether that’s the Internet or AI tools like GigaChat. Just be mindful of information quality: verify, think critically, analyze, and compare.
- Peer-to-peer (P2P) learning is the exchange of knowledge and experience with peers, where everyone acts as both mentor and student. This approach allows you to gain a deeper understanding of the material by learning from one another.
- Feel free to ask for help: around you are peers who are also navigating this path for the first time. Share your own experience and ideas with others. Join Rocket.Chat to stay updated with the latest community announcements.
- Your learning is meaningless if you just copy someone else’s solutions. When receiving help from others, always make sure you fully understand the “why”, “how”, and “purpose” behind the solution. Don’t be afraid to make mistakes.
- Does the task seem impossible? Take a break, get some fresh air and clear your mind — this has helped many people. Maybe after that, the solution will come to you naturally.
- The learning process is just as important as the result. It’s not just about completing the task — it’s about understanding HOW to solve it.

### Preamble

Maps are important to people. They help us understand what is going on and make decisions. We can see a landscape, we can see different items or objects on it and how they relate to each other in terms of distance or some other term.

Maps have been used extensively in combat. It is hard to find anything more useful than them for creating strategy and tactics. When we talk about a space or area we need to navigate, drawing a map on a napkin is almost a reflexive action. It is hard for us to visualize to another person what we are seeing in our imagination without a piece of paper and a pencil.

![0](assets/img_0276.png)

The important thing is that the same objects can be mapped in many different ways.

Several decades ago, the way maps exist in our world and the way we use them changed. We do not use paper maps as much as we used to. Sometimes, to get from point A to point B in the city, you had to have several maps, just in case. They might have had different qualities for different areas and different years of production.

Today, maps are in our smartphones. We can easily interact with them. We can search them. Likewise, we can calculate the distance between two points. We can get the information about the time needed to reach the destination point by different means of transportation. Millions of people who lived in the past would envy us.

But maps are not necessarily equal to geography. People can map literally anything: the sky, DNA, network topology, business environment, brain, galaxies, buildings, engineering systems.

## Chapter II

### Introduction

Geospatial analytics is a field that appears at the intersection of data analysis and data visualization. It is widely used in telecommunications, logistics, transportation, the oil industry, agricultural companies, and government agencies that manage territories. Any time you need to gain insights from data that has coordinates in space, geospatial analytics is a must.

The most common tasks vary, but almost all of them involve maps. For example, the list of responsibilities from a job description:

- Analyze spatial data using mapping software.
- Discover patterns and trends by spatially mapping data.
- Design digital maps using geographic data and other data sources.
- Create "shapefiles" to merge topographic data with external data by overlaying external data over a topographic map.
- Create maps that show the spatial distribution of various types of data, such as crime statistics and hospital locations.
- Develop mapping applications and tools.
- Convert physical maps into a digital form for computer use.
- Perform data munging and cleaning to convert data into the desired form.
- Create reports on geographic data using data visualizations.
- Maintain a digital library of geographic maps in various file types.

So there are only a few specialized algorithms for geographic data, and most of them involve visualizing data on maps.

## Chapter III

### Rules of project

The goal of this project is to give you a first approach to Geospatial Analytics. You will try different tasks to analyze taxi rides. The efficiency of any taxi company depends on it.

## Chapter IV

### Instructions.

- This project will be evaluated by humans only. You are free to organize and name your files as you wish.
- Here and throughout, we use Python 3 as the only correct version of Python.
- The standard does not apply to this project. However, you are asked to be clear and structured in the design of your source code.
- Place the datasets in the **data** subfolder.

## Chapter V

### Mandatory part

#### a. Task

In this project, you will try to gain some valuable insights into the behavior of customers and taxi drivers. Maybe it will help a taxi company to optimize its business.

Here are the tasks you have to do:

1. Find out and visualize on a map the most popular areas where people ordered taxis and where they went.
2. Find and visualize the most popular routes in different time intervals.
3. find locations of city infrastructure in the dataset and visualize how customers got to one of them on an animated map.
4. Visualize a taxi driver's day and how much money he earned using an animated map.
5. Visualize a day in the city (working day and weekend day) using an animated map.

#### b. Dataset

You will work with another part of the same dataset of taxi rides. It contains data from 2014-09-05 to 2019-06-23. This time it contains data about taxi drivers, coordinates of pick-up and drop-off locations, timestamps, and fares.

You will also find the files needed to visualize a map of the city.

> **Note:** You can find the dataset on the project page.

#### c. Implementation

You can work in [Google Colab](https://colab.research.google.com/) or Jupyter Notebooks on your computer. You can use any library or any framework that you find convenient.

**Most popular areas**

1. Perform a clustering analysis of pick-up and drop-off locations based on their coordinates. The clusters may be different for each of the categories (pick-ups and drop-offs).
2. Draw the boundaries and centroids of the clusters on a map. You will have two maps.
3. Use a color scale to indicate which clusters (i.e., areas) have the most pick-ups and drop-offs.

**Most Popular Routes**

1. Perform a clustering analysis of taxi trips based on the coordinates of the pick-up and drop-off locations.
2. Draw the centroids of the top 5 popular clusters (routes).
3. Draw routes between the centroids of a cluster — not a direct line from point A to point B, but a path that takes into account the city streets.

**City infrastructure**

1. Find locations of city infrastructure (airports, stadiums, parks, universities) using the data and create your own algorithm to find them. Find at least 6 such locations.
2. Find the rush hour for each of the locations — timestamp when the location had the largest number of departures and save the information in this file: "rush\_hours\_empty.csv" (in the attachment).
3. Visualize one day of any of the locations, including that rush hour, showing how people from different places came to the location and then left it on an animated map.
4. When the trip ends, it should disappear from the map. In other words, it should look like neurons firing in the brain.
5. The map should show the time.

**One day of a taxi driver**

1. For the taxi driver with ID (2ea4ad2950f3bbdfdcfa7adb48e0dcee49d8a714b7024342f0302eeb9e891dfd55a6f35bb7bc7af06398fb4f55583e1659cb11b432848296bfd2b7d3084e7de1), visualize his trips during the day (2019-05-31). View the current amount of money earned.
2. When the ride ends, it should NOT disappear from the animated map.
3. Every time the ride ends, the money counter should be updated.
4. The map should show the time.

**One day of the city**

1. Visualize all rides in the city during the day (2019-05-16) on an animated map.
2. When the ride ends, it should disappear from the map. In other words, it should look like neurons firing in the brain.
3. The map should show the time.

#### d. Submission

Your repository should contain one or more notebooks with your solutions and visualizations.

It should also contain the rush-hour file for the city infrastructure objects. It will be compared with our file. We will compute the intersection of your set with our set of locations and rush hours. The intersection should have at least 3 elements. The columns that will be considered are: longitude, latitude, num\_of\_rides, trip end timestamp.

## Chapter VI

### Bonus part

- Design your visualization as a website with interactive elements (for example, where you can select a date or driver ID, select a location, etc.).
- Try to get a better result with the intersection — at least 5 elements.