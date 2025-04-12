# ShelluMama: Unix Shell Clone

## Features

- Basic command execution
- I/O redirection (`<`, `>`, `>>`)
- Command piping (`|`)
- Multiple commands (`;`)
- Logical operators (`&&`)
- Command history
- Signal handling

## Building the Shell

```bash
gcc -o shell shell.c
```

## Running the Shell

```bash
./shell
```

## Feature Testing Guide

### Basic Shell Functionality

```bash
# Test simple commands
ls
pwd
echo "Hello World"

# Test built-in commands
cd /tmp
pwd
cd ~
pwd
```

### I/O Redirection

```bash
# Input redirection
cat < /etc/passwd

# Output redirection
ls -la > output.txt
cat output.txt

# Output redirection with append
echo "First line" > append_test.txt
echo "Second line" >> append_test.txt
cat append_test.txt  # Should show both lines
```

### Command Piping

```bash
# Simple pipe
ls -la | grep ".txt"

# Multiple pipes
cat /etc/passwd | grep "root" | wc -l

# Complex piping
ls -la | grep "." | sort -r | head -n 3
```

### Multiple Commands (Semicolon)

```bash
# Execute multiple commands in sequence
echo "Testing" ; ls ; pwd
```

### Logical Operations (&&)

```bash
# Second command runs only if first succeeds
ls && echo "ls succeeded"
ls /nonexistent && echo "This won't print"

# Chain multiple commands with &&
mkdir test_dir && cd test_dir && pwd && cd .. && rm -r test_dir
```

### Command History

```bash
# Run several commands, then:
history
```

### Signal Handling

```bash
# Start a long-running command and press CTRL+C
sleep 10
# Press CTRL+C while it's running

# Verify the shell is still running by executing another command
echo "Shell is still alive"
```

### Combined Features

```bash
# Redirection with pipes
ls -la | grep ".txt" > text_files.txt

# Multiple commands with different features
echo "Testing" > test.txt ; cat test.txt | grep "Test" && echo "Found it!"

# Complex test case
find / -name "*.txt" 2>/dev/null | grep "etc" | sort | head -n 5 > result.txt && cat result.txt
```

## Built-in Commands

- `cd [directory]`: Change current directory
- `history`: Show command history
- `exit`: Exit the shell

## Error Handling

The shell provides error messages for:
- Command not found
- Permission denied
- File not found
- Other system errors

## Notes

- CTRL+C terminates the current command but not the shell
- The shell supports up to 100 history entries
- Pipes can be chained up to 10 times in a single command
