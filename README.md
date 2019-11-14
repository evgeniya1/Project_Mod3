# Grade distribution analysis of UW Madison dataset

This project is devoted to the explorational analysis of A-grade fraction distribution based on the extensive university (UW Madison) grading dataset collected over 11 years period. It is mainly focused on hypothesis testing aimed to identify statistical significance of the class size, field of study, and instructors.

## Data collection

Dataset is taken from https://www.kaggle.com/Madgrades/uw-madison-courses. This dataset contains information about the University of Wisconsin - Madison classes taught between 2006 and 2017 that includes 22 terms. Initial set contains 193,262 observations for classes taught by 18,598 instructors in 200 subjects. After filtering S/U, Cr/N and missing (zero-size class) grades, missing sections and instructors, the dataset includes information about 74,853 classes, only 39 % of original dataset contains information necessary grades.

## Problem formulation

These are the questions to answer:

- What is the influence of an instructor on A-grade fraction?
- What is the influence of class size on A-grade fraction?
- Where bimodality comes from? Is it a class size?
- What is the A-grade fraction distribution for a specific instructor with respect to the class size?
- What is the influence of STEM versus humanity field of study with respect to the class size?
 
 ## Exploratory data analysis
 
Figure below shows the distribution of A-grade fraction together with mean ![equation](https://latex.codecogs.com/gif.latex?$\mu$) with 95% confidence interval, median ![equation](https://latex.codecogs.com/gif.latex?$\widetilde\mu$), standard deviation ![equation](https://latex.codecogs.com/gif.latex?$\sigma$), and number of observations (*N*).
 
![](https://github.com/evgeniya1/Project_Mod3/blob/master/figs/distribution_A.png)

A-fraction grade distribution is clearly not normal, it is bimodal. Q-Q plot below shows how strongly it deviate from normal. Moreover Kolmogorov–Smirnov (KS) test for normality of the distribution gives statistics value of 0.503 and p-value close to zero, in aggrement with the fact than distribution is not normal/Gaussian.

![](https://github.com/evgeniya1/Project_Mod3/blob/master/figs/qqplot.png)

The first question to answer is: what is the influence of an instructor on A-grades fraction? To answer, let me first explore the dataset with regards to instructors. Figure as well as summary table below show the distribution of number of classes taught by one instructor. 

![](https://github.com/evgeniya1/Project_Mod3/blob/master/figs/num_classes_per_instructor.png)

|title|count|	mean|	std|	min|	25%|	50%|	75%|	max|
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
|classes per one instructor	|10165	|7.363797	|10.609767	|1	|1	|3	|9	|239|

It is interesting to note that, median is 3 classes per instructor, i.e. about half of instructors teaches not more than 3 classes within 11 year period in one university, meaning that instructors are replaced frequently.
