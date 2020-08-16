# Terminology
|  Terms   | Their meaning                                                                     |
| :------: | :-------------------------------------------------------------------------------- |
|   MCU    | **M**icro **C**ontroller **U**nit,                                                |
| Debugger | A tool to examine the cause of error in computer program testing and maintenance. |

# Development environment for embedded

`{'mod':'speak'}` There is no fit-all-size tool for handling all processes of designing embedded systems because it is a combination of computer **hardware** and **software** intended to interact with the physical world. Tools such as SPICE or Proteus may assist the testing and development of the systems' software. However, they cannot facilitate the testing of the interactions between the system and the physical world. In such a context, the two realities in which an embedded system must function are:

1. The software aspect, where instruction data are loaded onto the MCU and perform the processing the "input" and "output" of digitalised data.
2. The hardware aspect is where the embedded system shall sense and react to the dynamics of the physical environment. The stimuli of these dynamics may be created by their actions or from the external physical environment.

In general, it is more difficult to build software for embedded systems than other software that runs on a PC. The testing of embedded system software involves the state of the physical world for which the system interacts. Unlike the regime of pure software development where errors can be paused and examined precisely by using a debugger, there is no pause or replay button for objects that live in the physical world. For this reason, a developer of embedded systems must learns to use multiple tools for each aspect of software development and physical world simulations.

## Reasons for using C?

`{'mod':'speak'}` C is a general-purpose computer programming language which can be used in wide variety of applications. Operating systems, application software for computers ranging from supercomputers to embedded systems are written in C. While C has been a versatile programming language, it has been the most suitable one when it comes to Embedded Systems. In spite of being invented more than 30 years ago, when it comes to Embedded Systems, there is no other programming language which even comes close to C and here are the some reasons why:

### 1. Processor Independent
`{'mod':'speak'}` C language is not specific to any microprocessor nor micro-controller or any system. It can work on various hardware configuration. C doesn’t require same set of hardware to run a program. C language is platform independent whereas the applications written in C are not. Hence the concept “Write once Compile anywhere” came.

For example we can compile and execute a C program written for one hardware in another hardware with little to no change. If there is a change required, it is only in terms of platform (Operating System) specific functions and system calls. This is said to be machine independent. While writing a program in C, user doesn’t have to know the underlying hardware specific details of the machine, since the compiler takes care of it. When developers compile a C program for a particular hardware, respective assembly code is generated. It is then linked with libraries (static and dynamic) to give an executable file. It should be noted that only C code is machine independent, the executable file generated is Machine as well as Platform (OS) dependent. So, whenever a code written in C must be used in another machine, it should be compiled and executed again.

### 2. Portability

`{'mod':'speak'}` Portability of a language is mainly important when an application program must be moved to other operating systems. Code developed in C is more portable and user can compile it on other platforms with least modifications. C code is efficient, easy to understand, maintain and debug. A program can be written in one machine and can be run on other machines.

### 3. Performance

`{'mod':'speak'}` C code gets compiled into raw binary executable which can be directly loaded into memory and executed. C provides optimized machine instructions for the given input, which increases the performance of the embedded system. Most of the high-level languages rely on libraries, hence they require more memory which is a major challenge in embedded systems.

For example, In Java, we need JVM (Java Virtual Machine) in addition to the jar files (Executable) which adds additional overhead in terms of performance and memory consumption. Newer languages provide support for garbage collection, dynamic typing etc., which degrades their performance. Since C does none of that, there is little to no overhead.

### 4. Bit Manipulation

`{'mod':'speak'}` C is more flexible, structured language that provides “low level bit wise data manipulation” using the bit-wise operators. Using bit-wise operators, one could play with available bits, which comes handy when it comes to Embedded Systems (e.g. Handling registers).

### 5. Memory Management

`{'mod':'speak'}` It provides direct memory control without sacrificing benefits of high-level languages. We can directly access memory using pointers and perform various operations using them. When memory requirement is not known, we can allocate it dynamically and when memory requirement is known, we can allocate the memory statically. This is one of the main reasons for why is C the most preferred language for embedded systems.

## What will learn in this module:

`{'mod':'speak'}` In this module you will learn about:

1. Setup the GCC C Compiler for the PC, we will need this tool to learn about C programming, and later integrate our software with the AVR simulator
2. Create a Visual Studio Code C Project folder.
3. Learn to use the Makefile too, which comes with the GCC tool chain