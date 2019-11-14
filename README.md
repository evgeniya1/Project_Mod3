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

### Influence of instructor

The first question to answer is: what is the influence of an instructor on A-grades fraction? To answer, let me first explore the dataset with regards to instructors. Figure as well as summary table below show the distribution of number of classes taught by one instructor. 

![](https://github.com/evgeniya1/Project_Mod3/blob/master/figs/num_classes_per_instructor.png)

|title|number of observations|	mean|	std|	min|	25%|	50%|	75%|	max|
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
|classes per one instructor	|10165	|7.36	|10.61	|1	|1	|3	|9	|239|

It is interesting to note that, median is 3 classes per instructor, i.e. about half of instructors teaches not more than 3 classes within 11 year period in one university, meaning that instructors are replaced frequently.

Next plot shows A-fraction distribution for a given instructor (shown in blue) together with overall distribution among all instructors (red line). Here instructors are sorted by the number of classes taught in descending order, i.e. data for top 10 most frequent instructors is presented below. The summary statistics from simple t-test comparing mean of a given instructor (see title for each graph) with the population mean for A-fraction grade distribution is also listed in each graph. Here *x* is A-fraction mean, ![equation](https://latex.codecogs.com/gif.latex?$\widetilde x$) is median, *s* is sample standard deviation, *n* is number of classes taught, ![equation](https://latex.codecogs.com/gif.latex?$\widetilde class$) is average class size for classes taught by the given instructor, *p* is the *p*-value for t-test (for *p*-value < 0.05 null hipothesis, that sample distribution and population have the same mean, should be rejected).

![](https://github.com/evgeniya1/Project_Mod3/blob/master/figs/Afrac_dist_instructor.png)

T-test confirms that all top instructors (by the number of classes taught) form different groups, which is statistically significant.

 ### Influence of class size
 
 Moving to class size influence, figure and summary table below shows the distribution of classes by the number of students.

![](https://github.com/evgeniya1/Project_Mod3/blob/master/figs/class_size_dist.png)

|title|number of observations|	mean|	std|	min|	25%|	50%|	75%|	max|
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
|class size| 74853|	31.58| 45.92|	1|	11|18|	29|	717|

How do we define categories for class sizes? I decided to define boundaries using quirlites: class size is considered small if number of students belongs to [*min*, *Q1*] inteval, medium - [*Q1*, *Q3*], large - [*Q3*, *max*]. From the plot below
class of small size has prominent maximum at A-fraction = 1, medium is closer to uniform distribution, while larger has a prominent maximum around A-fraction = 0.2.

![](https://github.com/evgeniya1/Project_Mod3/blob/master/figs/Afrac_quartile.png)

To better understand the differences, a violin plot showing distributions for the defined class sizes is presented below.

![](https://github.com/evgeniya1/Project_Mod3/blob/master/figs/Afrac_class_size.png)

As can be seen from the plot above as confirmed by the non-parametric Kruskal-Wallis H-test, having the null hypothesis that the population medians of all of the groups are equal (p-value is extremely low, null hypothesis is rejected), different class sizes have statistically significantly different medians or at least one of the groups.

### Influence of class size and instructor

Now the question is does class size influence holds for any instructor? To answer this question, first we need to select instructors that taught classes with have more uniform distribution with respect to the class size and simultaneously having larger number of classes taught to have enough observations.

![](https://github.com/evgeniya1/Project_Mod3/blob/master/figs/table_sort_instructors.png)

According to the figure below that shows the violin plots for A-fraction distribution, top 10 instructor clearly have different grading styles: for some there is a difference between class sizes, but for some this no difference.

![](https://github.com/evgeniya1/Project_Mod3/blob/master/figs/instuctor_uniform_max.png)

For selected 247 instructors (out of total 10165) with threshold of 5 classes (not less than 5 classes taught in each class size category) based on the same Kruskal-Wallis H-test but done for a given instructor, about 61% of instructors grade classes of different sizes differently (*p*-value treshold is 0.05), while for the rest 39% of instructors there is no statistically significant defference in grading classes of different sizes. 

 ### Influence of class size and field of study
 
 Lastly, is there an influence of field of study, i.e. STEM or humanity? Figure below shows the violin plot of A-fraction grade distribution for different sizes and fields of study. It can be seen that the class size influence remains the same in both fields of study.
 
![](https://github.com/evgeniya1/Project_Mod3/blob/master/figs/class_size_subject_type.png)

According to the Kruskal-Wallis H-test, there is a significant difference in terms of medians between STEM and humanity groups in each class size category.

## Conclusions

Exploratory data analysis and hypothesis testing of the grading dataset from UW Madison university collected over 11 years period arrive to the following conclusions. 

- Majority of instructors grade differently if compared to the overall population in terms of A-grade.
- Groups formed by the class size (small, medium, large) differ significantly in terms of A-grade fraction median.
- For 61 % of instructors class size has significant influence on A-grade fraction.
- There is a statistically significant difference for A-grade fraction between STEM and humanity fields of study that persists for different class sizes.
