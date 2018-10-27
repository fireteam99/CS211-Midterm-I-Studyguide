# CS211 Midterm I Study Guide
## Recent Trends In Hardware
### Main Components In Computer
Include: Cpu, Memory, Bus, I/O Devices like keyboards, graphics, neworking, and storage.
### Von Neumann Model
Computers are seperated into three parts: memory, control unit, and arithmetic and logic unit. Moery stores data and instructions. The control unit fetches further instructions. the arithmetic and logic units do operations based on the instrucitons passed.
### Basic CPU Function
Fetch --> Decode --> Execute
### Running on Hardware
**High - Level Language**

```c
x = x + y;
```   
**Assembly Language**

```nasm
mov -0x8(%esp),
%ebx add %ebx, %eax
```  
**Machine Language**

```
7F 45 4C 46 01 01 01…
```  
### Operating System
Provides essential services to programs running on hardware such as virtual memory, multitasking, etc...
### Moore's Law
An observation that the number of transistors on chip double every 18 month. Can also be seen in processor speed, memory capacity, and disk capacity, which doubles 18 months, two years and every year, relativly speaking.
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
Include: `>, >=, <. <=, ==, !=`. The result is 1 (TRUE) or 0 (FALSE).
### Bit Operators
Contains the symbols: `~` complement used as `~x`, `&` bit AND used as `x & y`, and `|` bit OR used as `x | y`.
### Expressions and Assignments
Expressions are computations with a result. Example: `x + y * z`. Be aware that c does explicit type conversion with double being the rank and char/short int being the lowest rank. Assignments work by setting the value of an expression to a variable. Example: `a = x + y * z`.
### Control Statements
Conditional: if else, switch. Iteration: while, for, do while. Goto: break, continue, goto.
### If Statements
Keeps on evaluating expressions until one found with non-zero result.

```
if (condition 1) {
    body...
} else if (condition 2) {
    body...
} else {
    body...
}
```

### Switch Statements
Evaluates an integer expression and after finding the 1st case with matching contatcy executes statements until encountering break or end of switch. Remember to include a default case.

```
switch(expr) {
    case 1:
        statement 1;
    case 2:
        statement 2;
    defualt:
        statement 3;
}
```
### Loops

```
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
The `break` statement forces an immediate exit from siwtch or loop and goes to the code following that switch or loop. The `continue` statements skips the rest of the code in the body of a loop and restarts the loop.
