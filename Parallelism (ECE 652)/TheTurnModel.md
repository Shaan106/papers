# The Turn Model for adaptive routing
Christopher J. Glass and Lionel M. Ni.
SIGARCH Comput. Archit. News 20, 2 (May 1992). 
https://doi.org/10.1145/146628.140384

## Summary

The authors present a model for designing wormhole routing algorithms that are deadlock free, livelock free, minimal or nonminimal, and maximally adaptive. By the time of this paper, it is considered that point to point routing (ie via meshes, n-dimensional cubes etc) is much better and scalable than shared bus transactions. This paper presents a method of preventing deadlocks in wormhole routing without needing additional virtual channels or any additional hardware for that matter, they achieve this simply by analyzing the types of turns taken by the routing algorithms.

Their model can be (trivially) summarized as deadlocks happen when cycles happen. Cycles can be prevented if one of the items in the cycle takes a different turn, although this part needs to be checked as more complex cycles can form. The authors provide a method by which you can examine a network and decide which turns can be removed to prevent deadlocks.

Shows several examples for 2D meshes. When elimination works, when it doesn't. Shows how solution generally works here to avoid deadlocks. This is continued and this method is shown to work for n-dimensional meshes, k-ary n-cubes and hypercubes.

There are then simulations that are run to show the benefits of their specific implementations of this model in different kinds of traffic patterns (although the uniform pattern needed a caveat about global information about the network activity).

## Strengths

- One of the easiest to follow papers I have read. And also clear to see the contributions in formally identifying how to prevent deadlocks in an arbitrary network.

- On a similar note, the applied examples conveyed their point very well, and I appreciated their redefinition of important keywords they mentioned just so that the reader is on the same page as the author to begin with.

## Weaknesses

- I feel like a program to do this for you is possible, maybe specifying a language which takes in the types of turns and outputs the turns that can be removed to prevent deadlocks. This would be useful for larger, more complex networks and also likely prevent human error.

- I get this is not exactly for performance modelling but the traffic models were kind of unrealistic
    - ie "probability of being one packet of 10 or 200 flits is equal" seems a bit too trivial

## Questions

- Back to weakness 1, is there a program that automatically generates deadlock-free routing algorithms for arbitrary networks now? This seems like a solvable problem?