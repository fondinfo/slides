![](http://fondinfo.github.io/images/sys/motherboard-example.jpg)
# Computers
## Introduction to Computer Science <br> Michele Tomaiuolo @ Ingegneria UniPR

---

![](http://fondinfo.github.io/images/hist/1837-analytical-engine.jpg)
# 💡️ Computer

- *Programmable* machine
    - Automatically stores and processes…
    - Data in discrete format (I/O)…
    - According to program instructions
- Different *computation models*
    - Elementary operations and the concept of algorithm
    - Def. computability: solvable problem, or not
- 1837, Charles Babbage, *Analytical Engine*
    - Projects only: ALU, CU, memory, decimal base
    - “Turing complete” model with *branching* and *loop*
    - Ada Lovelace, “program” for Bernoulli numbers

---

![](http://fondinfo.github.io/images/hist/zuse.jpg) ![](http://fondinfo.github.io/images/hist/eniac.jpg)
# 💡️ First Computers

- 1941, *Z3* (Berlin, Konrad Zuse)
    - First programmable computer
    - Binary floats, no jumps, *relay-based*
    - Program on tape, limited memory
- 1946, *ENIAC* (Philadelphia)
    - Base 10, branching, wired program
    - 6 programmers: Jean Bartik, Kay McNulty, Betty Snyder…
- Impetus from *WWII* and Cold War
    - Ballistics, weather, Manhattan project, H-bomb…

---

![](http://fondinfo.github.io/images/hist/von-neumann.jpg) ![](http://fondinfo.github.io/images/sys/von-neumann-architecture.svg)
# 💡️ Von Neumann Architecture

- Data and code in *Random Access Memory*
    - Theoretical UTM model (Turing, 1936)
    - But RAM → *jumps*, *branching*, *subroutines*
- 1945, JvN: “*First Draft of a Report on the EDVAC*”
    - 1951, successor to ENIAC, JvN consultation
    - Designs by Eckert & Mauchly @ UPenn
- 1948, *SSEM* or *Manchester “baby”*
    - Data and programs in RAM
    - → 1949, Mark 1

>

[Henin (2013). “The Stored Program”. Mondo digitale #46.](https://www.dropbox.com/s/iayjm8k60o1vf9z/06_Henin.pdf?dl=1)

---

# 💡️ Computer girls

![large](http://fondinfo.github.io/images/hist/women-in-cs.jpg)

>

Grace Hopper, Margaret Hamilton — Women in CS courses: 37%, 1983 → 18%, 2013

---

# ⭐ Central Processing Unit

- CPU: “brain” of the computer
    - Executes programs
    - Controls other parts of the computer
- Composed of two parts:
    - **Control Unit (CU)**: interprets instructions, commands other parts of the CPU, controls flow between CPU and memory
    - **Arithmetic Logical Unit (ALU)**: performs arithmetic and logical operations, performs data comparisons

---

# ⭐ CPU Architecture

![large](http://fondinfo.github.io/images/sys/cpu-architecture.png)

---

![](http://fondinfo.github.io/images/sys/settling-time.svg) ![](http://fondinfo.github.io/images/sys/propagation-delay.png)
# 🔬 Synchronous Logic Circuits

- Switching delay of logic gates
    - `0→1 / 1→0` transition
    - Signal transition ≠ step
    - Delay, overshooting, ringing
    - Due to parasitic capacitances and inductances
- *Clock* regulates the entire circuit
    - Time to stabilize all signals

---

# ⭐ Main CPU Cycle

- **Fetch**: CU retrieves the instruction from the memory location indicated by the PC (Program Counter) register and stores it in the IR (Instruction Register)
- **Decode**: CU interprets the instruction, optionally reads necessary data from memory
- **Execute**: CU commands the parts
- **Store**: results stored in main memory or CPU registers

---

# ⭐ Reading from Memory

![large](http://fondinfo.github.io/images/sys/cpu-memory.svg)

---

# 🔬 Read Sequence

![large](http://fondinfo.github.io/images/sys/cpu-read-1.svg)

---

# 🔬 Read Sequence

![large](http://fondinfo.github.io/images/sys/cpu-read-2.svg)

---

# 🔬 Write Sequence

![large](http://fondinfo.github.io/images/sys/cpu-write-1.svg)

---

# 🔬 Write Sequence

![large](http://fondinfo.github.io/images/sys/cpu-write-2.svg)

---

# 🔬 Instruction Fetch

![large](http://fondinfo.github.io/images/sys/cpu-fetch.svg)

---

# 🔬 Instruction Interpretation

- At the end of the *fetch* phase, IR contains the instruction to be executed
    - **Opcode + operands**
    - *Machine language*: meaning depends on the CPU
- In the example: **`5`** `012$_{hex}$` = **`0101`** `0000 0001 0010$_{bin}$`
    - Opcode = **`0101$_{bin}$`**
    - E.g. Read a word from the accumulator register...
    - And store it in a memory address (operand)

---

# 🔬 Instruction Execution

![large](http://fondinfo.github.io/images/sys/cpu-exec.svg)

---

![large](http://fondinfo.github.io/images/sys/motherboard.svg)
# ⭐ PC Architecture

![small](http://fondinfo.github.io/images/sys/motherboard-example.jpg)

- *Northbridge*, now integrated into the CPU
    - Graphics & Memory Controller Hub (GMCH) : ~ 50 GB/s
- *Southbridge*, or “chipset”
    - Disks and I/O peripherals : ~ 500 MB/s

---

![large](http://fondinfo.github.io/images/sys/flynn.svg)
# ⭐ Flynn's Classification

- **Parallelism**: ↑ performance, with same speed per single instruction
    - S/M: single/multiple
    - I/D: instruction/data
- *SISD*: one operation at a time; traditional single-processor and core machines
- *MISD*: unusual, for fault tolerance; heterogeneous systems, on the same data, must yield the same results
- *SIMD*: naturally parallelizable operations; vector computing units and GPUs
- *MIMD*: different instructions on different data; architectures with multiple cores or autonomous processors, distributed systems

---

# ⭐ Assembler

- **Machine language**: defines the instruction set understandable by the CPU
    - *CISC*: Complex Instruction Set Computing
    - *RISC*: Reduced Instruction Set Computing
- Assembler: translates from **assembly language** (mnemonic) to machine language (1~1 mapping)
- Ex. *x86 Assembly* → machine (variable-length instructions)

``` asm
MOV AH, 11 → 1011 0 100 00001011
```

- 4 bits for op-code (`1011`), instruction type
- `w` bit (`0`): 8-bit or 16-bit operation, (0 or 1 resp.)
- 3 bits for destination register (`100`)
- 8 bits of data for operand: `11$_{dec}$` = `00001011$_{bin}$`
