# Use ECP, not ECC, for Hard Failures in Resistive Memories

Stuart Schechter, Gabriel H. Loh, Karin Strauss, Doug Burger
Microsoft Research, Georgia Tech
2010

## Summary

This paper puts forward a new method of error correction to replace ECC in the case of hard failures in resistive memories. The authors argue that the future of memory is using phase change memory (PCMs) as it (1) provides a more scalable technology than DRAM, (2) is less prone to transient errors and (3) is the closest to commercialization. However, the major drawback of PCMs is that they have a limited number of writes before they break. PCM cells start to breakdown after 10^7 - 10^9 writes, whereas DRAM cells can take up to 10^15 writes. The paper provides ECP which essentially replaces ECC or any other scheme for phase change memories. The idea is to have a pointer to the memory cells which are found faulty, and re-route memory reads/writes to/from those cells to some replacement cells so that the memory system can last longer even under failure (and also not have as many errors as you no longer perform memory transactions with faulty cells). The paper then goes on to provide further refinements to their model (such as reads and writes not being 512 bits wide). These refinements lead to more opportunity for their scheme to be made better, such as through the rotation of memory locations so that memory writes are spread evenly across memory evenly.

## Strengths

- Very cool idea to completely change error correction for a new technology.

- It was nice to see methods being developed for a not-yet-commercialized technology, I like the idea of trying to go outside the already established methods/ideas and build infrastructure to allow new and different technologies to be used.

- The arguments made very clear and made the paper very easy to follow and understand.

## Weaknesses

- I don't like this: "The ECP approach assumes that soft errors are not a problem for phase-change memories"
    - This seems silly. Soft errors would clearly still exist, albeit less frequently. 
    - What happens if a soft error occurs in transit? You can't just say that doesn't happen because we are using PCMs.
    - This assumption seems like it would negatively affect perfomance of a correct system in the real world, maybe transient errors are just not common enough?

- Comparing ECC and ECP was strange, it seems to me like they are addressing different problems. It seems to me like both are needed for PCMs, lack of ECC is odd.

## Questions

- Are PCMs really completely immune to soft errors? 

### Bonus (not quite a weakness)
- I really did not find the motivation convincing. They did not argue for the case of PCMs well enough. From the paper it seems like PCMs are more energy intensive and have lower reliability. I think they should have incorporated more of the benefits of PCMs into their argument (ie more data to store when PCMs arrive, higher density etc).
