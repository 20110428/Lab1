# 20110428_Nguyễn Sỹ Khải

# Task 1:Buffer Overflow
## 1.1
## Overview

This demonstrates a buffer overflow exploit on a vulnerable C program. The exploit takes advantage of the unsafe use of `gets()` to overwrite the return address on the stack and execute a hidden function.

## Vulnerable Program

```c
#include<stdio.h>
#include<unistd.h>

void secretFunc()
{
    printf("Congratulation!\n:");
}

int vuln(){
    char array[200];
    printf("Enter text:");
    gets(array);
    return 0;
}

int main(int argc, char* argv[]){
    if (argv[1] == 0){
        printf("Missing arguments\n");
    }
    vuln();
    return 0;
}
