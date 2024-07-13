---
layout: page
title: JeffOS
description: JeffOS, an interactive and educational virtual CPU and OS environment!
img: assets/img/jeff_os.png
importance: 1
category: Python
related_publications: false
---

#### Source code

<a href="https://github.com/GeoffreyKarnbach/JeffOS">Go to the GitHub repository!</a>

#### Description
This project simulates a processor with its own RAM and ROM (each being a simple array, of different sizes, RAM with 1024 int fields (1 kInt), ROM with 8192 int field (8 kInt). In order to program the CPU to run operations,
customs programs can be written in an own assembly like language.

For more information on the different commands, take a look at "INSTRUCTIONS".

#### Implementation

On a high level, a new processor is created with an RAM and ROM instance, and the processor is passed to a dispatcher object, that is responsible for scheduling the execution of programs. The programs get run by 
being executed command after command by the dispatcher (a program must be a valid codefile embedded in a process).

#### <u>Component description</u>

##### ROM (more like a harddrive):

Data can be written and read from the ROM, an array of up to 8192 integers, zero'ed at startup. The instructions READ and WRITE can be used to interact with the ROM. Right now, the main usage of the ROM is to output
into a persistent storage, that doesn't get overwritten by another process if the data would be in the RAM. Furthermore, complex programs could free RAM (lower capacity) by copying the data to the ROM.

Possible improvements:
- Add overhead to perform IO operations (read / write) on ROM, to emulate actual latencies
- Persist ROM across program restarts into a file, saved on the machine

##### RAM (Random-Access Memory)

Similat to ROM, data can be written and read to and from the RAM. The RAM is implemented as an array of 1024 integers. Each position can be freely accessed using the LOAD and STORE instructions.

##### Semaphore (Synchronisation)

In order to be able to perform critical computations in a multi-cored system, semaphores can be used. By owning a semaphore, a process can ensure, that no other process can at the same time access resources guarded
by the given semaphore.

Each semaphore object has a value and a queue of waiting processes. If a process requests the semaphore (WAIT), the process reduces the semaphore by 1 and if it is equal to 0, it can proceed. If the value of the semaphore
now is smaller than 0, the process is blocked and added to the queue. The process automatically gets added to a blocked Queue in the dispatcher, to avoid useless Processor Computation Time Allocation.

When a process frees a semaphore (POST), its value is increased by 1 and the next process in the queue is removed from the blocked queue, therefore again being available to be picked by the dispatcher for further processor
time allocation.

The semaphores are managed directly by the processor object and stored in a dictionnary (to avoid two semaphores with the same name referencing different objects => this could lead to race conditions, as the semaphores
would not guard the access to certain resouces effectively anymore). Semaphores can be controlled using the INIT, SEMWAIT and SEMPOST instructions.

##### Process (represents a process around a codefile containing a sequence of instructions)

As commonly known in Operating Systems, processes are programs in execution. In our case, we manage the register backups from the CPU if the process is not currently active, we manage which line in the code is currently
executed and much more. Furthermore, any instruction is run through the process by calling the corresponding function in the processor (that emulates a CPU).

##### Processor (a simple CPU emulation)

In our small ecosystem, we have a processor that has 8 registers (from "A" to "H"). Furthermore, two flags can be enabled, the "Z" flag if the result of the previous operation was equal to the numerical value 0, or the
"N" flag, if the result of the previous operation was a negative value. Those flags are either set to true or false, while the registers can all take an integer as value.

Any instruction that a process runs from the program file is run on the processor, by calling its corresponding function on the processor object. Those functions directly address the registers, flags and the RAM/ROM or
semaphore objects, if they are used by the current instruction. Furthermore, the processor can import and export its register, therefore allowing a process to load the current status of the processor before the processor
for instance switched to another process (having other values for each register).

##### Dispatcher (the core of JeffOS)

The dispatcher controls which processes are currently active, blocked (for instance waiting for a sempahore) or suspended. Right now, processed are run one after another, depending on the order that they got added to the
dispatcher. To allow multiple processed to run "simultanously" or to simulate parallel execution, different scheduling algorithms could be implemented (Round Robin for instance)

The Dispatcher is the component, that could be expanded the most, as for now, programs are just run sequentially, one after another, without switching between processed.

<br>

#### Instructions / Program files

To control the processor, different instructions are available, each being described in the "INSTRUCTIONS" file.

#### Concrete example

A simple program, located in "Programs/ProgramD" is available to compute the n-th Fibonacci value. To do so, the user has to preload the value of n into the first (0-th) position of the ROM. This valus is read at the
beginning of the program execution. The result of the program is written in ROM position 1023.

The ROM is always printed to STDOUT once no more programs have to be run (see \__init__.py)

#### Run it yourself

In order to run the JeffOS simulation yourself, start by cloning the repository, and writing your own program (for instance in the "/Programs" directory. To execute the program, add it (remove for instance the ProgramD)
in the init file, and wait for the program to finish executing. The ROM will be printed out to STDOUT, allowing you to take a glance at the output of your program (as long as you use the WRITE instruction at some point).

#### Further work

The project could be greatly enhanced by adding further instructions, coming closer to typical assembly instructions for instance available in RISC systems (for instance take a look at https://marks.page/riscv/).
Furthermore implementing scheduling algorithms with different strategies, as well as short/mid/long term scheduling, would allow for different programs to run in "parallel" (or at least not sequential but each for a
number of instructions before the dispatcher sets another process as the active process and allows it to run some instructions itself).

Feel free to create a Pull Request if you want to contribute, or to report any issues by creating a new Issue.

DISCLAIMER: This project was coded quickly and was not thoroughly tested. It was intended as a fun project to apply in a more practical context some concepts I learned in an Operating Systems class at TU Vienna.