# get_next_line - Custom Line Reading Implementation
Welcome to my get_next_line repository! This project features my implementation of the get_next_line function in C, designed to read a line from a file descriptor.
The function dynamically allocates memory as needed to handle lines of arbitrary length.

## Implementation Overview

* Files
get_next_line.c: Contains the main get_next_line function.
get_next_line_bonus.c: An alternative version of get_next_line with additional features.
* Helper Functions
befor(char *buff): Extracts characters from the beginning of the buffer until a newline character is encountered, creating a new string.
after(char *buff): Extracts characters after the newline character in the buffer, creating a new string.
read_and_add(char *save, int fd): Reads from the file descriptor and adds the content to the existing save buffer.

## Function Signatures
get_next_line(int fd)
```
#include "get_next_line.h"

char *get_next_line(int fd);
```
Reads a line from the specified file descriptor (fd) and returns it as a dynamically allocated string.
The function continues reading until a newline character is encountered, and the line is returned without the newline.
Returns NULL on errors or when there are no more lines to read.

get_next_line_bonus(int fd)
```
#include "get_next_line_bonus.h"

char *get_next_line_bonus(int fd);
```
Similar to get_next_line, but designed for handling multiple file descriptors simultaneously.
The state for each file descriptor is stored separately.

## Usage Example
```
#include "get_next_line.h"

int main() {
    int fd = open("example.txt", O_RDONLY);
    char *line;

    while (get_next_line(fd, &line) > 0) {
        printf("%s\n", line);
        free(line);
    }

    close(fd);
    return 0;
}
```
This example demonstrates how to use the get_next_line function to read lines from a file and print them.

## Compilation
To compile the get_next_line function, include the relevant header file (get_next_line.h) and link with the necessary libraries.
You can compile manually with:
```
gcc -Wall -Wextra -Werror -D BUFFER_SIZE=32 get_next_line.c main.c -o gnl_example
```
For the get_next_line_bonus version:
```
gcc -Wall -Wextra -Werror -D BUFFER_SIZE=32 get_next_line_bonus.c main_bonus.c -o gnl_example_bonus
```
## Note
These get_next_line implementations are based on a specific buffer size defined during compilation (BUFFER_SIZE).
Contributions and feedback are welcome to improve and adapt the implementation for different use cases.

Happy line reading with get_next_line!
