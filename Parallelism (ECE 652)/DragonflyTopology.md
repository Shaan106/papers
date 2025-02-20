# Technology-Driven, Highly-Scalable Dragonfly Topology. 
John Kim, Wiliam J. Dally, Steve Scott, and Dennis Abts. 2008. 
SIGARCH Comput. Archit. News 36, 3 (June 2008), 77–88. 
https://doi.org/10.1145/1394608.1382129

## Summary

Want to start using high radix routers as modern systems incorporate more and more distributed components. The problem is that this requires high-radix routers with radix of ~2√N where N is network size, and as N grows this is not feasible.

The radix of each router is k = p + a + h − 1, (radix = num_terminals + num_local_routers - 1 + num_connected_global_routers). Each group has ap connections to the group's terminals and ah connections to the system's global routers. Therefore, as a group the router has a radix of k' = ap + ah = a(p+h). This is much more efficient than having a bunch of individual routers being scaled up (since k' >> k). 

Choices can be made for p, a and h which can be optimized for different network sizes and traffic patterns. The authors provide a few examples of how to optimize these parameters for different network sizes and traffic patterns (such as exploiting package locality by having more interconnections to neighboring routers).

The authors also discuss the special routing algorithms needed for this topology. The issue lies in the fact that global routing within groups requires jumps to other routers and this can prevent local information about global channels from being utilized like it traditionally is. This sometimes mean that minimally routed packets end up taking much longer to reach their destination in adversarial traffic patterns. The authors provide a custom routing algorithm to deal with this.

Furthermore, the authors show how this network topology actually has a much better cost per node than other topologies, mostly due to the higher effective radix of each group of routers.

## Strengths

- The simplicity of the idea is really quite amazing, it's really subtle but leads to some amazing properties.

- I appreciated the authors providing the logical/mathematical derivations behind why this topology is better, this paper is really clear in what it is trying to say.

## Weaknesses

- Honestly, none. I thought they conveyed the idea well, found the weaknesses and addressed them.

## Questions

- I can see a similar kind of idea that is used in the groups being done for higher-dimensional base routers, is this a thing? Can you possibly get an even better scaling factor?
