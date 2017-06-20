# C / C++ Programming Class 2

[]( ### 5 Minute Break - testing comment capability)

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
```c
main () {
  char rock[] = "C Programmers Rock";  
  printf ("%s\n", rock);

  printf ("String Length = %lu\n",    strlen(rock) );
    
  printf ("specific letters in hexadecimal\n");
  printf ("First letter  = 0x%02x\n", rock[0] );
  printf ("Last letter   = 0x%02x\n", rock[strlen(rock) - 1] );
  printf ("NULL at end   = 0x%02x\n", rock[strlen(rock)] );
}
```
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

---
# Ternary Expressions
### C provides ternary (three part) expressions that can concisely replace many multi line if, else expressions:
### value\_assigned = boolean ? value\_if\_true : value\_if\_false;
```c
#include <stdbool.h>
 
// only left or right pin can be true for a joystick
// uses two ternary expressions on one line for conciseness
void get_angle (bool leftPin, bool rightPin) {
  int angle = leftPin ? -30 : (rightPin ? 30 : 0);
  printf ("leftPin = %d, rightPin = %d,", leftPin, rightPin);
  printf (" angle = %d\n", angle);
}

main () {
  get_angle ( false, false );
  get_angle ( true,  false );
  get_angle ( false, true  );
}
```
<script src="//repl.it/embed/IuXe/2.js"></script>

---
# While Loops
### C provides convenient looping controlled by conditional:
### while (condition) { … }  _or_  do { … } while (condition);
```c
#include <time.h>

main () {
time_t oldTime, newTime;
int count = 0;
 
  time ( &oldTime ); // pass time variables to time function by
  oldTime += 2;      // reference ‘&’ so they can be modified
  do {
    time ( &newTime );
    count++;
  }
  while (oldTime > newTime);
  printf ("count reached %d in 2 seconds\n", count);
}
```
<script src="//repl.it/embed/IuYV/2.js"></script>

---
# Switch Statements
### The switch statement provides a easy way of having various code sections run based on a variables value:
### switch (value) { case 1: code; case 2: code; default: code}
```c
void check (char letter) {
  switch (letter) {
    case 'A': printf ("Letter A seen\n");
      break;
    case 'B': printf ("Letter B seen\n");
      break;
    default: printf ("Bad letter \"%c\" seen\n", letter);
  }
}

main () {
  check ('A');
  check ('B');
  check ('Z');
}
```
<script src="//repl.it/embed/IuYt/1.js"></script>

---
# Goto Statements
### The goto statement is a much maligned way to cause code execution to jump to a new location in a function:
### goto lineLable;
### lineLabel: code;
```c
main () {
  goto firstLabel;
  printf (“Unreachable code”);
firstLabel:
  printf (“Destination first label\n”);
  goto thirdLabel;
secondLabel:
  printf (“Destination second label\n”);
  goto fourthLabel;
thirdLabel:
  printf (“Destination third label\n”);
  goto secondLabel;
fourthLabel: ;
}
```
<script src="//repl.it/embed/IuZM/1.js"></script>
---

