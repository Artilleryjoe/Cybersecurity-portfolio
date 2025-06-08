# Lab 15: Performing a Memory-Based Attack

## Course  
CYB/500: Advanced Cybersecurity Concepts

## Objective  
Demonstrate a basic memory-based (buffer overflow) attack by overflowing a character array in a simple C program.

## Tools Used  
- GCC (GNU Compiler Collection)  
- Linux Terminal  
- C programming

## Procedure  
- Create a new file: `touch bof.c`  
- Open it: `nano bof.c`  
- Enter the following code:

# Lab 15: Performing a Memory-Based Attack

## Course  
CYB/500: Advanced Cybersecurity Concepts

## Objective  
Demonstrate a basic memory-based (buffer overflow) attack by overflowing a character array in a simple C program.

## Tools Used  
- GCC (GNU Compiler Collection)  
- Linux Terminal  
- C programming

## Procedure  
- Create a new file: `touch bof.c`  
- Open it: `nano bof.c`  
- Enter the following code:

    ````c
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


- Compile: `gcc -o bof bof.c`
- Run: `./bof`
- Test normal and overflow input (e.g., input more than 10 characters)

## Results

- Normal input:

      ```Enter your name: Alice  
      Your name is Alice  
      Next memory location contains: [ ]```

- Overflow input:
  
      ```Enter your name: ABCDEFGHIJKL  
      Your name is ABCDEFGHIJKL  
      Next memory location contains: [ L ]```

## Lessons Learned

