# RISCV-Workshop
# Table of Contents
  - [DAY-1 - Introduction to RISC V ISA and GNU compiler toolchain](#day-1---introduction-to-risc-v-isa-and-gnu-compiler-toolchain)
  - [DAY-2 - Introduction to ABI and Basic Verification Flow](#day-2---introduction-to-abi-and-basic-verification-flow)
  - [DAY-3 - Digital Logic with TL - Verilog and Makerchip](#day-3---digital-logic-with-tl---verilog-and-makerchip)
  - [DAY-4 - Basic RISCV CPU Computer Microarchitecture](#day-4---basic-riscv-cpu-computer-microarchitecture)
  - [DAY-5 Complete Pipelined RISCV CPU Microarchitecture](#day-5-complete-pipelined-riscv-cpu-microarchitecture)


  - [Contributors](#contributors)
  - [Acknowledgements](#acknowledgements)



## DAY-1 - Introduction to RISC V ISA and GNU compiler toolchain


<details>
 <summary>
    RV-D1SKI Introduction to RISC V : Basic Keywords
 </summary>

## RV-D1SKI L1 Introduction 

ISA in layman terms is the language of the computers. If there is a code snippet that needs to be implemented on a harware, it has to be first converted to machine instructions furthermore into binary format. The higher level program(c) will be converted to an RTL and then subsequently mapped onto the hardware. An Instruction Set Architecture (ISA) is part of the abstract model of a computer that defines how the CPU is controlled by the software. The ISA acts as an interface between the hardware and the software, specifying both what the processor is capable of doing as well as how it gets done.


## RV_D1SK1_L2_From Apps To Hardware

Even the apps that are used so widely, are ultimately run on a hardware. This is done with the help of an intermidiate system called **system software** . It comprises of OS, kernel,compilers and assemblers. 

<img width="1440" alt="Screenshot 2023-08-17 at 4 11 54 PM" src="https://github.com/Sushma-Ravindra/IIITB-ASIC-1/assets/141133883/b4de1c2b-f427-4183-86c3-835d3d0f0f42">

_Compiler_: In computing, a compiler is a computer program that translates computer code written in one programming language (the source language) into another language (the target language). The name "compiler" is primarily used for programs that translate source code from a high-level programming language to a low-level programming language (e.g. assembly language, object code, or machine code) to create an executable program ie exe file. 


_Assembler_ : An assembler is a type of computer program that takes in basic instructions and converts them into a pattern of bits that the computer's processor can use to perform basic operations. The assembler's job is to convert assembler or assembly language code into machine code that the computer can then read and execute.


_Architecture of the computer_ : So architecture or ISA is the abstract interface between higher languages and generated machine level instructions by the compiler.

<img width="1440" alt="Screenshot 2023-08-17 at 4 10 56 PM" src="https://github.com/Sushma-Ravindra/IIITB-ASIC-1/assets/141133883/f2990f36-d867-453c-afd6-4f2a54730975">


Now, for the hardware to read instructions from the bit stream, there is need for RTL languages that further synthesis the instruction received from higher level languages into a netlist which can be implemented on the hardware.

<img width="1440" alt="Screenshot 2023-08-17 at 4 11 54 PM" src="https://github.com/Sushma-Ravindra/IIITB-ASIC-1/assets/141133883/1ee3f21b-2dc7-44f6-8a05-f552931af168">


## RV_D1SK1_L3_Detailed Description Of Course Content 

Beginning with basic C codes for integer addition and operations. Demo of the course content is given taking the mentioned code as example.

1) Pseudo Instructions: mv, ld, li.
2) Base Integer Instructions: Also called RV64i :  addi, lui , auipc. 64 bit refers to the data size it is operating on.
3) Multipy extenstion : RV64m : mulw , divw.
4) Single and Double Precision Floating point Extention : RV64F and RV64D : fsd, fmul.

Following are the few additional topics to be covered in the course.


_Application Binary Interface_
_Memory Allocation and Data Pointer_
_Signed and Unsigned Integer representation_

</details>




<details>
 <summary>
    RV-D1SK2 - Labwork for RISCV toolchain
 </summary>

## RV-D1SK2 - L1 - C Program to compute sum from 1 to N. 

Open a file named sum_1_to_n. using leafpad editor.
```
  $leafpad sum_1_to_n.c

```

Write your C code for sum of numbers from 1 to n (say n =9).
Compile using GNU compiler.
 ```
 $gcc sum_1_to_n.c

```

Run the compiled object file (Default object file formed with the name a.out). 

```
  $./a/out

```

## RV-D1SK2 - L2 - C - GCC Compile and Disassemble.

The same C program is now compiled using RISC-V toolchain. Spike simulator is used to run the object file , and also as a debugger.



## RV-D1SK2 - L3 - Spike Simulation and Debug.

Since we have previously created our sum_1_to_n.c program file, now to run the same program using RISC-V simulator:

```
$riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum_1_to_n.o sum_1_to_n.c

```
Command info: riscv64-unknown-elf-gcc => RISC-V compiler , -Ofast => Compiler option (Various compiler options like -O1, -o1, -Ofast) , -mabi=lp64 => ABI of long int pointer , -march=rv64i => architecture-64bit , -o => output , sum_1_to_n.o => object file , sum_1_to_n.c => C program file

In order to see what is the assembly code for the C program that is run ,i.e to see the disassembled file, run the following in a new tab in the terminal:
```
$riscv64-unknown-elf-objdump -d sum_1_to_n.o | less

```





</details>

<details>
 <summary>
    RV-D1SK3 - Integer Number Representation
 </summary>


## RV-D1SK3 - L1 - 64 bit Number System for Unsigned Numbers

## RV-D1SK3 - L2 - 64 bit Number System for Signed Numbers

## RV-D1SK3 - L3 - Lab for Signed and Unsigned Numbers


</details>




## DAY-2 - Introduction to ABI and Basic Verification Flow

<details>
 <summary>
    RV-D2SK1 - Application Binary Interface
 </summary>

## RV-D2SK1 - L1 - Introducation to Application Binary Interface

## RV-D2SK1 - L2 - Memory Allocation for Double Words

## RV-D2SK1 - L3 - Load, Add ,Store Instructions with examples

## RV-D2SK1 - L4 - Concluding 32 Registers and their respective ABI names

</details>


<details>
 <summary>
    RV-D2SK2 - Labworks using ABI function calls
 </summary>


## RV-D2SK2 - L1 - Study New Algorithm for SUM 1 to N using ASM
## RV-D2SK2 - L2 - Review ASM function Calls
## RV-D2SK2 - L3 - Simulate New C program wirh function Call 

</details>

<details>
 <summary>
    RV-D2SK3 - Basic Verification Flow using iVerilog
 </summary>

## RV-D2SK3 - L1 - Lab to run C prog on RISCV CPU

</details>


## DAY-3 - Digital Logic with TL - Verilog and Makerchip

<details>
  <summary>
    RV-D3SK1 - Combinational Logic in TL-Verilog in Makerchip 
  </summary>

 ## RV-D3SK1 - L1 - Introduction to Logic Gates
 ## RV-D3SK1 - L2 - Basic MUX Implementation and Introdiction to Makerchip
 ## RV-D3SK1 - L3 - Labs for Combinational Logic

 </details>

 
<details>
  <summary>
    RV-D3SK2 - Sequential Logic 
  </summary>

## RV-D3SK2 - L1 - Introduction to Sequential Logic and Counter Lab
## RV-D3SK2 - L2 - Sequential Calculator Lab


</details>


<details>
  <summary>
    RV-D3SK3 - Pipelined Logic 
  </summary>

## RV-D3SK3 - L1 - Pipelined Logic and Retiming
## RV-D3SK3 - L2 - Pipeline Logic Advantages and Demo on Platform
## RV-D3SK3 - L3 - Lab on Error Condtions within Computation Pipeline
## RV-D3SK3 - L4 - Lab on 2 Cycle Calculator

</details>


<details>
  <summary>
    RV-D3SK4 - Validity 
  </summary>

  
 ## RV-D3SK4 - L1 - Introduction to VALIDITY and its Advantages
 ## RV-D3SK4 - L2 - Lab on validity and valid when condition
 ## RV-D3SK4 - L3 - Lab to complete total distance
 ## RV-D3SK4 - L4 - Lab on 2 cycle calculator with validity 
 ## RV-D3SK4 - L5 - Calculator single Value Memory Lab

 </details>

<details>
  <summary>
    RV-D3SK5 - Wrap Up
  </summary>
 
## RV-D3SK5 - Introduction to Hierarchy Concept 


</details>


## DAY-4 - Basic RISCV CPU Computer Microarchitecture

<details>
  <summary>
    RV-D4SK1 - Introduction to Simple RISCV Microarchitecture
  </summary>

## RV-D4SK1 - L1 - Microarchitecture of Single Cycle RISCV CPU
## RV-D4SK2 - L2 - Starting Point Code for RISCV Labs - 1
## RV-D4SK2 - L3 - Starting Point Code for RISCV Labs - 2

</details>


<details>
  <summary>
    RV-D4SK2 - Fetch and Decode
  </summary>

##  RV-D4SK2 - L1 - Implementation Plan and Lab for PC
##  RV-D4SK2 - L2 - Lab for instruction fetch logic
##  RV-D4SK2 - L3 - Lab for RV instruction types IRSBJU Decode Logic
##  RV-D4SK2 - L4 - Lab for instruction immediate decode logic for RV ISBUJ
##  RV-D4SK2 - L5 - Lab to decode other fields of Instruction of RV ISBUJ
##  RV-D4SK2 - L6 - Lab to decode instruction fields based on Instruction type RV ISBUJ
##  RV-D4SK2 - L7 - Lab to decode individual Instruction


  
</details>


<details>
  <summary>
    RV-D4SK3 - RISCV Control Logic 
  </summary>

 
## RV-D4SK3 - L1 - Lab for Register file read -1 
## RV-D4SK3 - L2 - Lab for Register file read -2
## RV-D4SK3 - L3 - Lab for ALU operations
## RV-D4SK3 - L4 - Lab for Register file write 
## RV-D4SK3 - L5 - Concept of array and Rgister file details
## RV-D4SK3 - L6 - Lab for implementing branch Instructions
## RV-D4SK3 - L7 - Lab fpr completing branch instructions implementations
## RV-D4SK3 - L8 - Lab to create simple testbench

</details>


## DAY-5 Complete Pipelined RISCV CPU Microarchitecture



<details>
  <summary>
    RV-D5SK1 - Pipelining the CPU  
  </summary>

  ## RV-D5SK1 - L1 - Introduction to control flow hazard and read after write hazard
  ## RV-D5SK1 - L2 - Create 3 cycle valid signal
  ## RV-D5SK1 - L3 - Code 3 cycle RISCV architecture to take care of invalid signal
  ## RV-D5SK1 - L4 - To modify 3 cycle RISCV to distribute logic 

</details>


<details>
  <summary>
    RV-D5SK2 - Solution to Pipeline Hazard
  </summary>


## RV-D5SK2 - L1 - Register File Bypass to address RD after WR hazard
## RV-D5SK2 - L2 - Braches to correct branch target path
## RV-D5SK2 - L3 - Complete instuction decode 
## RV-D5SK2 - L4 - Code complete ALU
</details>

<details>
  <summary>
    RV-D5SK3 - Load Store Instruction and completing RISCV CPU
  </summary>

## RV-D5SK3 - L1 - Introduction and Lab to redirect load
## RV-D5SK3 - L2 - Load data from Memory to Rgister file
## RV-D5SK3 - L3 - Add loads and stores to test program
## RV-D5SK3 - L4 - Add control logic for JUMP instructions
## RV-D5SK3 - L5 - Wrap up 













## Contributors
SUSHMA R


## Acknowledgements 
www.vsdiat.com

www.github/kunal123.com

www.google.com

www.chipedge.com/everything-you-need-to-know-about-synthesis-in-vlsi/

www.electronicsforyou.com

