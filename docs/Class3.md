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

