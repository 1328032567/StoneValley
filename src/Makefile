# Compiler
CC = gcc

# Compiler flags
CFLAGS = -Wall -g -O2

# Source files
SRC = $(wildcard *.c)

# Object files
OBJ = $(SRC:.c=.o)

# Static library name
TARGET = libsv.a

# Test files
TEST_UNIX = sort_test/sort_test_unix.c
TEST_MAC = sort_test/sort_test_unix.c
TEST_WIN = sort_test/sort_test_win.c

# Default target
all: $(TARGET)

# Create static library
$(TARGET): $(OBJ)
	ar rcs $@ $^

# Compilation rule for object files
%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@

# Test target
.PHONY: test
test:
	@echo "Specify 'unix', 'mac' or 'win' to test."

# Unix test
.PHONY: test-unix
test-unix: $(TARGET) $(TEST_UNIX)
	$(CC) -o sort_test_unix $(TEST_UNIX) -L. -lsv
	time ./sort_test_unix -1

# Max test
.PHONY: test-mac
test-mac: $(OBJ) $(TEST_MAC)
	$(CC) -o sort_test_mac $(TEST_MAC) $(OBJ)
	time ./sort_test_mac -1

# Windows test
.PHONY: test-win
test-win: $(TARGET) $(TEST_WIN)
	$(CC) -o sort_test_win $(TEST_WIN) -L. -lsv
	time ./sort_test_win -1

# Clean up
clean:
	rm -f $(OBJ) $(TARGET) sort_test_unix sort_test_win

# Phony targets
.PHONY: all clean test test-unix test-mac test-win
