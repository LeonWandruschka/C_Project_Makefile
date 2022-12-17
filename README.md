# Usage

## Prior requirements

## Project setup


The file containing ```main``` and all other ```.c``` files must be placed in ```src```.
The ```.h``` files must be placed in ```include```.
The ```executable``` file is placed in the ```build``` folder. 

To create the folders you can simply call ```make create-folders```

.
├── src
│   └──  main.c
│   └──  foo.c
│   └──  bar.c
├── include
│   └──  foo.h
│   └──  bar.h
├── build
│   └──  executable


Commands:
- make build
- make run 
- make debug
- make clean
- make cleanobj
- make create-folders
- make valgrind
- make doxygen


| ARGUMENTS | Additional info |
|---|---|
| (Default) DEBUG = 0 | -O3 -std=c17 |
| DEBUG = 1 | -g -O0 -Wall -Wextra -Wpedantic -Wconversion -std=c17 |
| (Default) COMPILER = 0 | clang |
| COMPILER = 1 | gcc |
| (Default) REMOVE_OBJ_FILES = 1 | Removes Objectfiles (.o) from build directory |
| REMOVE_OBJ_FILES = 0 | Creates all Objectfiles (.o) in the build directory |
| (Default) DEBUGGER = 0 | Sets debugger to lldb |
| DEBUGGER = 1 | Sets debugger to gdb |





### make build

The ```make build``` command builds the current project and puts the executable file in the build folder.
All created .o files will be deleted.

### make run

The ```make run``` command builds the current project and executes it.
All created .o files will be deleted.
(To option to give Arguments to the program is not implemented yet.)

### make debug

The ```make debug``` command builds the project and executes the programm with gdb or lldb as debugger.
The .o files will not be deleted!
It is not necessary to call ```make debug``` with DEBUG=1.
The correct compiler flags will be used automatically.

### make clean

The ```make clean``` command removes all files from the build folder.

### make cleanobj 

The ```make cleanobj``` command removes all existing .o files in the build folder

### make create-folders

The ```make create-folders``` command creates the needed folders ```src```,```include``` and ```build``` if they do not exist. (Only needed at the beinning of a new project)

### make valgrind

The ```make valgrind``` builds the project and uses valgrind to search for possible memory errors / leaks.
(Please check [Pre requirements](Pre requirements))

### make doxygen

The ```make doxygen``` command creates a new doxygen documentation.
(Please check [Pre requirements](Pre requirements))

