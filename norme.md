# Norme

## editor

you can use any editor you wan't but do not add config file (.vscode, .qtpro, ...)

## git

- gitignore will be added to the git repo and need to be updated
- build folder will not be added to the git repo

## compilation

- the qmake build system will be used on windows, and the cmake build system on linux
- when you add files to the project build list you need to add them to all of the build systems
- if you don't update one of the build system for any reason add all the modifications in the modif.txt file so someone else can do it
- the build folder will have the same treeview as the src folder and will have all of the build files
- the executable will be in the build folder

## namespaces

- don't use `using namespace nsp;`
- every part of the compiler will have it's own namespace:
    - tokenizer : `Tokenizer`
    - parser : `Parser`
    - code generator : `CodeGenerator`
    - ... etc
- you can add namespaces but they need to be added as comment in their .hpp file like this:
    ```
    /* Namespace <name> [<description>]
     *  globals:
     *    - globalName1 [<description>]
     *    - globalName2 [<description>]
     *    - globalName3 [<description>]
     *    - ...
     *  functions:
     *    - functionName1 [<description>]
     *    - functionName2 [<description>]
     *    - functionName3 [<description>]
     *    - ...
     *  functions:
     *    - ClassName1 [<description>]
     *    - ClassName2 [<description>]
     *    - ClassName3 [<description>]
     *    - ...
     */
    ```
- all namespaces will be prototypped in the .hpp file like : `namespace <name> {<namespace prototypes>}`

## names

- variables and function names are in camel case but with start character in lower case :
```
    int TokenNumber(0); // incorrect
    int tokenNumber(0); // correct

    int printHello(); // correct
    int PrintHello(); // incorrect
```
- global variables names need to start with `g_` : 
```
    int[12] g_numbers; // correct
    int[12] g_Numbers; // incorrect (see begining of the name part)
    int[12] numbers; // incorrect (see begining of the name part)
```
- class, namespaces, struct, unions and enums names are camel case but with start character in uppercase:
```
    class TokenInfo; // correct
    class tokenInfo; // incorrect
    class Tokeninfo; // incorrect

    namespace TokenizerUtils; // correct
    namespace tokenizerUtils; // incorrect
    namespace Tokenizerutils; // incorrect
```

## classes

- property are private (or protected only for inheritance) and method are public
- static property/method are prohibited and will be static globals and functions
- 

## global variables

- globals will all be defined in .hpp file as : 
```
    /* global <name> */
    extern <type> g_<name>;
```
- if you have globals that will be use only in the file their are in, use `static` keyword
```
    static int g_myNumber;
```

## functions

- functions parameter won't have names in prototypes and functions will all be defined in .hpp file as : 
```
    /* function <name> (<returnType>)
        <paramType> <paramName> : <description>
        <paramType> <paramName> : <description>
        <paramType> <paramName> : <description>
        ...
    */
    <returnType> <name>(<paramType>, <paramType>);
```
- if you have globals that will be use only in the file their are in, use `static` keyword
```
    static int g_myNumber;
```

## documentations

- all hpp files will be documented in the .md file with the same name in the same treeview buty in the doc folder:
```
|-include
|       |_tokenizer
|                 |-part1.hpp
|                 |_part2.hpp
|-src
|   |_tokenizer
|             |-part1.cpp
|             |_part2.cpp
|_docs
     |_tokenizer
               |-part1.md
               |_part2.md
```
- the documentations of the classes, functions, structure, ... will have simple examples and good description of the functions, parameters, and return value
- the documentations of global variables need complete description
