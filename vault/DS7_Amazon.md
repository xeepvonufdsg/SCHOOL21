# Amazon

## Customers Who Bought This Item Also Bought

*Summary: this project is an introduction to Apache Spark (Python API) and network and graph analysis.*

## Contents

1. [Chapter I](#chapter-i) \
   1.1. [Preamble](#preamble)
2. [Chapter II](#chapter-ii) \
   2.1. [Introduction](#introduction)
3. [Chapter III](#chapter-iii) \
   3.1. [Goals](#goals)
4. [Chapter IV](#chapter-iv) \
   4.1. [General instructions](#general-instructions)
5. [Chapter V](#chapter-v) \
   5.1. [Mandatory part](#mandatory-part)
6. [Chapter VI](#chapter-vi) \
   6.1. [Bonus part](#bonus-part)
7. [Chapter VI](#chapter-vi) \
   7.1. [Submission and peer-to-peer evaluation](#submission-and-peer-to-peer-evaluation)

## Chapter I

How to learn at “School 21”:

- Here, you’ll find a unique learning experience with a lot of freedom. You’re given a task and left to find your own way to solve it, using whatever resources work best for you — whether that’s the Internet or AI tools like GigaChat. Just be mindful of information quality: verify, think critically, analyze, and compare.
- Peer-to-peer (P2P) learning is the exchange of knowledge and experience with peers, where everyone acts as both mentor and student. This approach allows you to gain a deeper understanding of the material by learning from one another.
- Feel free to ask for help: around you are peers who are also navigating this path for the first time. Share your own experience and ideas with others. Join Rocket.Chat to stay updated with the latest community announcements.
- Your learning is meaningless if you just copy someone else’s solutions. When receiving help from others, always make sure you fully understand the “why”, “how”, and “purpose” behind the solution. Don’t be afraid to make mistakes.
- Does the task seem impossible? Take a break, get some fresh air and clear your mind — this has helped many people. Maybe after that, the solution will come to you naturally.
- The learning process is just as important as the result. It’s not just about completing the task — it’s about understanding HOW to solve it.

### Preamble

**Big data** is an umbrella term that encompasses data, algorithms, and technologies. Data should be large in terms of volume (GB, TB, PB, etc.). There should also be algorithms that extract knowledge from the data, as well as technologies that help store and process it.

Humans have been using data since ancient times. Most of the algorithms we use today were created in the 20th century. The reason so many companies want to use data and algorithms is because of the level of existing technology. These technologies have made the process of extracting value from data cheaper and simpler.

Before that, we operated under the vertical scaling paradigm. We needed increasingly productive computers. Ultimately, we would have needed a supercomputer. They are and were very expensive.

Then, we realized that we could combine commodity servers in a cluster to use for distributed storage and computing. This marked the beginning of the Big Data era. **Hadoop** is the most well-known ecosystem, including many tools that help work with big data. HDFS stands for Hadoop Distributed File System. YARN stands for Yet Another Resource Negotiator. HBase is a columnar database. MapReduce is a paradigm and algorithm for distributed processing.

There was a problem with using Hadoop MapReduce (Hadoop Streaming): it took too long because it had to read from and write to the disk many times during the process. Some people decided to create a new tool that would solve this problem by computing as much as possible in RAM. They called the tool Spark. Then, it was added to the Apache Foundation Accelerator. Since then, it has been known as **Apache Spark**.

Although it was a glitchy tool in the beginning, with jobs failing due to **out-of-memory errors (OOM)** and no one knowing how to solve the problem, it has become stable enough to be used in production mode by companies. Starting with version 2, it became the central element of big data infrastructure. You can use it for batch and real-time processing, as well as for data engineering and data science tasks. It has connectors to many popular tools and databases. Apache Spark is now the king of big data.

## Chapter II

### Introduction

A **graph** is a useful concept. It includes vertices and edges between them. A graph can be directed if you can go from A to B, but not from B to A. A graph can also be weighted if there is a "distance" between the vertices. Graphs can be used in geospatial analysis when roads are considered edges. They can also be used in social networks to find the most influential members or recommend a friend. Graphs can also be used in recommender systems to recommend items that are frequently bought together. Apache Spark actually uses a **DAG** (directed acyclic graph) to create a plan of computations and optimizations.

One can calculate different metrics that describe the graph (or subgraph) or the vertices individually. However, we will not describe all of them in order to maintain a balance between learning Apache Spark and graph analysis.

Metrics describing graph in general:

- maximum, minimum, average distance (different kinds) between vertices,
- different metrics of connectivity in the graph,
- different measures of centrality,
- different measures of reciprocity (in directed graphs).

When it comes to vertices, the standard task is to calculate various centrality measures and identify the most central or "influential" elements of the network.

## Chapter III

### Goals

The goal of this project is to introduce you to Apache Spark and graph analysis. You will complete various tasks analyzing Amazon’s “Customers Who Bought This Item Also Bought” recommender system. This will help you develop other approaches to recommending goods.

## Chapter IV

### General instructions

- This project will only be evaluated by humans. You may organize and name your files as you wish.
- Here and throughout, we use Python 3 as the only correct version of Python.
- The project was tested on Apache Spark 2.4.7 and GraphFrames 0.8.0. You may use newer versions, bearing this in mind.
- It is prohibited to use any Python libraries, such as Pandas, Scikit-learn, NumPy, NetworkX, etc., except for those needed to visualize graphs. Everything else should be processed using Apache Spark and its third-party libraries.
- The norm is not applied to this project. Nevertheless, you are asked to be clear and structured in the conception of your source code.
- Store the datasets in the subfolder **data**.

## Chapter V

### Mandatory part

#### A. Task

In this project, you will analyze which goods were bought together on Amazon to gain valuable insights. This may help you come up with new ideas for recommendations.

Here are the tasks you need to complete:

- Data preprocessing in Apache Spark and creating a graph using GraphFrames.
- Descriptive analysis of the dataset and graph.
- Creating bundles of goods to recommend.
- Visualizing a strongly connected component of the graph.
- Creating a new version of the recommender system that creates five recommendations for each item in the dataset.

#### B. Dataset

You will work with the [dataset](https://git.21-school.ru/masters/DS7_Amazon.ID_886425/-/blob/5/./datasets/amazon-meta.txt.gz) of goods on Amazon. The dataset contains the IDs of the items, their titles, categories, sales ranks, and ratings, as well as five items recommended by Amazon in the “Customers Who Bought This Item Also Bought” section.

> **Note:** You can find the dataset in the project page.

#### C. Implementation

You can work in [Google Colab](https://colab.research.google.com/) or Jupyter Notebooks on your computer. The first task is to understand how to install Apache Spark and GraphFrames and use them.

**Data Preprocessing**

1. Create a Spark DataFrame from the text file dataset. The structure is unclear and difficult to read. This is a good opportunity to get familiar with Apache Spark.
2. Create the additional dataframes required to create a GraphFrames graph.
3. Create a graph showing how the goods were purchased together.

**Descriptive Analysis**

1. Calculate the number of books, music, and sports items in the dataset.
2. Calculate the maximum number of out-edges for a vertex.
3. Calculate the maximum number of in-edges for a vertex and the corresponding title for that item.
4. Calculate the fraction of reciprocal connections (from A to B and from B to A). In seven decimal places.
5. Find all the triangles in the graph. Find the item (title) included in the most triangles.
6. Find the most important title with the highest page rank. It has links from other important items. The probability of resetting to a random vertex is 0.1, and the maximum number of iterations is 10.

**Bundles and Collections**

1. Create bundles of three goods that are related to each other as follows: A recommends B, C recommends B, and A and C recommend each other. Calculate the number of these bundles.
2. Create the same kind of bundles, but only for the music group. Calculate the number of these bundles.
3. Create collections in the DVD group of items connected to each other, not necessarily directly, but through a chain of other items. This means that there is a path between them. The path should be reciprocal. Find the number of elements in the largest collection.

**Graph Visualization**

1. Using any graph visualization tool or library you find useful, visualize the graph of DVDs.
2. The requirements are:\
   a. The vertices and edges should be distinguishable when zooming in and out.\
   b. The colors of the vertices and edges should be different.\
   c. It should be easy to identify the vertices with the largest in-degree.\
   d. Use at least three different layouts.

Below are examples:

![0](assets/img_1039.png)

**New Recommender System**

1. Propose and implement three different ways to recommend five items for each item in the dataset.
2. We will not assess your recommendations. There is no hidden data, as there is no ground truth. We could test how closely your five items align with the five items used by Amazon, but that doesn't mean your recommendations are worse. The subtask is to describe how you would test your recommendations in the real world.

#### D. Submission

Your repository should contain one or more notebooks with your solutions and visualizations. It should also contain three CSV files, each with five recommendations corresponding to an item. You can download the template from [here](https://git.21-school.ru/masters/DS7_Amazon.ID_886425/-/blob/5/./datasets/recomms.csv).

It should also contain the JSON file with the different measures and metrics that you calculated earlier. You can download it from [here](https://git.21-school.ru/masters/DS7_Amazon.ID_886425/-/blob/5/./datasets/measures.json) and fill it with your values.

## Chapter VI

### Bonus Part

1. Find three more ways to make five recommendations using graph and network measures and metrics. Save them in three different files.
2. Create an interactive webpage based on your graph visualization project.

## Chapter VII

### Submission and peer-to-peer evaluation

Submit your work to your Git repository as usual. Only work submitted to your repository will be graded. Here are the points that your peer corrector will have to check:

- If no prohibited Python libraries were used.
- If all the measures and metrics are calculated correctly.
- If there is a graph visualization.
- If there are recommendations for each ID in the dataset.
- If there is a written methodology for choosing the best recommender algorithm when there is no hidden test data.