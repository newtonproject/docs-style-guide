# Copyright & File Header #
```

/**
  * Job Database abstract layer implementation
  * @version $Rev$
  * @author xiawu@lubangame.com
  * @copyright (c) 2016 Beijing ShenJiangHuDong Technology Co., Ltd. All rights reserved.
  */

```

# Annotation language #
The comment language is in English.

# Java #
## Source file base ##
### Filename ###

The source filename consists of the class name of the top-level class it contains (case sensitive), plus the .java suffix. (except the package-info.java file).
 
### File encoding: UTF-8 ###
Source files are encoded in UTF-8.
 
### Source file structure ###
The source files are composed of the following parts in order:

a. License or copyright statement information. (if required)
b. package declaration statement.
c. import statement.
d. class class declaration (each source file can only have a single top class).

There should be only one blank line between each section as an interval.
 
### License or copyright declaration information ####

If you need to declare license or copyright information, you should declare it at the beginning of the file.

### Package statement ###

The line declared by the package has no limit on the length of the line. The single line length limit (detailed in Section 4.4, 80 or 100) does not apply to package declarations.
 
### Import statement ###
 
#### Do not use wildcard import ####

Wildcard imports should not be used, regardless of whether they are static imports.
 
#### No line length limit ####
 
The line of the import statement has no limit on the length of the line. The single line length limit (detailed in Section 4.4, 80 or 100) does not apply to the line of the import statement.
 
#### Preface and blank line####
 
The import statement should be divided into groups, each separated by a single line of blank lines. The order of grouping is as follows:
 
a. All static imports are grouped together.
b. The import of the com.google package is grouped together.
c. A reference to the third-party package used. Each top-level third-party package is grouped together. Third-party packages are sorted by ASCII code. For example: android, com, junit, org, sun
d. Java packages are grouped together.
e. Javax packages are grouped together.
 
Empty lines are not separated between import statements in the same group. The import statements in the same group are sorted by ASCII code.
 
## Class declaration##
 
### Only declare a single top class ###
 
There can only be one top-level class in each source file. Except for the package-info.java file.
 
### Class member order ###
 
The order of class members has a great impact on the legibility of the code, but there is no uniform and correct standard. Different classes may have different sorting methods.
 
The important thing is that each class is sorted according to a certain logical law. When asked in time, I can explain why this sorts. For example, the newly added member method is not simply placed at the end of the class code, sorted by date is not logically sorted.
 
#### Overloading method: should not be separated ####
 
When a class has multiple constructors, or multiple member methods of the same name, these functions should be written together and should not be separated by other members.
 
 
## Format##
 
Terminology: A block-like construct refers to the implementation part of a class, member function, and constructor (the middle part of curly braces). Note that array initialization is described in Section 4.8.3.1, and all array initialization can be thought of as a block structure (not mandatory).
 
### Curly braces ###
 
#### Braces are used where needed ####
 
Braces are generally used in statements such as if, else, for, do, and while. It needs to be used even when its implementation is empty or has only one sentence.
 
#### Non-empty statement block uses K&R style ####
 
For non-empty statement blocks, curly braces follow the K&R style:
 
a. no line breaks before the left parenthesis.
b. after the left parenthesis, wrap.
c. Wrap the line before the closing parenthesis.
d. If the closing parenthesis ends a statement block or function body, constructor body, or named class body, you need to wrap. For example, when the right parenthesis is followed by an else or a comma, it should not be wrapped.
 
#### Empty statement block: Make the code more concise ####
 
An empty block of statements, which can be followed by a closing brace directly after the opening brace, without spaces or line breaks. But when a block of statements consisting of several statement blocks is combined, you need to wrap. (Example: if/else-if/else try/catch/finally).
 
example:

```

Void doNothing () {}

```
 
### Indentation of statement block: 4 spaces ###
 
Whenever a new block of statements is generated, the indentation adds two spaces. When the block ends, the indentation returns to the previous level of indentation. Indentation requirements apply to both code and comments in the entire statement block. (For examples, see the example in Section 4.1.2 above).
 
### One line at most has only one code ###
 
A line break is required at the end of each code.
 
### Line length limit: 80 or 100 ###
 
Different items can choose to use 80 characters or 100 characters as a limit. In addition to the following special cases, other code content is subject to this length limit. This will be explained in detail in Section 4.5.
 
Exceptions:
a. according to the line length limit, can not be achieved (for example: the long URL address in javadoc, or a long JSNI method reference);
b. package and import statements are not limited by length.
c. The command line command line in the comment will be copied directly to the shell for execution.
 
###Long line break###
 
Terminology: When a line of code is legal according to other specifications, just to avoid line breaks beyond the line length limit, it is called long line break.
 
Long line breaks, there is no comprehensive, definitive specification for all scenarios. But in many of the same situations, we often use some effective method of breaking lines.
 
Note: Encapsulating long lines as functions, or using local variables, can also solve some cases where the line length limit is exceeded. It is not necessary to break.
 
#### Where is the line broken ####
 
The main principle of line breaks is to choose to break lines at a higher level of grammatical logic. Some other principles are as follows:
a. When a non-assignment statement breaks a line, it breaks before the operator symbol. (This is different from other specifications such as Google's C++ specification and JavaScrip specification).
b. When an assignment operation is broken, it is usually broken after the assignment symbol. But you can also break before.
c. When the calling function or constructor needs to break the line, the left parenthesis connected to the function name is on one line. That is, the line is broken after the left parenthesis.
d. When the comma is broken, the previous statement separated from the comma is broken. That is, after the comma breaks.
 
 
#### Indentation of broken lines: at least 4 characters ####
 
After the line breaks, the line after the first line, we call the continuation line. Each continuation line is at least four characters indented on the first line.
In the case of multiple continuation lines after the original line, the indentation can be greater than 4 characters. If multiple continuation lines are broken by the same syntax element, they can use the same indentation.
 
### White space ###
 
#### Vertical space ####
 
Single line blank lines are used in the following situations:
a. class members need to be separated by blank lines: for example, member variables, constructors, member functions, inner classes, static initializers, instance initializers.
    Exception: Blank lines between member variables are not required. Generally, blank lines in the middle of multiple member variables are used to logically group member variables.
b. Inside the function, set a blank line as the interval according to the logic grouping requirements of the code.
c. Before the first member of the class, or after the last member ends, use a blank line interval. (optional)
d. The situation described in other parts of this document that requires a blank line. (eg the import statement in Section 3.3)
 
It is permissible to use multiple lines of blank lines in a single blank line, but it is not required or encouraged.
 
 
#### Horizontal space ####
 
In addition to grammar, other rules, word separation, comments, and javadoc, horizontal ASCII spaces only appear when:
 
a. All reserved keywords must be separated by spaces between the left parenthesis on the same line immediately after it. (eg if, for, catch)
b. All reserved keywords are separated from the right curly brace before it. (eg else, catch)
c. Spaces are required before the left brace. There are only two exceptions:

```

    @SomeAnnotation({a, b})
   String [][] x # {{ "foo" }};

```

d. All binary operators and the two sides of the ternary operator are separated by spaces.
After e, comma, colon, semicolon, and right parenthesis, spaces are required.
f. / / ​​Double slash when starting a line of comments. Both sides of the double slash should be separated by spaces. And you can use multiple spaces, but not mandatory.
g. When the variable is declared, the variable type and the variable name need to be separated by a space.
h. When initializing an array, the curly braces can be separated by spaces or not. (Example: new int[] {5, 6} and new int[] { 5, 6 } can be)
 
Note: This principle does not affect the spaces at the beginning or end of a line. Only for the separation between the internal characters of the line.
 
#### Horizontal alignment: Do not force requirements ####
 
Terminology: Horizontal alignment means that a symbol of the line is aligned up and down with a symbol of the previous line by adding multiple spaces.
 
This alignment is allowed, but it is not mandatory.
 
The following are examples of no horizontal alignment and horizontal alignment;

```

Private int x ; // this is fine
Private color color ; // this too
 
Private int x ; // permitted, but future edits
Private color color ; // may leave it unaligned
 
```

Note: Horizontal alignment increases the readability of the code, but adds to the difficulty of maintaining the code in the future. Considering that only one line of code needs to be changed during maintenance, the previous alignment does not need to be changed. In order to align, you are more likely to change a line of code, and you need to change several lines of code nearby, and these lines of code changes may cause some code changes to maintain alignment. That original change, we call it the "explosion radius." This kind of change, in the worst case, can lead to a lot of meaningless work, even in the best case, it will affect the version history information, slow down the speed of code review, and cause more merge code conflicts. .
 
 
### Group brackets: Suggested use ###
 
Non-essential grouping brackets can only be omitted if the writer and the code reviewer believe that you will not cause the code to understand the error without it, or if it does not make the code easier to understand. There is no reason to think that anyone reading the code can remember the priority of all java operators.
 
 
###Special structures ###
 
#### Enumeration Type ####
 
Each comma is followed by an enumeration variable and no line breaks are required.
Enum type, if there is no function and javadoc, the processing format can be processed according to array initialization.
 
Example:

```

Private enum Suit { CLUBS , HEARTS , SPADES , DIAMONDS }

```
 
An enumerated type is also a class, so other formatting requirements of the Class class also apply to enumerated types.
 
 
#### Variable Declaration ####
 
##### Declare a variable every time #####
 
Do not use a single declaration to declare multiple variables. For example, int a, b;
 
##### Declare when needed, complete initialization as soon as possible #####
 
Local variables should not be habitually declared at the beginning of a statement block, but should be declared as close as possible to where they were first used to reduce their use.
Local variables should be initialized when they are declared. If you cannot initialize at the time of declaration, you should complete the initialization as soon as possible.#### Array ####
 
##### Array initialization: can be similar to block code processing #####
 
The initialization of all arrays can be handled in the same format as the block code. For example, the following formats are allowed:
 
##### Can't declare an array like C style #####
 
Square brackets should be part of the variable type and should not be placed with the variable name. For example: it should be String [] args instead of String args[] .
 
#### switch statement ####
 
Terminology: The switch statement refers to one or more sets of statement blocks in the switch curly braces. Each set of statement blocks begins with one or more switch tags (such as case FOO: or default:).
 
##### Indentation #####
 
Like other statement blocks, the switch curly braces indent two characters.
After each switch tag, the new non-labeled line that follows is indented by two characters in the same way as the curly braces. At the end of the label, revert to the previous indentation, ending with curly braces.
 
##### Continue to execute comments down #####
 
In the switch statement, after the code corresponding to each tag is executed, it should end with a statement (for example: break, continue, return, or throw an exception). Otherwise, the comment should indicate that the code needs to continue to execute the next tag. Code. The comment description text can be used to indicate that the code needs to continue to execute (usually //fall through). This comment does not require commenting after the last tag. E.g:
 
 
##### default tag needs to be explicitly declared #####
 
In each switch statement, you need to explicitly declare the default tag. Need to display the statement even if there is no code.
 
 
#### Annotations ####
 
When Annotations is applied to a class, function, or constructor, it should be immediately after the javadoc. There is only one Annotations per line.
The line of Annotations is not limited by the length of the line, and there is no need to increase the indentation. E.g:
 
```

@Override
@Nullable
Public String getNameIfPresent () { ... }

```
 
Exceptions:
If there is only one Annotations and no parameters. It can be placed on the same line as the class or method name. E.g:

```

@Override public int hashCode () { ... }
 
```

When Annotations is applied to a member variable, it is also immediately after the javadoc. The difference is that multiple annotations can be placed on the same line. E.g:

```

@Partial @Mock DataLoader loader ;
 
```

There are no specific specifications for the use of Annotations for parameters or local variables.
 
 
####Note####
 
##### Statement block comment style #####
 
The indentation of the comment is the same as the code indentation it annotates. Comments can be made with /\* \*/ or with //. When using /\*\*/ for multi-line comments, each line should start with \* and \* should be aligned up and down.
E.g:
   
 
When multi-line comments, if you want the integrated development environment to automatically align comments, you should use /\*\*/, // generally not automatically aligned.
 
#### Symbols ####
 
Modifiers for multiple classes and member variables are sorted in the order in which they are described in the Java Language Specification. Specifically is:
 
Public protected private abstract static final transient volatile synchronized native strictfp
 
## Naming ##
 
### General specification for all named identifiers ###
 
The identifier should only use ASCII letters, numbers, and underscores, and the letters are case sensitive. Therefore all identifiers should match the regular expression \w+ .
In Google Style, the identifier does not require a special prefix or suffix, such as: name_ , mName , s_name , and kName .
 
### Different types of identifier specifications ###
 
#### Package names ####
 
The package names are all in lowercase letters, passed through. Underscores should not be used.
 
####Class names####
 
The naming of types, using uppercase and lowercase character spacing starting with uppercase letters (UpperCamelCase).
Class naming generally uses nouns or noun phrases. The naming of interfaces can sometimes also use adjectives or adjective phrases. The annotation does not have a fixed specification.
 
The name of the test class should start with the name of the class it tests, and add the end of Test at the end. For example: HashTest, HashIntegrationTest.
 
 
####Method names####
 
Method naming, using the case of uppercase and lowercase characters starting with a lowercase letter (lowerCamelCase).
Method naming generally uses verbs or verb phrases.
 
In JUnit's test method, you can use an underscore to distinguish the name of the test logic, often using the following structure: test <MethodUnderTest>_ <state> . For example: testPop_emptyStack.
Test methods can also be named in other ways.
 
 
#### Constant names ####
 
Constant naming, all using uppercase characters, and words and words are separated by underscores. (CONSTANCE_CASE).
 
A constant is a static member variable, but not all static member variables are constants. When choosing to name a variable using a constant naming convention, you need to know if the variable is a constant. For example, if the state of this variable can change, then this variable is almost certainly not a constant. Just variables that are not going to change are not enough to be a constant. The following are examples of constants and non-constants:
   
 
Constants are generally named using nouns or noun phrases.
 
#### Unusual member variable name ####
 
A very large number of member variables (both static and non-static) are named using lowerCamelCase.
Nouns or noun phrases are generally used.
 
#### Parameter names ####
 
Parameter naming is named by lowerCamelCase.
You should avoid using a character as a parameter naming method.
 
#### Local variable names ####
 
Local variables are named using lowerCamelCase. It can be used in a shorter and more relaxed way than other types of naming.
But even so, you should try to avoid naming with a single letter, except for temporary variables used in the loop body.
 
Even if the local variable is final and immutable, it cannot be considered a constant and should not be named using constant naming.
 
####Type names####
 
Type names are named in two ways:
 
a. A single uppercase letter, sometimes followed by a number. (for example, E, T, X, T2).
b. Like the general class name (see Section 5.2.2), and then the last capital letter. (for example, RequestT, FooBarT).
 
### Definition of CamelCase ###
 
Sometimes when some phrases are written as Camel cases, there are many ways to write them. For example, some abbreviations, or some combination words: IPv6 or iOS.
In order to unify the writing, Google style gives a way of writing almost as one.
 
a. Convert all characters to ASCII characters and remove the 'etc. For example, "Müller's algorithm" is converted to "Muellers algorithm".
b. Split the result of the previous conversion into one word. Divide from the space and from the rest of the punctuation.
    Note: Some words that are already Camel cases should also be split at this time. (e.g. AdWords is split into ad words). But words such as iOS, it is not a Camel case word, but a word that people use in practice, so there is no need to split.
c. After the above two parts, first convert all the letters to lowercase, and then convert the first letter of each word to uppercase.
d. Finally, all the words are joined together to form an identifier.
 
Note: The original case rules for words should be completely ignored. Here are some examples:
 
The \* sign indicates acceptable, but is not recommended.
 
Note that some words are in English and can be used with or without - using directly. For example, "nonempty" and "non-empty" are all possible. Therefore, the method name is either checkNonempty or checkNonEmpty.
 
##Programming practices##
 
 
### @override should use ###
 
@override annotations should be used as long as they are grammatical.
 
 
### Exception capture should not be ignored ###
 
In general, catch exceptions should not be ignored, but need to be properly handled. For example, the error log is printed, or if it is considered that this exception does not occur, it should be re-thrown as an assertion exception.
 
If the exception of this catch does not require any processing, it should be explained by a comment. E.g:
 
 
 
Exception: In the test class, sometimes the specified exception is thrown for the method, such an exception can be ignored. But this exception usually needs to be named: expected. E.g:
 
 
 
### Static member access: should pass the class, not the object ###
 
When a static member is accessed, it should be accessed by the class name instead of the concrete instance object of the class.

 
### Do not use the Finalizers method ###
 
The finalize method of overloading Object is very, very rare.
 
# Android #

## Images ##

Named in English.

Global image: global_ + [function name] + suffix

Module picture: [module name]_ + [function name] + suffix

## Layout files ##

The global layout file begins with global_.

Module layout: [module name]_ + [type name]_ + [function name]_ + suffix (.xml)
