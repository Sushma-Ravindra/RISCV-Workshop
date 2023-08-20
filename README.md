# RISCV-Workshop
# Table of Contents
  - [DAY-1 - Introduction to RISC V ISA and GNU compiler toolchain](#day-1---introduction-to-risc-v-isa-and-gnu-compiler-toolchain)





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



## RV-D1SK2 - L2 - C - GCC Compile and Disassemble.

## RV-D1SK2 - L3 - Spike Simulation and Debug.

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



































## Contributors
SUSHMA R


## Acknowledgements 
www.vsdiat.com

www.github/kunal123.com

www.google.com

www.chipedge.com/everything-you-need-to-know-about-synthesis-in-vlsi/

www.electronicsforyou.com

