# Digital Design and Computer Architecture 读书笔记

章节目录

- [ ] Chapter 1 From Zero to One
  - [ ] 1.1 The Game Plan
  - [ ] 1.2 The Art of Managing Complexity
    - [ ] 1.2.1 Abstraction
    - [ ] 1.2.2 Discipline
    - [ ] 1.2.3 The Three-Y’s
  - [ ] 1.3 The Digital Abstraction
  - [ ] 1.4 Number Systems
    - [ ] 1.4.1 Decimal Numbers
    - [ ] 1.4.2 Binary Numbers
    - [ ] 1.4.3 Hexadecimal Numbers
    - [ ] 1.4.4 Bytes, Nibbles, and All That Jazz
    - [ ] 1.4.5 Binary Addition
    - [ ] 1.4.6 Signed Binary Numbers
  - [ ] 1.5 Logic Gates
    - [ ] 1.5.1 NOT Gate
    - [ ] 1.5.2 Buffer
    - [ ] 1.5.3 AND Gate
    - [ ] 1.5.4 OR Gate
    - [ ] 1.5.5 Other Two-Input Gates
    - [ ] 1.5.6 Multiple-Input Gates
  - [ ] 1.6 Beneath the Digital Abstraction
    - [ ] 1.6.1 Supply Voltage
    - [ ] 1.6.2 Logic Levels
    - [ ] 1.6.3 Noise Margins
    - [ ] 1.6.4 DC Transfer Characteristics
    - [ ] 1.6.5 The Static Discipline
  - [ ] 1.7 CMOS Transistors
    - [ ] 1.7.1 Semiconductors
    - [ ] 1.7.2 Diodes
    - [ ] 1.7.3 Capacitors
    - [ ] 1.7.4 nMOS and pMOS Transistors
    - [ ] 1.7.5 CMOS NOT Gate
    - [ ] 1.7.6 Other CMOS Logic Gates
    - [ ] 1.7.7 Transmission Gates
    - [ ] 1.7.8 Pseudo-nMOS Logic
  - [ ] 1.8 Power Consumption
  - [ ] 1.9 Summary and a Look Ahead
  - [ ] Exercises
  - [ ] Interview Questions
- [ ] Chapter 2 Combinational Logic Design
  - [ ] 2.1 Introduction
  - [ ] 2.2 Boolean Equations
    - [ ] 2.2.1 Terminology
    - [ ] 2.2.2 Sum-of-Products Form
    - [ ] 2.2.3 Product-of-Sums Form
  - [ ] 2.3 Boolean Algebra
    - [ ] 2.3.1 Axioms
    - [ ] 2.3.2 Theorems of One Variable
    - [ ] 2.3.3 Theorems of Several Variables
    - [ ] 2.3.4 The Truth Behind It All
    - [ ] 2.3.5 Simplifying Equations
  - [ ] 2.4 From Logic to Gates
  - [ ] 2.5 Multilevel Combinational Logic
    - [ ] 2.5.1 Hardware Reduction
    - [ ] 2.5.2 Bubble Pushing
  - [ ] 2.6 X’s and Z’s, Oh My
    - [ ] 2.6.1 Illegal Value: X
    - [ ] 2.6.2 Floating Value: Z
  - [ ] 2.7 Karnaugh Maps
    - [ ] 2.7.1 Circular Thinking
    - [ ] 2.7.2 Logic Minimization with K-Maps
    - [ ] 2.7.3 Don’t Cares
    - [ ] 2.7.4 The Big Picture
  - [ ] 2.8 Combinational Building Blocks
    - [ ] 2.8.1 Multiplexers
    - [ ] 2.8.2 Decoders
  - [ ] 2.9 Timing
    - [ ] 2.9.1 Propagation and Contamination Delay
    - [ ] 2.9.2 Glitches
  - [ ] 2.10 Summary
  - [ ] Exercises
  - [ ] Interview Questions
- [ ] Chapter 3 Sequential Logic Design
  - [ ] 3.1 Introduction
  - [ ] 3.2 Latches and Flip-Flops
    - [ ] 3.2.1 SR Latch
    - [ ] 3.2.2 D Latch
    - [ ] 3.2.3 D Flip-Flop
    - [ ] 3.2.4 Register
    - [ ] 3.2.5 Enabled Flip-Flop
    - [ ] 3.2.6 Resettable Flip-Flop
    - [ ] 3.2.7 Transistor-Level Latch and Flip-Flop Designs
    - [ ] 3.2.8 Putting It All Together
  - [ ] 3.3 Synchronous Logic Design
    - [ ] 3.3.1 Some Problematic Circuits
    - [ ] 3.3.2 Synchronous Sequential Circuits
    - [ ] 3.3.3 Synchronous and Asynchronous Circuits
  - [ ] 3.4 Finite State Machines
    - [ ] 3.4.1 FSM Design Example
    - [ ] 3.4.2 State Encodings
    - [ ] 3.4.3 Moore and Mealy Machines
    - [ ] 3.4.4 Factoring State Machines
    - [ ] 3.4.5 Deriving an FSM from a Schematic
    - [ ] 3.4.6 FSM Review
  - [ ] 3.5 Timing of Sequential Logic
    - [ ] 3.5.1 The Dynamic Discipline
    - [ ] 3.5.2 System Timing
    - [ ] 3.5.3 Clock Skew
    - [ ] 3.5.4 Metastability
    - [ ] 3.5.5 Synchronizers
    - [ ] 3.5.6 Derivation of Resolution Time
  - [ ] 3.6 Parallelism
  - [ ] 3.7 Summary
  - [ ] Exercises
  - [ ] Interview Questions
- [ ] Chapter 4 Hardware Description Languages
  - [ ] 4.1 Introduction
    - [ ] 4.1.1 Modules
    - [ ] 4.1.2 Language Origins
    - [ ] 4.1.3 Simulation and Synthesis
  - [ ] 4.2 Combinational Logic
    - [ ] 4.2.1 Bitwise Operators
    - [ ] 4.2.2 Comments and White Space
    - [ ] 4.2.3 Reduction Operators
    - [ ] 4.2.4 Conditional Assignment
    - [ ] 4.2.5 Internal Variables
    - [ ] 4.2.6 Precedence
    - [ ] 4.2.7 Numbers
    - [ ] 4.2.8 Z’s and X’s
    - [ ] 4.2.9 Bit Swizzling
    - [ ] 4.2.10 Delays
  - [ ] 4.3 Structural Modeling
  - [ ] 4.4 Sequential Logic
    - [ ] 4.4.1 Registers
    - [ ] 4.4.2 Resettable Registers
    - [ ] 4.4.3 Enabled Registers
    - [ ] 4.4.4 Multiple Registers
    - [ ] 4.4.5 Latches
  - [ ] 4.5 More Combinational Logic
    - [ ] 4.5.1 Case Statements
    - [ ] 4.5.2 If Statements
    - [ ] 4.5.3 Truth Tables with Don’t Cares
    - [ ] 4.5.4 Blocking and Nonblocking Assignments
  - [ ] 4.6 Finite State Machines
  - [ ] 4.7 Data Types
    - [ ] 4.7.1 SystemVerilog
    - [ ] 4.7.2 VHDL
  - [ ] 4.8 Parameterized Modules
  - [ ] 4.9 Testbenches
  - [ ] 4.10 Summary
  - [ ] Exercises
  - [ ] Interview Questions
- [ ] Chapter 5 Digital Building Blocks
  - [ ] 5.1 Introduction
  - [ ] 5.2 Arithmetic Circuits
    - [ ] 5.2.1 Addition
    - [ ] 5.2.2 Subtraction
    - [ ] 5.2.3 Comparators
    - [ ] 5.2.4 ALU
    - [ ] 5.2.5 Shifters and Rotators
    - [ ] 5.2.6 Multiplication
    - [ ] 5.2.7 Division
    - [ ] 5.2.8 Further Reading
  - [ ] 5.3 Number Systems
    - [ ] 5.3.1 Fixed-Point Number Systems
    - [ ] 5.3.2 Floating-Point Number Systems
  - [ ] 5.4 Sequential Building Blocks
    - [ ] 5.4.1 Counters
    - [ ] 5.4.2 Shift Registers
  - [ ] 5.5 Memory Arrays
    - [ ] 5.5.1 Overview
    - [ ] 5.5.2 Dynamic Random Access Memory (DRAM)
    - [ ] 5.5.3 Static Random Access Memory (SRAM)
    - [ ] 5.5.4 Area and Delay
    - [ ] 5.5.5 Register Files
    - [ ] 5.5.6 Read Only Memory
    - [ ] 5.5.7 Logic Using Memory Arrays
    - [ ] 5.5.8 Memory HDL.
  - [ ] 5.6 Logic Arrays
    - [ ] 5.6.1 Programmable Logic Array
    - [ ] 5.6.2 Field Programmable Gate Array
    - [ ] 5.6.3 Array Implementations
  - [ ] 5.7 Summary
  - [ ] Exercises
  - [ ] Interview Questions
- [ ] Chapter 6 Architecture
  - [ ] 6.1 Introduction
  - [ ] 6.2 Assembly Language
    - [ ] 6.2.1 Instructions
    - [ ] 6.2.2 Operands: Registers, Memory, and Constants
  - [ ] 6.3 Machine Language
    - [ ] 6.3.1 R-Type Instructions
    - [ ] 6.3.2 I-Type Instructions
    - [ ] 6.3.3 J-Type Instructions
    - [ ] 6.3.4 Interpreting Machine Language Code
    - [ ] 6.3.5 The Power of the Stored Program
  - [ ] 6.4 Programming
    - [ ] 6.4.1 Arithmetic/Logical Instructions
    - [ ] 6.4.2 Branching
    - [ ] 6.4.3 Conditional Statements
    - [ ] 6.4.4 Getting Loopy
    - [ ] 6.4.5 Arrays
    - [ ] 6.4.6 Function Calls
  - [ ] 6.5 Addressing Modes
  - [ ] 6.6 Lights, Camera, Action: Compiling, Assembling, and Loading
    - [ ] 6.6.1 The Memory Map
    - [ ] 6.6.2 Translating and Starting a Program
  - [ ] 6.7 Odds and Ends
    - [ ] 6.7.1 Pseudoinstructions
    - [ ] 6.7.2 Exceptions
    - [ ] 6.7.3 Signed and Unsigned Instructions
    - [ ] 6.7.4 Floating-Point Instructions
  - [ ] 6.8 Real-World Perspective: x86 Architecture
    - [ ] 6.8.1 x86 Registers
    - [ ] 6.8.2 x86 Operands
    - [ ] 6.8.3 Status Flags
    - [ ] 6.8.4 x86 Instructions
    - [ ] 6.8.5 x86 Instruction Encoding
    - [ ] 6.8.6 Other x86 Peculiarities
    - [ ] 6.8.7 The Big Picture
  - [ ] 6.9 Summary
  - [ ] Exercises
  - [ ] Interview Questions
- [ ] Chapter 7 Microarchitecture
  - [ ] 7.1 Introduction
    - [ ] 7.1.1 Architectural State and Instruction Set
    - [ ] 7.1.2 Design Process
    - [ ] 7.1.3 MIPS Microarchitectures
  - [ ] 7.2 Performance Analysis
    - [ ] 7.3 Single-Cycle Processor
    - [ ] 7.3.1 Single-Cycle Datapath
    - [ ] 7.3.2 Single-Cycle Control
    - [ ] 7.3.3 More Instructions
    - [ ] 7.3.4 Performance Analysis
  - [ ] 7.4 Multicycle Processor
    - [ ] 7.4.1 Multicycle Datapath
    - [ ] 7.4.2 Multicycle Control
    - [ ] 7.4.3 More Instructions
    - [ ] 7.4.4 Performance Analysis
  - [ ] 7.5 Pipelined Processor
    - [ ] 7.5.1 Pipelined Datapath
    - [ ] 7.5.2 Pipelined Control
    - [ ] 7.5.3 Hazards
    - [ ] 7.5.4 More Instructions
    - [ ] 7.5.5 Performance Analysis
  - [ ] 7.6 HDL Representation
    - [ ] 7.6.1 Single-Cycle Processor
    - [ ] 7.6.2 Generic Building Blocks
    - [ ] 7.6.3 Testbench
  - [ ] 7.7 Exceptions
  - [ ] 7.8 Advanced Microarchitecture
    - [ ] 7.8.1 Deep Pipelines
    - [ ] 7.8.2 Branch Prediction
    - [ ] 7.8.3 Superscalar Processor
    - [ ] 7.8.4 Out-of-Order Processor
    - [ ] 7.8.5 Register Renaming
    - [ ] 7.8.6 Single Instruction Multiple Data
    - [ ] 7.8.7 Multithreading
    - [ ] 7.8.8 Homogeneous Multiprocessors
    - [ ] 7.8.9 Heterogeneous Multiprocessors
  - [ ] 7.9 Real-World Perspective: x86 Microarchitecture
  - [ ] 7.10 Summary
  - [ ] Exercises
  - [ ] Interview Questions
- [ ] Chapter 8 Memory and I/O Systems
  - [ ] 8.1 Introduction
  - [ ] 8.2 Memory System Performance Analysis
  - [ ] 8.3 Caches
    - [ ] 8.3.1 What Data is Held in the Cache?
    - [ ] 8.3.2 How is Data Found?
    - [ ] 8.3.3 What Data is Replaced?
    - [ ] 8.3.4 Advanced Cache Design
    - [ ] 8.3.5 The Evolution of MIPS Caches
  - [ ] 8.4 Virtual Memory
    - [ ] 8.4.1 Address Translation
    - [ ] 8.4.2 The Page Table
    - [ ] 8.4.3 The Translation Lookaside Buffer
    - [ ] 8.4.4 Memory Protection
    - [ ] 8.4.5 Replacement Policies
    - [ ] 8.4.6 Multilevel Page Tables
  - [ ] 8.5 I/O Introduction
  - [ ] 8.6 Embedded I/O Systems
    - [ ] 8.6.1 PIC32MX675F512H Microcontroller
    - [ ] 8.6.2 General-Purpose Digital I/O
    - [ ] 8.6.3 Serial I/O
    - [ ] 8.6.4 Timers
    - [ ] 8.6.5 Interrupts
    - [ ] 8.6.6 Analog I/O
    - [ ] 8.6.7 Other Microcontroller Peripherals
  - [ ] 8.7 PC I/O Systems
    - [ ] 8.7.1 USB
    - [ ] 8.7.2 PCI and PCI Express
    - [ ] 8.7.3 DDR3 Memory
    - [ ] 8.7.4 Networking
    - [ ] 8.7.5 SATA
    - [ ] 8.7.6 Interfacing to a PC
  - [ ] 8.8 Real-World Perspective: x86 Memory and I/O Systems
    - [ ] 8.8.1 x86 Cache Systems
    - [ ] 8.8.2 x86 Virtual Memory
    - [ ] 8.8.3 x86 Programmed I/O
  - [ ] 8.9 Summary
  - [ ] Epilogue
  - [ ] Exercises
  - [ ] Interview Questions

## 参考及引用

[1] Digital Design and Computer Architecture. David Money Harris & Sarah L. Harris.
