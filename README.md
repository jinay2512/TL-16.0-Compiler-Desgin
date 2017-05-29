# TL-Compiler

##########################################################
[COMMAND]

chmod +x exec.sh
./exec.sh <filepath to basename.tl>

##########################################################
[EXAMPLE] 

./exec.sh simple1.tl 

Generates:

simple1.tok------> File containing List of tokens or Error
simple1.ast.dot--> graphviz dot file (type checked)
simple1.ast.jpg------> jpg render of dot file (type checked, with red nodes as error)

##########################################################
[TOUBLESHOOT]

if some error persists, try:

python3 ./../ast_visual.py <basename.tl>

##########################################################
There are example files in this directory, Please ignore them.
