# Pascal-Interpreter

This is a pascal interpreter from scratch using Python language. The input is a pascal code file and this interpreter 
evaluates the arithmetic expressions, variables declaration, type-checking, symbol table management, nested procedures, Pascal program syntax and more.

The properties of this interpreter are - 
1. It does a lexical analysis (or scans or tokenizes) of the input file to generate tokens, one at a time.
2. It generates reserved keyword tokens along with declared tokens of various types. 
3. It uses a recursive-descent parser approach to evaluate and generate a tree from the lexer object.
4. It also allows comments in the pascal code file for better implementation.
5. Uses Abstract-Syntax tree (AST) as an intermediate representation (IR).
6. Implements a NodeVisitor class as a walker class for the AST.
7. Implements a Symbol Table to define variables and built in type symbols. 
8. Implements define and lookup methods in the symbol table to define a variable and lookup that variable for type-checking and maintain the integrity of the code.

The grammar of this language-implementation is -

1. program : PROGRAM variable SEMI block DOT
2. block : declarations compound_statement
3. declarations : VAR (variable_declaration SEMI) | (PROCEDURE ID SEMI block SEMI)* | empty
4. variable_declaration : ID (COMMA ID)* COLON type_spec
5. type_spec : INTEGER
6. compound_statement : BEGIN statement_list END
7. statement_list : statement | statement SEMI statement_list
8. statement : compound_statement | assignment_statement | empty
9. assignment_statement : variable ASSIGN expr
10. empty :
11. expr : term ((PLUS | MINUS) term)*
12. term : factor ((MUL | INTEGER_DIV | FLOAT_DIV) factor)*
13. factor : PLUS factor
             | MINUS factor
             | INTEGER_CONST
             | REAL_CONST
             | LPAREN expr RPAREN
             | variable
14. variable: ID

The symbol Table management is an interestinng concept that help maintain the correctness of the code and it is important to understand and implement that so that the integrity of the pascal code is maintained.

The grammer stated above will help you understand how the code is analyzed and is evaluated. 

See this in action - 

![Demo](https://cloud.githubusercontent.com/assets/22873739/24975598/3c81b59a-1f94-11e7-8872-7ebb1139350c.png)

Run the file as it is given in the screenshot above. What you will see here is the Symbol Table content and Global Memory scope of the program and the final value of each variable after evaluating arithmetic expressions (if any).

Enjoy :D 

P.S. - More commits coming soon :)
