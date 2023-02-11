RaceConditionsAndSignals

The goal of this project is to run a parent program (called "parent") that takes a single argument (the number of child processes it should create, at least 3 and at most 10). It will iteratively fork, set up the arguments and environment for the child, and then call execve to execute another program (called "child"). Each child process will print a greeting message to the terminal; those messages will appear in reverse order of process creation.

The purposes of each of the following files are stated below:


parent.c - This is the parent process, which will be similar to the forker program from ProcessManagement, except that it will only pass 2 or 3 arguments to each process. The steps it must carry out are described below.

child.c - This is the child process. Once it receives sigusr1 it prints a greeting with its ordinal number and PID, and then sends sigusr1 to the next process (using kill()).

await.c - This will contain three functions, which are used by both the parent and child. The functions are: usr1handler(), which will execute when sigusr1 is delivered and set the variable eventdone to 1; setup_handler(), which will install the handler using the sigaction() system call; and await_event(), which will execute the pattern shown above to block until sigusr1 is delivered.

constants.h - This is a header file that will define some useful constants.

makefile - This will compile the parent program from parent.c and await.c, and compile the child program from child.c and await.c.


Compile the source code by typing the following at the prompt $:
$ make

Code is available upon request