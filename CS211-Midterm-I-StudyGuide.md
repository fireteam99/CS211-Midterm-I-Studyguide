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
Evaluates an integer expression and after finding the 1st case with matching contatcy executes statements until encountering break or end of switch. Remember to include a default case.

```c
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
The `break` statement forces an immediate exit from siwtch or loop and goes to the code following that switch or loop. The `continue` statements skips the rest of the code in the body of a loop and restarts the loop.
### Functions
Components include: Name, Return type, Parameers, and Body.

```
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
C's memory model is the same as the underlying virtual memory system. Variables are simply names for contiguous sequences of bytes. Variable names are equivelent to memory addresses.
### Pointers
Pointers are a variable that store an address. Declared as `type *pointer_name`. `*` is the dereference operator which ives the value stored at the address pointed to: `*p`. `&` gives the address of a variable: `&v`.
### Null Pointer
NULL is a predefined constant that contains a value that is an illegal address so we know it points to nothing. Usually `Null = 0`.
### Type Casting
Note that C is not strongly typed.
### Arrays
Arrays are contiguous sequences of data items of the same type. Declaration: `type name[amount]` --> `int nums[10]`
Array indexs always start at zero. C compiler and runtime does not check for boudaries.
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
Arrays are baessed by reference but array items are passed by value. This means there will be pointer decay and the size of the the array is lost when passed to a function.
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
We need dynamic memory allocation when we don't how much data we have during compile time. These varibles are declared on the heap rather than the stack.
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
### Running on Hardware
The ISA (Instruction Set Architecture) interfeces between the soft ware and hardware.
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
We can encode things by using bits. For example a playing card has 4 suits, and 13 ranks. We can simply use one byte where 4 bits represent the rank 2 two bits represent the suit.
### Negative Integers
In writing we denote negative numbers with a negative sign `-`. We can designate a bit to be the signed like `4 = 0100` and `-4 = 1100` but this results in two zero values which is inconvenient for arithmetic `0 = 0000` and `-0 = 1000`.
### 1s' Complement
We can find -x by simply negating the bits of x. `001 = 1` `110 = -1`
However, there are still two zeros and is inconvenient for arithmetic.
### 2s' Complement
We can make the most significant bit negative so that to find -x we simply negate the bits in x and add 1. This gets rid of the extra zero problem but there in an extra minimum value. Adding, subtracting, and multiplying works without changes and is now used on most computers. Remember that 0 signifies positive and 1 signifies negative. `100 = -4` `101 = -3` `110 = -2` `111 = -1` `000 = 0` `001 = 1` `010 = 2` `011 = 3`
### Range of 2s' Complement
For unsigned integers, k bits you can represent 2^k values. If they are natural numbers the range is `0 through 2^k-1`. However for 2s' complement the minimum value of x for k bits is `-2^(k-1)` and the maximum value is `2^(k-1) - 1`. This is because we add one to the negated value.
