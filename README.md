# 31-Bit CPU Design in Logisim

## Learning Objectives
1. **Explore the Architecture of a 31-bit Processor** – Dive deep into its design principles and operational flow.  
2. **Build Core CPU Components** – Implement and integrate vital elements like the ALU, registers, and the control unit to bring the processor to life.  
3. **Create a Custom Instruction Set** – Design and execute your own instruction set within Logisim for practical simulation.  
4. **Master Data Flow and Memory Operations** – Gain hands-on experience with data transfer, instruction processing, and memory management.  
5. **Decode and Execute with the Control Unit** – Understand how the control unit orchestrates instruction decoding and execution.  
6. **Simulate a Full CPU Cycle** – Experience the entire process from instruction fetch to execution and result write-back.  

---

## Introduction
A **Central Processing Unit (CPU)** serves as the brain of any computing system, responsible for interpreting instructions and executing arithmetic and logical operations. This project demonstrates the design and implementation of a **31-bit CPU using Logisim**, incorporating several key components:

- **Arithmetic Logic Unit (ALU)** – Executes arithmetic and logical computations on 31-bit data.  
- **Registers** – Provide temporary storage for data and instructions during processing.  
- **Memory** – Holds both instructions and data required for execution.  
- **Control Unit** – Interprets instructions and coordinates operations by generating precise control signals.  

Each component plays a crucial role in ensuring efficient data processing and smooth execution of instructions.

---

## CPU Design Overview
- **31-bit data bus and address bus** for memory and computation.  
- **Registers**:
  - **MBR (Memory Buffer Register)** – Temporary buffer for data retrieved from memory.  
  - **MAR (Memory Address Register)** – Holds memory addresses for read/write operations.  
  - **PC (Program Counter)** – Holds the address of the next instruction.  
  - **IR (Instruction Register)** – Holds the current instruction being executed.  
  - **CPL** – Control-related register.  
  - **PLR (Parallel Load Register)** – Supports parallel data transfer.  
- **ALU** – Performs arithmetic (ADD, ISZ) and logical (AND) operations.  
- **Control Unit** – Generates control signals to execute instructions.  

---

## CPU Components

### Memory Buffer Register (MBR)
The **MBR** acts as a temporary buffer for data retrieved from memory before processing by the ALU or writing back to memory. It ensures seamless CPU-memory communication.  

### Memory Address Register (MAR)
The **MAR** holds the address of the memory location the CPU wants to access, ensuring accurate delivery of memory addresses during instruction execution.  

### Program Counter (PC)
The **PC** holds the address of the next instruction and automatically increments after each instruction, allowing sequential program execution. It can be updated during jump or branch operations.  

### Instruction Register (IR)
The **IR** holds the instruction currently being executed. The control unit decodes it to determine which operation to perform.  

### ALU
- **Arithmetic Operations:** `ADD`, `ISZ`  
- **Logical Operations:** `AND`  
- **Data Transfer:** `LOAD`, `STORE`  

### Control Unit (CU)
The **CU** manages instruction execution by generating control signals. It handles:

1. **Instruction Fetching** – Fetches instructions from memory into the IR.  
2. **Decoding** – Determines the operation type and operands.  
3. **Execution** – Coordinates with the ALU and memory to perform the operation.  
4. **Memory Access** – Reads/writes data via MAR and MBR.  
5. **Program Flow Control** – Updates PC to point to the next instruction.  

---

## Instruction Set

| INSTRUCTION | OPCODE (HEX) | INSTRUCTION | OPCODE (HEX) |
|-------------|--------------|-------------|--------------|
| AND         | 00           | BUN         | 05           |
| ADD         | 01           | LOAD        | 06           |
| STORE       | 02           | HALT        | 07           |
| ISZ         | 03           | EO          | 08           |
| BSB         | 04           | RS          | 09           |
| CMP         | A            |             |              |

---

## Instruction Execution Process
1. **Instruction Fetch:** PC → MAR → IR  
2. **Instruction Decode:** CU decodes the opcode and operands.  
3. **Instruction Execution:** ALU performs computation or memory transfer.  
4. **Write Back & PC Update:** Result stored, PC updated for next instruction.  

---

## Sample Program on RAM
