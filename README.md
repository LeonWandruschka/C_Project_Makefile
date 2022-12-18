# Usage

## Prior requirements

To use commands like ```make valgrind``` or ```make doxygen``` you need to have the right dependencies installed.\
Be aware that valgrind was only tested on linux.

See how to install: [VALGRIND](#valgrind-installation) or [Doxygen](#doxygen-installation)

### Valgrind installation

0. Uninstall the non working valgrind version with root rights (eg. sudo): \ ```apt-get --purge valgrind``` or ```dpkg --remove valgrind``` or ```yum remove valgrind``` \ (Only if you have a older version of valgrind installed)

1. Obtain sources from [here](https://sourceware.org/pub/valgrind/valgrind-3.20.0.tar.bz2).

2. Identify the latest version (for example 3.20.0)

3. Download sources: ```wget https://sourceware.org/pub/valgrind/valgrind-3.20.0.tar.bz2```

4. Decompress archive ```tar xvf valgrind-3.17.0.tar.bz2```

5. Go to uncompressed archive ```cd valgrind-3.20.0```

6. Configure ```./configure```

7. Compile ```make```

8. Install ```make install``` (with root rights [sudo])

### Doxygen installation

Linux \
```sudo apt-get install doxygen```

MacOs \
```brew install doxygen```

Windows \
Get it [here](https://www.doxygen.nl/files/doxygen-1.9.5-setup.exe).

## Project setup


The file containing ```main``` and all other ```.c``` files must be placed in ```src```.
The ```.h``` files must be placed in ```include```.
The ```executable``` file is placed in the ```build``` folder. 

To create the folders you can simply call ```make create-folders```

```
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
```

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
| (Default) LOG_FILE = 0 | Text from valgrind will be presented in terminal |
| LOG_FILE = 1 | Text from valgrind will be safed in log_valgrind.log file |





### make build

The ```make build``` command builds the current project and puts the executable file in the build folder.
All created .o files will be deleted.

### make run

The ```make run``` command builds the current project and executes it.
All created .o files will be deleted. \
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

The ```make valgrind``` builds the project and uses valgrind to search for possible memory errors / leaks. \
(Please check [Pre requirements](#prior-requirements))

### make doxygen

The ```make doxygen``` command creates a new doxygen documentation. \
(Please check [Pre requirements](#prior-requirements))

