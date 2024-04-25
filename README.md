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
  




































### Processor

The [processor ]{.calibre4}is the central brain of a computer ---
accepting and executing orders regarding performing computations and
transferring data. Initially, this term used to be synonymous
with [central processing unit ]{.calibre4}(CPU) --- however, once the
[multi-core processors ]{.calibre4}have appeared, we reached a situation
where computations in a standard computer are handled by a set a few (or
more in some super-computers) internally connected CPUs, which are now
collectively called a [processor.]{.calibre4}

![](./main-4.jpg)

Figure 4 shows a general structure model of a CPU, indicating a few
basic functional modules. That model, at least roughly, has been
followed during the technological development of CPUs over the last 50
years. At the same time, keep in mind that the actual physical structure
of contemporary CPUs is much more complex, and falls outside the scope
of this lecture. For example, Figure 5 shows a bit more detailed
structure of a modern CPU (of Intel Skylake family), though even that
picture is still largely simplified (for example, in omitting some
subcomponents belonging to the MMU),

Below, we will describe the basic processor modules according to the
general picture (shown in Figure 4).

![](./main-5.jpg)

#### Execution unit

A key component on the scheme is the [execution unit ]{.calibre4}(EU),
in which all the computations take place. The [arithmetic-logic unit
]{.calibre4}(ALU) deals with computations on integer numbers
(encoded with "0\"s and "l"s as explained on the previous lectures),
both arithmetic and logic ones. To reduce the load on ALU, the most
complex operations on the fractional numbers (also called
[floating-point. ]{.calibre5}due to the elasticity of the IEEE encoding)
are performed in a specialized unit, called [floating-point unit
]{.calibre4}(FPU), That unit is also used for computations on vectors
(about which you'll learn more on a linear algebra course).

To be able to store data, intermediate results, or addresses necessary
in ongoing computations, we also need processor [registers,
]{.calibre4}i.e, small-size memory cells.

#### []{#main-3.xhtml#bookmark2}Other components {.calibre14}

The whole space of the other components (i.e, not included in the EU)
used to be collectively named the [control unit ]{.calibre4}(CU), though
in recent years this term seems to have been less used --- possibly due
to rapid development of this part of the processor and its expanding
scope of responsibility.

Anyway, in this part of the processor, there is the [decoder
]{.calibre4}(also known as [instruction unit,]{.calibre5} UI), which
deals with fetching [orders ]{.calibre4}(or: [instructions)]{.calibre5}
from the memory and executing them, which may involve requesting a
particular ALU computation, fetching data from RAM, sending some data to
RAM etc.

For the decoder to obtain the necessary information from the memory,
it's necessary to do some computations on memory addresses, which is the
role of the [address unit ]{.calibre4}(AU), Here, as the memory design
gradually developed and grew in complexity, in particular due to
introduction of [memory virtualization]{.calibre5} (which will be
discussed in a later lecture), computers have been equipped with
another, more complex [memory management unit ]{.calibre4}(MMU),

On the way between the processor and "main" memory, we can see the
intermediate memory, called [cache. ]{.calibre4}The reason for its
existence lies in the variety of available types of memory: while the
main RAM is relatively cheap (and hence available in larger amounts),
the in-proeessor memory (registers and cache) is smaller but much faster
to use. That makes it beneficial to keep the most recently fetched
values in the cache, so that they're already "handy" whenever needed
again in the near future. Moreover, introducing more and more types of
memory with various efficiency parameters has led to a constant
development of the idea of cache: the contemporary standard involves
[three levels ]{.calibre4}of cache just for the "ordinary" data fetched
from the main RAM (called LI, L2, L3; each of them being larger and
slower than the previous one), and some additional cache buffers for
data of another kind (e.g, a separate instruction cache).

The last element of Figure 4 is a CPU-internal [ROM ]{.calibre4}module,
used by the decoder when translating incoming processor orders to a
detailed list of [micro-orders]{.calibre5} (see below).

Similarly as in the whole computer, the signals between various
processor subsystems are transferred with internal [buses.]{.calibre4}

#### []{#main-3.xhtml#bookmark3}Orders, machine code and micro-orders {.calibre14}

The processor orders are represented in computer memory in the form of
[machine code, ]{.calibre4}that is, a compact, binary encoding, in which
the kind of the elementary action to be taken (e.g, "add", "subtract",
"fetch from memory" etc.) takes just a few bits of space. That makes it
much more concise than in popular programming languages, but on the
other hand much less legible for a human eye (and that's one of the
reasons why humans practically don't program directly in machine code).
On the other hand, machine code is the only language understood directly
by the processor; programs in all other language are most often
translated to machine code in the process of [compilation.]{.calibre5}

The [instruction set ]{.calibre4}of a processor specified the kinds of
instructions supported by a particular processor model. The modern
processors often support very sophisticated instruction sets, in which a
single order can involve [e.g. ]{.calibre4}executing a few arithmetic
operations combined with communicating with the memory. In such case, we
speak of [micro-orders ]{.calibre4}as the single operations executed in
ALU, or single transfers from/to the memory. Then, one of the
responsibilities of the decoder is translating processor orders to
appropriate sequences of micro-orders.

#### []{#main-3.xhtml#bookmark4}CISC and RISC approaches {.calibre14}

The orders executed by ALU in computers from the 1970's were in an
almost-one-to-one correspondence with the orders used by programmers.
However, a large part (around 80%) of instruction types was rarely used
(they formed only about 20% of executed instructions). In late 1970's,
an idea emerged to decrease the processor instruction set, which would
allow to simplify its structure and hence optimize its performance.

Another idea to improve performance was to reduce the number of memory
references by introducing a large number (hundreds) of registers --- so
that processor orders could operate only on registers, with the
exception of special orders for [loading]{.calibre5}[ ]{.calibre4}values
from memory and [storing]{.calibre5}[ ]{.calibre4}them in the
memory, (Some resemblance to the idea of caching can be seen here,
though in this case, to keep a simple model, the proposal was to just
increase the pool of registers). An additional gain from simplifying the
structure of orders was reaching the situation in which all orders have
the same length in the machine code and take the same number of clock
cycles --- which facilitates optimizing execution of such code (e.g, by
[pipelining]{.calibre5}[ ]{.calibre4}which we will describe in the
lecture "Processor and programs").

The above two ideas form the core assumptions of the [RISC
]{.calibre4}([reduced instruction set computer)
]{.calibre5}architecture. While its potential advantages have been
described above, its main disadvantage turned out to be in reducing the
processor instruction set in a way incompatible with the existing
standards. Since the RISC processors did not support many orders which
have been already usually available in the machine code, running
programs on these processors required changes in how they were
compiled, and keeping efficiency of machine code while using only a
reduced instruction set turned out to be challenging.

As a result --- at least when looking at the supported instruction set
--- the RISC approach is practically absent among laptops, workstations
or servers. On the other hand, it's widely used in some simpler or newer
device classes, such as smartphones, tablets or embedded devices (that's
what you'll find in all sorts of "smart home" appliances). Also, the
fastest super-computers (including the record holder,
[Fugaku)]{.calibre5}[ ]{.calibre4}are often built according to the RISC
architecture.

On the opposite side to RISC, we have the [CISC ]{.calibre4}([complex
instruction set computer)]{.calibre5}[ ]{.calibre4}architecture, in
which the processor supports complex, specialized orders, often
involving combinations of arithmetic operations and multiple memory
access. In this approach, the processor typically has much
less registers, based on the assumption that intensive memory
communication is not a bad thing in the machine code (or, more
precisely, that it'll be [successfuly ]{.calibre4}optimized in practice
by utilizing the caching mechanism).

Most of contemporary personal computers support a rich instruction set
of CICS type; still, they can be also described as following the RISC
approach in terms of their internal structure. The crucial thing here is
the already mentioned mechanism of translating processor orders to finer
microorders, where for simplicity the goal is typically to reduce the
list of supported micro-order types (in the RISC spirit). In extreme
cases, we can even say that an "internal processor" of RISC type
is tasked with executing orders received by the "external processor" of
CISC type, or that a ClSC-style [interface]{.calibre5}[ ]{.calibre4}is
being [emulated ]{.calibre4}by a RlSC-style
[implementation.]{.calibre5}[ ]{.calibre4}In this way, it's sought to
combine the advantages of both approaches, keeping the most internal
structure simple, but at the same time retaining support for a rich set
of instructions allowed in the machine code.

The comparison of both considered models is summarized below.

::: cbj_banner
![](./main-6.jpg){.calibre13}
:::

# Processor and programs  
  
In this lecture, we continue discussing the procesor. This time, however, we will focus less on its hardware structure, and more on managing execution of whole sequences of orders and the most important optimization techniques used there.
  
### Pipelining  
  
#### The idea 

As we said previously, the internal structure of the processor often reflects the RISC approach. We will now discuss, how (very roughly) a processor order is executed in the RISC model. It splits into 5 main phases:

1.    IF (Instruction Fetch): retrieving the next order to be executed (from the instruction cache).

2.    ID (Instruction Decode): This decodes the order, i.e, makes the initial steps to learn the addresses of its arguments, initiates retrieving values of these arguments, and sends the necessary controlling signals.

3.    EX (Execute): The proper computations take place in the ALU.

4.    MA (Memory Access): If necessary, data are read from or saved into RAM.

5.    WB (Write Back): The result of the instruction is stored into the registers.

In case of sequential execution, where one CPU executes at most one order at a time, this would mean that e.g, the instruction decode block would be idle during the work of ALU, and conversely. That's a clear inoptimality, which is typically avoided (since the 1980's) by the technique known as pipelining.

The idea is to simultaneously execute different phases of multiple instructions. In the ideal situation, in each moment the processor would execute the IF, ID, EX, MA and WB phases for 5 consecutive orders:

(./main-7.png)

#### Complications

There are, however, a few reasons for which that may not always succeed. A classic example is when some arithmetic computation order happens directly after another such order A but it on the result of A, i.e. that result is one of the arguments for B. Then, in phase ID (for B) we will need to fetch from the registers a value (the result of A) which would be only stored that later, namely, in phase WB for A!

The simplest way of dealing with such case is to simply introduce a delay. Then, the execution can look e.g. like this:

![](./main-8.jpg)

Clock cycles

Figure 2. The simplest solution of a data hazard --- by introducing a large delay.

Situations leading to such delays are called hazards. Generally, they split into 3 kinds:

* Data hazard --- an order needs data which are not yet ready.
  
* Control hazard --- when executing a jump order, the processor may not be able to determine which order is going to be executed as the next one.

This problem is evident for a [conditional jump,]{.calibre5}[
]{.calibre4}when the choice of the next order can depend on some
computation yet to be finished. However, it can occur also for an
[unconditional jump. ]{.calibre5}as long as the instruction set of the
particular processor exposes an order of the kind "jump to the
instruction lying at the address which is currently stored in register
[X\" ]{.calibre4}--- in such case, even though the occurrence of a jump
is predictable, the processor still needs to do additional work to check
the current value of the register [X.]{.calibre4}

[•    Structural hazard ]{.calibre4}--- simultaneous execution of
different phases of different orders may still require using the same
resources.

This can happen e.g. when orders involve floating-point computations,
for which phase [EX ]{.calibre4}takes much longer than for typical
processor orders.

As we already mentioned, a possible solution --- applicable to each of
these cases --- is to delay executing the later of the "conflicting"
orders (and, consequently, all the following ones). However, abusing
that strategy leads to a significant decrease in overall processor
efficiency, so --- if only possible --- the processor designers tend to
avoid it.

Therefore, other strategies of resolving hazards have been developed:

• For data hazards, a common technique is [forwarding ]{.calibre4}(also
called [bypassing).]{.calibre5}

Note that, in the previously described example, at the time when the
order [B ]{.calibre4}[actually needs ]{.calibre5}the computation
arguments delivered to the ALU (i.e. at the beginning of its phase [EX),
]{.calibre4}[we\'re. already after]{.calibre5}[ ]{.calibre4}the actual
computation of the result of [A ]{.calibre4}(in its phase [EX).
]{.calibre4}What hasn't happened yet is storing that result into the
target register for [A ]{.calibre4}(in its phase [WB), ]{.calibre4}or
retrieving that value back for the purposes of [B ]{.calibre4}(in its
phase [ID) ]{.calibre4}--- however, in this case, what we really need
is just sending the output of ALU back to the input of ALU, which can be
done more efficiently without intermediate registers.

Hence: rather than wait, we pass the necessary value
[directly:]{.calibre5} from the output of ALU to its input (that is,
from phase [EX ]{.calibre4}of [A ]{.calibre4}to phase [EX ]{.calibre4}of
[B), ]{.calibre4}To be able to do this, we need a special physical
connection (a "bypass\") in the processor.

::: cbj_banner
::: cbj_banner
![](./main-9.jpg){.calibre13}
:::
:::

• For control hazards, one can use [speculative execution:
]{.calibre4}the processor [guesses]{.calibre5} which branch will run,
and starts executing the order according to its guess.

Such predictions can be made e.g, based on the history (through
remembering whether the previous executions of this particular order ---
if any happened so far --- had led to a jump or not). If such history is
unavailable, the processor can e.g, guess that a jump will happen if it
leads "backwards\" in the code, but not if "forwards\". It\'s estimated
that these kinds of predictions have ea. 90% of accuracy. Unfortunately,
a wrong guess leads to a delay. Therefore, if possible, another
technique (see below) is used.

::: cbj_banner
::: cbj_banner
![](./main-10.jpg){.calibre13}
:::
:::

![](./main-11.jpg)

![](./main-12.jpg

![](./main-13.jpg)


Figure 4. A comparison of resolving a control hazard with two
techniques: delay (upper row) vs. speculative execution (lower row).

In the above example, the order B is a conditional jump to order E: the
processor learns whether this jump should happen in the processor in
phase ID of order B.

•    In the variant using delay, executing the subsequent order (either
C or E) always begins in clock cycle 4.

•    When using speculative execution, the processor, when in phase IF
for order B, recognizes a conditional jump instruction and assumes the
condition will turn out to be true, thus planning order E to be executed
next.

If the jump should indeed happen (the left column), the execution of E
(and also its successor, F) can proceed without complications. If,
however, the decision to make a jump turns out to be wrong (the right
column), we cancel execution of E (here, again, some form of a physical
bypass is needed), and schedule execution of order C instead. Note that,
in this case, the slot consisting of cycles 3 7 has been "wasted", so
the efficiency remains the same as for the "delay" strategy.

• For hazards of all types, one can use the technique of [out-of-order
execution, ]{.calibre4}which means executing orders in a
[different]{.calibre5}[ ]{.calibre4}order than that resulting from their
placement in the machine code.

In the simplest version, the processor is equipped with ability to
detect [dependencies]{.calibre5}[ ]{.calibre4}between orders (such that
lead to hazards), as well as to detect neighboring pairs of [completely
independent]{.calibre5}[ ]{.calibre4}orders (i.e. such that neither of
them modifies registers read or written by the other one). The key fact
here is that, among a pair of [completely independent]{.calibre5}[
]{.calibre4}orders, we can choose [arbitrary]{.calibre5}[
]{.calibre4}order of executing them, without affecting the result of the
whole code --- and a smart choice of that may allow avoiding some hazard
(see example on Figure 5).

::: cbj_banner
![](./main-14.jpg){.calibre13}

Figure 5. Resolving a control hazard (same as in Figure 4) with
out-of-order execution. This time, the processor "notices" that
instructions A and B are [completely independent,]{.calibre5} so they
can be executed in any order: moreover, by running A directly after a
conditional jump B, we gain time for deciding whether to make the jump.
This removes the need for guessing, and also the threat of wasting a
cycle in case of a wrong guess. Thanks to this, in the second variant,
execution is faster by 1 cycle comparing to Figure 4.
:::

Of course, that kind of "perceptivity\" of a processor requires it to do
more computations and have a more complex structure; still, this kind of
computations are simpler than these done e.g. in the ALU, which led the
RISC processor designers to incorporate this technique into
the processor (rather than leave it as a responsibility of compilers).

• As for structural hazards, in the pipelining setting described so far
these hazards are least important; they will become a larger problem in
processors using more optimization techniques which we\'ll describe
below. There, the main ways of dealing with them will be to increase
the number of registers and/or the data transmission bandwidth.

Of course, the methods for resolving hazards which we described above
require support from the processor, which means more complexity in its
structure and more computations to do.

[]{#main-5.xhtml}

### []{#main-5.xhtml#bookmark0 .calibre8}Parallelism and concurrency {.calibre12}

#### []{#main-5.xhtml#bookmark1}Parallel computing {.calibre14}

The Pentium P5 processor (from 1993) was the first broadly used
[superscalar processor, ]{.calibre4}i.e. one performing multiple orders
simultaneously thanks to using multiple execution units. Since 1998,
this approach has become standard in processor design. This means that,
currently, executing processor orders looks as follows:

::: cbj_banner
![](./main-15.png){.calibre13}
:::

Multiplication can be also applied not to whole execution units, but
just the ALU or FPU units.

The situation in which the computer performs multiple tasks
[simultaneously]{.calibre5} is generally named [parallel computing.
]{.calibre4}Although the already mentioned pipelining can be treated as
a special case of parallel computing, it is an example of limited
parallelism (due to the rule that no two different orders can have the
same phase executed at one time). This limitation had various effects:
on one side, it limited the efficiency gain (to 5x at most); on the
other hand, it allowed avoiding various types of potential hazards. For
example, once we allow simultaneous execution of phase MA for multiple
instructions, we face potential conflicts in accessing the RAM memory.

::: cbj_banner
![](./main-16.jpg){.calibre13}
:::

are equivalent in terms of their desired effect; however, they differ in
that the version on the left contains a hazard (regarding variable a),
while the version on the right is free from it.

In most cases, such optimizations are made already by the compilers, and
the programmers are not forced to make such analyses on their own. In
addition, (particularly when various orders may take different amounts
of time to complete) avoiding hazards may require using additional
registers. The consequence is a growing number of registers in
processors.

#### []{#main-5.xhtml#bookmark2}Scheduling processes and concurrency {.calibre14}

Speaking of running many programs at one time, it\'s worth mentioning
the concept of processes.

A [process ]{.calibre4}is --- simplifying a bit --- a running instance
of a program. For example, when we write a program in Java (or any other
language) printing "Hello World", running that program will
typically result in creating a new process. Such process will need
access to various resources: processor, memory, I/O devices etc. For
now, we focus on the processor. Our "Hello World" program will not be
the only process running on the computer at that time: next to it, the
user may be running e.g, a web browser, sound player, word processor
etc. Moreover, the operating system would be also running as a process,
though a [priviledged]{.calibre5} one, in charge of managing other
processes and [scheduling ]{.calibre5}resource access for them.

If the number of running processes stayed below the number of available
CPUs, we could hope for full parallelism. However, the practice is very
different (for example, while writing these words, on a 4-core laptop, I
have about 340 processes running). This means that one of the resources
for which the processes compete is the [processor access, ]{.calibre4}or
in other words, the right to execute orders. The operating system may
--- at almost any time --- take this right away from any user
process (which is called [preempting ]{.calibre4}that process). The
preempted process then becomes [suspended ]{.calibre4}and awaits being
woken up again, which will allow it to continue executing. This, of
course, requires the operating system and the processor to store the
whole relevant [process context, ]{.calibre4}so that --- from the
viewpoint of the temporary suspended process --- nothing would have
changed once it's woken up.

The above scheme of [scheduling processes ]{.calibre4}existed in
operating systems even back in the times of single-core processors,
before the advent of real parallelism. Even in the early 1990's,
systems like MS Windows exposed an [illusion]{.calibre5} of running
multiple programs [at once]{.calibre5} (while in fact various programs
were granted processor access in short [interlacing]{.calibre5} time
intervals). The situation in which interlacing various processes leads
to an [apparent]{.calibre5} simultaneity of execution is called
[concurrency. ]{.calibre4}This effect can be observed in modern
computers at all times, regardless of the number of available cores, and
it involves similar hazards as for real parallelism.

#### []{#main-5.xhtml#bookmark3}Interrupts {.calibre14}

On the processor level, scheduling processes is enabled by [interrupts
]{.calibre4}--- special signals which the processor can receive, leading
to suspending the currently running process and --- instead ---
invoking a designated [interrupt handler ]{.calibre4}routine.

Interrupts can occur for various reasons, including:

•    a signal from an input/output device

(E.g, a keyboard key press, a mouse move, but also arrival of a network
packet)

•    a clock signal

(Of course, not every one! However, by using appropriate cycle counters
in the processor, the operating system can "set up a timer" for a
specific timestamp --- this happens e.g, when, in any programming
language, we use an instruction of the type "sleep for 1 second")

•    various kinds of errors while executing processor orders

(A simple example of that is division by zero, A more sophisticated
example, though fundamental for how modern computers work, is a "failure
in finding the requested fragment" in RAM memory, due to the so-called
[virtual memory]{.calibre5} being used --- which we will describe
in more detail on a later lecture)

The procedures following an interrupt are quite complex and will not be
described here in detail. Let us just remark that the handler for a
clock interrupt involves passing control to the operating system ---
which then has an option of analyzing the history of execution of
various processes, and choosing the process (es) which should be now
given processor access.

Some other types of interrupts (including division by zero) do not
require an intervention of the operating system; moreover, the user
process has sometimes a possibility to define a custom interrupt
handler, after completing which, the processor may (depending on the
interrupt type):

•    terminate the process which has been interrupted;

•    resume that process, starting from the instruction which has been
interrupted;

•    resume that process, starting from the instruction following the
one which has been interrupted.

This mechanism is a low-level analogue (and sometimes --- e.g, for
division by zero --- also the technical foundation) of what is known in
higher-level languages as [exception handling]{.calibre5}: "if in
this area of the code a division by zero occurs, take action X", A
particularly important application is [debugging-,]{.calibre5} if e.g, a
program attempts to refer to an unavailable segment of memory, handling
of the resulting interrupt may include --- before the termination of the
faulty process --- printing out the content of registers (and, with
support from a higher-level language compiler, also variables),
which can significantly aid in diagnosing the error.

#### []{#main-5.xhtml#bookmark4}Relevance for the programmer {.calibre14}

Finally, let us remark that, while pipelining is built so deeply into
RISC processors that it's essentially "invisible" even for assembler
programmers, the topics described above can influence the way of writing
programs significantly, even in higher-level languages.

The leading languages (C/C++, Java, Python) allow parallelizing a
program or at least making it concurrent --- by explicit creation of
additional processes (or so-called threads) --- which can decisively
improve their efficiency, particularly when intensive computations are
involved. There are two main reasons for this:

•    Even on a superscalar machine, an "ordinary" program
(single-process, single-threaded) will by default execute only one core
at a time. Therefore, in such case, it pays off to
[parallelize]{.calibre5} its execution to multiple CPUs,

•    Independently of the above, if our program contains some
computations as well as some blocking operations (e.g, fetching data
from the network, accessing some slow type of memory, awaiting input
from the user etc,), just making it [concurrent]{.calibre5} can allow
executing some actions during the time when other ones are blocked,
(Operating systems and processors are designed to maximize that kind of
gains: for example, whenever a thread begins awaiting data from
the network or from the keyboard, it gets preempted instantly, to let
another unblocked thread execute as soon as possible).

The topic of interrupts, while fundamental for how modern computers
work, is relatively less important for most programmers, (Interrupt
handling is technically available only in assemblers and some relatively
low-level programming languages like C/C++, and even there it's
exploited rarely, which is due to the involved complexity, as well as
availability of higher-level mechanisms like signals and programming
exceptions).

#### []{#main-5.xhtml#bookmark5}Limitations: Amdahl's law {.calibre14}

Unfortunately, usually the code contains some portions which must be
executed sequentially. For example, the sequence of instructions a = 2;
b = a; cannot be parallelized as the result of the second instruction
depends on the first one. The amount of code which is not parallelizable
depends on the kind of problem solved by the code,

Amdahl's law introduces a limitation on the acceleration of a program
achievable by running it on N processors. If the whole code
[was]{.calibre5} parallelizable, then (assuming an ideal hardware
support) the program could be accelerated by N times. Now, however,
consider a more realistic situation when only P% of the computations can
be done in parallel, (By [P]{.calibre5}% [of the
computations]{.calibre5} we mean here computations which take P% of time
of the total program executing time). This means that:

• (100 --- P)% of the code will run sequentially, and hence will take
(100 --- P)% of the original running time of the whole program;

•    P% of the code may be executed in parallel, and hence that part
will take --- in the perfect case --- Np% of the original running time
of the whole program.

As a result, a program executed on N processors will be accelerated [at
most]{.calibre5} by the following number of times:

100

100 - P + Np \'

For example, if we can use 4 processors, and 10% of the computations
must be sequential, than the [maximal]{.calibre5} possible factor of
acceleration will be:

::: cbj_banner
![](./main-17.png){.calibre13}
:::

Therefore, if running such a program fully sequentially took 10 seconds,
then there is no chance on 4 processors to run it in less than 3
seconds. Moreover, even if we had arbitrarily many processors, and a
computer architecture which allows no overheads related to concurrency,
we still won't be able to get below 1 second.

[]{#main-6.xhtml}

### []{#main-6.xhtml#bookmark0 .calibre8}Landscape of registers {.calibre12}

Registers are a crucial part of the processor, storing all the arguments
and results of computations. As processors evolved, they started
including registers of various sizes, purpose, and even access mode. We
will now discuss in more detail the landscape of registers in the
processors whose architecture is said to belong to the x86 family (which
includes the currently most popular processors in personal computers,
including Intel and AMD),

#### []{#main-6.xhtml#bookmark1}Availability to the programmer {.calibre14}

In most programming languages, the programmer does not (and often even
cannot) deal with controlling values in specific registers.

When using the leading higher-level languages (e.g, Java, C, C++ etc,),
we almost always work with more abstract [variables]{.calibre5}, and do
not have to care about where and how their values would be stored in the
processor, (Such details are typically responsibility of a compiler,
translating our program to machine code understood by the processor).

Still, it may happen that we exceptionally care about performance (e.g,
when writing some device driver), or that it\'s us who writes that
compiler --- then, we use languages of lower level, called [assemblers,
]{.calibre4}which are much closer to the machine code. Assemblers will
be discussed in more detail on a later lecture; for now, the important
thing is that [assemblers ]{.calibre4}give the programmer [direct access
]{.calibre4}to specific registers (though, as we\'ll see in a moment,
not to all of them).

#### []{#main-6.xhtml#bookmark2}Register types in the x86 architecture {.calibre14}

[General purpose registers]{.calibre4}

The most frequently used class of registers are the [general purpose
registers, ]{.calibre4}which can store data, as well as addresses of RAM
memory cells from which the data should be fetched (or to which should
be sent).

In the x86 family, these look as follows:

::: cbj_banner
![](./main-18.jpg){.calibre13}
:::

\*AX --- used in arithmetic operations

\*BX --- used as a pointer to data (located in segment register DS, when
in segmented mode)

\*CX --- used in shift/rotate instructions and loops

\*DX --- used in arithmetic operations and I/O operations

\*SP --- pointer to the top of the stack

\*BP --- used to point to the base of the stack

\*SI --- used as a pointer to a source in stream operations

\*DI --- used as a pointer to a destination in stream operations

Figure 7. The general purpose registers in the x86 architecture.

(Role descriptions taken from: https
://en.wikibooks.org/wiki/X86_Assembly/X86_Architecture)

In this picture, directly neighboring rows do not represent separate
memory but just another way of viewing the same memory. For example, EAX
is physically [a part of ]{.calibre4}RAX, consisting of its 32 [lower
]{.calibre4}(or: [younger)]{.calibre5} bits. Similarly, AX is the lower
half of EAX, AH and AL are respectively the higher [(H)]{.calibre5} and
lower [(L)]{.calibre5} halves of AX, EDI is the lower half of RDI, etc.

These half-divisions exist for historical reasons: in the older times,
the only available registers were shorter than 64 bits. By keeping them,
we achieve backwards compatibility, i.e, the ability to execute programs
which were compiled for an older architecture (in which the machine code
could [e.g. ]{.calibre4}refer to the register [CX ]{.calibre4}and, even
more importantly, could [assume]{.calibre5} that [CX ]{.calibre4}is
16-bit long).

While the above registers can be read and written by machine code (and
thus also by an assembler programmer), they can also --- depending on
the context --- play an additional role (according to the description in
Figure 7), which means that the programmer may need to care for ensuring
their proper content. This involves in particular the second row of
registers [(\*SP, ]{.calibre4}\*BP, \*DI, \*SI), which basically deal
with addresses. For example, \*SP and \*BP store pointers, respectively,
to the top and the base of the [stack]{.calibre5}, which is a fragment
of RAM memory used by the processor in a way analogous to how a stack
machine (described on the lecture "Introduction") works.

[Other registers]{.calibre4}

Besides the abovementioned registers, the processor contains also other
ones, with more specialized purposes, involving storing data
[or]{.calibre5} addresses. These include, for example:

[•    segment registers, ]{.calibre4}storing the memory location of the
[code segment]{.calibre5} for the currently executed program [(CS),
]{.calibre4}or of several [data segments]{.calibre5} [(DS, ES
]{.calibre4}etc,);

•    pojfloating point registers, used in FPU computations;

•    even more specialized registers (e.g, the processors supporting
AVX-512 model, from 2016, offer 512-bit [vector registers).]{.calibre4}

Clearly, registers store numbers in the formats described on previous
lectures (e.g, IEEE-754), During arithmetic operations, we can encounter
an [overflow,]{.calibre5} i.e, a result which does not fit into the
target register. Such situation will be communicated by the processor by
setting the value of an [appropriate]{.calibre5} bit in the [flags
register (RFLAGS/EFLAGS), ]{.calibre4}Analogously, other bits in that
register play the role of [flags: ]{.calibre4}some of them inform about
the most recent operation, some others e.g, about the processor
operating mode (see below in this lecture). Also in this case ---just
like the processor technically exposes [AH, AL ]{.calibre4}etc, as
physical parts of [RAX ]{.calibre4}--- the individual bits of the flags
register are available in x86 as separate registers (e.g, the overflow
flag is named [CF),]{.calibre4}

Another crucial functionality of the processor registers is to control
executing a program. The [instruction pointer (RIP/EIP/IP)
]{.calibre4}stores the address of the next instruction planned for
execution. Typically, after completing each instruction, it is simply
increased by the length of the just-completed instruction (which makes
the processor proceed to the following one); a different scenario may
happen for a jump instruction, (It is exactly the instruction pointer
that determines what is fetched in phase [IF, ]{.calibre4}and setting
the proper value of that register was the actual goal of the techniques
presented in Figures 4 and 5), The instruction pointer, while important
as a part of the processor, is an example of a register that is
[unavailable to the programmer: ]{.calibre4}writing to it (or even
reading its value) directly is prohibited in the assembler.

Summing up, we discussed registers of various kinds: general purpose,
floating point, vector registers, segment registers and special
registers (instruction pointer, flags). That still does not exhaust
all registers available in the processor; however, these are the most
important ones from the user's viewpoint.

[]{#main-7.xhtml}

### []{#main-7.xhtml#bookmark0 .calibre8}Bit-length and operating modes {.calibre12}

As we already saw in Figure 7, address registers can have 64 bits. This
is the standard in modern processors and there are no reasons for it to
change soon.

Until the 2000's, most processors only exposed 32-bit address registers.
This allowed referring to 2^32^ different memory addresses. Assuming
that each address specifies a RAM memory location with 1 byte's
precision, this produced an addressing scheme capable of covering 2^32^
B = 4 GiB --- [way above ]{.calibre5}the typical RAM size in the 1990's,
but [below]{.calibre5} today's standards.

With 64 bits at our disposal, we can address an amount of memory that is
huge even by today's standards: it's 2^64^ B = 16EiB (where 1 EiB =
1,024 PiB = 1,048,576 TiB) while the RAM size in contemporary personal
computers rarely exceeds 32 GiB, Therefore, in practice, currently used
addressing schemes exploit a smaller number of bits, e.g, 40 (which
covers 1 TiB) or, in some processors of AMD64 type, 52 (which covers
4PiB),

Unfortunately, switching the bit-length of processors from 32 to 64
required not only adjusting the internal architecture (registers size,
but also buses, memory etc,), but also sever changes on the software
side. It has caused e.g, development of new, significantly different
versions of operating systems (for example, starting from the XP
version, Microsoft used to prepare [separate]{.calibre5} editions
of Windows for the 32-bit architecture and for the 64-bit architecture;
only Windows 11 (from 2021) is purposed exclusively for the 64-bit
machines). Even more sophisticated applications (like an
internet browser) have separate versions depending on the architecture.
Similarly, input/output device drivers depend on the bit-length.

As suggested by Figure 7, analogous changes of bit-length happened also
earlier: from 8 to 16, and then to 32, The latter of these changes took
place in the early 1990's (and was also forced by the growing size of
available RAM --- even though techniques for addressing more than 2^16^B
= 64kiB were developed, after exceeding a few megabytes they became
insufficient or ineffective). At that point, to ensure backward
compatibility, 3 processor operating modes were introduced:

[•    Real mode ]{.calibre4}--- in which the processor operates in the
same way as an Intel 8086 model (which was introduced to the market in
1978!)

[•    Protected mode ]{.calibre4}--- the default mode for 32-bit processors. It allows using 32-bit address registers and, consequently, using a larger address space than available in the real mode. The name [protected]{.calibre5} reflects the fact that this mode assigns a separate memory area to each process, which is by default unavailable to all other processes. That's a form of processor support for multitasking, as it causes that a faulty program (referring to "foreign" memory locations) will not be able to harm other programs, (Of course, writing viruses is still possible, but it became harder than it used to be in the real mode),  
  
[•    Virtual 8086 mode ]{.calibre4}--- essentially a sub-mode of the protected mode, in which it's possible to run programs written for 16-bit machines. This also simulates the behavior of an Intel 8086 model; however, the differences from the real mode (including e.g, handling input/output ports) make it possible to run multiple processes at once, including both 16-bit and 32-bit ones.  
  
Similarly, the switch from the 32-bit to the 64-bit architecture has led to creating 2 more operating modes (each with some sub-types). The details are shown below:

::: cbj_banner
![](./main-19.jpg){.calibre13}
:::

By default, the processor operates in the Long mode, which can support programs written for the 64-bit or 32-bit architectures, or even 16-bit programs (though only those purposed for the protected mode). Programs written for the 16-bit real mode (as well as virtual, though that's a rare case) will not be supported. Even though programs from 1980's are now very seldom used in home applications, the code dating back to those types does still appear inside operating systems, or in some other specialistic applications (e.g, in the numeric computations used by astronomers).
