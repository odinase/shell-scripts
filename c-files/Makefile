# Which compiler to use
CC := g++

# Compiler flags go here.
CFLAGS := -g -Wall -std=c++17

# Include path
SRCDIR := src
INC := include

# Linker flags go here.
# LDFLAGS = -lcomedi -lm

SRC_FILE_EXT := cpp
OBJ_FILE_EXT := o

# list of sources
SRC := $(wildcard $(INC)/*.$(SRC_FILE_EXT)) $(wildcard $(INC)/*/*.$(SRC_FILE_EXT)) $(SRCDIR)/main.$(SRC_FILE_EXT)

# Create general INC variable that scale with library
# INC += $(wildcard $(SRC:%/*.cpp=%))
INC +=  $(sort $(dir $(wildcard include/*))) $(sort $(dir $(wildcard include/*/*)))
INC := $(INC:%=-I%)

# Define all object files.
OBJ := $(SRC:.$(SRC_FILE_EXT)=.$(OBJ_FILE_EXT)) 

# program executable file name.
TARGET := exec

# top-level rule, to compile everything.
all: $(TARGET)

# rule to link the program
$(TARGET): $(OBJ)
	@echo Linking files...
	@$(CC) $^ -o $@

# Compile: create object files from source files.
%.$(OBJ_FILE_EXT) : %.$(SRC_FILE_EXT)
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

