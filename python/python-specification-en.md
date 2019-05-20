## 备注##
Please refer to the glossary for all naming.

If not specified, the programming specification follows [https://www.python.org/dev/peps/pep-0008/ PEP8].

# Copyright & File Head #
```
"""Job Database abstract layer implementation

"""

__copyright__ = """ Copyright (c) 2018 Newton Foundation. All rights reserved."""
__version__ = '1.0'
__author__ = 'xiawu@newtonproject.org'

```

# Annotation Language #
The comment language is in English.

##码布局##

### 缩进###
Use 4 spaces for each indentation.

Continued line 3) should be aligned with other elements wrapped in parentheses, square brackets, curly braces, or using hanging indentation. When using hanging indentation, these considerations should be followed: the first line cannot have parameters and further indentation should be used to distinguish the continuation line from the other lines.


Code that conforms to this convention:
```
# Aligned with opening delimiter
Foo # long_function_name(var_one, var_two,
                         Var_three, var_four)
 
# More indentation included to distinguish this from the rest.
Def long_function_name(
        Var_one, var_two, var_three,
        Var_four):
    Print(var_one)
```


Code that does not conform to this convention:
```
# Arguments on first line forbidden when not using vertical alignment
Foo # long_function_name(var_one, var_two,
    Var_three, var_four)
 
# Further indentation required as indentation is not distinguishable
Def long_function_name(
    Var_one, var_two, var_three,
    Var_four):
    Print(var_one)
```


Optional code that conforms to the convention:
```
# Extra indentation is not necessary.
Foo # long_function_name(
  Var_one, var_two,
  Var_three, var_four)
```


The closing square brackets/parentheses/brackets should be placed just below the first non-null character of the last line of the multiline content, as shown below:
```
My_list # [
    1, 2, 3,
    4, 5, 6,
    ]
Result # some_function_that_takes_arguments(
    ‘a‘, ‘b’, ‘c’,
    ‘d‘, ‘e‘, ‘f’,
    )
```


Or placed directly below the first character of the starting line of multiple lines of content 5), as shown below:
```
My_list # [
    1, 2, 3,
    4, 5, 6,
]
Result # some_function_that_takes_arguments(
    ‘a‘, ‘b’, ‘c’,
    ‘d‘, ‘e‘, ‘f’,
)
```


### Tab or space ###


Spaces are the preferred indentation.

For consistency, you should keep using tabs in code that uses tabs as indentation.

Python 3 does not support space indentation and tab indentation.Mixed indentation code in Python 2 should also be converted to uniform use of spaces.

When you call the Python 2 command-line tool with the -t option, the code that runs the mixed indentation will warn you that when you use the -tt option, the code that runs the mixed indent will report an error. It is strongly recommended to use both options.

### Single line maximum length ###


Limit all lines to within 79 characters.

For code segments with few structural constraints (such as document strings, comments), the maximum line length should be within 72 characters.

Limiting the width of the code editing window makes it possible to edit multiple files side by side, and when using the code review tool, it is good to display different code versions in two adjacent columns.

The default line break settings in many tools break the visual structure of the code, making it harder to understand. Some editors place marker characters at the end of the line when they wrap. If you limit the maximum length of the code, you can avoid line breaks in these editors with a maximum width of 80 characters. And some web-based tools may not provide dynamic word wrap at all.

Some teams prefer longer single-line code. If a team has reached a consensus on the length of a single line of code and the team maintains its code specifically, the maximum length of the nominal one-line code will be kept under the premise that the document string and comments are kept within 72 characters. It is also possible to increase from 80 characters to 100 (effectively increasing the maximum length of actual characters to 99).

The Python standard library is conservative and has chosen to limit the length of a single line of code to 79 characters (within 72 characters of the document string/comment).

The most recommended long line break is in Python implicit lines in parentheses, square brackets, and curly braces. 6). Instead of using backslashes to escape continuations, you should prefer to use long lines in parentheses to implicitly continue.


And sometimes the backslash is suitable for use. For example, a longer with statement cannot use an implicit line continuation, you need to use a backslash:
```
With open(‘/path/to/some/file/you/want/to/read‘) as file_1, open(‘/path/to/some/file/being/written‘, ‘w‘) as file_2:
    File_2.write(file_1.read())
```

Another case is that a backslash is also needed in the assert statement.

Be sure to use the appropriate line to retract. At both ends of the binary operator, the recommended position for the newline is after the operator, not before the operator. Here are some examples:
```
Class Rectangle(Blob):
 
    Def __init__(self, width, height,
                 Color#‘black‘, emphasis#None, highlight#0):
        If (width ## 0 and height ## 0 and
                Color ## ‘red‘ and emphasis ## ‘strong’ or
                Highlight > 100):
            Raise ValueError("sorry, you lose")
        If width ## 0 and height ## 0 and (color ## ‘red‘ or
                                           Approval is None):
            Raise ValueError("I don't think so -- values ​​are %s, %s" %
                             (width, height))
        Blob.__init__(self, width, height,
                      Color, emphasis, highlight)
```


### blank space ###


Use two blank lines to separate top-level function definitions and class definitions.

Use a single blank line to separate the method definitions within the class.

Additional blank lines can be used (as little as possible) to separate groups of related functions. Blank lines should be omitted between a bunch of related single line codes.

Use blank lines to distinguish logical code blocks in functions (as little as possible).

Python recognizes control-L (that is, ^L) newline characters as white space. Control-L is recognized as a page break in many tools and can be used to page. Note, however, that in some editors or web-based code browsers, control-L does not recognize line breaks and will be displayed as other characters.


### 源文件编码###


In the core release of Python, you should primarily use UTF-8 encoding (or ASCII in Python 2).

Use ASCII in Python 2 and use UTF-8 in Python 3 should not be encoded in the file.

In the standard library, non-default encodings are often used only for test-oriented code or comments containing author names that are not ASCII-encoded characters. Otherwise, it is recommended to use \x, \u, \U, \N and other escape characters to represent non-ASCII characters in the string literal.

In Python 3.0 and more advanced versions of Python, the source file encoding for the Python standard library is as follows: 7): All identifiers in the Python standard library must use only ACSII-encoded characters, and use English whenever possible. Writing (in many cases, abbreviations and technical terms are used in non-English). In addition, string text and comments must also be encoded in ASCII. The only exception is a test case that tests non-ASCII encoding features, written with the author's name. For author names of non-Latin characters, they should be translated into Latin letters.

It is recommended that open source projects for developers and users around the world follow these rules.

### 导入###

* The import statement should normally be in a separate line, for example:

```
#Compliance with the agreed code:
Import os
Import sys
 
# Code that does not conform to this convention:
Import os,sys
```

But such an import is also reasonable:
```
From subprocess import Popen, PIPE
```

* The Import statement should always be placed at the very front end of the source file, i.e. after the module comments and document strings, before the global variables and constants are defined.


 Multiple Import statements should always be written in this order:


  1. Import of standard library

  2. Related third party library import

  3. Related import of local application/library


Each set of import statements should be separated by a blank line.


Put any relevant __all__ specification after the imports.8)

* It is recommended to use an import statement in absolute import form, which is not only more readable, but also has better import behavior (at least better error) when configuration errors (such as when a directory in a package ends in sys.path):

```
Import mypkg.sibling
From mypkg import sibling
From mypkg.sibling import example
```

Clear relative import is actually acceptable compared to absolute import, especially when using absolute import to handle unnecessary complex package layouts.

```
From . import sibling
From .sibling import example
```

The Python standard library code should avoid complex package layouts and always use absolute imports.

Relative imports should not be used in Python 3, and this feature has been removed in Python 3.

* When importing a class in a module that contains a class, this way of writing is reasonable:

```
From myclass import MyClass
From foo.bar.yourclass import YourClass
```

But if this way of writing causes class name conflicts, please write like this:

```
Import myclass
Import foo.bar.yourclass
```

It is referenced using "myclass.MyClass" and "foo.bar.yourclass.YourClass".

* Wildcard import (from <module> import \*) should be disabled, as doing so will cause the named objects to become unclear in the imported namespace, confusing the reader and other automation tools. However, there are also reasons to use wildcard import: you need to republish the internal API as a public API (for example, use pure Python to rewrite an excuse for an optional acceleration module, and you don't know beforehand that this interface will be heavily write).

When renaming naming in this way, the coding guidelines described below still apply.

### Expressions and blanks in statements ###

#### Piece of cake ####

Avoid using extra spaces in the following situations:

* In parentheses, square brackets, curly brackets

```
#Compliance with the agreed code
Spam(ham[1], {eggs: 2})

#不符合协议的码
Spam( ham[ 1 ], { eggs: 2 } )
```

* Before the comma, semicolon, and colon:


```
#Compliance with the agreed code
If x ## 4: print x, y; x, y # y, x
#不符合协议的码
If x ## 4 : print x , y ; x , y # y , x
```


* before the left parenthesis of the argument list of the function call


```
#Compliance convention code
Spam(1)
#不符合协议的码
Spam (1)
```


* before the left square bracket of the slice or index


```
#Compliance with the agreed code
Dict[‘key‘] # list[index]
#不符合协议的码
Dict [‘key‘] # list [index]```


* Extra space on either side of the assignment (or other) operator


```
#Compliance with the agreed code
x # 1
y # 2
Long_variable # 3
#不符合协议的码
x # 1
y # 2
Long_variable # 3
```


#### other suggestion ####

* Always use a single space at both ends of the following binary operators: assignment operator (#), parameter assignment (+#, -#, etc.), comparison operators (##, <, >, !#, <> , ⇐, >#, in, not in, is, is not), Boolean operators (and, or, not).


* Joining multiple operators with different priorities, consider using spaces on both sides of low-priority operators. Please make your own judgment, no matter what, don't use more than one space, and keep the number of spaces at both ends of the binary operator consistent.

```
#Compliance with the agreed code
i # i + 1
Submitted +# 1
x # x*2 - 1
Hypot2 # x*x + y*y
c # (a+b) * (a-b)
#不符合协议的码
i#i+1
Submitted +#1
x # x * 2 - 1
Hypot2 # x * x + y * y
c # (a + b) * (a - b)
```


* Do not use spaces around the # symbol indicating the keyword argument or the default value of the argument.

```
#Compliance with the agreed code
Def complex(real, imag#0.0):
    Return magic(r#real, i#imag)
#不符合协议的码
Def complex(real, imag # 0.0):
    Return magic(r # real, i # imag)
```


* Compliance statements (multiple statements in one physical line) are not recommended.

```
#Compliance with suggested code
If foo ## ‘blah’:
    Do_blah_thing()
Do_one()
Do_two()
Do_three()
#不为推荐的码
If foo ## ‘blah‘: do_blah_thing()
Do_one(); do_two(); do_three()
```


* Although it's okay to put shorter if/for/while statements on the same physical line, don't do this for multi- clause statements, and also to avoid folding long lines.

```
#不符合协议的码
If foo ## ‘blah‘: do_blah_thing()
For x in lst: total +# x
While t < 10: t # delay()
#Absolutely don't write this
If foo ## ‘blah‘: do_blah_thing()
Else: do_non_blah_thing()
 
Try: something()
Finally: cleanup()
 
Do_one(); do_two(); do_three(long, argument,
                             List, like, this)
 
If foo ## ‘blah‘: one(); two(); three()
```


### 注###


Comments that contradict the code are better than none. Please keep the comments updated with the code.

The comment should be a complete sentence. Phrase comments or whole-sentence comments should begin with an uppercase letter unless the comment begins with an initial lowercase identifier.

The period after the paragraph comment can be omitted, and in the comment block, each complete sentence should end with a period.

After the period ending, you should follow the two whitespace characters.

When writing English notes, refer to the English Writing Guide 9

Non-English programmers are also required to write notes in English, unless you are 120% guaranteed, there will be no people who do not use your language to read your code.


####块注####


Usually a quick comment is used to describe the code that follows it and is as important as the code. Each line in the block comment should start with a # sign followed by a white space (unless it is a shrink in the comment block).

The natural segments within the block comment are separated by a blank line starting with #.


#### Inline Notes ####


Use inline comments as little as possible.

Inline comments should be in the same line as the statement, separated by at least two whitespace characters, and begin with a # sign plus a white space

Inline comments are not necessary and distract the reader when the annotation semantics are obvious. For example, don't write a comment like this:


```
x # x + 1 # Increment x
```


But in some cases, inline comments are also useful.

```
x # x + 1 # Compensate for border
```

#### Document String ####


Refer to PEP 257 for conventions on writing docstrings.

Please write a docstring for all public modules, classes, and methods. For non-public methods, the docstring is not required, but you should still write a comment for it to indicate its purpose. Method comments should be written below the method definition line.

PEP 257 describes the specification of writing good docstrings. Note that a document string ending in "" should be a separate line with that symbol, preferably with a blank line in front of it. For example:

```
"""Return a foobang
 
Optional plotz says to frobnicate the bizbaz first.
 
"""
```

For a single-line docstring, it is also possible to put "" at the end of the line.

#### Function Comment ####
```
Def login(username, password):
    """Authenticate by given username and password

   :param str username: The user name
   :param str password: The password, max length is 16
   :return: the result, 0 is fail, 1 is success
   :rtype: int

    """
```

###版注记###


If you need a version change tag in your code, write it like this.

```
__version__ # "$Revision: 70b79ccd671a $"
# $Source$
```

## Error and code specification check ##
Use [https://pypi.python.org/pypi/flake8 flake8] for error and code specification checks.

# Django编程风格#
## 导入##
Use [https://github.com/timothycrosley/isort#readme isort] for automatic import.
```

$ pip install isort
$ isort -rc .

```

Models import
```

From user import models as user_models

```

Services import
```

From user import services as user_services

```

Utils import
```

From utils import http

```


## 模板版###
In the django template, the template statement is separated from the content by a space.
```

{{ foo }}

```
The following is wrong
```

{{foo}}

```

## view style ##
In the django view function, the first parameter is named request, ie
```

Def my_view(request, foo):
    # ...

```
The following is wrong
```

Def my_view(req, foo):
    # ...

```

##模型风格##
"class Meta" is defined after the attribute field, adding a blank line between the separated field and the class definition
```

Class Person(models.Model):
    First_name # models.CharField(max_length#20)
    Last_name # models.CharField(max_length#40)

    Class Meta:
        Verbose_name_plural # 'people'

```
Instead of
```

Class Person(models.Model):
    First_name # models.CharField(max_length#20)
    Last_name # models.CharField(max_length#40)
    Class Meta:
        Verbose_name_plural # 'people'

```
Nor is it
```

Class Person(models.Model):
    Class Meta:
        Verbose_name_plural # 'people'

    First_name # models.CharField(max_length#20)
    Last_name # models.CharField(max_length#40)

```
The order in which internal classes and standard methods are defined
```
Database field definition
Custom manager property
Class Meta
Def __str__()
Def save()
Def get_absolute_url()
Custom method
```

##其他##
* All strings in py and html templates need to support internationalization.

* Import statements that are not used need to be deleted in time. Use flake8 to identify the specific import statement that needs to be deleted.
