# Ex.No:4
# RECOGNITION OF A VALID VARIABLE WHICH STARTS WITH A LETTER FOLLOWED BY ANY NUMBER OF LETTERS OR DIGITS USING YACC
## Register Number: 212223040002
## Date: 30/09/2025
## Aim:
To write a YACC program to recognize a valid variable which starts with a letter followed by any number of letters or digits.
## ALGORITHM
1.	Start the program.
2.	Write a program in the vi editor and save it with .l extension.
3.	In the lex program, write the translation rules for the keywords int, float and double and for the identifier.
4.	Write a program in the vi editor and save it with .y extension.
5.	Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l
6.	Compile the yacc program with YACC compiler to produce output file as y.tab.c. eg $ yacc –d arith_id.y
7.	Compile these with the C compiler as gcc lex.yy.c y.tab.c
8.	Enter a statement as input and the valid variables are identified as output.
## PROGRAM:
##### lex file:
```
%{
#include "expr4.tab.h"
%}

%%

[a-zA-Z][a-zA-Z0-9]*    { return VARIABLE; }
.|\n                    { return INVALID; }

%%
int yywrap() {
    return 1;
}


```
###### yacc file:
```
%{
#include <stdio.h>
#include <stdlib.h>

int yylex(void);
void yyerror(const char *s);
%}

%token VARIABLE INVALID

%%

input:
    VARIABLE { printf("Valid variable name\n"); }
  | INVALID  { printf("Invalid variable name\n"); }
  ;

%%

int main() {
    printf("Enter a variable name: ");
    yyparse();
    return 0;
}

void yyerror(const char *s) {
    // we handle invalid input in the grammar, so this can stay empty
}


```
## Output:
###### Valid Input :
<img width="430" height="77" alt="image" src="https://github.com/user-attachments/assets/a05c59a6-34fb-41cb-9776-523656e2469d" />

###### Invalid Input :
<img width="508" height="71" alt="image" src="https://github.com/user-attachments/assets/7c0da1f5-ff25-45d9-9173-023262d37ba5" />


## Result
A YACC program to recognize a valid variable which starts with a letter followed by any number of letters or digits is executed successfully and the output is verified.
