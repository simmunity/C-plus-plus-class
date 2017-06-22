# C / C++ Programming Class 3

---
# Advanced C Language Features for Complex Data Structures and Dynamic Code Execution
## Objectives

- **Master C pointers to data and functions, creating and dereferencing them as needed**
- **Use function arguments passed by reference**
- **Use arrays of pointers**
- **Master pointer arithmetic**
- **Use function pointers to create dynamic code**

---
# Review of Computer Memory
### PCs and smart phones (64  & 32 bit capable) and single chip embedded system computers (32, 16 and 8 bit) all use 8 bit bytes and byte addressable RAM
### All computers except embedded MCU's use special virtual memory hardware to provide each process its own private memory space. This hardware helps the operating system create private memory spaces where each process uses addresses that all start at 0x10000. 
### The reality is that address maps to different physical RAM address locations.  An application does not know its memory location 0x10000 is mapped to 0x49FEE00, and another application has it's address 0x10000 mapped to 0X17FD800.
[ [ [ Need graphic, and preferable animated or video visualization ] ] ] 

---
# Pointers To Data
### C pointers are incredibly powerful, flexible, and dangerous if used carelessly.  Off by one bugs and stale pointers can cause erratic program behavior:
```c 
char   * pointerToChar;
int    * piValue;   // Hungarian variable naming standard, Pointer to Integer Value
double * pdPi;
char   * psString;
char * * ppsString; // pointer to pointer to string
```

### Pointers on PC's and phones are either 32 bits (4 bytes) or 64bits (8 bytes) long and are unsigned integers.  Pointers on 8 and 16 bit processors usually are 16 or 20 bits limiting them to 65536 bytes or 1 megabyte.  The number a pointer holds is the memory address of the first byte of the data they "point" to.  32 bit pointers can point at 4gigs of RAM.  64 bit pointers can point at 16 exabytes though even server PC's only have physical slots and PCB traces allowing up to hundreds of gigabytes.
### Lets play with pointers in Xcode by using CProgrammingPt3 project.  Open the Extra.c file and grab the POINTERS TO DATA section

[ [ [ again, would be nice to have graphics depicting pointers and various data types as byte sequences ] ] ]

---
# Function Arguments Passed By Reference
### C functions can only return a single simple data type or pointer to complex type but can accept multiple parameters that are pointers (references) which the function can modify allowing functions to produce multiple selected results:
```c 
bool ParseNum (char * psText, char * * ppsNew, int * piNum)
```
### This function returns a boolean result.  It accepts a pointer to text to parse in psText.  It accepts a pointer to a pointer to the final new text position if a valid pointer i passed or if a NULL is passed does not change it.  The last parameter is a pointer to the integer result of converting the number from text to binary if successful.  If the conversion is unsuccessful, the integer result is unmodified.
 
### Lets play with this function in Xcode  (use CProgrammingPt3 project)
Open the Extra.c file and grab FUNCTION ARGUMENTS BY REFERENCE section

---
# Arrays Of Pointers
### C arrays can include any type of data including pointers to any type including arrays of intrinsic and user defined types.  Arrays of pointers are often used in algorithms such as hash tables where collections of values hang off each hash table row:
```c
char * numbers[] = {"987654321", "971", "-876543210", "12345,432109"};
```
### The example creates a 4 element array of pointers to 4 character arrays.  In the code below, the ParseNumber function accepts the fourth (index value 3) pointer.
```c
if ( ParseNumber(numbers[3], & pNext, & firstNum)) {
```
### Lets play with arrays of pointers in Xcode using the CProgrammingPt3 project.  Open the Extra.c file and grab the ARRAYS OF POINTERS section

---
# Pointer Arithmetic
### Pointer arithmetic in combination with casting pointers from one type of data to another is one of C's most powerful capabilities, and one of its most dangerous capabilities.  Graphics, kernel, database engine and programming language developers require this capability:
```c
*(pNewPosition + RED + colorDepth * ((columns * 2) + 6)) );
```
### This code retrieves a red channel color byte from a bitmap stored in memory at row 2 and column 6 based on a color depth of 3 bytes per pixel.
 
### Lets play with these in Xcode using the CProgrammingPt3 project.  Open the Extra.c file and grab the POINTER ARITHMETIC section

---
# Function Pointers
### Function pointers are used in places where different data types and operations need to be dynamically chosen at run-time.  Also call-back functions are usually specified as function pointers in the initiating function:
```c
void (* funcArray[])(int, int) = {add, subtract, multiply, divide};  // defines an array of 4 function pointers
 
(*funcArray[opIndex])(first, second);  // calls a function
```
### Function pointers are often used with library functions such as sorting routines to provide a type specific compare function.  Call back functions and graphics routines also use function pointers to provide flexibility.

### Lets play with these in Xcode using the CProgrammingPt3 project. Open the Extra.c file and grab the FUNCTION POINTERS section

---