![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/6e00d042-05e0-4464-ac2d-5ac51bea3e46)# RISCV-Workshop
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

Since we have previously created our sum_1_to_n.c program file, now to run the same program using RISC-V simulator:

```
$riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum_1_to_n.o sum_1_to_n.c

```
Command info: riscv64-unknown-elf-gcc => RISC-V compiler , -Ofast => Compiler option (Various compiler options like -O1, -o1, -Ofast) , -mabi=lp64 => ABI of long int pointer , -march=rv64i => architecture-64bit , -o => output , sum_1_to_n.o => object file , sum_1_to_n.c => C program file

In order to see what is the assembly code for the C program that is run ,i.e to see the disassembled file, run the following in a new tab in the terminal:
```
$riscv64-unknown-elf-objdump -d sum_1_to_n.o | less

```

The same C program is now compiled using RISC-V toolchain. Spike simulator is used to run the object file , and also as a debugger.
```
  $ riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
  $ riscv64-unknown-elf-objdump -d sum1ton.o | less
  # different command 
  $ riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
  $ riscv64-unknown-elf-objdump -d sum1ton.o | less
  $ spike pk sum1ton.o
```
![Screenshot from 2023-08-22 22-13-45](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/ce0fb07c-2f8d-4d52-aabb-66b9443aadda)
![Screenshot from 2023-08-22 22-18-50](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/bbdd8ce7-5785-46c7-aa7d-2d11b618bd29)
![Screenshot from 2023-08-22 22-21-24](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/4d0c659d-9e10-4303-af5b-94e5db98c176)
![Screenshot from 2023-08-22 22-25-45](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/96a29653-e7d3-4184-9f63-f714ac15c216)



## RV-D1SK2 - L3 - Spike Simulation and Debug.


Some data representation terms we use:
Byte - A byte is a fundamental unit of digital information that consists of a group of eight bits.
Word - A word is a basic unit of data that a processor can operate on in a single instruction. It typically corresponds to the natural data width of the processor's architecture. In RISC-V Word is of length 32bits.
Double Word - In computer architecture and data representation, a "double word" is a term used to describe a unit of data that is twice the size of a "word." In RISC-V Double word is of length 64bits.
Most Significant bit(MSB) - MSB stands for "Most Significant Bit." It is a term used in digital systems and binary representation to refer to the bit in a binary number that holds the highest positional value.
Least Significant bit(LSB) - LSB stands for "Least Significant Bit." It is the term used in binary representation to refer to the bit in a binary number that holds the lowest positional value. In other words, the Least Significant Bit is the rightmost bit in a binary representation.

![Screenshot from 2023-08-22 22-54-56](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/b4b26952-5c68-4547-887a-b7f709ac2f89)

The total unsigned numbers we can form using n-bits is given as : 2^(n) - 1.
We use 2's complement representation to represent the negative numbers.
For signed representation, the MSB bit indicated the sign of the number. If MSB=0, it is a positive number and MSB=1 indicates a negative number.



    In signed representation of binary numbers, the range of positive numbers we can represent using n-bits is: 0 to (2^(n-1) - 1) and the range of negative numbers is: -1 to -2^(n-1).
    
![Screenshot from 2023-08-22 22-56-53](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/7b74a7a7-24c7-41e9-b417-04c1a426894e)


    

</details>

<details>
 <summary>
    RV-D1SK3 - Integer Number Representation
 </summary>


## RV-D1SK3 - L1 - 64 bit Number System for Unsigned Numbers

Some data representation terms we use:
Byte - A byte is a fundamental unit of digital information that consists of a group of eight bits.
Word - A word is a basic unit of data that a processor can operate on in a single instruction. It typically corresponds to the natural data width of the processor's architecture. In RISC-V Word is of length 32bits.
Double Word - In computer architecture and data representation, a "double word" is a term used to describe a unit of data that is twice the size of a "word." In RISC-V Double word is of length 64bits.
Most Significant bit(MSB) - MSB stands for "Most Significant Bit." It is a term used in digital systems and binary representation to refer to the bit in a binary number that holds the highest positional value.
Least Significant bit(LSB) - LSB stands for "Least Significant Bit." It is the term used in binary representation to refer to the bit in a binary number that holds the lowest positional value. In other words, the Least Significant Bit is the rightmost bit in a binary representation.

![Screenshot from 2023-08-22 17-51-55](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/72e6e07e-3a3d-4052-8839-6c938b19d030)
![Screenshot from 2023-08-22 17-51-42](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/1780a8be-b44e-4a67-8e14-a3a68584b854)


## RV-D1SK3 - L2 - 64 bit Number System for Signed Numbers
 

In signed representation of binary numbers, the range of positive numbers we can represent using n-bits is: 0 to (2^(n-1) - 1) and the range of negative numbers is: -1 to -2^(n-1).
2's complement The two's complement is a mathematical technique used in computing to represent signed integers (positive and negative whole numbers) using the binary number system.

To convert a negative integer to its two's complement representation:
Take the positive binary representation.
Flip all the bits (change 0s to 1s and 1s to 0s).
Add 1 to the resulting value.
Positive number MSB=0 Negative number MSB=1


![Screenshot from 2023-08-22 22-56-53](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/11c2f83d-5193-4129-96b0-2b7327a4b912)


![Screenshot from 2023-08-22 17-52-14](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/2b8f169d-2c77-4eb3-bfe0-6365cf560d88)



## RV-D1SK3 - L3 - Lab for Signed and Unsigned Numbers


Let us do a lab exercise based on the signed and unsigned binary numbers:

 The following code is to rpresent the highest binary number in unsigned representation:

```
  #include <stdio.h>
  #include <math.h>
  int main() {
  unsigned long long int max = (unsigned long long int) (pow(2,64) -1);
  printf("highest number represented by unsigned long long int is %llu\n", max);
  return 0;
  }
```

Output:
![Screenshot from 2023-08-22 23-02-11](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/a875620f-c22a-4947-9f74-f38b2c54e032)


Modifying the above program to check whether the result we got is the highest number are not:

```
#include<stdio.h>
#include<math.h>

int main() {
	long long int max = (long long int) (pow(2,10) * -1);
	printf("highest number represented by long long int is %lld\n", max);
	return 0;
}

```
Output:


![Screenshot from 2023-08-22 23-04-56](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/829b1020-93b5-45a7-8309-076e18433716)


Now, Create a new file signedHighest.c with the following code in it:
```
#include<stdio.h>
#include<math.h>

int main() {
	long long int max = (long long int) (pow(2,63) -1);
	long long int min = (long long int) (pow(2,63) * -1);
	printf("highest number represented by long long int is %lld\n", max);
  printf("lowest number represented by long long int is %lld\n", min);
	return 0;
}
```
Output:
![Screenshot from 2023-08-22 23-10-28](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/48fa4e34-4840-44d4-8899-ad50a1db54a0)



</details>




## DAY-2 - Introduction to ABI and Basic Verification Flow

<details>
 <summary>
    RV-D2SK1 - Application Binary Interface
 </summary>



Application Binary Interface - In the context of RISC-V, the ABI specifies how system calls are invoked and how data is passed between user-mode applications and the operating system. Specifically, the ABI defines which registers are used for passing parameters to system calls and for receiving return values. It also specifies how the system call number (which corresponds to the specific service being requested) is passed to the operating system.
Register Width in RISC-V - The width of registers in the RISC-V architecture is determined by the value of XLEN, which represents the native word size of the processor. XLEN is defined at the time the RISC-V architecture is implemented and can be different for different variations of the architecture.
![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/92a0b9f5-73db-43a9-8362-7e9025139f04)


For RV64 (RISC-V 64-bit architecture), XLEN is 64 bits. This means that general-purpose registers and other data paths in the processor are 64 bits wide.
For RV32 (RISC-V 32-bit architecture), XLEN is 32 bits. In this case, general-purpose registers and data paths are 32 bits wide.

Registers - In RISC-V there are 32 registers(x1-x31). We can load the registers in two different ways.

Load directly into the registers.
Load into the memory and then to register.(Each memory cell hold 1byte for 64bits data to load into memory we need 8 such memory cells)

Little-endian memory addressing system - RISC-V belongs to the little endian memory addressing system.In a little-endian system, the least significant byte (LSB) of a multi-byte value is stored at the lowest memory address, while the most significant byte (MSB) is stored at the highest memory address.



Application Binary Interface:

It is a mode through which the application programmer can access the contents of hardware resources of the processor. The access of porcessor is done via registers.
In RISC-V specification, we have 32 registers whose width is defined by the keyword "XLEN". It is XLEN-32 bit for Rv32 and XLEN-64 for Rv64.
For RV64, the data can either be loaded to registers directly or we can first load tha data into memory which holds 8-bits in each memory address and then transfer it to the registers.
All the instructions in RISC-V is of 32-bits.
    1.ld(load doubleword) is a command to load the contents of memory into register.
    2.add is used to add the contents of the registers/memory.
    3.sd(store doubleword) is used to store the contents of register back to the memory.


![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/666a240a-18dd-4457-bc99-43d439deb36c)


![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/16cdc2d5-aa66-4228-a7d7-e6e8238cfe9a)



![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/65742ca0-082f-4b72-a1bd-cd8cc8eb4963)





In the RISC-V instruction set architecture (ISA), instructions are categorized based on their formats and functionalities. The I-type, R-type, and S-type instructions are three common categories of instructions in RISC-V. These categories help describe the structure of the instruction and how they operate on data.

    I-Type Instructions (Immediate): I-type instructions are used for operations that involve an immediate value (constant) and a register. The immediate value is encoded within the instruction itself. Common examples include ADDI (add immediate), LW (load word), and SW (store word). Syntax: OP rd, rs1, imm

    R-Type Instructions (Register): R-type instructions are used for operations that involve registers. The operation is specified by the opcode, and both source registers and destination registers are used. Common examples include ADD (add), SUB (subtract), and AND (bitwise AND). Syntax: OP rd, rs1, rs2

    S-Type Instructions (Store): S-type instructions are used for storing data from a register into memory. They involve two registers and an offset that determines the memory location. Common examples include SW (store word) and SH (store halfword). Syntax: OP rs2, imm(rs1) Registers As we can see in the above figure 5bits are needed to represent each register. So if we calculate total number of registers we can have it will be, 2^5=32. Different types of registers is shown above.




</details>


<details>
 <summary>
    RV-D2SK2 - Labworks using ABI function calls
 </summary>














Using ASM(Assembly language program) we are writing the code for sum of numbers from 1 to 9. We have main program in 1to9_custom.c file which does the function call and the function get calls in load.

```
#include<stdio.h>
extern int load(int x,int y); //defined function over here

int main{
int result=0;
int count=9;
result = load(0x0, count+1);

printf("sum of numbers from 1 to %d is %d\n", count,result);
}


//load.S
.section .text	
.global load
.type load, @function

load: 
	add  a4, a0, 0
	add  a2, a1, 0
	add  a3, 0, 0
loop:
	add  a4, a4, a3
	add  a3, a3, 1
	blt  a3, a2, loop
	add  a0, a4, 0
	ret

```

Run the above codes using spike compiler and observe: 

file:///home/lasya/Pictures/Screenshots/Screenshot%20from%202023-08-22%2018-22-15.png![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/8e1e94a6-17c5-4f74-b6ac-2ed544459105)


View the assembly code:
riscv64-unknown-elf-objdump -d sum1ton.o | less

file:///home/lasya/Pictures/Screenshots/Screenshot%20from%202023-08-22%2018-24-47.png![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/da9f2a79-7044-42d2-9ef1-1bd55f3bdbd8)











</details>

<details>
 <summary>
    RV-D2SK3 - Basic Verification Flow using iVerilog
 </summary>

We will follow the following procedure in this lab session:

![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/2123e583-e183-4f67-ad77-96c1213c92a8)

There is this rv32im.sh file which is the script file which contain scripts that are needed to convert into hex file which is firmware.hex and load it into picor32.v memory using testbench.v and simulate it at the end.

```
riscv64-unknown-elf-gcc -c -mabi=ilp32 -march=rv32im -o 1to9_custom.o 1to9_custom.c 
riscv64-unknown-elf-gcc -c -mabi=ilp32 -march=rv32im -o load.o load.S

riscv64-unknown-elf-gcc -c -mabi=ilp32 -march=rv32im -o syscalls.o syscalls.c
riscv64-unknown-elf-gcc -mabi=ilp32 -march=rv32im -Wl,--gc-sections -o firmware.elf load.o 1to9_custom.o syscalls.o -T riscv.ld -lstdc++
chmod -x firmware.elf
riscv64-unknown-elf-gcc -mabi=ilp32 -march=rv32im -nostdlib -o start.elf start.S -T start.ld -lstdc++
chmod -x start.elf
riscv64-unknown-elf-objcopy -O verilog start.elf start.tmp
riscv64-unknown-elf-objcopy -O verilog firmware.elf firmware.tmp
 cat start.tmp firmware.tmp > firmware.hex
python3 hex8tohex32.py firmware.hex > firmware32.hex
rm -f start.tmp firmware.tmp
iverilog -o testbench.vvp testbench.v picorv32.v
chmod -x testbench.vvp
vvp -N testbench.vvp
```


Use following commands to the riscv cpu program code:
```
	vim 1to9_custom.c
	chmod 777 rv32im.sh // change the permissions if needed
	./rv32im.sh 
```
file:///home/lasya/Pictures/Screenshots/Screenshot%20from%202023-08-22%2018-34-47.png![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/dc2542a4-3b85-4adc-b0a7-1837aa9704df)












</details>















## DAY-3 - Digital Logic with TL - Verilog and Makerchip

<details>
  <summary>
    RV-D3SK1 - Combinational Logic in TL-Verilog in Makerchip 
  </summary>

 ## RV-D3SK1 - L1 - Introduction to Logic Gates
Introduction to Logic gates
Logic gates are fundamental building blocks of digital circuits and are used to perform logical operations on binary data, which consists of 0s and 1s. These gates are the foundational components that allow computers and other digital devices to process and manipulate information.

![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/5f10bdaa-6143-447c-8495-f6a5784c78de)


TL-verilog which is Transactional - Level verilog is a higher-level abstraction of hardware description language (HDL) used for modeling and designing digital systems at a higher level of abstraction. It's often used to describe the behavior of a system without delving into the low-level implementation details. This level of abstraction is particularly useful for system-level design and simulation.
In contrast to the traditional gate-level Verilog, which focuses on describing the circuit interconnections and physical gates, transactional-level Verilog allows designers to describe the operation of the system using more abstract constructs.

Makerchip Makerchip is an online platform and integrated development environment (IDE) that allows users to design, simulate, and implement digital systems using hardware description languages (HDLs) like TL-verilog, Verilog and VHDL. It provides a user-friendly environment for creating and testing digital designs, making it especially useful for learning, teaching, and prototyping digital circuits and systems.
This is how makerchip platform looks like(below is the example of pythagorean) 

![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/da315b60-030c-4e01-8830-de05dd3f86e6)


 
 ## RV-D3SK1 - L2 - Basic MUX Implementation and Introduction to Makerchip


Go to makerchip.com and launch Makerchip IDE.
Go to Learn, click on Examples and select FPGA multipler.

![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/b8883b97-c251-415f-bd02-36c06db3c103)

![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/566674c5-2f14-413b-ae9f-38b46c0b3a30)

![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/c42727ab-3aa6-4494-be3d-5cd4e54877d4)

![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/9371a1ca-ceac-4c49-9b85-f23c4d1e878d)

![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/3e81da6d-aada-47e3-b435-40e22a4aa791)



 
 ## RV-D3SK1 - L3 - Labs for Combinational Logic

Moving on to a combinational calculator on Makerchip ide using TLverilog
 
```
\TLV
 $reset = *reset;

 $val1[31:0] = $rand1[3:0];
 $val2[31:0] = $rand2[3:0];

 $sum[31:0] = $val1 + $val2;
 $diff[31:0] = $val1 - $val2;
 $prod[31:0] = $val1 * $val2;
 $quot[31:0] = $val1 / $val2;

$out[31:0] = $opt[1] ? ($opt[0] ? $quot : $prod) : ($opt[0] ? $diff : $sum);

*passed = *cyc_cnt > 40;
*failed = 1'b0;
\SV
  endmodule
```


![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/2c415356-49c4-4127-b27d-1946c4db531b)

 

 </details>

 
<details>
  <summary>
    RV-D3SK2 - Sequential Logic 
  </summary>

## RV-D3SK2 - L1 - Introduction to Sequential Logic and Counter Lab
Sequential Logic needs a clock for operation.

![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/c75532a3-93ae-4b62-ad17-8baa644cc731)


![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/a142c906-62e9-499c-9ebb-6a6eb9b553cc)


![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/3829f951-67d3-4a81-91a7-e2d5376f9100)


## RV-D3SK2 - L2 - Sequential Calculator Lab


![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/6fe8f1f3-97fb-4474-84fa-ea63db977668)

```
 $reset = *reset;

 $val2[31:0] = $rand2[3:0];
 $val1[31:0] = >>1$out[31:0];

 $sum[31:0] = $val1 +  $val2;
 $diff[31:0] = $val1 - $val2;
 $prod[31:0] = $val1 * $val2;
 $quot[31:0] = $val1 / $val2;

 $out[31:0] = $reset ? 0 : ($opt[1] ? ($opt[0] ? $quot : $prod) : ($opt[0] ? $diff : $sum));

*passed = *cyc_cnt > 40;
*failed = 1'b0;
\SV
endmodule

```
![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/4e3087a8-67a5-4f88-ad1a-6e70d6dba14f)





</details>


<details>
  <summary>
    RV-D3SK3 - Pipelined Logic 
  </summary>

## RV-D3SK3 - L1 - Pipelined Logic and Retiming

Pipelining or timing abstract is an important feature in TL verilog as it can be implemented very easily with fewer codes as compared to system verilog which reduces bugs to a great extent. An example of the pipeling for pythogoras theorem using both TL verilog and system verilog in this repo . In TL verilog pipeling can be implemented by defining the pipeline as |calc and the different pipeline stages should be properly align and are indicated by @1, @2 and so on.
Pipeline - Timing abstract Pipeline timing abstraction in Transaction-Level (TL) Verilog involves modeling the behavior of a pipelined digital system at a higher level of abstraction. Pipelining is a technique used to improve the throughput of digital systems by breaking down a complex operation into multiple stages, allowing multiple operations to be in progress simultaneously. Pipeline timing helps to operate at higher frequency.





## RV-D3SK3 - L2 - Pipeline Logic Advantages and Demo on Platform

Pipeline is implemented using Pythogorean theorem in hardware

![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/c01af7cd-2432-4d8b-b584-d17b92a3adb5)



Implement the Fibonacci Series in a pipeline:

![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/9340d0da-e48b-4679-8a91-987501a2b5d8)




## RV-D3SK3 - L3 - Lab on Error Condtions within Computation Pipeline

```
\TLV
$reset = *reset;

|comp
  @1
     $err1 = $bad_input || $illegeal_op;
  @3
     $err2 = $err1 || $over_flow;
  @6
     $err3 = $err2 || $div_by_zer0;

*passed = *cyc_cnt > 40;
 *failed = 1'b0;
\SV
 endmodule
```

![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/cebbc18d-a069-4cc3-9808-aab0fbcdb491)


## RV-D3SK3 - L4 - Lab on 2 Cycle Calculator


Counter 

![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/0f2a982a-7503-4de9-a6c3-d2711dcc8693)

![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/c5da1eca-37e8-4218-8792-ecaa8fb30f9d)


Cycle Calculator


![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/a012dd5f-92a3-4376-9f85-02b25c102474)

![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/d1e973ce-e928-4764-b3c0-5a298c9ba388)




</details>


<details>
  <summary>
    RV-D3SK4 - Validity 
  </summary>

In Transaction-Level Verilog (TL-Verilog), which is an extension of the Verilog hardware description language (HDL), "validity" refers to the concept of indicating whether a piece of data is valid or not. TL-Verilog is designed to facilitate high-level modeling and rapid design entry, particularly for transaction-level modeling.
A new scope, called “when” scope is introduced for this and it is denoted as ?$valid. This new scope has many advantages - easier design, cleaner debug, better error checking and automated clock gating. Validity provides :
Easier debug
Cleaner design
Better error checking
Automated Clock gating
Clock Gating: Clock gating is a power-saving technique used in digital circuit design to reduce the dynamic power consumption of a circuit by controlling the clock signal to specific components or modules when they are not actively needed. TL-Verilog can produce fine-grained gating(Enable). It involves enabling or disabling the clock signal to certain portions of a circuit based on their operational requirements. This helps conserve power by reducing unnecessary clock switching and activity. In clock gating, the clock signal is used as a control signal to enable or disable the operation of certain elements within a design. When a component's clock is gated off (disabled), it effectively stops processing and consuming power, thereby reducing power consumption. When the component's clock is gated on (enabled), it resumes normal operation.

Implementing the Pythagoran's theorem with validity:


DISTANCE ACCUMULATOR:



![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/378a529f-7838-4313-946e-b48097bfd0d7)

```
 $reset = *reset;

 |calc
 	 @1
     $reset = *reset;
        
  ?$vaild      
     @1
        $aa_seq[31:0] = $aa[3:0] * $aa;
        $bb_seq[31:0] = $bb[3:0] * $bb;;
  
     @2
        $cc_seq[31:0] = $aa_seq + $bb_seq;;
  
     @3
        $cc[31:0] = sqrt($cc_seq);
        
  @4
     $total_distance[63:0] = 
        $reset ? '0 :
        $valid ? >>1$total_distance + $cc :
                 >>1$total_distance;
```

![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/c2c9a4c8-3aca-4dd1-8cf3-9d81f4f759eb)


To implement Cycle calculator with Validity:

![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/dc90864b-7cb7-42ae-89ed-d0d837613521)

```
|calc
  @0
     $reset = *reset;
     
  @1
     $val1 [31:0] = >>2$out [31:0];
     $val2 [31:0] = $rand2[3:0];
     
     $valid = $reset ? 1'b0 : >>1$valid + 1'b1 ;
     $valid_or_reset = $valid || $reset;
     
  ?$vaild_or_reset
     @1   
        $sum [31:0] = $val1 + $val2;
        $diff[31:0] = $val1 - $val2;
        $prod[31:0] = $val1 * $val2;
        $quot[31:0] = $val1 / $val2;
        
     @2   
        $out [31:0] = $reset ? 32'b0 :
                      ($op[1:0] == 2'b00) ? $sum :
                      ($op[1:0] == 2'b01) ? $diff :
                      ($op[1:0] == 2'b10) ? $prod :
                                            $quot ;
```

![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/6e360025-1e4a-484d-9c39-910572a6b2ae)



To implement Calculator with single value memory:

![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/6599c788-5d07-4857-92e8-4b70b6d88fab)


```
|calc
  @0
     $reset = *reset;
     
  @1
     $val1 [31:0] = >>2$out;
     $val2 [31:0] = $rand2[3:0];
     
     $valid = $reset ? 1'b0 : >>1$valid + 1'b1 ;
     $valid_or_reset = $valid || $reset;
     
  ?$vaild_or_reset
     @1   
        $sum [31:0] = $val1 + $val2;
        $diff[31:0] = $val1 - $val2;
        $prod[31:0] = $val1 * $val2;
        $quot[31:0] = $val1 / $val2;
        
     @2   
        $mem[31:0] = $reset ? 32'b0 :
                     ($op[2:0] == 3'b101) ? $val1 : >>2$mem ;
        
        $out [31:0] = $reset ? 32'b0 :
                      ($op[2:0] == 3'b000) ? $sum :
                      ($op[2:0] == 3'b001) ? $diff :
                      ($op[2:0] == 3'b010) ? $prod :
                      ($op[2:0] == 3'b011) ? $quot :
                      ($op[2:0] == 3'b100) ? >>2$mem : >>2$out ;
```


![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/8d4f12d2-3449-4d55-a544-27d551dc8315)






 </details>

<details>
  <summary>
    RV-D3SK5 - Wrap Up
  </summary>
THe concept of Hierarchy is explored in Makerchip with the help of examples.


Conways Game of LIfe


![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/553aba36-a7eb-4f7e-a4d3-975de6506aa6)

Pythagoran's theorem:
```
|calc
      
      // DUT
      /coord[1:0]
         @1
            $sq[9:0] = $value[3:0] ** 2;
      @2
         $cc_sq[10:0] = /coord[0]$sq + /coord[1]$sq;
      @3
         $cc[4:0] = sqrt($cc_sq);


      // Print
      @3
         \SV_plus
            always_ff @(posedge clk) begin
               \$display("sqrt((\%2d ^ 2) + (\%2d ^ 2)) = %2d", /coord[0]$value, /coord[1]$value, $cc);
            end


```


![image](https://github.com/Sushma-Ravindra/RISCV-Workshop/assets/141133883/5d01ae5f-c734-4543-a106-58b16a407908)




 


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

