# Power: A First-Class Architectural Design Constraint

## Paper 
Power: A First-Class Architectural Design Constraint \
Trevor Mudge \
IEEE Computer, vol. 34, no. 4, pp. 52–58 \
April 2001 \
https://users.cs.duke.edu/~lkw34/papers/mudge-power-ieeecomputer2001.pdf


## Problem Description and Motivation

Professor Mudge brings forward a theme that has been often overlooked in computing: the energy cost. He emphasises the role of power in chip design by pointing out facts like the fact that power accounts for ~25% of the cost in server facilities. With the exponential growth of the internet and technologies that rely on hardware, the cost of this power is just going to increase. Prof Mudge stresses the fact we cannot continue designing processors in this way or we are going to be creating processors that are unsustainable in many ways.

## Main Ideas/Approach (soln, method, technq)

Prof Mudge build his argument upon the equation for power in CMOS circuits:

$P = ACV^2f + \tau AVI_{short} + VI_{leak}$

He mentions that reducing $V_{threshold}$ is not feasable due to it increasing leakage power (but appreciates this will be an issue in the future). And so instead the current aspect to be focussed on is reducing activity and improving power efficient parallel computing. Furthermore, he states that these optimizations cannot be done in isolation as statistics like Peak power and Dynamic power are very important to a design and are not encapsulated by these statistics.

Then Prof Mudge lays out a few methods of achieving the goal of reducing power: through Logic (clock gating, half freqeuncy clocks, asynchronous logic), through Architecture (better speculation, better memory systems caches and RAM, buses, parallel processing and pipelining), through the OS (manging the processor voltage through the OS), and through highly-specialized "inelegant" co-processors (like the network chips on mobile devices).

In the end there are comparisions of processors modern at the time of writing with the XScale processor, one developed to optimize for power. This comparision shows just how much room for processor energy efficiency there is - and one that has not yet been fully investigated.

## Strengths and Weaknesses

### Strengths
I think this piece does a very good job at providing a broad overview of what methods we have at our disposal to create more energy efficient processors. I feel as if I understand why power inefficiency is there in a chip, and have a high-level understanding of many techniques to make chips more power efficient.

### Weaknesses
I think there could have been a better discussion about why energy efficiency is an issue rather than just stopping at it accounts ~25% of server costs. Is there an effect on processor performance? Processor lifetime? Manufacturability? These are all questions that, if answered, I think motivate the problem better.

## Questions for Discussion

If we design a low power system in most systems won't that mean we could potentially improve performance by allowing more power? Take buses for example. They take a lot of excess energy, and let's say we reduce their power consumption which prevents us from hitting a thermal limit allowing us to put more bus width in for more data transfer. And so overall no power is saved. As long as the incentive for performance is higher than that of low power won't research into this area do nothing but increase performance in the end?
