# A/B testing for Business Analysts 
> [Udemy Course](https://www.udacity.com/course/ab-testing--ud979)

Alteryx is a data analytics software. You can find out more about [Alteryx here](https://www.alteryx.com/).

Here is a list of free courses that can help you get familiar with this software:

- [Problem Solving with Advanced Analytics](https://www.udacity.com/course/problem-solving-with-advanced-analytics--ud976)
- [Creating an Analytical Dataset](https://www.udacity.com/course/creating-an-analytical-dataset--ud977)

Read more about the **Plot of Means** tool [here](https://help.alteryx.com/2018.3/Plot_of_Means.htm)

## Randomized Experiment

### More Detail on Unit of Diversion Web Experiments
Udacity has another course entire focused on web-based A/B tests. If you'd like to dive into more detail on unit of diversion, go [here](https://classroom.udacity.com/courses/ud257/lessons/4001558669/concepts/39700990000923).

Here are the main questions you need to address to design a randomized experiment:
- What is the unit of diversion?
- What is the population of people we're targeting?
- What is the duration of the test?
- What is the size of our treatment and control groups?

## T-Tests Types
There are three types of t-tests you can use: **paired, the equal variance, or the unequal variance**. In a random experiment you will usually assume that variances between the groups are different, so we’ll use an unequal variance t-test. 

You can read more here:
- [Paired Sample T-Test](https://www.statisticssolutions.com/manova-analysis-paired-sample-t-test/)
- [Unequal Variance](http://www.real-statistics.com/students-t-distribution/two-sample-t-test-uequal-variances/)
- [Equal Variance](http://www.real-statistics.com/students-t-distribution/two-sample-t-test-equal-variances/)

## Matched Pair Design Tests

For a refresher on how to find and deal with outliers, go to the course: [Creating an Analytical Dataset](https://classroom.udacity.com/courses/ud977/lessons/56630bff-890b-4f55-ab05-26c65eafc4f0/concepts/a252a8ec-5e9c-4b55-8285-e0743d64e1b5#)

### Pricing Elasticity

"Price elasticity of demand is a measure of the relationship between a change in the quantity demanded of a particular good and a change in its price. Price elasticity of demand is a term in economics often used when discussing price sensitivity." Investopedia.

If you'd like to read more about pricing elasticity, Investopedia has a good breakdown of the concept. Use this [link](https://www.investopedia.com/terms/p/priceelasticity.asp#ixzz4KDgCH9a0) - it's about a 3-4 minute read.

> **Note:** It does say in the video 1 year plus a minimum of 6 periods, but if you look at the AB Trends tool documentation it indicates the rule of thumb is actually 12 periods (in addition to the year) if you are measuring weekly. Keep this in mind as we move forwards.

[AB Trends Tool Documentation](https://help.alteryx.com/2018.3/AB_Trend.htm)

### Overview

Here is an overview of our plan:

1. Prepare Data from two raw data files (found at the bottom of the page)
    - Point of Sales Transaction file
    - Treatment Stores file containing price levels and store identifiers

2. Create three data files:

Use these two raw data files to create 3 files. These files are:

   - Weekly store traffic data for A/B Trend Tool -> Produces our seasonality and trend indices to help us match our treatment and control stores
   - Store list data for A/B Controls tool -> Produces which control stores to match with our treatment stores along with results from the A/B Trend Tool
   - Sales data for A/B Analysis tool -> Produces the final results
  
3. Use the three data files to match our treatment and control stores to calculate the sales lift.

Below is a rough workflow of how to take the raw data files to create the necessary data in order to use the A/B Analysis tool. This is not a complete Alteryx workflow, but just a diagram to help you understand what we'll be doing for the rest of this lesson.

