# C / C++ Programming Class 5

---
### C++ language features add object orientation, greater code modularity and large project scalability to C language.
## Objectives
- **Master use of object oriented programming added to C**
- **Use classes and this**
- **Use the new operator**
- **Explore function overloading**
- **Use encapsulation**

---
# Object Orientation
### C++ provides a convenient way to group related data and methods together in a single "object" using a class:
```c
class invader {
  public:
    invader (int x, int y, int type)
 { xPos = x; yPos = y; alienType = type};
    move (void) { ... };
  private:
    void nextPose (void) { ... };
    int  xPos;
    int  yPos;
    int  alienType;
};
```
### C++ allows classes to be instantiated conveniently:
```c 
invader * alien = new invader (100, 150, FAT_ALIEN);
```

---
# Function Overloading
### C++ allows function overloading, where functions have the same name but different parameters:
```c
class Turret {
  public:
   Turret (void) { xPos = 20 }; // default to 20
   Turret (int x) { xPos = x; }; // consructor
  private:
    int  xPos;
    ...
};
```
### C++ function overloading avoids function name spaghetti
```c
Turret secondTurret; // use default constructor
Turret * mainTurret = new Turret (30);
```

---
# Encapsulation
### C++ makes it convenient to group and protect class variables from access by code outside the class using the private keyword:
```c
class Turret {
  public:
   Turret (void) { xPos = 20 }; // default to 20
   Turret (int x) { xPos = x; }; // consructor
   Weapon missile;
  private:
    int  xPos;
    int  livesRemaining;
    int  score;
};
```
### C++ only allows methods in the class Turret access to private variables such as xPos and score

---
