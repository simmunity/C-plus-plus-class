# C / C++ Programming Class 2

---
# C Language Fundamental Functionality and Features

## Objectives

- **Identify and use essential C language features that provide text and data input, output and processing using iteration**
- **Describe differences between and use both ASCII and Unicode character strings**
- **Master For loops and conditionals**
- **Master While loops and Switch statements**
- **Use Standard C Libraries**

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
  
  printf ("Unreachable code");
  
firstLabel:
  printf ("Destination first label\n");
  goto thirdLabel;

secondLabel:
  printf ("Destination second label\n");
  goto fourthLabel;

thirdLabel:
  printf ("Destination third label\n");
  goto secondLabel;

fourthLabel:
  printf ("Destination fourth label\n");
  printf ("Last goto reached\n");
}
```
<script src="//repl.it/embed/IuZM/2.js"></script>
---

# How To Setup The Command Line Terminal App
### Xcode programs can be created that do not use a graphical window for user interaction and will use the Terminal application found in the Utilities folder inside the Applications folder.  Due to a problem with permissions in the latest Sierra OS/X version, to have Xcode launch the Terminal application when your program runs you have to make a copy of the application and then rename it to Terminal2.app.  When using the curriculum Xcode projects or your own new command line projects, follow the instructions below in Xcode.  Copy Terminal and rename only once.

![](images/TerminalUseInstructions.png)

---
# Using Standard C Libraries
### Standard libraries for C are pretty complete and consistent.  On Arduino the standard libraries have omissions and anomalies often introduced to make the code smaller by excluding adanced features.  printf is one such function that has been simplified by Arduino:

### To simplify porting code we write from Xcode to Arduino, the curriculum provides a set of convienent functions in a library called TermAndKey.h and .c that abstract the differences between the two platforms.  These are the function prototypes (definitions):
```c
#include <stdio.h>
#include <stdbool.h>
#include <time.h>
#include <sys/types.h>
#include <termios.h>
#include <unistd.h>

void position_cursor (int Y, int X);
void clear_screen (void);
void init_getch (void);
int getch(void);
bool get_letter (char * pLetter);
uint64_t get_time_in_milliseconds_since_boot(void);
```
### Lets play with these in Xcode.  Launch Xcode, then load CprogrammingPt2 project and configure the terminal as described in the section on setting up the Terminal app.  Enable the STANDARD\_LIBRARIES section using code in the Extra.c file (change to conditional code sections with seperate files for each exercise).
 
---
# How To Run and Debug Programs
### When Xcode is configured to produce a command line application and the Terminal app is setup and your program compiles, you can set breakpoints and run the program.  The debugger will pause the program execution so you can inspect variables and other program state.
### [ [ [ put video or series of screen grabs at least ] ] ]

---
# Make A Navigateable Smily Character Program
### The MAKE NAVIGABLE SMILY CHARACTER section of Extra.c provides a starting point to exercise the #include "TermAndKey.h" library and explore the terminal applications keyboard input and display capabilities for use in small games.
### Lets play with these in Xcode  (use CProgrammingPt2 project)
### In the project, open the Extra.c file and grab the MAKE NAVIGATABLE SMILY CHARACTER section.### The example code uses the three C constructs we've recently explored to allow you to move a icon around the screen inside the Terminal application using the WASD key navigation convention.
```c
 do { … } while;
 switch (value) { case 1: ; case 2: ; default: ;}
 ternary_result = (ternary_condition > 1) ? value1 : value2;
```
### Lets set breakpoints on cases and then change their behavior by modifying the code.

---
# Snake Game Variations
### Creating small games in C is a way use many language features in meaningful ways:
### The SNAKE GAME VARIATIONS section of Extra.c provides a starting point to explore making small games that are suitable for running in the Terminal application.  I had a wonderful time playing Rogue and Hack character graphic dungeon games and making many animated games such as Space Invaders using just character graphics.
 
### Lets code SNAKE GAME in Xcode  (use CProgrammingPt2 project)
 
### In the project, open the Extra.c file and grab the SNAKE GAME VARIATIONS section
 
### This starter code riffs off the SMILY CHARACTER code and adds elements needed for the popular SNAKE game.  There are over ten base challenges to complete and a stretch challenges that each student should complete independently.  Challenges include increasing difficulty, various obstacles and enemies, an AI snake opponent and more.  Have fun.

---
# Snake Game Challenges
### Completing challenges is a great way to iterate on the Snake Game and deepen coding experience and debugging skills
### SNAKE GAME Challenges:
- Challenge 1, Add Bell sound effect at appropriate times using printf ("\a");
- Challenge 2, Do not exit the application on GAME OVER, ask user, y/n?
- Challenge 3, Add 20 character long tail length limit to snake
- Challenge 4, Make snake tail slowly grow longer to a maximum of 200 segments
- Challenge 5, Add obstacles at start and then add more as game progresses
- Challenge 6, Change the game so the snake head moves based on a fixed timer
- Challenge 7, Provide a game start count down and game score counter with high score
- Challenge 8, Make the snake head move slightly faster as the game progresses
- Challenge 9, Make the dying snake head explode and body whither away in an animation
- Challenge 10, Add periodically appearing enemy "bugs" that wander and vanish
- Challenge 11, Add snake food (mice) adn then grow the snakes length
- Challenge 12, Make a game configuration console to adjust difficulty and game options
- Stretch Challenge, Add an AI opponent snake that starts off facing down
- Extra credit: Break up code into a set of functions
- Extra credit: Invent new game play dynamics, changing maze obstacles?, smart AI enemies?

---
