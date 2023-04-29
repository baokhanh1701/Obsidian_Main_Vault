# A. Memory-related data structures in the kernel
# Introduction
### Process's memory

Traditionally, a Unix process is divided into segments. The standard segments are: 
- code segment, 
	- Binary code of the program (running as the process)
- data segment, 
	- Global vars, data structures
- BSS (block started by symbol), 
	- Unitialized global data structures
- and stack segment.
	- Local vars, return addresses,...

Under Linux, a process can execute in 2 modes:
#### User mode (usually executed)
When a process is running in user mode, it is said to be “in userland”.
blue regions represent virtual addresses that are mapped to physical memory, 
whereas white regions are unmapped.
![[Pasted image 20230316115147.png]]
### Consists of (in Each)
##### Code segment: 
If we have a function `func()` and let `p` be the address of `func() (p = &func;)`. We know that p will point within the code segment.
##### Data segment: 
- The initialized variables
- To get the address of the data segment we declare a global variable and then print out its address. This address must be inside the data segment.
##### BSS
- The uninitialized global variables of a process. To get an address which occurs inside the BSS, we declare an uninitialized global variable, then print its address.
##### Stack
- Automatic variables (local variables) will be allocated on the stack.
- Printint out the address of local vars will provide us with the addresses within the stack segment.
- Handle function calls.
- Starts at a high address in memory and grows down to increase its size.
- Usually, the value of stack pointer is hold by stack pointer register inside the processor. Stack space is limited, we cannot extend the stack exceed a given size. 4 If we do so, stack overflow will occurs and crash our program. To identify the default stack size, use the following command: `ulimit -s`
- Different from heap, data of stack are automatically allocated and cleaned through procedure invocation termination, Therefore, in C programming, we do not need to allocate and free local variables. In Linux, a process is permitted to have multiple stack regions. Each regions belongs to a thread.
#### Kernel mode (system calls)
when it is running in kernel mode it is said to be “in kernel space”.

### Interprocess Communication
- **Information sharing**: 
	- Since several applications may be interested in the same piece of information (for instance, copying and pasting), we must provide an environment to allow concurrent access to such information. 
- **Computation speedup**: 
	- If we want a particular task to run faster, we must break it into subtasks, each of which will be executing in parallel with the others. Notice that such a speedup can be achieved only if the computer has multiple processing cores. 
- **Modularity**: 
	- We may want to construct the system in a modular fashion, dividing the system functions into separate processes or threads.

> Therefore, we need communication methods to transfer data among processes, which are also known as inter-process communication (IPC) protocols.

	For example, a Web browser may request a Web page from a Web server, which then sends HTML data. This transfer of data usually uses sockets in a telephone-like connection.
		The shell creates an ls process and a separate lpr process, connecting the two with a pipe, represented by the "|" symbol.
		A pipe permits one-way communication between two related processes.
		The ls process writes data into the pipe, and the lpr process reads data from the pipe.

