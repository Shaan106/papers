# Web search for a planet: The Google cluster architecture
L. A. Barroso, J. Dean and U. Holzle
in IEEE Micro, vol. 23, no. 2, pp. 22-28, March-April 2003, 
doi: 10.1109/MM.2003.1196112.

## Summary

This article was about the architecture that powers Google's search engine. The main focus was on the parallelism and redundancy that Google uses to provide a fast and reliable search engine. The article starts by discussing the importance of energy efficiency and price-performance ratio in the design of the system. The parallelism in the system is achieved by partitioning the overall index and letting different queries run on different processors.

The most important factors that influence the design of the system are energy efficiency and price-performance ratio. This is because the workload is so parallelizable that essentially it is irrelevant how performant a piece of hardware is, and the program can be almost arbitrarily sped up via parallelism. This means the most important fact is performance per unit of cost, as that leads to the most speedup possible for the least price (as they don't exactly have to car about single threaded performance).

### Strengths

- Clear example of why understanding what you are running and modelling for is extremely important for what hardware you develop.

- Simple principle, well developed, easy to read.

### Weaknesses

- Cost of parallelism vs better hardware? They just said parallelism better but didn't talk about the costs that has (power etc), as in it could be better for power to have more performant hardware.

## Questions

- What about the cost of worse hardware having to be replaced more often? Is it the case that cheaper hardware wears out more quickly?