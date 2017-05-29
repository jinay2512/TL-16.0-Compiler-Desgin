# TL 16.0 Compiler

# I. Purpose
The project is to design and develop a compiler for the "Toy Language", described in TL 16.0 specifi- cations, which is derived from a simplified subset of Pascal. The compiler translates TL source code, producing output at several intermediate stages, into MIPS assembly code executable in a simulator. The project is developed as part of the Programming Languages and Compilers Course during Spring 2017. We implemented this compiler using Python 3.5 language and Pycharm  IDE.

# II. Architecture
# A. Scanner
- The scanner expects a TL input file, <basename>.tl, to be specified as command-line argument when it is invoked. If the input file is not a syntactically-valid program (i.e., if the program contains a lexical element that is not a legal token or does not match the BNF grammar), the compiler outputs an error message to standard error stream.
- Our Scanner class is present in file scanner.py which implements tokenization using Regular Expressions. It also does a pre check to validate that the input program follows the rules of the TL 16.0 BNF grammar, using an external module named pyparsing. This step is  optional.
- An instance of the Scanner class would store the program it got from the input file in its attribute named program. Tokens are represented using Token class which is also present in scanner.py  file. When parse function of scanner the object is invoked the program is tokenized and the token_objects attribute of the scanner object is populated with the token objects and tokens attribute is populated with the string representation of the token objects. The string representation of the stream of token objects is output in the <basename>.tok file.

# B. Parser and Type Checking
- TThere are two parsers involved in this phase, Parse Tree Parser and Abstract Syntax Tree Parser. Both are independent of each other in our case. Parse Tree Parser present in parsetreeparsing.py, is just used to generate the parse tree and visualize it using parsetree_visual.py. On the other hand Abstract Syntax Parser present in astparsing.py is used to generate AST which is further used in next phase.There are two parsers involved in this phase, Parse Tree Parser and Abstract Syntax Tree Parser. Both are independent of each other in our case. Parse Tree Parser present in parsetreeparsing.py, is just used to generate the parse tree and visualize it using parsetree_visual.py. On the other hand Abstract Syntax Parser present in astparsing.py is used to generate AST which is further used in next phase. On the other hand Abstract Syntax Parser present in astparsing.py is used to generate AST which is further used in next phase.
- AST Parser incorporates type checking with the help of a variable map dictionary (variable_map attribute of AST Parser). We  implemented  a visualization  script  ast_visual.py which is  used to generate <basename>.ast.dot file, which is further used to render a <basename>.ast.jpg file containing type checked AST representation, this is done if graphviz application is installed in the system. If graphviz is not installed the ast_visual.py would just generate the DOT  file.

# C. MIPS Assembly and Control Flow Graph
- AST received by assembly generator script asmgeneration.py converts the Abstract Syntax Tree into assembly code directly, skipping the intermediate code generation step. The string represen- tation of the MIPS code is output in the <basename>.s  file.
- In parallel CFG is also generated using cfg_visual.py in the form of DOT file with name rep- resentation as <basename>.cfg.dot, which is further used to render a <basename>.cfg.jpg file containing type checked AST representation, this is done if graphviz application is installed in the system. If graphviz is not installed the cfg_visual.py would just generate the DOT  file.

# III. Technologies Used
The whole compiler was coded in using Python 3.5 and Pycharm IDE. Other tools like Graphviz and QT simulator where used to check the AST, CFG and execution of the MIPS  instructions.
