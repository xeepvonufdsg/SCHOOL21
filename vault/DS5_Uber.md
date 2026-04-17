# Uber

## Taxi Demand Forecast

*Summary:* This project is an introduction to time series analysis, including stationarity, exponential smoothing, and SARIMA.

💡 [Tap here](https://new.oprosso.net/p/4cb31ec3f47a4596bc758ea1861fb624) **to leave your feedback on the project**. It's anonymous and will help our team improve your educational experience. We recommend you complete the survey immediately after completing the project.

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

Does time exist? Is there absolute time (the idea supported by Isaac Newton) or is time only a relation between events and cannot be an independent measure (the idea supported by Leibniz)? Do the past and the future exist, so that we could hypothetically travel in time? Or do they have no existence of their own and represent only changes that have happened or will happen?

As you can see, there are many philosophical debates about time. But the same is true in physics. Famous scientists using modern theories of quantum mechanics, general and special relativity, and string theory try to answer the same questions. Using various equations, they realized that we could theoretically travel in time if we had some loops in the space-time geometry ([closed time-like curves](https://en.wikipedia.org/wiki/G%C3%B6del_metric)). As Albert
Einstein said: "In this case, the distinction "earlier-later" is abandoned for world-points that are far apart in the cosmological sense, and those paradoxes regarding the direction of the causal connection arise".

Some paradoxes do occur. For example, the grandfather paradox: what would happen if you traveled back in time and killed your grandfather before your father was conceived? To solve this, the [Novikov Self-Consistency Principle] (<https://en.wikipedia.org/wiki/Novikov_self-consistency_principle>) has been proposed. The principle states that if there is an event that would cause a paradox or any "change" in the past, then the probability of that event is zero. Thus, it would be impossible to create time paradoxes.

All in all, what we can really say is that what we know for sure about time is literally nothing. We do not know that it exists absolutely. We do not know if we can travel in time and what the rules are. We do not know what devices can be created to make time travel.

Anyway, whether time is an absolute concept or just a relation to the present is not really important when we deal with some practical and everyday tasks. We know for sure that there will be some changes. If we can predict them by time travel or by simpler methods, we will benefit from it.

## Chapter II

### Introduction

It has been said that forecasting is like driving a car while looking in the rearview mirror. It is a nice analogy, but is it true? In a way, yes. We do look at the past to predict the future: if something was absent in the past, it cannot be predicted in the future. But a better analogy is that we train a driver who experiences many different situations on the road and can make a good prediction of what might happen in the next few moments. He looks in the rearview mirror from time to time: not to learn from the past, but to see the present better and to predict where all the actors around the car might be at any given moment.

Let us see what kind of drivers we might have to predict in the future. What you were doing before was making predictions, but it was not about the state of an object at t+1 moment. It was a prediction about the state of an object in general, in static, whether it was a classification problem or a regression problem. When we talk about dynamic prediction, we need different algorithms — Time Series Analysis (TSA) algorithms.

Imagine that we have to make a weather forecast (temperature) for tomorrow using only the available statistics from the past. We could use the average temperature based on the whole dataset. Another option would be to use the average temperature based on the past few years. It might be a better idea to consider global warming as a trend component.

Another approach is to use the average temperature of the last few days or their weighted sum. This is called a weighted moving average. The more sophisticated approach is to look into the past, but give more weight to the recent data than to the old. It is called [exponential smoothing] (<https://en.wikipedia.org/wiki/Exponential_smoothing>). However, it does not work well if there is a trend. It is better to use double exponential smoothing to deal with that. But if you have not only a trend but also a seasonal component, then it is better to use triple exponential smoothing (Holt-Winters model). It applies exponential smoothing three times.

There is another class of possible solutions — ARIMA (Autoregressive Integrated Moving Average). Its core idea is that the main predictor of the series is the series itself. Your current data may have a good correlation with the data from
of t-1, t-2, t-3, ... period (lag). This is called autoregression. Integrated means that in order to make the series [stationary](http://www.blackarbs.com/blog/time-series-analysis-in-python-linear-models-to-garch/11/1/2016), we have to differentiate it. A moving average model takes the lagged forecast errors as input. ARIMA models have three hyperparameters for each of these parts: p (AR), d (I), q (MA). There are some [rules](https://people.duke.edu/~rnau/arimrule.htm) on how to choose them.

There is another branch of ARIMA called SARIMA — seasonal ARIMA. It has four more parameters, but for the seasonal component. P — seasonal autoregressive order, D — seasonal difference order, Q — seasonal moving average order, m — the
number of time steps for a single seasonal period.

What else can you do? Well, you can still apply classical machine learning algorithms. What you need to do is to extract features as usual (weekday, holiday, time of day, etc.) and make predictions based on them, solving a regression task.

And of course, since a time series is a sequence, you can apply the RNNs you used before to work with text.

Lots to try, right?

## Chapter III

### Rules of project

The goal of this project is to give you a first approach to Time Series Analysis. You will try different algorithms to predict taxi demand in different areas of a city for the next week. The efficiency of any taxi business depends on this.

## Chapter IV

### Instructions

- This project will be evaluated by humans only. You are free to organize and name your files as you wish.
- Here and throughout, we use Python 3 as the only correct version of Python.
- For training deep learning algorithms you can try [Google Colab](https://colab.research.google.com/). It offers free kernels (Runtime) with GPU that are faster than CPU for such tasks.
- The standard does not apply to this project. However, you are asked to be clear and structured in your source code design.
- Store the datasets in the subdirectory **data**.

## Chapter V

### Mandatory part

#### a. Task

In this project you will work on demand forecasting. This task can be useful for many different industries: manufacturers, retailers, banks, etc. This time you will help a taxi company to optimize its business. If you can predict that X taxis will be needed in certain areas tomorrow at that time, you can reduce the arrival time and be better than your competitors.

To do this, you need to try different architectures:

1. naive averages,
2. moving averages
3. exponential smoothing algorithms,
4. ARIMA models,
5. classical machine learning
6. Deep Learning algorithms for sequences.

#### b. Dataset

You will work with the dataset of taxi rides. It contains data from 2019-04-01 to 2019-06-23 for 77 different areas of the city. And you need to make predictions for the next 7 days in 15 minute intervals (673): how many taxi orders are expected in each area.

> **Note:** You can find the dataset in the project page:
>
> 1. taxi\_pickups\_area.csv;
> 2. taxi\_submission\_file.csv.

#### c. Implementation

You can work in [Google Colab](https://colab.research.google.com/) or Jupyter Notebooks on your computer. You can use any library or framework you like. You should keep a research journal with all information about the approaches used and their metrics.

**Naive averages**

1. For each domain, make a prediction using the global average for that domain for the next 673 intervals.
2. Compute the mean absolute error (MAE) for your own validation dataset.

**Moving averages**

1. For each range, make a prediction with different moving averages for that range for the next 673 intervals.
2. Compute the mean absolute error (MAE) for the validation dataset.

**Exponential Smoothing**

1. For each range, make a prediction using 3 different exponential smoothing algorithms for that range for the next 673 intervals. Optimize the weights.
2. Compute the mean absolute error (MAE) for the validation dataset.

**ARIMA**

1. For each domain, make a prediction using the best SARIMA model according to the AIC metrics for that domain for the next 673 intervals.
2. Compute the mean absolute error (MAE) for the validation dataset.

#### d. Submission

Choose your best approach and save the prediction in the submission file (`taxi_submission_file.csv` in the attachment). You can use any of the heuristics above algorithms that you find useful. For example, converting negative numbers to zeros, etc.

You must achieve an average MAE of at most 10.0 on the test dataset.

Your repository should contain one or more notebooks with your solutions.

## Chapter VI

### Bonus Part

- Try using machine learning algorithms for time series analysis. For each domain, make a prediction for the next 673 intervals.
- Try using deep learning algorithms for time series analysis. Make a prediction for each range for the next 673 intervals.
- Try to get an even better average MAE on the test dataset — 8.0.