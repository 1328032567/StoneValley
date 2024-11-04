# Compiler
CC = gcc

# Compiler flags
CFLAGS = -Wall -g

# Source files
SRC = $(wildcard *.c)


# Object files
OBJ = $(SRC:.c=.o)

# Static library name
TARGET = libsv.a

# Default target
all: $(TARGET)

# Create static library
$(TARGET): $(OBJ)
	ar rcs $@ $^

# Compilation rule
%.o: %.c $(HEADERS)
	$(CC) $(CFLAGS) -c $< -o $@

# Clean up
clean:
	rm -f $(OBJ) $(TARGET)

# Phony targets
.PHONY: all clean
