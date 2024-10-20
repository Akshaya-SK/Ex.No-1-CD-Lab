Ex. No : 1

IMPLEMENTATION OF SYMBOL TABLE

Register Number : 212223040011

Date : 19-10-2024

AIM:

To write a C program to implement a symbol table.

ALGORITHM:

Start the program.
Get the input from the user with the terminating symbol ‘$’.
Allocate memory for the variable by dynamic memory allocation function.
If the next character of the symbol is an operator then only the memory is allocated.
While reading, the input symbol is inserted into symbol table along with its memory address.
The steps are repeated till ‘$’ is reached.
To reach a variable, enter the variable to be searched and symbol table has been checked for corresponding variable, the variable along with its address is displayed as result.
Stop the program.

PROGRAM:

```#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <stdlib.h> // Added for malloc and free

#define MAX_EXPRESSION_SIZE 100

int main() {
    int i = 0, j = 0, x = 0, n, flag = 0;
    void *add[5];
    char b[MAX_EXPRESSION_SIZE], d[15], c, srch;

    printf("Enter the Expression terminated by $: ");
    while ((c = getchar()) != '$' && i < MAX_EXPRESSION_SIZE - 1) {
        b[i++] = c;
    }
    b[i] = '\0'; // Null-terminate the string
    n = i - 1;

    printf("Given Expression: %s\n", b);

    printf("\nSymbol Table\n");
    printf("Symbol\taddr\ttype\n");

    for (j = 0; j <= n; j++) {
        c = b[j];
        if (isalpha((unsigned char)c)) { 
            // Check if it's an alphabet
            if (j == n || strchr("+-*=;", b[j + 1])) {
                // Allocate memory and handle it properly
                void *p = malloc(sizeof(char));
                if (p == NULL) {
                    printf("Memory allocation failed!\n");
                    return 1;
                }
                add[x] = p;
                d[x] = c;
                printf("%c\t%p\tidentifier\n", c, p);
                x++;
            }
        }
    }

    printf("\nThe symbol to be searched: ");
    while ((srch = getchar()) == '\n'); // Skip newline character

    for (i = 0; i < x; i++) {
        if (srch == d[i]) {
            printf("Symbol Found\n");
            printf("%c@address %p\n", srch, add[i]);
            flag = 1;
            break;
        }
    }

    if (flag == 0) {
        printf("Symbol Not Found\n");
    }

    // Free dynamically allocated memory
    for (i = 0; i < x; i++) {
        free(add[i]);
    }

    return 0;
}
```
OUTPUT:

![image](https://github.com/user-attachments/assets/695108ce-b98d-4fad-bc7a-8119c41de146)

RESULT:

The program to implement a symbol table is executed and the output is verified.
