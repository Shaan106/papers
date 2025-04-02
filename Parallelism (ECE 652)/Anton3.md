#  Anton 3: twenty microseconds of molecular dynamics simulation before lunch.
Prof Towles et al 2021. 
In Proceedings of the International Conference for High Performance Computing, Networking, Storage and Analysis (SC '21). Association for Computing Machinery, New York, NY, USA, Article 1, 1–11. 
https://doi.org/10.1145/3458817.3487397

## Summary

Anton 3 is a supercomputer developed to deal with the hard problem of molecular dynamics. Molecular dynamics is a particularly hard problem due to its non-linear scaling as the number of atoms increase for the problem, which is usually makes it computationally impossible to simulate insightful models. It is a significant step over the already state of the art Anton 2 system. The general idea here seemed to deal a lot with keeping all the components of the system constantly fed with appropriate work, so that utilization was maximized (since there are a lot of instructions to compute). 

There are a couple of main improvements in Anton 3 (although the system seems to be built from the ground up in a lot of cases). The first part is a new custom network which is mostly due to new process nodes making component interconnects harder (cannot just trivially autoroute for the best performance). There is alos a specialized pairwise interaction component that works at different precisions based on what kind of computation (long or short range forces), which allows for die area to be used for doing high precision computations on what is more relevant and less on what requires less precision. Furthermore, there are also specialized bond calculations. This is mostly to allow for more feeding in of data area than computation chip area, which is a common theme in Anton 3. 

The system also naturally is much more computationally efficient per unit work done by the nature of its "algorithm in the silicon" design. It beats previous architectures by several orders of magnitudes in performance and thus can allow for simulations that are either much longer or have many more atoms or both than was possible before.

## Strengths


- Obviously, the performance being that much better than all the other computers is crazy. I did not know you can get that much performance out of specialized hardware.

- Using compression for communication was a cool idea, and it makes a lot of sense in cases like this where you almost always know the I/O data format and it's not general purpose.

- It was suprisingly cool to see how much of the architecture is just keeping functional units fed and utilized.

## Weaknesses

- Does the loss of accuracy via approximation matter? There seems to be a few mentions of less "accurate" things being done. I can imagine this snowballing into more error as the simulation goes on for longer.

- Would it not be inefficient to model such inherently quantum systems with a classical computer?

## Questions

- What is the interface/software like? is there a cuda-like interface?

- What is the precision Anton 3 goes to? Are IEEE standards followed? Is there a custom data format?

