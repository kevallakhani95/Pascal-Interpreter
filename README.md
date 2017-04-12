# Pascal-Interpreter

This is a pascal interpreter I developed from scratch using Python language. The input is a pascal code and this interpreter 
evaluates the arithmetic expressions, variables declaration, type-chacking, symbol table management, nested procedures and more.

The properties of this interpreter are - 
1. It does a lexical analysis (or scans or tokenizes) of the input file to generate tokens, one at a time.
2. It generates reserved keyword tokens along with declared tokens of various types. 
3. It uses a recursive-descent parser approach to evaluate and generate a tree from the lexer object.
4. It also allows comments in the pascal code file for better implementation.
5. Uses Abstract-Syntax tree (AST) as an intermidiate representation (IR).
6. Implements a NodeVisitor class as a walker class for the AST.
7. Implements a Symbol Table to define variables and built in type symbols. 
8. Implements define and lookup methods in the symbol table to define a variable and lookup that variable for type-checking 
and maintain the integrity of the code.

The grammar of this language-implementation is -
i. program : PROGRAM variable SEMI block DOT
ii. block : declarations compound_statement
iii. declarations : VAR (variable_declaration SEMI)+
                     | (PROCEDURE ID SEMI block SEMI)*
                     | empty
        variable_declaration : ID (COMMA ID)* COLON type_spec
        type_spec : INTEGER
        compound_statement : BEGIN statement_list END
        statement_list : statement
                       | statement SEMI statement_list
        statement : compound_statement
                  | assignment_statement
                  | empty
        assignment_statement : variable ASSIGN expr
        empty :
        expr : term ((PLUS | MINUS) term)*
        term : factor ((MUL | INTEGER_DIV | FLOAT_DIV) factor)*
        factor : PLUS factor
               | MINUS factor
               | INTEGER_CONST
               | REAL_CONST
               | LPAREN expr RPAREN
               | variable
        variable: ID

