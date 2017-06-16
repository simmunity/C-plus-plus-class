# C / C++ Programming Class 2

[]( ### 5 Minute Break)

---
# C Language Fundamental Functionality and Features

# Objectives

### Identify and use essential C language features that provide text and data input, output and processing using iteration
### Describe differences between and use both ASCII and Unicode character strings
### Master For loops and conditionals
### Master While loops and Switch statements
### Use Standard C Libraries
---
# ASCII Strings
### Strings in C are stored as arrays of bytes encoded using ASCII or Unicode with a binary zero (NULL) terminator:
[]() {```c
main () {
  char rock[] = "C Programmers Rock";  
  printf ("%s\n", rock);

  printf ("String Length = %lu\n",    strlen(rock) );
    
  printf ("specific letters in hexadecimal\n");
  printf ("First letter  = 0x%02x\n", rock[0] );
  printf ("Last letter   = 0x%02x\n", rock[strlen(rock) - 1] );
  printf ("NULL at end   = 0x%02x\n", rock[strlen(rock)] );
}
```}
<script src="//repl.it/embed/IpS6/1.js"></script>

---
# Unicode Strings
### Unicode strings in C are stored as arrays of bytes encoded typically using UTF-8 with a binary zero (NULL) terminator:
```c
main () {
  char unicode[] = "\U0001F60A \u03C6 \u221A \u2467";
  printf("Some unicode %s characters\n", unicode);
}
```
<script src="//repl.it/embed/IpTg/2.js"></script>

Note: Support for UTF-8, UTF-16 and UTF-32 is not identical on different operating systems and also require using special string functions

---
# for loops and conditionals
### C provides excellent iteration and conditional control structures using for and if, else:
```c
#define ITEMS 5
main () {
  double sum = 0.0;
  double values[ITEMS] = {4.95, 7.50, 3.95, 2.15, 9.99};
 
  for (int x = 0; x < ITEMS; x++) {
    if (x == 0) {
      printf ("Item costs $%0.2lf", values[x]);
    } else {
      printf (" + $%0.2lf", values[x])
    }
    sum += values[x];
  }
  printf (" = Total $%0.2lf\n", sum);
}
```
<script src="//repl.it/embed/IpUE/1.js"></script>

Lets try this in Xcode

---
