# Test3.ComputerStructure.ProcessorAndPrograms
Test3.ComputerStructure.ProcessorAndPrograms

# Computer structure  
  
After the previous lectures - serving as an introduction - we can now proceed to answering the more general questions:  
  
* What serves which purpose in a computer?  
* What are the subcomponents of a processor?
  
The following lectures will expand some topics appearing on this one (e.g. "how does a computer run a program?"), though they'll also touch other detailed topics.  
  
## Modern integrated circuits  
  
In the lecture "Integrated circuits", we dealt with logic gates and larger digital circuits built from them. In these years, logic gates are esentially no more manufactured as separate products; instead, the smallest building blocks are integrated circuits which combine multiple gates according to a particular application: starting from the simpler ones described in the previous lecture (adders, flip-flops, comparators etc.), through much more complex ones. A typical integrated circuit available in an electronic shop will now look like this:

[![Figure 1. The look of an example integrated circuit.
(Source: https://en.wikipedia.org/wiki/Integrated_circuit)](https://github.com/TAK-PJATK/Test3.ComputerStructure.ProcessorAndPrograms/blob/main/IC.png?raw=true)](https://en.wikipedia.org/wiki/Integrated_circuit)  
Figure 1. The look of an example integrated circuit.  
(Source: https://en.wikipedia.org/wiki/Integrated_circuit)  

On the picture, we see a cover, hiding the proper circuit, made mostly of silicon. Here, physical characteristics are crucial for the e?ciency of computation. We need a clean silicon crystal, sliced into so-called _wafers_, of thickness 1 mm or less. On that, the transistors building up the whole circuit are placed.

## Miniaturization  
  
The computing efficiency of an integrated circuit depends essentially on two factors: the number of transistors, and their execution speed. In both cases, the key for success is miniaturization: on one hand, it allows fitting more transistors in a given space; on the other hand, (as we explain on the lecture "Integrated circuits") smaller transistors need less time to propagate the electric signal, which allows a higher system clock frequency. The need for miniaturizing is even larger given that - sadly - the current technological limitations only allow a single layer of transistors placed directly on the silicon wafers. (If we could place them in multiple layers, we would clearly at much more of them inside a typical computer).  
  
At this moment, typical transistor diameters are a few or a dozen nanometers (where 1 nm =
10−9 m). For comparison, that is about 1 over 10,000 of the thickness of a human hair. This already
allows building huge integrated circuits: one of the most powerful processors currently, NVIDIA
H100, contains around 80 billion transistors.
Looking at the history, since the 1960's, shrinking transistors ? and, accordingly, increasing their
number in currently available computer models ? has been the key factor for the growing trend
in computer e?ciency, and has been behaving exponentially, in compliance with the empirical
Moore's law (which we already described in the lecture ?Introduction?): ?qthe number of transistors
double around every 2 years?. In these years, however, we seem to be approaching an important
technological barrier, where transistors get nearly as tiny as single atoms! (For example, we already
have the technology to produce transistors of diameter 2 nm and thickness 0.3 nm; the smaller of
these numbers is the size of single carbon atom).
Hence, it seems increasingly more possible that, in a dozen of years, Moore's law may stop describing
reality, and the actual growth of computers' e?ciency will signi?cantly slow down comparing to its
predictions. On the other hand, we cannot make such claims for certain, e.g. due to a possibility of
technologic developments in other directions than miniaturization (potential multi-layer circuits, or
e.g. quantum computing).



