# Engineering trust with semantic guardians
Ilya Wagner and Valeria Bertacco. 2007. 
In Proceedings of the conference on Design, automation and test in Europe (DATE '07). 
EDA Consortium, San Jose, CA, USA, 743–748.

## Summary

Lots of bugs find their way to production. This paper presents an approach called semantic guardian. The idea is for components to have two modes of operation, normal and safe. It is meant to be easy to switch between these modes, and the idea is that having these built in is a lot less work than the additional work needed for complete validation. The semantic guardian is a hardware component that monitors the pipeline and can detect when the pipeline is in an untrusted state. The idea is to have a small amount of trusted hardware that can monitor the pipeline and detect when it is in an untrusted state. The semantic guardian is a small piece of hardware that monitors the pipeline and can detect when the pipeline is in an untrusted state. The idea is to have a small amount of trusted hardware that can monitor the pipeline and detect when it is in an untrusted state. When the pipeline is in an untrusted state, the semantic guardian can switch the pipeline into a safe mode of operation, thus keeping all execution in a theoretically safe state without much overhead.

## Strengths

- Over time, as more validation is done more and more of the run time can be in normal mode. This is quite cool as it seems to take the long time to market of a chip and make it possibly significantly shorter

- I found the extraction of safe states from the control logic to be quite clever.

## Weaknesses

- The validation team could have been wrong. This doesn't cover that case at all, and it seems almost silly to say that the validation team is perfect.

- What about manufacturing defects?

## Questions

- Is the selling point of this just that you can have a quicker time to market? Otherwise I don't really see the benefit of this over DIVA.