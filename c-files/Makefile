# Which compiler to use
CC := c++

# Compiler flags go here.
CFLAGS := -g -Wall -std=c++17

# Include path
SRCDIR := src
INC := include

# Linker flags go here.
# LDFLAGS = -lcomedi -lm

# list of sources
SRC := $(wildcard $(INC)/*.cpp) $(wildcard $(INC)/*/*.cpp) $(SRCDIR)/main.cpp

# Create general INC variable that scale with library
# INC += $(wildcard $(SRC:%/*.cpp=%))
INC +=  $(sort $(dir $(wildcard include/*))) $(sort $(dir $(wildcard include/*/*)))
INC := $(INC:%=-I%)

# Define all object files.
OBJ := $(SRC:.cpp=.o) 

# program executable file name.
TARGET := exec

# Correct file ending for Windows systems
# UNAME = $(shell uname)

# ifeq ($(shell grep -qE "(Microsoft|WSL)" /proc/version &> /dev/null))
# 	TARGET := $(TARGET).exe    
# endif

# ifeq ($(UNAME), MINGW32_NT-6.2)
# 	TARGET = $(TARGET).exe
# endif


# top-level rule, to compile everything.
all: $(TARGET)

# rule to link the program
$(TARGET): $(OBJ)
	@echo Linking files...
	@$(CC) $^ -o $@

# Compile: create object files from C source files.
%.o : %.cpp
	@echo Compiling files...
	@$(CC) $(CFLAGS) -c $< -o $@ $(INC)

# rule for cleaning re-compilable files.
clean:
	@echo Cleaning up object files...
	@rm -f $(OBJ)
	@echo Complete!

rebuild:	clean all

# To execute program with make
run:	all
	@./$(TARGET)

# Debugging purposes
print-%  : ; @echo $* = $($*)

.PHONY: all rebuild clean run


