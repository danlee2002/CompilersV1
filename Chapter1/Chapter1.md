# Chapter 1
## Introduction 
- Program languages provide a bridge between machines and people
- They are the mediums of what allows to fully harness the power of modern technology
- Compilers are what allow us to take the abstraction that makes up programming languages and put it into action
## Language Processors:
- Converts a language from one source language to another source language 
  $SourceLanguage \rightarrow Compiler \rightarrow Target Program$
 In certain cases, the target program can call user input and produce an output 
- In other words:
$$SourceLanguage \rightarrow Compiler \rightarrow Target Program \\
input \rightarrow TargetProgram  \rightarrow output$$

## Intrepreters:
- A bit different from compilers, interpreters aim to produce an output based on inputs specified by the users
## Hybrid Compilers:
- Some programming languages such as Java, utilize a combination both interpreters and compilers to produce an output 
- In the case of Java, a compiler compiles Java files into byte code which is execitable by the JVM
- Large programs tend to compiler programs in piece and use a linker to reference locations within afile
# The Structure of Compiler:
- Now we have a basic understanding of the compiler black box let's explore the mapping process: analysis and synthesis
- Analysis is the process in which a source language is taken and converted into an intermediate reprsentation
- During this process, additional information about the nature of the program is collected in a **symbol table**
- We often call this the front-end of the compiler
- On the other hand, the back-end or synthesis of the compiler is the format in which the intermediate representation is converted to the target program
- In many cases, the analysis and the synthesis process occurs multiple times 
-  Below is what may happen for some given language:
$$
characterStream \rightarrow LexicalAnalyzer \rightarrow TokenStream \rightarrow SyntaxAnalyze \rightarrow  SyntaxTree \\ \rightarrow SemanticAnalyzer \rightarrow syntaxTree \rightarrow IntermediateCodeGenerator \\
IntermediateRepresentation/ SymbolTable \rightarrow MachineIndependentCodeOptimizer \rightarrow \\
IntermediateRepresentation \rightarrow Code Generator\rightarrow targetMachineCode \rightarrow\\
MachineDependentOptimizer \rightarrow TargetMachineCode
$$
## Lexical Analysis
- Lexical Analysis or scanning is the process in which a stream of characters making up some source program is read and group into sequences called **lexemes**
- For each **lexemes**, an output token of the form $<token-name, attribute-value>$ is created
- The attribute-value points to an entry in the symbol table for this token
- Assume we have a source program with the following snippet of code 
**Figure 1.1**
```python 
position = initial + rate * 60
```
1. ```position``` is a lexeme that would be mapped into a token ```<id,,1>``` where id is an abstract symbol standing for identifier and 1 points to the symbol-table entry for an identifier holds information about identifiers, such as its name and type
2. ```=``` is a lexeme that is mapped into the token ```<=>```, the attribute value is ommited since there is no need for the attriute value
3. ```initial``` is a lexeme that is mapped into the token ```<id, 2 >```
4. ```+``` is a lexeme that is mapped into the token ```<+>```
5. ```rate``` is a lexeme that is mapped into the token ```<id,3>```
6. ``` *``` is a lexeme mapped into the token ```<*>```
7. 60 is a lexeme that is mapped into the token ```<60>```
- After we perform our lexical analysis, **figure 1.1** is turned into the following statement:
```<id,1><=><id,2><+><id,3><*><60> ```
  