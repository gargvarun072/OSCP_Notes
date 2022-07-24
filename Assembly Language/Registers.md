Registers

# Registers

### General Purpose Registers 

1. *EAX(Accumulator Register)* - It is generally used for arithmetical and logical instructions. Also used for storing operands and result data 
2. *EBX(Base Register)* - It is used to store the value of the offset(Pointer to data) 
3. *ECX(Counter Register)* - It is used in looping and rotation 
4. EDX(Data Register) - It is used in multiplication an input/output port addressing 
5. *ESI(Source Index)* - It is used in the pointer addressing of data and as a source in some string related operations. It’s offset is relative to data segment
6. *EDI(Destination Index)* - It is used in the pointer addressing of data and as a destination in some string related operations. It's offset is relative to extra segment 
7. *ESP(Stack Pointer)* - It points to the topmost item of the stack. If the stack is empty the stack pointer will be (FFFE)H. It’s offset address relative to stack segment 
8. *EBP(Stack Data Pointer)* - It is primary used in accessing parameters passed by the stack. It’s offset address relative to stack segment 
9. *EIP(Instruction Pointer)* - The EIP register contains the address of the next instruction to be executed 

### Segment Registers
It is used to keep track of segments and to allow backward compatibility 

1. CS 
2. DS  
3. SS 

### Control Registers
It is used to control the function of the processor  

***EIP(Instruction Pointer)*** - The EIP register contains the address of the next instruction to be executed 

 