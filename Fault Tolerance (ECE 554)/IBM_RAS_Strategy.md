# RAS strategy for IBM S/390 G5 and G6
M. Mueller, L. C. Alves, W. Fischer, M. L. Fair and I. Modi,
IBM Journal of Research and Development, Sept. 1999,
doi: 10.1147/rd.435.0875.

## Summary

This paper is about the Reliability, availiability and serviceability strategy that IBM used to develop its highly fault tolerant and always operational G5 and G6 servers. The paper talks about the various components required for a system to be RAS compliant, and specifically about how IBM went about achieving this. The paper breaks the special capablities of the G5 and G6 servers into four categories: error prevention, error detection, error recovery, and problem determination. Each category talks about what path was taken to enable things such as error detection, and why their approach was an optimal solution. Furthermore, IBM also includes a lot of "good to know" information about the servers, such as about the servicing and customer specific hardware that is likely to be useful for a potential customer to know.

### Strengths

- Good motivation and methodology, it is interesting to see how fault tolerance is marketed to the real world

- I liked the section about fencing off components with hard faults in a way that is as human free as possible. I especially liked how several levels of granularity were used, so that the minimum amount of hardware was taken offline.

### Weaknesses

- "This causes an unmeasurable performance degradation" (failing cache lines to be logically removed)
    - numbers, examples? they talked about simulations, but I did not see any objective way to see a benefit here apart from the authors' word. Maybe some numbers would convince customers as well?

- There seems to be a lot of overhead for the sake of reliability, would have been nice to see the performance/power tradeoffs that were made to achieve this level of reliability

## Questions

- Did these components ever really sell? I'm starting to see a pattern where fault tolerance is a cool idea but no one seems to have a true use for it? Maybe it's a skewed opinion but this level of fault tolerance just seems redundant.