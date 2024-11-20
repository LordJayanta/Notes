## source 
- [geeksforgeeks](https://www.geeksforgeeks.org/variables-in-c/?ref=lbp)

## Tabel of Content
- [C Variable Types](#c-variable-types)


## C Variable Types
The C variables can be classified into the following types:
1. Local Variables
2. Global Variables
3. Static Variables
4. Automatic Variables
5. Extern Variables
6. Register Variables


###  Local Variables in C
```c
#include <stdio.h>

void function(){
    int x = 10; // local variable
    printf("%d", x);
}
int main() { function(); }
```

###  Global  Variables in C
```c
#include <stdio.h>

int x = 20; // global variable

void function1() { printf("Function 1: %d\n", x); }

void function2() { printf("Function 2: %d\n", x); }

int main()
{

    function1();
    function2();
    return 0;
}
```