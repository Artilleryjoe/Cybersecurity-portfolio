# Lab 15: Performing a Memory-Based Attack

## Course  
**CYB/500: Advanced Cybersecurity Concepts**

## Objective  
This lab demonstrates how to craft and execute a basic memory-based (buffer overflow) attack by manipulating stack memory in a simple C application. The goal is to observe how user input can overwrite adjacent memory regions when proper input validation is not enforced.

## Tools Used  
- GCC (GNU Compiler Collection)  
- Linux Terminal  
- Custom C code (`bof.c`)  
- Standard I/O libraries  

## Procedure  
- Create a new C source file using `touch bof.c`
- Open the file with `nano bof.c`
- Write the following vulnerable C program:
  ```c
  #include <stdio.h>
  #include <stdlib.h>

  int main(int argc, char *argv[]) {
      char name[10] = "";
      char nextvar[10] = "";

      printf("-----------------\n");
      printf("Enter your name: ");
      scanf("%s", name);

      printf("Your name is %s\n", name);
      printf("Next memory location contains: [ %s ]\n", nextvar);

      return 0;
  }

  Save and compile the file using gcc -o bof bof.c

Verify compilation with ls

Run the program with ./bof

Enter input that exceeds the 10-character buffer size to observe stack corruption
Example: Inputting AAAAAAAAAAAAA shows how nextvar is affected by buffer overflow

Results
Normal input results in expected behavior:
  ```pgsql
Enter your name: Alice  
Your name is Alice  
Next memory location contains: [ ]
Overflow input (ABCDEFGHIJKL):

```pgsql
Your name is ABCDEFGHIJKL  
Next memory location contains: [ L ]
This demonstrates that excess characters written to name overflow into nextvar, confirming a stack-based buffer overflow vulnerability.

Lessons Learned
- Even small C programs can contain serious vulnerabilities when memory management isn't handled properly.
- Buffer overflows are a common entry point for memory-based attacks and emphasize the need for secure coding practices (e.g., bounds checking).
- Exploiting this type of bug in real-world software could lead to arbitrary code execution, data leakage, or system crashes.
- Using tools like valgrind, stack canaries, or safer input functions (fgets over scanf) can mitigate such issues.
