# Part Quality Analysis


This project aims at building an interactive website that provides an overview of the available machine parts data of one of the leading electric and autonomous vehicles producers and its part & feature analysis to asses process capability.

The Goal page provides the scope of the assignmment. It also details out the constraints and assumptions made for the analysis of the project.


The Data menu has two entries:

* The first one is about the data structure

* The second entry gives detailed information about data dictionary and contains multiple tabs


The Visualization menu has 4 entries:

* The first one is Static Visualization 1 Statistical Analysis. It lists out all the static visualizations in different tabs along with the code (folded and can be expanded for reference)

* The second entry provides an insight into Static Visualization 2 in Dimensionality reduction using PCA and TSNE

* The third entry is based on Static Visualization 3 in Predictive Modeling

* The last entry is Interactive Visualization with Shiny integration


The Project-Timeline page provides a recap of the steps along with thir timeline


Objectives

* To Highlight worst performing features compared to individual tolerances.

* To find the features which have the largest differences between fixtures.

* To find the features which have the largest differences between machines.

* To provide a summary of part quality.


Constraints
The look up dictionary for the term ‘Nominal’ was not available. Hence it was assumed that all measurement observations are relative to the Nominal value and it would not have significant contribution while performing different comparisons

The measurement values are not normally distributed. Some of the tranformations that were explored are log transformation, BoxCox Transformation, abs(measurements - mean). However, for simplicity, all have been aprroximated as normal distribution. Further individually transforming the data columns can improve this analysis.

Interactive website is built on shiny & R, it requires a “server” to run. This can be my own computer, or an actual server (e.g., shinyapps.io). If it has to sent across as an markdown html file with run-time set to Shiny the recipient will be able to run the app as well if they have R, shiny, etc. installed.

An alternate way to share a running shiny app that anyone can access is to host it using shinyapps.io for free. However, the free tier is not the fastest and not secure. Hence, the shiny version of the current assignment would be demonstrated during the onsite interview through personal laptop.

 

Calculations
 

Metric 1: For any feature / specification, the proportion of failure across its column (dimensional feature) is an indication of its quality, which is given by:
∑failures/(∑failures+∑pass)

Metric 2: To investigate further on how badly the failed features/ parts stand out from its natural distribution, we do a weighted sum of its standard-score and fail_flag to develop a failure score. This should capture both, how often it failed and how badly it has failed. Extend of Failure is given by:
∑(std_scores∗fail_flag)/ (∑(std_scores∗fail_flag)+∑(std_scores∗pass_flag))
  Here fail_flag = 1 and pass_flag = 0
