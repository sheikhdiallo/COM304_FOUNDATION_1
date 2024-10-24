[Main Menu](../../sessions/README.md) | [session6](../session6/) | [Subroutines and Stacks](../docs/stacks-routines.md)

# Subroutines and Stacks

A key concept in programming is the use of subroutines or procedures, which are sections of code that perform a specific function and can be repeatedly called from many different parts of the main program

In order to enter a subroutine, the processor must first save whatever it was doing i.e. the registers which contain the current data before starting to the new routine.

When the subroutine finishes, the processor must restore the previous state and jump back to the next instruction after the instruction which caused the jump to the subroutine.

A Stack is a common mechanism which enables this behaviour.

`Stacks` are regions of memory which are reserved for storing subroutine states and passing variables between subroutines.
The top of the stack is pointed to by a `Stack Pointer`.

In the ARM chip has three registers for handing program flow and the stack.

| name               | function                        |
|:-------------------|:--------------------------------|
|R13 (SP)            | Stack Pointer                   |
|R14 (LR)            | Link Register<BR>LR is link register used to hold the return address for a function call.                   |
|R15 (PC)            | Program Counter<BR> The PC value is altered as the core executes instructions. An explicit write to R15 by software will alter the program flow. |

The Program Counter always points to the next instruction to be executed. 
It is incremented as each instruction completes.

If a program wants to jump to a subroutine, an instruction causes the starting address of the subroutine to be loaded into the program counter.

|                     |Address | instruction       |  registers                                         | stack                                                   |explanation    |
|:--------------------|:-------|:------------------|:---------------------------------------------------|---------------------------------------------------------|---------------|
|main program         |        |                   |PC 0x0000<BR>LR 0x0000<BR>SP 0x0000<BR>R4 0x0001    |0x1000 - 0x0000                                          |               |
|                     | 0x0001 | bl 0x8ab0         |PC 0x0001<BR>LR 0x0000<BR>SP 0x1000<BR>R4 0x0001    |0x1000 - 0x0000                                          |(1) Jump to subroutine at address  0x8ab0<BR>record next instruction address in LR |
|                     |        |                   |PC 0x8ab0<BR>LR 0x0002<BR>SP 0x1000<BR>R4 0x0001    |0x1000 - 0x0001                                          |(6) resume main program - now in continuous loop to end              |
|                     |        |                   |                                                    |                                                         |               |
|                     | 0x0002 | bl 0x0002         |PC 0x0002<BR>LR 0x0003<BR>SP 0x1000<BR>R4 0x0001    |0x1000 - 0x0000                                          |Continuous loop indicating end of program |      
|                     |        |                   |                                                    |                                                         |               |
|subroutine           | 0x8ab0 | push {r4, lr}     |PC 0x8ab0<BR>LR 0x0003<BR>SP 0x1003<BR>R4 0x0001    |0x1000 - 0x0001<BR>0x1002 - 0x0001<BR>0x1003 - 0x0003<BR>|(2) Push r4 and LR onto stack              |
|                     |        |                   |                                                    |                                                         |(3) Do main instructions of subroutine before returning              |
|                     | 0x8ab1 | pop {r4,pc}       |PC 0x0002<BR>LR ------<BR>SP 0x1003<BR>R4 ------    |0x1000 - 0x0000                                          |(4) Pop r4 off stack pop LR off stack INTO PC which causes a jump  |
|                     |        |                   |PC 0x0002<BR>LR 0x0003<BR>SP 0x1000<BR>R4 0x0001    |0x1000 - 0x0000                                          |(5) Jump back to main program at 0x0002              |





|subroutine           | 0x8ab2 | bx lr         |PC 0x0002<BR>LR 0x0003<BR>SP 0x1000<BR>R4 0x0001    |0x1000 - 0x0000 |  push r4 and LR onto stack              |
|                     |        |                   |                                                    |                 |               |
|                     |        |                   |                                                    |                 |               |