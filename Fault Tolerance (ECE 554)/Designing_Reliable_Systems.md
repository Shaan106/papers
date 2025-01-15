# DESIGNING RELIABLE SYSTEMS FROM UNRELIABLE COMPONENTS: THE CHALLENGES OF TRANSISTOR VARIABILITY AND DEGRADATION
Borkar, 2005

## Summary

This paper discusses the challenges we are going to face as we scale technology in the future. As transistors and components become smaller and more sensitive, reliability of components becomes an even larger issue. The paper argues that reliability is a metric that should be considered during this development, much like power and performance metrics. The paper also presents a lot of the causes of unreliability in components, such as transistor variability and random radiation effects, and also presents possible solutions to these problems, through techniques such as multi-processor redundancy and error correcting codes.


### Strengths

- The paper does a good job in presenting the challenges that are going to be faced in the future as technology scales. The problem is clear, and the "call to action" is clear - we need to start considering reliability as an important metric in our designs.

- I appreciated some of the examples given in the paper, where there are often common misconceptions - such as with the example of the clock signal passing through fewer gates in a clock cycle leading to a lower probability of meeting the frequency goal.

### Weaknesses

- I would have liked to see a bit more on the evolution and improvement of error detection and correction techniques - are these scaling at the same rate as the technology they are protecting?

## Questions

- Related to the weaknesses, how are these error detection and correction techniques actually improving? Are they scaling at the same rate as the technology they are protecting?