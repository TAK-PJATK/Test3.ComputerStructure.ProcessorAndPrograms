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
  
The computing efficiency of an integrated circuit depends essentially on two factors: the number of transistors, and their execution speed. In both cases, the key for success is **miniaturization**: on one hand, it allows fitting more transistors in a given space; on the other hand, (as we explain on the lecture "Integrated circuits") smaller transistors need less time to propagate the electric signal, which allows a higher system clock frequency. The need for miniaturizing is even larger given that - sadly - the current technological limitations only allow a **single layer** of transistors placed directly on the silicon wafers. (If we could place them in multiple layers, we would clearly at much more of them inside a typical computer).  
  
At this moment, typical transistor diameters are **a few or a dozen nanometers** (where 1 nm = 10-9 m). For comparison, that is about 1 over 10,000 of the thickness of a human hair. This already allows building huge integrated circuits: one of the most powerful processors currently, NVIDIA H100, contains around 80 billion transistors.  
  
Looking at the history, since the 1960’s, shrinking transistors — and, accordingly, increasing their number in currently available computer models — has been the **key factor** for the growing trend in computer efficiency, and has been behaving **exponentially**, in compliance with the empirical **Moore’s law** (which we already described in the lecture “Introduction”): “the number of transistors double around every 2 years”. In these years, however, we seem to be approaching an important technological **barrier**, where transistors get nearly as tiny as single atoms! (For example, we already have the technology to produce transistors of diameter 2nm and thickness 0,3 nm; the smaller of these numbers is the size of single carbon atom).  
  
Hence, it seems increasingly more possible that, in a dozen of years, Moore’s law may stop describing reality, and the actual growth of computers’ efficiency will significantly slow down comparing to its predictions. On the other hand, we cannot make such claims for certain, e.g, due to a possibility of technologic developments in other directions than miniaturization (potential multi-layer circuits, or e.g, quantum computing).

## This area is complex  
  
Starting from this lecture, we’ll deal almost entirely with digital circuits containing many thousands of logic gates. These are called VLSI circuits (_very large scale of integration_). (One can also speak of small scale up to 10 gates, medium 10-100 gates, and large up to a few thousand). This means that, speaking of circuit structure and related technology, we will omit many details.  
  
These details can be extremely important, as shown by recently introduced US sanctions on transferring technologies and certain kinds of integrated circuits (in particular, NVIDIA H100) to China, On the other hand, the importance (and complexity) of effectively producing even relatively simple circuits has been demonstrated by their market shortages due to supply chain issues during the Covid-19 epidemic.  

## General structure of a computer  
  
We will now present a simplified model of a computer which will not touch e.g, the following aspects:
* performing computations outside the processor  
* classification of input/output devices  
* multi-core computing
  
The simplest scheme of computer structure may look as follows:  

![Figure 2. The general structure of a computer.](https://github.com/TAK-PJATK/Test3.ComputerStructure.ProcessorAndPrograms/blob/main/TheGeneralStructureofacomputer.PNG?raw=true)   
Figure 2. The general structure of a computer.  
  
### Processor  
The heart of a computer is the processor — an integrated circuit
containing an astronomical number of transistors (together with its
cover), performing arithmetic and logic computations based on
the specified program. We will describe its structure in more detail in
another section below.  
  
### Memory  
The computer memory comprises of all integrated circuits and other
devices which allow storing information.
Some amount of memory can be found inside the processor, which
allows storing the most relevant temporary results “handy”, and thus
speeds up computations, (Specifically, that consists of
processor regsiters and cache). However, that in-proeessor memory is
limited to relatively small amount, connected with current
computations, while in most applications we need to store much more
data (giga- or even terabytes) for a longer time — think of hours or
even years. Therefore, a necessary component of a modern computer
structure is memory which is separate from the processor
(whose examples are: RAM, hard drives, USB drives, CD/DVD disks
etc,),
A deeper discussion of memory, its types and ways of functioning will
appear on a later lecture. For now, let us remark a fundamental split
(from the viewpoint of functionality and meaning for the general
computer structure) of memory into two kinds:
• Read-only memory (ROM) stores data which are not going to
change, e.g, the startup routines for the computer.
This type of memory does not require constant supply of electric power.
It’s programmed once for all, during manufacturing process, (Note
though that the “ROM” term happens also to be used in a broader
meaning, and does not always necessarily imply actually being “read-
only”),
• Random access memory (RAM) stores the data, programs, and
work results, allowing multiple modifications at later times.
It’s usually much larger than ROM, and requires electric power to
preserve the information (in relation to how we described registers in
the lecture “Integrated circuits”).
For evaluating memory types, the important properties are: speed,
capacity, and (as always in life) production costs. Sadly, it’s hard in
practice to optimize all these properties at the same time. Therefore,
computers often contain various types of RAM, We will describe this in
more detail in the future. Here, we’ll only mention a split of RAM into
two kinds: static RAM (SRAM) and dynamic RAM (DRAM),
DRAM requires refreshing (to prevent discharging capacitors from which
it is built), by periodical write operations of the already saved values.
That makes them slower than SRAM which needs no such refreshing.
On the other hand, DRAM cells consist of less elements, which allows
cheaper manufacturing and hence larger capacity. Therefore, most
memory dices are DRAM, SRAM is also used in computers: mostly in
those places where the speed of reading and writing is crucial, while
the amount of data is small enough to make the increased price
affordable (e.g, inside the processor).

### Other components  
  
The input/output devices (also called I/O devices, or peripherals) allow communication between the machine and the user. These include e.g, keyboard, mouse, screen, but also the network card. So, these are not just the “devices connected via USB or other ports” — they can also be physically located inside the computer box, or even be integrated with the motherboard.   
  
The device controllers are complex specialized integrated circuits which allow handling information travelling to and from input/output devices. This means that e.g, processing images or sound happens, in a large part, outside the computer processor but in the controller of the appropriate I/O device.  
  
The system clock is an electronic device which sends an electric signal
regularly switching its value between “0” and “1”, This allows
synchronization of data processing in the computer (the importance of
which we already mentioned in the lecture “Integrated circuits”).
The buses are purposed to transfer signals between the various devices
mentioned above. We distinguish three kinds of these:
• data buses which transfer the actual data;
• control buses which send signals controlling the data transfer (e.g,
announcing whether a write or read operation will happen; specifying
the amount of data to be transfered; acknowledging receiving data
successfully; also interruption signals);
this type of buses is also responsible for propagating the system clock
signal;
• address buses which send information about where data should be
stored to / read from.
To increase the throughput, data transfer via the buses may happen in
parallel, along multiple channels and in both directions at the same
time (in ease of full duplex buses). Still, the propagation time is one of
the bottlenecks for computer efficiency. That’s one of the reason for
which the recent evolution of computer structure tends to incorporate
more subsystems into the processor.
Harvard architecture
In the above diagram and description, we have not introduced a
distinction between data memory and instruction memory. The lack
of such distinction is postulated by the so-called von Neumann’s
architecture — a model developed by John von Neumann, John W,
Mauehlv, and John
Presper Eckert in 1945, This unification of memory is the main
difference between that model and the competing idea, called Harvard
architecture. In the Harvard architecture, the basic scheme looks as
follows:




An advantage of the Harvard architecture is its speed, as it fosters simultaneous fetching of instructions and data. Its disadvantage, though, is a need for separate buses, and a much more convoluted support for user-provided programs. In effect, this architecture is mostly used in devices running algorithms that have been hard-coded at the manufacturing stage. The main examples are digital signal processors (used e.g, for processing sound in mobile technology) or micro- controllers (used to drive electronic devices).  
  
Although the structure of typical modern computer (see Figure 2) essentially does not follow the Harvard model, we can still find its influence in some places. As already mentioned, a small fraction of memory is placed inside the processor (to reduce the data transmission time). In some parts of that memory, the split between instruction memory and data memory is applied.  
  


