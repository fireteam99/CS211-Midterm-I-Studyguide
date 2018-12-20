# CS211 Midterm I Study Guide
## Recent Trends In Hardware
### Main Components In Computer
Include: Cpu, Memory, Bus, I/O devices like keyboards, graphics, neworking, and storage.
### Von Neumann Model
Computers are seperated into three parts: memory, control unit, and arithmetic and logic unit. Memory stores data and instructions. The control unit fetches further instructions. The arithmetic and logic units do operations based on the instructions passed.
### Basic CPU Function
Fetch --> Decode --> Execute
### Running on Hardware
**High - Level Language**

```c
x = x + y;
```   
**Assembly Language**

```nasm
mov -0x8(%esp),%ebx
add %ebx, %eax
```  
**Machine Language**

```
7F 45 4C 46 01 01 01…
```  
### Operating System
Provides essential services to programs running on hardware such as virtual memory, multitasking, etc...
### Moore's Law
An observation that the number of transistors on chip double every 18 months. Can also be seen in processor speed, memory capacity, and disk capacity, which doubles 18 months, two years and every year, relativly speaking.
## The C Language
### Compared to Java
Java source code is compiled into byte code, runs in the jvm and finally on the hardware and OS. C is compiled and run in the hardware and OS.
### Comments
Denoted using `/* */` or `//`
### Variable Declaration
Starts with an optional modifier, type and then the name. `short int x;` `long double y;` `char z;`
### Basic Datatypes
There exits: ***char***, ***int***, ***float***, ***double***, with modifiers ***short***, ***long***, and ***signed***, ***unsigned***.
### Arithmetic Operatiors
Contains `*, /, %, +, -, ++, --`. Remember that `x++` changes the value after it is used and `++x` changes the value before it is used. Same with `x--` and `--x`.
### Relational Operators
Includes: `>, >=, <. <=, ==, !=`. The result is 1 (TRUE) or 0 (FALSE).
### Bit Operators
Contains the symbols: `~` complement used as `~x`, `&` bit AND used as `x & y`, and `|` bit OR used as `x | y`.
### Expressions and Assignments
Expressions are computations with a result. Example: `x + y * z`. Be aware that c does explicit type conversion with double being the rank and char/short int being the lowest rank. Assignments work by setting the value of an expression to a variable. Example: `a = x + y * z`.
### Control Statements
Conditional: if else, switch. Iteration: while, for, do while. Goto: break, continue, goto.
### If Statements
Keeps on evaluating expressions until one found with non-zero result.

```c
if (condition 1) {
    body...
} else if (condition 2) {
    body...
} else {
    body...
}
```

### Switch Statements
Evaluates an integer expression and after finding the 1st case with matching case and executes statements until encountering break or end of switch. Remember to include a default case.

```c
switch (expr) {
    case 1:
        statement 1;
    case 2:
        statement 2;
    defualt:
        statement 3;
}
```
### Loops

```c
// for
for (i = 0; i < 10; i ++) {
    ...
}
// while
while (i < 10) {
    ...
    i++;
}
// do while
do {
    ...
    i++
} while (i < 10)
```

### Specialized Go-to's
The `break` statement forces an immediate exit from switch or loop and goes to the code following that switch or loop. The `continue` statements skips the rest of the code in the body of a loop and restarts the loop.
### Functions
Components include: Name, Return type, Parameters, and Body.

```c
int Factorial(int n) {
	int i;
	int result = 1;
	for (i = 1; i <= n; i++) {
		result *= i;
	}
	return result;
}
```
### Function Calls
Functions that are not void can be used as a part of an expression `x = factorial(5)`. Functions that are void can be used as a statement `printList()`.
### Function Prototypes
In c, function prototypes are required when you use a function before you have implemented it.
### Input and Output
Contained in `stdio.h`. Two common functions are `printf("%d\n", counter);` and `scanf("%d", &startPoint);`.
### Memory
C's memory model is the same as the underlying virtual memory system. Variables are simply names for contiguous sequences of bytes. Variable names are equivalent to memory addresses.
### Pointers
Pointers are a variable that store an address. Declared as `type *pointer_name`. `*` is the dereference operator which ives the value stored at the address pointed to: `*p`. `&` gives the address of a variable: `&v`.
### Null Pointer
NULL is a predefined constant that contains a value that is an illegal address so we know it points to nothing. Usually `Null = 0`.
### Type Casting
Note that C is not strongly typed.
### Arrays
Arrays are contiguous sequences of data items of the same type. Declaration: `type name[amount]` --> `int nums[10]`
Array indexes always start at zero. C compiler and runtime does not check for boundaries.
### Array Storage
Elements in array are stored contigously in memory so if you know where the first item is and the length, you can access every element using offsets.
### Arrays and Pointers
Arrays are basically syntactic sugar for pointers.

```c
 char word[10];
 char *cptr;
 cptr = word; /* points to word[0] */
```
### Pointer Arithmetic
You can increment or decrement pointers by an offset to access memory adjacent to the pointer. Don't go out of bounds.
### Passing Arrays as Arguments
Arrays are passed by reference but array items are passed by value. This means there will be pointer decay and the size of the array is lost when passed to a function.
### Common Array Errors in C
Do not overrun array limits due to no out of bounds checking and the size of an array must be known at compile time.
### Strings
C strings are stored as arrays of characters with a null terminator. Make sure you leave an extra space for `\0`.
Some useful functions include strcpy, strcmp. and strlen.
### Structures
Groups together related data of different data types kind of like objects. Defined as:

```c
struct person {
	int height;
	int weight;
	char *name;
};
```
It tells the compiler how big the struct is and how the data items are laid out in memory. To declare a struct: `struct person john;`. Declaration can be simplified by using a typdef.


```c
typedef struct Persons {
int height;
	int weight;
	char *name;
} Person;
```
Now we can declare a person by simply doing `Person john;`.
### Pointer to Structs
To declare a pointer to a struct: `struct Person *john;`. To access members of struct we can use the dot operator `.` and dereference it `(*person).name` or just the special arrow operator `->` directly `person->name `.
### Dynamic Allocation
We need dynamic memory allocation when we don't how much data we have during compile time. These variables are declared on the heap rather than the stack.
### Memory Management 101
When a function call is performed the run-time system allocates resources such as local vars, arguments, and results. The state associated with a particular function is called an ***activation record***.
### Allocating on the Stack
The stack grows downwards in the activation record and when the function call returns, all activation records are removed.
### Allocating on the Heap
Also known as dynamic memory allocation, we ask the run time system for a chunk of memory which lives on after the function that created it has returned unlike variables on the stack. Commands include: `malloc` for creation and `free` for destruction.
### Using malloc
The sizeof operator returns the size of either a type or a variable. Use that multiplied by the amount of the data type you want stored `int *nums = malloc(sizeof(nums) * count);`.
### Using free
You need to free unused memory to prevent leaks. `free(nums);`
### typedef
Used to name types for convenience. `typedef <type> <name>;`
### Preprocessor
Examples are include statements and macros.
`#include <stdio.h>;`
`#define MAX_SIZE 12;`
### Standard C Library
Lots of useful stuff in it for I/O, String handling, File Manipulation, etc...
### Command Line Arguments
When using shell: `$ hello 5` white spaces are used to sperate characters but is shell dependent. `argc` contains the count of command arguments passed + 1 because the first command line argument will be the name of the program. Likewise, `argv[]` will contain the strings themselves, but remember `argv[1]` is usually the name of the program.
### fopen
Opens a file in your program. `FILE *fopen(char* name, char* mode);` The first argument is the path of the file you want to open and the second argument contains the modes `r` for read, `w` for write starting at the beginning of the file and `a` for writing starting at the end of the file.
### fprintf and fscanf
Once open, a file written to or read from using `fprintf()` like: `fprintf(outfile, "The answer is %d\n", x);` and `fscanf()` like `fscanf(infile, "%s %d/%d/%d %lf",
 &name, &bMonth, &bDay, &bYear, &gpa);`.
Remember that programs have three streams open `stdin, stdout, sterr`.
### Multidimensional Arrays
On the stack they can be declared as `array[ROWS][COLS]`. When passing them to a function, the rows dimension can be dropped, but the number of culumns is needed. `void transpose(double matrix[][3]);`
### Double Pointers
Single pointers and single dimension arrays can be used interchangably but for higher dimensions char[X][Y] is simple an array of arrays all of the items are stored contigously in memory as a rectangle. It would look something like this: `char[2][2] = [item(0,0) , item(0,1), item(1,0), item(1,1)]`. On the other hand, `char **argv` is just a pointer to a pointer.
### Allocating Multidimensional Arrays
#### Single Pointer
There are two ways you can dynamically allocate a 2d array. The first is to flatten the 2d array by allocating `x = rows * cols` memory using `data_type *arr = malloc(sizeof(data_type) * x)`. Afterwards you can access the nth row and mth column using this offset: `arr[n*cols) + m]`  This is similar to how the stack allocates 2d arrays. 
#### Double Pointer
First allocate a 1d array of pointers corresponding to how many rows the array has. `data_type **arr = malloc(sizeof(int *) * rows);`. Then you use a nested for loop make each of those pointers point to a 1d array of the actual data you want. `arr[i][j] = malloc(sizeof(int) * cols);`
### Compilation
**C Source code --> Pre-processor --> Compiler --> Assembly --> Assembler --> Relocatable Object --> Linker --> Executable**  
Seperate compilation follows the same steps but links the multiple relocatable objects together at the end.
## Datatypes
### Running on Hardware
The ISA (Instruction Set Architecture) interfaces between the soft ware and hardware.
### Base n Notation
Numbers are written as a sequence of digits that are multiplied by a place value. For example in base 10, one hundred and twelve is written as: `1 * 10^2 + 1 * 10^1 + 2 * 10^0`
### Base 2: Binary
The only digits are 0 and 1 in binary. A bit is one binary digit. Binary is good for computers because you can represent them as on/off switches, but are hard to read for humans.
### Base 16: Hexadecimal
Digits include 0-9 and A-F which represent ten through fifteen. Since 16 = 2^4, one hex digit is 4 bits. Bytes are two hex digits (00-FF).
### Base 8: Octal
Digits are 0-7. More compact that binary where one octal digit is 3 bits.
### Base Conversions
You want to convert the number you are changing to base 10 first. Then you can repeatedly divide by the base you want to the whatever power you need and then divide again until there is no remainder. To convert 100 to base 8, we know its 1(8^2) + 4(8^1) + 4(8^0) = 144base8
### Base n Rationals
Decimals can be represented past the "radix" (decimal) point by multiplying by negative powers of n.
### Value vs Notation
Decimals, binary, and hex are just ways to write numbers. Computers use binary to encode integers and perform arithmetic. Computers simply convert to decimal when outputting floats and ints.
### Data Sizes
Primitive number types used a fixed number of digits and are usually multiples of 8 as 8 bits = 1 byte. Chars are 1 byte, ints are 2 or 4 bytes, pointers are 4 or 9 bytes, floats are 4 bytes, and doubles are 8 bytes.
### Big and Little-Endian
Large data types consist of multiple bytes so you have to split them up to store them. Lets consider a large number like `AB10CD2F`. Big Endian stores the most significant byte at the smallest address `AB 10 CD 2F`. Little Endian stores the least significant byte at the smallest address `2F CD 10 AB`. Most network standards are big-endian and some file formats have byte-order marks.
### Encoding Data
We can encode things by using bits. For example a playing card has 4 suits, and 13 ranks. We can simply use one byte - where 4 bits represent the rank and 2 two bits which represent the suit.
### Negative Integers
In writing we denote negative numbers with a negative sign `-`. We can designate a bit to be the signed like `4 = 0100` and `-4 = 1100` but this results in two zero values which is inconvenient for arithmetic `0 = 0000` and `-0 = 1000`.
### 1s' Complement
We can find -x by simply negating the bits of x. `001 = 1` `110 = -1`
However, there are still two zeros and is inconvenient for arithmetic.
### 2s' Complement
We can make the most significant bit negative so that to find -x we simply negate the bits in x and add 1. This gets rid of the extra zero problem but there in an extra minimum value. Adding, subtracting, and multiplying works without changes so it is used on most computers. Remember that in the first bit, 0 signifies positive and 1 signifies negative. `100 = -4` `101 = -3` `110 = -2` `111 = -1` `000 = 0` `001 = 1` `010 = 2` `011 = 3`
### Range of 2s' Complement
For unsigned integers, k bits you can represent 2^k values. If they are natural numbers the range is `0 through 2^k-1`. However for 2s' complement the minimum value of x for k bits is `-2^(k-1)` and the maximum value is `2^(k-1) - 1`. This is because we add one to a two's complement number.
### 2'z Complement Addition & Subtraction
Addition is the same as unsigned binary addition but subtration requires us to invert the subtrahend and add. We also ignore the carries.
### Multiplication
It's the same thing as normal multiplication but just with ones and zeros. We only need to know add and shift to multiply.
### Divison
It's complicated.
### Unsigned Ints in C
Declared as `unsigned int i = 10;`. To cast just do `i = (unsigned) j;`. Casting will leave bits unchanged so `(unsigned) -1 = 2^k = 1` where k is the number of bits the integer has.
### Bit Shifting
The operators `<<` and `>>` shift an integer by some number of places to the left or right. Remember that shifting left is equivilent to multiplying by 2 `n << c = n × 2^c` and shifting right is equivilent to dividing by 2 `n << c = n × 2^c`.
## Floating Point
### Scientific Notation
A more compact way of writing long decimal numbers by distinguishing magnitude from precision. In base 10 we have `1,250,000 = 1.25 × 10^6` and in base 2 we have `0.00101 = 1.01 × 2^-3`.
### Fixed-Point Numbers
We need to chose an exponent (b^e) and mantissa (m) which are both integers. For example for 10.50 `m = 1050 ` and `b^e = 10^-2`. We can simply use integer operations to add and subtract. To multiply we use integer multiplication and then we multuply by b^e. For example: `(45 × 10-2)(1000 × 10-2) = (45 × 1000 × 10-2) × 10-2 = 450 × 10-2`. Remember that values closer to 0 are more precise because floating point numbers get more dense.
### IEEE 754 Floating-Point
This is the most commonly used representation for floating-oint and defines single (32 bit), double (64 bit), and extended (80 bit) precisions. Some processors support half (16 bit) or quad (128 bit) too.
### Normal Values
IEEE FP numbers have three parts: the sign `s`, exponenet `e`, and significand `m`. `s` is always one bit but `e` and `m` depend on the precision. Normal values are represented as `(-1)^s * m * 2^(e - bias(E))`, where 1 ≤ m < 2. The `bias(E) = 2^(E–1)–1`, where E is the number of bits in e where `e ≠ 0` and` e ≠ 2^(E–1)`(e.g., all ones). Note that it might be easier to memorize bias(E) as a single zero and then `E-1` ones. For example: `Bias(10) = 0111111111` or `Bias(6) = 011111`.
### Other Values
Zero and denormal values are less than any normal value. This is when `(-1)^s * m * 2^(e - bias(E)`, where `0 ≤ m < 1`. The value is zero when `m = 0` and `e = 0`. Denormal if `m ≠ 0 and e = 0`. Denormal numbers are extremely small. There are also nonfinite values `±∞` if `m = 0` and `e = 2^E –1` (all ones) and NaN if `m ≠ 0` and `e = 2^E –1` (all ones).
### Conversion from Decimal to FP
Before we begin we know E stands for bits in the exponent and M stands for bits in the mantissa. In IEEE single precision, the exponent has E = 8 bits and the mantissa has M = 23 bits. Lets convert `5.625` to floating point. This number is positive so we know our sign bit is going to `0`. Next we rewrite it in binary: `101.101`. Then rewrite in binary scientific notation: `1.01101 * 2^2`. In order to find the stored exponent we must first add our bias which can be found using the formula `2^(E-1) - 1`. Plugging in, we have `2^(8-1)-1 = 127` and we complete the calculation adding it to our exponent `2 + 127 = 129`. In the last step, we convert `129` to binary which is `10000001`. We then drop the integer part of m and extend to M bits: `1.01101 --> 0.1101 --> 01101000000000000000000`. Now that we have s, e, and m, just put them in order to get: `0 100000001 01101000000000000000000`. [Here is a good tutorial for decimal to FP.](https://www.youtube.com/watch?v=tx-M_rqhuUA&t=6s)
### Conversion from FP to Decimal
The decimal number is given in the following formula: `(-1)^s * (1 + m) * 2^(e - Bias(E))`. Lets try to convert the floating point number `1000 1000 1000 1000 1000 0000 0000 0000` to decimal. Off the bat we know our sign bit `s = 1`, our exponent `e = 0001 0001`, and our mantissa is the remaining `m = 0001 0001 0000 0000 0000 000`. Now we need to convert our exponent to it's actual form by subtracting the bias. In this case our bias is 127 so `0002 0001 = 17 --> 17 - 127 = -110` so e = -110. Last we convert `0001 0001 0000 0000 0000 000` tp base 10 which is `0.06640625`. Finally, we put all of the numbers into the formula and get `(-1)^1 * (1 + 0.06640625) * 2^(-110) = -1.06640625 * 2^-110`. So our final answer is **-1.06640625 * 2^-110**. [Here is a good tutorial for FP to decimal.](https://www.youtube.com/watch?v=4DfXdJdaNYs)
### FP in general
*Some things to be aware of...*

* The single digit in front of the radix is dropped in the mantissa as it is implied by the exponent.
* If the dropped digit is 1 then value is normal if 0 then value is denormal
* If the exponent is all 0s but not the mantissa, the number is denormal
* If the exponent is all 1s and the mantissa is all 0s, number is positive or negative infinity based on the sign bit
* If the exponent is all 1s but mantissa is not all 0s, number is NaN

## Assembly
### Programming Meets Hardware
High-Level Language Program --> Assembly Language Program --> Machine Language Program
### Performance with Programs
1. Program: Data structures + algorithms
2. Compiler translates code
3. Instruction set architecture
4. Hardware Implementation

### Instruction Set Architecture (ISA)
ISA is a set of instructions that the CPU can execute. It also gives information on the state of the system regarding registers, memory state, and program counter. Example: what instruction to execute next, how many and how large registers are, and how we specify memory addresses.
### IA32 (X86 ISA)
There are many assembly languages as they are processor-specific. Some examples are IA32, IA64, PowerPC, and MIPS.
### X86 Evolution
8086 – 1978 – 29K transistors – 5-10MHz  
I386 – 1985 – 275K transistors – 16-33 MHz  
Pentium4 – 2005 – 230M transistors – 2800-3800 MHz  
Haswell – 2013 – > 2B transistors – 3200-3900 MHz  
Some added features include larger caches, multiple cores and support for data parrallelism (SIMD, and AVX extensions.
### CISC vs RISC
CISC (complex instruction set) are usex by x86 have more complicated instructions but reduce code size and have a more complex hardware implenetation. RISC (reduce instruction set) like ARM have simpler instructions but large code size, and simpler hardware implmentation.
Note that CISC implementation like x86 are good for backwards compatability but bad for taking advantage of hardware advances.
### Assembly Programming
We use assembly because it interfaces closely with hardware. It is better than binary because it is much easier for us to read and we can use relative instead of absolute addresses.
### Memory
The main memory is a massive array of bits where we can store and read information from.
### Processor: ALU and Registers
The ALU performs arithmetic and logical operations while the registers act as temporary storage for information we need to work with.
### C, Assembly Code and Machine Code
Suppose we have the following c code:

```c
int accum;
int sum(int x, int y)
{
	int t = x + y;
	accum += t;
	return t;
}
```
We can convert it to assembly using `gcc -O1 -m32 –S code.c`.

```nasm
sum:
	push %ebp
	movl %esp, %ebp
	movl 12(%ebp), %eax
	addl 8(%ebp), %eax
	addl %eax, accum
	popl %ebp
	ret
```
We can get machine code using `objdump –d code.o`.

```
0000000 <sum>:
 0: 55 						push %ebp
 1: 89 e5 					mov %esp,%ebp
 3: 8b 45 0c 				mov 0xc(%ebp),%eax
 6: 03 45 08 				add 0x8(%ebp),%eax
 9: 01 05 00 00 00 00 		add %eax, accum
 f: 5d 						pop %ebp
 10: 						c3 ret
```
### Assembly Characteristics
#### Data Types
Assembly has no real data types. There is only integer data of 1, 2, or 4 bytes of data values and address (untyped pointers), Floating point data of 4, 8, or 10 bytes, and contigiously allocated bytes in memory that are equivilent to arrays and structures. 
#### Type Checking
Note that there is no type checking so there is no protection from misinterpretation of data.
#### Operations
The only operations allowed are arithmetic function on register or memory data, transfering data from memory and register, and transfer control in the form of unconditional jumps and conditional branches.
### x86 Characteristics
There are variable length instructions from 1 to 15 bytes, can address memory directly in most instructions, and uses Little-Endian format.
### Instruction Format
Generally we have `opcode operands`. Opcodes are short memonics for instructions purpose like `movb` or `addl`. Operands can be immediate, register, or memory. The number of operands passed depend on the command. For example: `movl %ebx, (%ecx)`.
### Machine Representation
`[ OPCODE | ADDRESSING MODE | OTHER BYTES ]`  
Assembly instructions are translated into a sequences of 1-15 bytes where the first part is the binary opcode and then instruction for the addressing mode which include the type of operands and how to interpret the operands. Some instructions like `push` are single byte because their addressing mode are implicitly specified.
### x86 Regusters
General purpose registers are 32 bits with 16 and 8 bit subregisters contained within. There are data registers (EAX, EBX, ECX, EDX) and pointer/index registers (EBP, ESP, EIP,ESI,EDI), and segment registers (CS, DS, SS, ES).
### Data Format
We have **Byte**: 8 bit, **Word**: 18 bits, **Double Word**: 32 bits, **Quad Word** 64 bits. Instructions can operate on any data size: `movl` on double word, `movw` on word, `movb` on byte.
### MOV Instruction
Follows the format `Mov SRC, DEST` where SRC and DEST are operands. SRC can be the contents of register, memory location, constant, or a label. DEST is a register or location in memory. MOV is used to copy data from constant to register, memory to register, register to memory, or register to register. You cannot copy memory to memory in a single instruction.
### Immediate Addressing
The operand (value found immediatly followign instruction) is encoded in 1, 2, or 4 bytes. There must be a `$` in front of the immediate operand. For example `movl $0x4040, %eax` moves the hexidecimal 4040 into register eax.
### Register Mode Addressing
We use `%` to denote a register: `%eax`. We use the value stored in the source operand and another register as destination for value.

```nasm
movl %eax, %ebx 	; Copies content of %eax into %ebx
movl $0x4040, %eax 	; Immediate addressing, copies 0x4040 into %eax
movl %eax, 0x0000f	; Absolute addressing, copies contents of %eax to memory location of 0x0000f
```
### Indirect Mode Addressing
We use the content of operand as an address. Designated with parentheses around operand. An offset can be specified as immediate mode. We can think of this as dereferencing a pointer. When using an offset, we can think of it as something similar to pointer arithmetic.

```nasm
movl (%ebp), %eax
; We use the value stored in %ebp as a memory address and then take the
; value at that memory address and copy it into %eax
movl -4(%ebp), %eax
; We treat the value in #ebp as memory, find the address -4 away from it
; and then we copy the contents at that ofsetted address into %eax
```
### Indexed Mode Addressing
We can add the contents of two registers to get address of operand. This is particularily useful wen dealing with arrays because we can have one register hold the base address while the other one holds the index. Note that Index cannot be ESP.

```nasm
movl (%ebp, %esi), %eax ; Copy the value at (address = ebp + esi) into eax
movl 8(%ebp, %esi), %eax ; Copy the value at (address = * + ebp +esi) into eax
```
### Scaled Indexed Mode Addressing
On top of Index Mode Addressing, Scaled Index Mode Addressing allows us to multiply the second operand by the scale (1, 2, 4, or 8).

```nasm
movl 0x80(%ebx, %esi, 4), %eax
; Copy the value at (address = ebx + esi * 4 + 0x80) into eax
```
This can be useful when dealing with structs or larger data types where we can scale by its size.
### Address Computation Examples
Given `%edx = 0xf000` and `%ecx = 0x100`, lets compute the following addressing expressions. 
`0x8(%edx) = 0x8 + 0xf000 = 0xf008`  
`(%edx,%ecx) = 0xf000 + 0x100 = 0xf100`  
`(%edx,%ecx,4) = 0xf000 + 0x100 * 4 = 0xf400`  
`0x80(,%edx,2) = 0x80 + 0 + 0xf000 * 2 = 0x1e080`
### movl Operand Combinations
#### Immediate
##### Register
The constant 0x4 is stored into register eax.  
`movl $0x4,%eax` --> `temp = 0x4;`  
##### Memory
The constant -147 is stored into an memory address stored in register eax.  
`movl $-147,(%eax)` --> `*p = -147;`
#### Register
##### Register
The contents in register eax are stored into register edx.
`movl %eax,%edx` --> `temp2 = temp1;`  
##### Memory
The contents in register eax are stored into the mem address stored in register edx.
`movl %eax,(%edx)` --> `*p = temp;`
#### Memory
##### Register
The contents in the memory address stored in register eax are moved into register edx.  
`movl (%eax), %edx` --> `temp = *p;`

---
**In general keep in mind that a register can either hold a data value, or a memory address.** Indirect addressing allows you to access data pointed to by memory address stored in registers.

### Stack Operations
`%esp` points to the address at the top of the stack. `pushl` and `pops` push contents onto or off the stack.

```nasm
pushl %eax 	; pushes item on stack into eax, then decrements esp
popl %ebx 	; pops item from stack into eax, then increments esp
```
Note that the stack will grow downwards from a high to low memory addresses.
### Swap Program Example 32 bit
```c
void swap (int *xp, int *yp)
{
	// set local var t0 to value at xp
	int t0 = *xp;
	// set local var t1 to value at yp
	int t1 = *yp;
	// set value at xp to t1
	*xp = t1;
	// set value at yp to t0
	*yp = t0;
}
```
In our conversion to assembly, lets look at the registers `%ecx, %edx, %eax, %ebx` and variables `yp, xp, t1, t2`.

```nasm
movl 12(%ebp),%ecx ; ecx = yp
movl 8(%ebp),%edx ; edx = xp
movl (%ecx),%eax ; eax = *yp (t1)
movl (%edx),%ebx ; ebx = *xp (t0)
movl %eax,(%edx) ; *xp = eax
movl %ebx,(%ecx) ; *yp = ebx 
```
We can find our parameters yp and xp by using offsets 12 and 8 from the base pointer `%ebp`. Then using the `movl` command, we store the memory addresses into registers `%ecs` and `%edx`. After we move the values pointed to by the memory addresses within `%ecs` and `%edx` into registers `%eax` and `%ebx` respectively. Finally, we move the value stored in `%eax` into the what is pointed to by the address stored in `%edx` and the same with `%ebx` and `%ecx` - effectively completing our swap. 
### Swap Program Example 64 bit
```c
void swap (int *xp, int *yp)
{
	// set local var t0 to value at xp
	int t0 = *xp;
	// set local var t1 to value at yp
	int t1 = *yp;
	// set value at xp to t1
	*xp = t1;
	// set value at yp to t0
	*yp = t0;
}
```
```nasm
swap:
	movl (%rdi), %edx ;store value of first param into %edx
	movl (%rsi), %eax ;store value of second param into %eax
	movl %eax, (%rdi) ;set value at rdi with %eax
	movl %edx, (%rsi) ;set value at rsi with %edx
	retq
```
In 64 bit, there are no stack operations because we have access to more registers, so we can simply store the parameters in registers instead of the stack.

### IA32 Stack
This is a region of memory that is managed as a stack. It grows towards lower addresses aka downwards. The register %esp indicates the lowest stack address aka the address of the top element of the stack.
#### Pushing
`pushl SRC` fetches the operand at SRC, decrements %esp by 4 and then writes the operand at address given by %esp.
#### Popping
`popl DEST` reads the operand at the address given by %esp, increments %esp by 4, and writes it to DEST.
### Push and Pop Details
#### Push
The `push` instruction pushes data onto the stack. This causes the stack to grow downwards which is why `%esp` is decremented by the size specified by command. For example, `pushl %eax` pushes the contents of `%eax` onto the stack and decrements the stack pointer by 4. Likewise `pushl $0xffffffff` pushes constant `0xffffffff` onto the stack and decrements the stack pointer by 4.
#### Pop
The `pop` instruction retrieves data from the stack. This causes the stack to strick upwards so `%esp` gets incremented by the size specified by command. Lets say the top of our stack contained the value `0xaaaaaaaa`. Then after executing `pushl %eax`, `%eax` will contain `0xaaaaaaaa` while the stack pointer gets incremented by 4.
### Procedure Control Flow
Uses the stack to support procedure call and return.
#### Procedure call
`call LABEL` Pushes return address on stack and jumps to LABEL.
#### Return address value
This is the address of instructions beyond the current function call.

```nasm
804854e:	e8 3d 06 00 00 call 8048b90 <main>
8048553: 	50 pushl %eax 
```
In this example we can see that the return address is `0x8048553`.
#### Procedure return
`ret` will pop a address from the stack and then jump to that address.

### Address Computation Instruction
`leal` allows us to compute addresses using addressing mode without actually accessing memory. Follows the format: `leal SRC, DEST` where src is the address mode expression, and sets DEST to the address specified by SRC. This is useful when we want to set a regester to be the address of something and not to set a register to what the address of something points to.
#### Comparison between movl and leal
```c
int x;
int *p = &x;
int a = = *x; 
int *b = x;
```
Lets assume that the int x is stored at address `0x100F`.

```nasm
movl 0x100F,%ecx ; Stores the address of int x into ecx
movl (%ecx), %eax ; Stores the value of x into eax
leal (%ecx), %ebx ; Stores the address of x into ebx
```
### Arithmetic Operations
**Instruction** 		**Computation**
addl Src,Dest --> Dest = Dest + Src  
subl Src,Dest --> Dest = Dest - Src  
imull Src,Dest --> Dest = Dest * Src  
sall Src,Dest --> Dest = Dest << Src (left shift)  
sarl Src,Dest --> Dest = Dest >> Src (right shift)  
xorl Src,Dest --> Dest = Dest ^ Src  
andl Src,Dest --> Dest = Dest & Src  
orl Src,Dest -->	Dest = Dest | Src  
incl --> Dest Dest = Dest + 1  
decl --> Dest Dest = Dest - 1  
negl --> Dest Dest = - Dest  
notl --> Dest Dest = ~ Dest  

### Arith Program Example
```c
int arith(int x, int y, int z)
{
	int t1 = x+y;
	int t2 = z+t1;
	int t3 = x+4;
	int t4 = y * 48;
	int t5 = t3 + t4;
	int rval = t2 * t5;
	return rval; 
}
```
```nasm
arith:
	pushl %ebp ;push the base pointer onto the stack
	movl %esp,%ebp ;set the base pointer to be the stack pointer
	movl 8(%ebp),%eax ;get param x from 8 offset from base pointer
	movl 12(%ebp),%edx ;get param y from 12 offset from base pointer
	leal (%edx,%eax),%ecx ;calculate x + y and store in ecx
	leal (%edx,%edx,2),%edx ;multiplies edx by 3 
	sall $4,%edx ;does a leftshift on edx by 4 to complete y * 48
	addl 16(%ebp),%ecx ;adds t4 from memory to ecx
	leal 4(%edx,%eax),%eax ;computes 4+t4+x
	imull %ecx,%eax ;computes t5 * t2
	movl %ebp,%esp ;sets the stack pointer to base pointer
	popl %ebp ;pops the base pointer to execute next code
	ret ;returns from function
```
### Saving Convention
#### Caller
Before calling a function, the caller will save the contents of certain registers called "caller-saved". These include %eax, %ecx, and %edx. The contents in these registers must be pushed onto the stack so that they can be restored when control returns to the caller in case the callee modifies them.
#### Callee
The callee must save the contents in registers %ebx, %edi, and %esi before executing any of the function body instructions.

### The C Call Stack
Lets take a closer look at what happens behind the scenes when a function gets called. To begin, lets look at a single function call by itself first. We have the code:

```c
int foobar(int a, int b, int c)
{
    int xx = a + 2;
    int yy = b + 3;
    int zz = c + 4;
    int sum = xx + yy + zz;

    return xx * yy * zz + sum;
}

int main()
{
    return foobar(77, 88, 99);
}
```  
Which results in the following stack frame:  
![stackframe1](resources/stackframe1.png)  
*Source: [https://eli.thegreenplace.net/2011/02/04/where-the-top-of-the-stack-is-on-x86/](https://eli.thegreenplace.net/2011/02/04/where-the-top-of-the-stack-is-on-x86/)*  
  
Notice that the function parameters `a, b, c` exist at the top of the stack in reverse order. Then it is followed by the return address and the saved base pointer. Below the base pointer, we have all of the local variables `xx, yy, zz, sum` in our function foobar(). Any other temporary variables or function calls by foobar() will exist below the saved base pointer.

--- 
Now lets take a look at a function that calls another function.  
![call_stack1](resources/call_stack1.png)  
First note that Foo()'s parameters, saved registers, temporary variables and return address is not shown in the drawing as it is above "Saved eax". What we can see however, is argument3, argument2, and argument1. These the parameters that get passed to function Bar(). The arguments are then followed by a return address so after Bar() finishes execution, control is restored to Foo(), which probably goes back to main(). As we can see below the return address we once again have the saved base pointer and another saved register. Finally below that, is the local variable beloing to Bar().
### Procedure Call Conventions
#### Caller
##### Pre-Call
1. Follow the caller-save convention by saving %eax, %ecx, and %edx.
2. To pass paremeters to the sub-routine push them into the stack in reverse order.
3. Use the `call` instruction to call the sub-routine which pushes the return address onto the top of the stack and branches to the sub-routine code.


##### Post-Call
1. Pops all of the parameters from the stack to restore it to previous state.
2. Restore the contents of the caller-saved registers by popping from stack. Caller can assume no other registers were modified by sub-routine.

---
#### Callee
##### Pre-Execution
1. Push the value of the base pointer %ebp onto the stack and then copy the value of stack pointer %esp into %ebp. Using `pushl %ebp` then `movl %esp, %ebp`. This is so that the location of parameters and local variables will known as a constant offset from the base pointer.
2. Allocate local variables by making space on the stack by decrementing the stack pointer.
3. Save the values of the callee-saved registers.

##### Post-Execution
1. The return value of the function is left in %eax.
2. Restore the old values of callee-saved registers from popping from the stack.
3. Deallocate local variables by moving the value of the base pointer to the stack pointer.
4. Restore the caller's base pointer by popping %ebp from the stack right before returning.
5. Return to the caller using the `ret` instruction.


### Control Flow/Conditionals
Conditional branches implement control flow in higher level language such as `if/then`, `while`, and `for`. An unconditional branch is something like a `break` or `continue`.

### Condition Codes
#### Single Bit Registers
* `CF` Carry Flag
* `SF` Sign Flag
* `ZF` Zero Glag
* `OF` OVerflow Flag

Condition Codes can either be set implicitly by almost all logic and arithmetic operations or explicitly using comparison operations. Note that condition codes are not set by the leal instruction.
#### Implicit
Lets do an example of implicit setting of condition codes. If we run the instruction `addl SRC, DEST`, the c equivlient of t = a + b, the **CF** will be set if there is a carry out from the most significant bit (used to detect unsigned overflow). **ZF** is set if `t == 0`. **SF** is set if `t < 0`. **OF** is set if there is a two's complement overflow `(a>0 && b>0 && t<0) || (a<0 && b<0 && t>=0)`.
#### Explicit
Here is an example of explicit setting of condition codes using the `testl SRC2, SRC1` instruction. Test essentially computes a&b but but throws away the result but sets the flags. **ZF** set when `a&b == b`. **SF** set when `a&b < 0`.
### Jumping
Jumps depend on condition codes as part of the syntax. They will check the appropriate flags to see if a jump should be performed.
![alt jump_codes_table](resources/jump_codes.png)
### Conditional Branch Example
```c
int max(int x, int y)
{
	if (x <= y)
		return y;
	else
		return x;
}
```
```nasm
_max:
	pushl %ebp ;pushes the base pointer onto the stack
	movl %esp,%ebp ;sets the base pointer to be the stack pointer
	movl 8(%ebp),%edx ;sends param x to edx
	movl 12(%ebp),%eax ;send param y to eax
	cmpl %eax,%edx ;compares x to y
	jle L9 ;jumps to L9 if x is less than or equal to y
	movl %edx,%eax ;sets return value to x
L9:
	movl %ebp,%esp ;sets stack pointer to base pointer
	popl %ebp ;pops basepointer from stack
	ret ;returns from function
```
Note that the value at %eax is the return value from the function due to the calling convention.
### Do-While Loops
Do while loops are a step up from machine code like goto statements.  
**Do-While**

```c
int fact_do(int x)
{
 int result = 1;
 do {
 result *= x;
 x = x-1;
 } while (x > 1);
 return result;
}
```
**Goto**

```c
int fact_goto(int x)
{
 int result = 1;
loop:
 result *= x;
 x = x-1;
 if (x > 1)
 goto loop;
 return result;
}
```
Both methods use backwards branching to loop. We only take the branch if the "while" condition holds.  
In assembly we get something like this:

```nasm
 pushl %ebp ; Setup
 movl %esp,%ebp ; Setup
 movl $1,%eax ; eax = 1
 movl 8(%ebp),%edx ; edx = x
L11:
 imull %edx,%eax ; result *= x
 decl %edx ; x--
 cmpl $1,%edx ; Compare x : 1
 jg L11 ; if > goto loop
 movl %ebp,%esp ; Finish
 popl %ebp ; Finish
 ret ; Finish
```
In each iteration of the loop, %edx is compared against 1 to see whether or not to branch back or continue execution.

### Converting Do-While to Goto
This can be done easily by adding an if statement that determines whether or not to jump backwards.

```c
// Do-While
do
 Body
 while (Test);

// Goto
loop:
 Body
 if (Test)
 goto loop
```
Note **Body** can be any number of C statements and **Test** is the expression that returns a integer/boolean value where if (test == 0 --> false, test != 0 --> true).

### Converting While Loops
To convert a while loop to do-while or goto, an additional jump needs to be made to see whether the initial condition was satisfied.

```c
// while
while (Test)
 Body
 
// do-while
if (!Test) // check the initial condition
 goto done; // edit loop if failed
do
 Body
 while(Test);
done:

// goto
if (!Test) // check initial condition
 goto done; // exit loop if failed
loop:
	Body
	if (Test)
	  goto loop;
done:
```
### Switch Statements
Switch statements are implemented in two ways.

1. A series of conditionals which is good if there are few cases but slow if there are many.
2. A jump table that avoid conditionals but only possible when the cases are small integer constants.

GCC will pick the appropriate one depending on the case structure.
### Jump Tables
Jump tables can be thought of as a very simple hashtable. The data is stored in an array like structure where the case value is used as a key to fetch the selected information. ![alt jump-table](resources/jump-table.png)
### Switch Statement Example
In order to use a jump table, case values are often enumerated. Lets look an at example of them in action.

```c
typedef enum
 {ADD, MULT, MINUS, DIV, MOD, BAD}
 op_type;
char unparse_symbol(op_type op)
{
 switch (op) {
 	...
 }
}
```
```nasm
unparse_symbol:
 pushl %ebp 		; Setup
 movl %esp,%ebp 	; Setup
 movl 8(%ebp),%eax 	; eax = op
 cmpl $5,%eax 		; Compare op : 5
 jmp .L49 			; If > goto done
 jmp *.L57(,%eax,4) ; goto Table[op]
```
Note the base address of the jump table is located at `.L57`. The instruction `jmp *.L57(,%eax,4)` goes to the address calculated by `.L57` + `%eax`(contains enumerated case value) * `4`(scales the value to fit an integer).

### Reading Condition Codes
The instruction `set<x>` sets a single byte based on the combinations of condition codes. ![setx](resources/setx.png)  
Because it only sets a single byte, it is commonly used in conjunction with `movzbl` after use with the singly byte registers to map to a full sized register.

```c
int gt (int x, int y) {
 return x > y;
}
```

```nasm
movl 12(%ebp),%eax 	; eax = y
cmpl %eax,8(%ebp) 	; Compare x : y
setg %al 			; al = x > y
movzbl %al,%eax 	; Zero rest of %eax
```
### Stack-Based Languages
Recursion is only possible in languages that are "Reentrant". This means that you can have multiple simutaneous instantiations of a single procedure. The stack is allocated in frames aka "activation records" which contains everything needed in a particular function call (local variables, return pointer, arguments...).

### Stack Frames
Stack frames are a temporary space that contain contain local variables, the return value, and things a function needs. They are set up before entering a procedure and deallocated when returning. The **stack pointer** `%esp` points to the top of the stack. The **frame pointer** `%ebp~ contains the start of the current frame.

### Stack Operation
Stack frames grow from top to bottom. Each time a new function is called, %ebp is pushed onto the stack and then set to equal %esp, and %esp is decremented to a lower address. Each time a function returns, %esp is set to equal %ebp and %ebp is restored from the stack.

### IA32/Linux Stack Frame
The caller stack frame contains the return address and arguments for the caller function. The current stack frame contains the parameters for the callee function, local variables, saved register context, and old frame pointer.

---
![stackframe2](resources/stackframe2.png)
---

###IA32/Linux Register Usage
* Special uses: `%ebp, %esp`
* Callee-save: `%ebx, %esi, %edi` old values are saved on stack prior to use
* Caller-save: `%eax, %edx, %ecx`
* Return value: `%eax`


### Basic Data Types
![stackframe2](resources/datatypes.png)

### Array Allocation
Arrays are simply contigously allocated region of a particular data type. Accessing an array using assembly requires the use of a scaled offset on the base address of the array.

### Structure Allocation
Again are contigously allocated regions in memory which contains members that may be different data types. To access a struct member, you must once again use a scaled offset on the base address. The size of the offsets are determined during compile time.

### Alignment
Primitive data types require K bytes so addresses must me multiples of K. As a result memory accessed by aligned double or quad words are much faster when the data is stored within the boundaries. To do this, a compiler inserts gaps in structures.

### Statisfying Alignment with Structures
To satify every element's alignment requirement, we choose the largest alignment requirement (K). The initial address and structure length must be multiples of K. However, the padding used for padding for an individual member depends on its own size.

```c
struct S1 {
 char c;
 int i[2];
 double v;
} *p;
```
In this struct, the largest data type is "double" so K = 8.  

---
(p+0) -->| c | padding |(p+4) i[0] | (p+8) i[1] | padding | (p+16) v |<-- (p+24) 

--- 
As can be seen, `int i[]` has the beggining addresses of 4 and 8 which are both divisible by 4. `double v` has the beggining address 16 which is divisible by 8. The final address is 24 which is also divisible by 8.

-
#### Important Notes
* The starting address of the struct array must be multiple of worst-case alignment for any element
* The offset of an alement within structure must be a multiple of element's akignment requirement
* The over all size of the structure must be a multiple of worst-case alignment for any element


### Ordering Elements Within Structure
We try to order the elements in a structure so that we waste as little space as possible due to alignment padding.

### Summary
* Array's don't have bounds checking
* Arrays are usually just a pointer to the first element
* Compilers turn array code into pointer code
* Uses addressing modes to scale array indicies
* Structure allocate bytes to be declared
* Structures are padded to satisfy alignment


## Digital Design
### Logical Gates
Includes:
NOT, AND, OR, NAND, NOR, XOR...  
Built using transistors that use discrete values in the form of voltage.
### Notation
* AND is denoted as multiplication: `A.B` 
* OR is denoted as addition `A+B`.
* NOR is denoted as a bar or more conveniently an apostrophie `A'`

### DeMorgans Law

1. (P.Q)' = P' + Q'
2. (P + Q)' = P'.Q

### Universal Gates
Any gate can be implemented using either NOR or NAND gates.

### More than 2 Inputs
AND/OR can take any number of inputs. AND = 1 if all inputs are 1 and OR = 1 if any of the inputs are 1.

### Circuit Design
Steps to create a circuit:

1. Think about what the circuit is designed to do
2. Create a truth table for the circuit
3. Derive boolean expression from truth table
4. Simplify boolean expression
5. Build circuit given boolean expression

### Converting Truth Table to Boolean Expression
When given a truth table, isolate the rows where the output is true, and AND all of your inputs while negating any input that has an input value of 0. ![alt tt-expr](https://sub.allaboutcircuits.com/images/14065.png)  
Often times the boolean expression is not in the simplest form so we can either use boolean algebra or k-maps to reduce it.
![alt expr-simp](https://sub.allaboutcircuits.com/images/14066.png)  
Finally, we can create the circuit by ANDing AB, BC, AC, and then ORing the results together. ![alt circuit](https://sub.allaboutcircuits.com/images/04366.png)

### Decoder
Decoders always have n inputs, and 2^n outputs. It allows you to determine which combination of the inputs are true. Note the outputs take the form of a reversed truth table. ![alt decoder](https://image.slidesharecdn.com/deppt-151120153445-lva1-app6892/95/encoder-and-decoder-in-digital-electronics-5-638.jpg?cb=1448033733)  
It's possible to create larger decoders from smaller decoders.
![alt decoder-larger](https://i.stack.imgur.com/b4lfd.png)

### Encoder
The encoder is the opposite of the decoder as it converts m bit input to n bit output where n <= m.

### Multiplexer
Contain n-bit selector and 2^n inputs, with one output. Output is equal to one of the inputs based on the selector.

---
4:1 Multiplexer
 ![alt mux](https://upload.wikimedia.org/wikipedia/commons/thumb/3/37/Mux_from_3_state_buffers.png/200px-Mux_from_3_state_buffers.png)
 
### 2 Variable K-Maps
K-maps allow us to simplify boolean expressions faster than using boolean algebra. We create a 2-d map that are contain squares that represent each minterm. The squares are then marked according to the values of the minterm derived from a truth table. In order to simplify the expression, we circle any two 1s that are next to each other vertically or horizontally. This gives us the expression of the variable that did not change across the two boxes. ![alt 2varkmap](https://digital-electronics.weebly.com/uploads/8/6/1/3/8613305/2x2kmap.gif)  
In the left box, note that we have 1s in `A'B'` and `A'B`. This means we can simplify the expression to just be `A'`. Conceptually that is based on the boolean algebra law `P.P' = 1`. In the right box we have `A'B` and `AB`. This time the expression simplifies to `B`. 
 
### 3 Variable K-Maps
![alt 3varkmap](https://electronicspost.com/wp-content/uploads/2015/05/161.png)  
Notice that with three variables we have B and C on the top. The progression of `00 --> 01 --> 11 --> 10` is called "grey code" where there is only a single change of 1s and 0s each time. This is neccessary so the k-map works correctly. Also, note that the **rectangles of 1s must be a power of 2** to be allowed and can "wrap around" the sides.

-
In the above map we have `A'B'C'` and `A'B'C'` where `A'B'` stay constant. We also have `ABC` and `ABC'` where `AB` stay constant. Our expression gets simplified from `A'B'C' + A'B'C + ABC + ABC'` to just `A'B' + AB'`.

### 4 Variable K-Maps
Four variable K-Maps are similar to the 3 and 2 variable ones but you can now create boxes from the corners in a diamond shape from wrapping around.
![alt 4varkmap](https://sub.allaboutcircuits.com/images/14124.png)  
Notice in this example there are two right answers depending how you decide to box square (11, 01).

### FSM to Digital Circit
Finite state machines consist of a state register and combinational logic.  
**Step 1**: Draw out the FSM as a state diagram.  
![alt state-diagram](https://sub.allaboutcircuits.com/images/44001.png) 
**Step 2**: Replace the state names with binary numbers.  
We have 3 states so we can represent them with 2 bits. `00` = initial standby, `01` = activate pulse, `10` = wait loop.
![alt binnames](https://sub.allaboutcircuits.com/images/44002.png)  
**Step 3**: Fill in state table.
![alt statetable](https://sub.allaboutcircuits.com/images/44003.png)
We use our diagram to figure to map each current state to the next state based on an input of 0 or 1. We also need to encode our output so for our case we use 0 and 1.  
  
**Step 4**: Using K-Maps we can figure out the expressions for the next state transition and outputs. For present state to next state, we need to have two 3-variable K-Maps. First for A, B, and I mapping to Anext, and second for A, B, and I mapping to Bnext. Then for the output, we have A, B mapping to Y. ![alt statekmaps](resources/fsm-kmaps.png)

**Step 5**: Prepare to Implemnt Circuit.
Complete circuit will take this form:
![alt generic](resources/generic_fsm_circuit.png)

**Step 6**: Assume that we are using a D-FF.  
Implements the state register.
![alt dff](resources/d-ff.png)

**Step 7**: Implement Next State Circuit.
We need to implement `A'BI' + AB'I` for Anext and `A'B'I` for Bnext.
![alt next-state-logc](resources/next-state-logic.png)

**Step 8**: Implement Output Circuit.
We meed to implement `A'B` for Y.
![alt output-logc](resources/output-logic.png)

**Step 9**: Put everything together.
![alt fin-logc](resources/finished-logic.png)

## Caches

