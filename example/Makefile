##### EXAMPLE MAKEFILE #####
# This Makefile is a simple implementation for the "hello-world" program. The
# project is divided between 3 files:
# 	- main.cc
# 	- hello-world.cc
# 	- hello-world.h
#
# The first two files both have the ".cc" extension, signifying that they are
# C++ source files. These contain the program's implementation.
#
# The third file has a ".h" extension, signifying that it is a header file. It
# contains a declaration for each function in the associated source file. Using
# the header files allows a source file to use the public functions of a file
# "included" in its source file.
#
# C++ is a compiled language, which means that all source files in a C++ program
# must be compiled into object files, which are then linked into an executable
# before it can be run. There are two object files ("main.o" and
# "hello-world.o") and one executable file ("test") created by the compiler for
# this program. The compiler takes two steps to create the executable. The first
# step is to compile object files for each of the soruce files. The next step is
# to link each of the object files and create the executable.

##### GLOBAL VARIABLES #####
# Below are the definitions for global variables of the Makefile. Using global
# variables makes it easy to make a change once that will take affect in
# multiple places in the Makefile.
# For example, we have decided to call our executable "test", but if we want to
# change that to something such as "executable", we only need to change the
# global variable and the Makefile will still work correctly.
# A globabl variable must be surrounded by parentheses and follow
# the "$". For example, $(VAR).

# The line below defines the OBJS variable, which holds all of the object files
# for the program.
OBJS = main.o hello-world.o

# The line below defines the EXEC variable, which holds the executable for the
# program.
EXEC = test

# The two lines below define the SRC and INC variables, which hold the source
# and header directories respectively.
SRC = src
INC = inc

# The line below defines the compiler we are using.
CC = g++

# The lines below identify flags used in the commands of Makefile.

DEBUG = -g
# The line below contains the flags for the compile step.
CFLAGS = -Wall -c $(DEBUG) -I$(INC)/
# The line below contains the flags for the linking step.
LFLAGS = -Wall $(DEBUG)

##### RULES #####
# The lines below contain the rule definitions. Each rule definition contains
# two lines: the first is the dependency list, and the second is the command.
#
# The dependency line has the following template:
# 	target : dependencies
# In order to "make" the target, each of its dependencies must already be "made"
#
# The commmand line is the command that is executed for the target. Prepending
# the "@" symbol before the command suppresses the console output.

# The lines below defines the "run" rule, which can be executed by typing "make
# run". It depends on the executable to be ready before it can be run. The
# command executes the executable.
run : $(EXEC)
	@./$(EXEC)

# The lines below defines the "test" (remember that EXEC is the global variable
# for "test") rule. It depends on each of the object files defined int OBJS (in
# this case, the main.o and hello-world.o object files). The command links the
# object files into the executable.
$(EXEC) : $(OBJS)
	@$(CC) -o $(EXEC) $(LFLAGS) $(OBJS)

# The lines below defines the rule to compile the "main.o" object file. It is
# one of the dependencies for the executable, and depends on the "main.cc"
# source file and the "hello-world.h" header file. The command compiles the
# "main.o" object file.
# Using the "\" at the end of the line allows a line to be separated over
# multiple lines for readability. In this case, the "dependency line" consists
# of the first three lines.
main.o : \
	$(SRC)/main.cc \
	$(INC)/hello-world.h
	@$(CC) $(CFLAGS) $(SRC)/main.cc

# THe lines below define the rule to compile the "hello-world.o" object file. It
# is another of the dependencies for the executable, and depends on the
# "hello-world.cc" source file and the "hello-world.h" header file. The command
# compiles the "hello-world.o" object file.
hello-world.o : \
	$(SRC)/hello-world.cc \
	$(INC)/hello-world.h
	@$(CC) $(CFLAGS) $(SRC)/hello-world.cc

# The lines below define the "clean" rule. It can be used to clean up the
# working directory, and should be executed after updating the Makefile. It
# does not have any dependencies, and is used to remove all of the object files and the executable. 
clean:
	\rm *o hello

