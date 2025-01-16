# A Large-Scale Study of Failures in High-Performance Computing Systems

## Summary

This paper is built around the novel collection of data for failure quantification and characterization in large scale computation systems. The authors spend a lot of the paper discussing the systems that they collect data from (Los Alamos Labs and a system that preferred to be kept anonymous). The paper characterizes the data, building a sort of documentation for all that is collected, very clearly labelling the data (from which system, what type of failure, time to fix etc). This data is then visually presented and some brief conclusions are drawn from these visualizations. Next the authors attempt to characterize the data with a few different models, such as the Weibull distribution, and the lognormal distribution. The authors also attempt to correlate the data with a few different factors, such as the number of processors, the number of nodes, and the number of cores. The paper concludes with a discussion of the implications of the data, and how it can be used to improve the reliability of these systems.

### Strengths

- The paper motivates the need for data in this field very well.

- The data collection, and documentation early in the paper are very strong. It is clear to see how this data is necessary and how this data can help a lot of work in this field.

- I was particularly impressed with how much effort was put into organizing and labelling the data as well as possible.

### Weaknesses

- I thought there was very little discussion of bias in this data. I can assume that the Los Alamos data is skewed due to type of hardware, the environment (altitude, radiation even). I really think this needed at least some discussion.

- The paper seemed to be very underdeveloped in the analysis of the data, which felt like more of an afterthought. I thought the data found and labelled was very strong, however some of the data analysis was weak.

- Further on the previous point, the paper claimed things such as the "Weibull distribution fits well" - which I am fine with if it was backed up statistically. I would have like to see the use of something like Pearson's r to back up these claims.

## Questions

- Is data like this ever evaluated further or inspected for bias? I feel as if a lot of the data collected could be skewed due to the environment it is collected in. Future papers could use this data and make incorrect conclusions because this data is taken as ground truth.