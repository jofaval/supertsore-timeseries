# Superstore #

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jofaval/superstore-timeseries/blob/master/notebook.ipynb)

## Table of contents

1. [📁 Data](#-data)
1. [📓 Description](#-description)
1. [✔️ Objectives](#-objectives)
1. [🧱 Tech stack](#-tech-stack)
1. [💹 Algorithms](#-algorithms)
1. [📊 Visualization](#-visualization)
1. [🤓 Conclusions](#-conclusions)
1. [©️ Credits](#-credits)

## 📁 Data
[↑ Back to the table](#table-of-contents)

The data is from the OpenML Datasets, [Superstore Sales Dataset](https://openml.org/search?type=data&status=active&id=43383&sort=runs).

## 📓 Description
[↑ Back to the table](#table-of-contents)

This dataset doesn't have an extensive description, nor does it have a description per se, it's a dataset about the products that customers bought on their store and the total amount over the time. From 2015 to 2019, almost completely. The orders were shipped, and we also have access to the shipping information.

This was a project "researched", well, found, on my own on the OpenML, I had an objective/idea in mind, I wanted to do a timeseries project. I could say I did not want to fall under the classics of temperature/stock prediction, but it's just that this dataset caught my attention by it's simplicity and good amount of rows. I like timeseries analysis but I do have to be honest and say that it's the least experienced I'm at of all the notebooks I've ever published to this date.

This notebook shows wordier conclusions, exploration, analysis, algorithm understanding as to better apply them, and most importantly, understanding why they are (not) working. This one is sorter to an extent, but it's straight to the point, if I had to say so myself, while it's still a newbie notebook, it's target audience should at least know some basics about data science and data analysis. Tensorflow's official doc came in the rescue, timeseries is an extensive topic with a lot of detail and depth.

This one took a day or so. It was pretty straight-forward at times. But tuning did take some time for.

## ✔️ Objectives
[↑ Back to the table](#table-of-contents)

In no specific order whatsoever:

- Apply all of the knowledge about timeseries projects and data exploration.
- Improve and increase my portfolio with intresting and different projects, also ones that I've never seen before.
- While increasing my portfolio, add more variety than just regression and classification.
- Explore different solutions and it's prons and cons.
- Use datasets from OpenML as sort of a first PoC as to what they have to offer in opposed to Kaggle, to say.
- Correctly map the dates while sanitizing and understanding them.

What were some of the main objectives?

- Use LSTM for a timeseries prediction without falling under the, try all of the algorithms.
- Predict the sales over the course of time, or to justify why it could not be done.
- Analyzing the order and shipping dates for anomalies, to learn more about them.
- Practice exploratory analysis on timeseries projects, and, specially, on dates.

## 🧱 Tech stack
[↑ Back to the table](#table-of-contents)

Python, that's it! R is a programming language that, as for the moment being, I have no experience with, even though it's powerful and broadly used, but I'd dare to say that no more than Python.

And one of the strongest points, if not the most, about Python, are it's libraries, so... the libraries I've used are:

- Pandas, data manipulation with an ease of use and exploration data analysis.
- Numpy, a really strong linear algebra library, used in the project for it's statistics utilities, SciPy may be an alternative, but I have no experience at all with it.
- Matplotlib and Seaborn, both fantastic libraries for data visualization, and they complement each other.
- Tensorflow and Keras, the industry standard for Deep Learning, the way to go, not really, it's just that for now I don't have that many experience with PyTorch

## 💹 Algorithms
[↑ Back to the table](#table-of-contents)

For the algorithm I followed by the book the Tensorflow official example about timeseries. Data preparation is the most important step to any model, and timeseries are no exception, the preparation differs quite a bit from the usual, but only in some aspects.

Proper normalization is one of the most important thing in a dataset for adequate and accurate results. Specially in timeseries where it's so sensible to scale difference.

Timeseries work with Time Windows, which basically are frames of inputs that are going to be passed down to the model. The number of time units that will be passed, the number of output units we want to predict, the units of time distance between them and the target feature(s) are the values it takes.

A "simplified" explanation would be:
The idea with timeseries is to, given **`N`** units of time (day, hours, seconds, etc.) predict the target value(s) for the next **`M`** units of time, it could be right after the last input unit of time, or **`O`** units after.

## 📊 Visualization
[↑ Back to the table](#table-of-contents)

As a heads up, the [official dataset's page](https://openml.org/search?type=data&status=active&id=43383&sort=runs) does already provide a quick glance at some statistic details of the information, and there's no complex mapping to be done, other than timeseries' base ground.

The only real use for Seaborn for this project, was to plot the correlation heatmap, there was no complex plot that required seaborn, and I liked matplotlib's style for this project, it's quite effective without going too overboard. There are time windows visualizations, those are handled by the Tensorflow `WindowGenerator` class, and overall cyclic pattern detection plots, which are just lineplots, really wide lineplots.

The date visualizations, this are still basic visualizations, but the way to interpret them, that's where the exploratory analysis changed, and so the way to present the plots. Dates are converted to sin and cos so they're more easily understandable to neural networks. So, that leaves us with sinusoidal plots, but one cool thing we can do with them is that, sinusoidal plots are suppposed to loop continously as long as the X axis has values, this means that, lineplots may be effective for the overall view, but if we scatterplot the values, we can detect any gap, any information loss or breach in the timeseries, which, there were a lot of small ones. It's something I discovered sort of by mistake, but, for sure, it's more than likely that it's out there.

Another cool visualization that this project offered is the order and ship dates relation, we had two dates, that means that we can see how far off one date was from each other by sorting with one another. When two dates are closer relative to time, the disruption will be nearly visible, the closer they are, that is. The further, the more disruption there will be, and the less understandable the plot it will become, it's sort of like a chaos meter.

Finally, another thing that was observed is that, the shipping dates went out of the scope of the dataset, I mean, this dataset comprehended 4 years, but the ship date showed intervals as if there was more than 4 years, just a little bit more. Which means that it's about orders between those four years, not necessarly shipped orders, just an order on the system in that date range.

## 🤓 Conclusions
[↑ Back to the table](#table-of-contents)

I go into more detail about the conclusions in the notebook's conclusions section, but to quote some parts:

_Cyclic patterns_
_Detecting any sort of cyclic (repeating) pattern, is a crucial part of a timeseries project. Specially in the exploratory analysis._
_Our timeseries model will adapt and learn from those patterns, if there's no pattern at all, it becomes harder for our model to adapt. In this project, no clear pattern was truly detected. But there were some denser points than others, and some minor repeating patterns every now and then._

_The influence of the past in the future_
_..._
_Having data from the start that's not relevant to the present can, and will confuse the model, but it is necessary to have past information, as events are at times but repeating patterns. You just have to be conscious how much past information is fed to the model._

Timeseries is really tricky, but intresting, it's like being a timelord uncovering the little neat details underneath the fabric of reality. It's also amazing how much you can, conceptually, do, with so little information and at least a timestamp.

## ©️ Credits
[↑ Back to the table](#table-of-contents)

All of the credits for the dataset goes to [OpenML](https://openml.org) for their open datasets iniciative.
To you, reader, this one was chaos, it was all over the place, so kudos to you.