# End-to-end arguments in system design.
J. H. Saltzer, D. P. Reed, and D. D. Clark. 1984. ACM Trans. Comput. Syst. 2, 4 (Nov. 1984), 277–288. https://doi.org/10.1145/357401.357402

## Summary

This paper argues that there is a lot of unnecessary redundancy in computer systems, especially at the lower levels. The authors argue that the end-to-end principle is the most important, a kind of "Occam's razor", and that the lower levels should not provide "perfect" reliability.

This is because more often than not applications provide (and necessarily need) higher scopes of checking and redundancy that makes the lower level redundancy obsolete and a burden on performance. The paper gives a lot of examples, such as file transfer, where the application level is responsible for checking the integrity of the file, and the lower levels need not provide this. The lower level packet transfer can be unreliable, but the application level can check the integrity of the file and request a retransmission if necessary, and thus the packet checking is redundant and a burden on performance.

However, the authors do realise that the amount of redundancy and at what level is very application specific, and figuring out what is essential and what is not is a complex and difficult task. The authors argue that this difficult task is not considered enough at the time of writing, and that it would lead to many performance benefits if it were considered more.

## Strengths

- I like the simplicity of the argument made, and how the points made are clearly conveyed to be very impactful.

- The discussion of the many applications where this principle is applied makes it very easy to understand and see the power of this principle.

## Weaknesses

- The paper at times seemed to call for less redundancy in the lower levels everywhere. I would have liked to see some discussion on where redundancy is still important, and where it is not.
    - For example, I can imagine cases such as the Apollo or Voyager missions where redundancy even at the lower levels is very important, as the cost of failure (even partially) is just so high.

## Questions

- I really liked Lampson's idea of the programmer being able to replace/modify OS level programming to the user's needs
    - It seems like a lot of problems arise from programmers re-doing things that already exist in the hardware/OS level. Have there been any systems that have been designed with Lampson's ideas in mind?
    - Although I could also see this leading to security and correctness issues - writing good code is hard, and giving OS or lower level access to programmers could be bad (eg Crowdstrike)