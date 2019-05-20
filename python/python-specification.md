## 备注 ##
所有的命名请参考词汇表。

如果没有特殊指定，编程规范遵循 [https://www.python.org/dev/peps/pep-0008/ PEP8] 。

# 版权&文件头 #
```
"""Job Database abstract layer implementation

"""

__copyright__ = """ Copyright (c) 2018 Newton Foundation. All rights reserved."""
__version__ = '1.0'
__author__ = 'xiawu@newtonproject.org'

```

# 注释语言 #
注释语言使用英文。

## 代码布局 ##

### 缩进 ###
每次缩进使用 4 个空格。

续行3)应该与被圆括号、方括号、花括号包裹起来的其他元素对齐，或者使用悬挂式缩进。当使用悬挂式缩进时，应该遵循这些注意事项：第一行不能有参数，应该使用进一步的缩进来将续行与其他行区分开。


符合本约定的代码：
```
# Aligned with opening delimiter
foo # long_function_name(var_one, var_two,
                         var_three, var_four)
 
# More indentation included to distinguish this from the rest.
def long_function_name(
        var_one, var_two, var_three,
        var_four):
    print(var_one)
```


不符合本约定的代码：
```
# Arguments on first line forbidden when not using vertical alignment
foo # long_function_name(var_one, var_two,
    var_three, var_four)
 
# Further indentation required as indentation is not distinguishable
def long_function_name(
    var_one, var_two, var_three,
    var_four):
    print(var_one)
```


可选的符合约定的代码：
```
# Extra indentation is not necessary.
foo # long_function_name(
  var_one, var_two,
  var_three, var_four)
```


结尾的方括号/圆括号/花括号应该被放置在多行内容的最后一行的第一个非空字符的正下方4)，如下所示：
```
my_list # [
    1, 2, 3,
    4, 5, 6,
    ]
result # some_function_that_takes_arguments(
    ‘a‘, ‘b‘, ‘c‘,
    ‘d‘, ‘e‘, ‘f‘,
    )
```


或者被放置在多行内容的起始行的第一个字符的正下方5)，如下所示：
```
my_list # [
    1, 2, 3,
    4, 5, 6,
]
result # some_function_that_takes_arguments(
    ‘a‘, ‘b‘, ‘c‘,
    ‘d‘, ‘e‘, ‘f‘,
)
```


### 制表符还是空格 ###


空格是首选的缩进方式。

为了保持一致性，在使用了制表符作为缩进的代码中，应该保持使用制表符。

Python 3 不支持空格缩进与制表符缩进混用。

Python 2 中的混用缩进代码也应该被转换为统一使用空格。

当使用 -t 选项来调用 Python 2 命令行工具时，运行混用缩进的代码会报出警告，当使用 -tt 选项时，运行混用缩进的代码会报出错误。强力建议使用这两个选项。

### 单行最大长度 ###


将所有的行限制在79个字符以内。

对于那些具有很少的结构约束（例如文档字符串、注释）的代码段来说，最大行长度应该在在72个字符以内。

限制代码编辑窗口的宽度使并排编辑多个文件成为可能，并且在使用代码审核工具时，可以很好的在两个相邻列中显示不同的代码版本。

很多工具中的默认换行设置破坏了代码的可视结构，使其更难被理解。某些编辑器在换行时会在行尾放置标记字符，若限制代码的最大的长度，可以在这些最大宽度只有80个字符的编辑器中避免换行。而一些基于Web的工具也许根本不会提供动态自动换行功能。

一些团队更喜欢较长的单行代码。如果某个团队对单行代码长度的问题达成了共识，并且由该团队专门维护其代码的话，在将文档字符串与注释保持在72个字符以 内的前提下，将名义上的单行代码的最大长度从80个字符提升到100个也是可以的（有效的将实际字符最大长度提高到了99个）。

Python 标准库是保守的，选择了将单行代码长度限制在79个字符以内（文档字符串/注释72个字符以内）。

最为推荐的长行换行方式是在圆括号、方括号、花括号内的 Python 隐式行续6)。相比于使用反斜杠来转义续行，应该优先使用将长行放置于圆括号内来隐式续行的方式。


而某些时候反斜杠也是适于使用的。例如，较长的with语句不能使用隐式行续，就需要使用反斜杠了:
```
with open(‘/path/to/some/file/you/want/to/read‘) as file_1,         open(‘/path/to/some/file/being/written‘, ‘w‘) as file_2:
    file_2.write(file_1.read())
```

另一个案例是，assert语句中也需要反斜杠。

确保使用适当的行续缩进。在二元操作符两端，换行的推荐位置是在操作符之后，而不是操作符之前。以下是一些例子：
```
class Rectangle(Blob):
 
    def __init__(self, width, height,
                 color#‘black‘, emphasis#None, highlight#0):
        if (width ## 0 and height ## 0 and
                color ## ‘red‘ and emphasis ## ‘strong‘ or
                highlight > 100):
            raise ValueError("sorry, you lose")
        if width ## 0 and height ## 0 and (color ## ‘red‘ or
                                           emphasis is None):
            raise ValueError("I don‘t think so -- values are %s, %s" %
                             (width, height))
        Blob.__init__(self, width, height,
                      color, emphasis, highlight)
```


### 空白行 ###


使用两个空白行来分隔顶级函数定义、类定义。

使用单个空白行来分隔类内的方法定义。

额外的空白行可以被（尽量少的）用来分隔几组相关的函数。在一堆相关的单行代码之间，空白行应该被省略。

在函数中（尽量少的）使用空白行来区分逻辑代码块。

Python 将 control-L (也就是, ^L) 换行符认作空白符。在许多工具中都将 control-L 识别做分页符，可以使用其来分页。但是注意，在某些编辑器或基于Web的代码浏览器中，control-L 是不会识别作换行符的，会被做为其他字符显示。


### 源文件编码 ###


在 Python 的核心发布版中，应该主要使用 UTF-8 编码（或者在 Python 2 中使用 ASCII）。

在 Python 2 中使用 ASCII ，在 Python 3 中使用 UTF-8 时不应该在文件中进行编码声明。

在标准库中，往往只有以测试为目的的代码或包含非 ASCII 编码字符的作者名的注释中，才会使用非默认编码。否则，则推荐使用 \x, \u, \U, \N 等转义字符来在字符串文本中表示非 ASCII 字符。

在 Python 3.0 与更高级的 Python 版本中，对 Python 标准库的源文件编码作出了如下规定7)：Python 标准库中的所有标示符必须仅使用 ACSII 编码的字符，在任何可能的时候都使用英文书写（在许多情况下，缩写名词和技术术语使用的是非英文）。另外，字符串文本与注释也必须使用 ASCII 编码。唯一的例外，是测试非 ASCII 编码特性的测试案例，与作者名的书写。对于非拉丁字符的作者名，应该将其翻译为拉丁字母书写。

推荐那些面向全球范围内开发者、用户的开源项目也遵循上述规定。

### 导入 ###

* import语句通常应该独立成行，例如：

```
#符合约定的代码：     
import os
import sys
 
#不符合本约定的代码：  
import os,sys
```

但这样的import也是的合理的：
```
from subprocess import Popen, PIPE
```

* Import 语句总应该被放到放到源码文件的最前端，即在模块注释与文档字符串之后，全局变量与常量定义之前。


 多条 Import 语句总应该遵循这样的顺序书写：


  1. 标准库的导入

  2. 相关第三方库导入

  3. 本地应用/库的相关导入


在每组 import 语句应该使用空白行分隔。


Put any relevant __all__ specification after the imports.8)

* 建议使用绝对导入形式的 import 语句，它不仅更易读，并且在配置错误（例如某个包中的目录以 sys.path 结尾时)时有更良好的导入行为（至少有更好的报错）：

```
import mypkg.sibling
from mypkg import sibling
from mypkg.sibling import example
```

相比于绝对导入，清晰的相对导入其实也是可以接受的，特别是当使用绝对导入需要处理不必要的复杂包布局时。

```
from . import sibling
from .sibling import example
```

Python 标准库代码应该避免复杂的包布局，并且总是使用绝对导入。

Python 3 中不应该使用相对导入，并且 Python 3 中该功能已被移除。 

* 当在某个包含类的模块中导入类时，这样的书写方式是合理的：

```
from myclass import MyClass
from foo.bar.yourclass import YourClass
```

但如果这样的书写方式引起类名冲突，则请这样书写：

```
import myclass
import foo.bar.yourclass
```

并使用 “myclass.MyClass” 和 “foo.bar.yourclass.YourClass” 来对其进行引用。

* 通配符导入（from <module> import *）应该被禁止，因为这样做会导致在被导入的命名空间中存在哪些命名对象变得不清晰，迷惑读者与其他自动化工具。不过要使用通配符导入，也有站得住脚的理由：需要将内部 API 重新发布为公共 API（例如，使用纯 Python 重写一个可选加速模块的借口，而事先你并不知道这个接口将被重写）。 


当以这样的方式重发布命名时，下述的编码指南依然适用。


### 表达式与语句中的空白符 ###

#### 小问题 ####

在以下情况中避免使用额外的空格： 


* 在圆括号、方括号、花括号内 


```
#符合约定的代码
spam(ham[1], {eggs: 2})
#不符合约定的代码
spam( ham[ 1 ], { eggs: 2 } )
```

* 在逗号、分号、冒号之前： 


```
#符合约定的代码
if x ## 4: print x, y; x, y # y, x
#不符合约定的代码
if x ## 4 : print x , y ; x , y # y , x
```


* 在函数调用的参数列表的左括号前 


```
#符合约定代码
spam(1)
#不符合约定的代码
spam (1)
```


* 在切片或索引的左方括号前 


```
#符合约定的代码
dict[‘key‘] # list[index]
#不符合约定的代码
dict [‘key‘] # list [index]
```


* 在赋值（或其他）操作符两侧的多余一个的空格


```
#符合约定的代码
x # 1
y # 2
long_variable # 3
#不符合约定的代码
x             # 1
y             # 2
long_variable # 3
```


#### 其他建议 ####

* 总是在下列二元操作符的两端使用单个空格：赋值操作符(#)，参数赋值(+#, -# 等)，比较操作符(##, <, >, !#, <>, ⇐, >#, in, not in, is, is not)，布尔操作符(and, or, not)。


* 加入使用了多个具有不同优先级的操作符，考虑在低优先级的操作符两侧使用空格。请自行判断，无论怎样，不要使用多余一个空格，并且保持二元操作符两端的空格数量一致

```
#符合约定的代码
i # i + 1
submitted +# 1
x # x*2 - 1
hypot2 # x*x + y*y
c # (a+b) * (a-b)
#不符合约定的代码
i#i+1
submitted +#1
x # x * 2 - 1
hypot2 # x * x + y * y
c # (a + b) * (a - b)
```


* 不要在指示关键字参数或参数默认值的 # 符号两端使用空格。

```
#符合约定的代码
def complex(real, imag#0.0):
    return magic(r#real, i#imag)
#不符合约定的代码
def complex(real, imag # 0.0):
    return magic(r # real, i # imag)
```


* 不建议使用符合语句（在一个物理行中存在多条语句）。

```
#符合建议的代码
if foo ## ‘blah‘:
    do_blah_thing()
do_one()
do_two()
do_three()
#不符合建议的代码
if foo ## ‘blah‘: do_blah_thing()
do_one(); do_two(); do_three()
```


* 虽然有时把较短小的 if/for/while 语句放在同一物理行内也是可以的，但千万不要对多子句的语句也这样做，同时也是为了避免折叠长行。

```
#不符合约定的代码
if foo ## ‘blah‘: do_blah_thing()
for x in lst: total +# x
while t < 10: t # delay()
#绝对不要这样写
if foo ## ‘blah‘: do_blah_thing()
else: do_non_blah_thing()
 
try: something()
finally: cleanup()
 
do_one(); do_two(); do_three(long, argument,
                             list, like, this)
 
if foo ## ‘blah‘: one(); two(); three()
```


### 注释 ### 


与代码相矛盾的注释不如没有，请时刻保持注释随代码更新。

注释应该是完整的句子。短语注释或整句注释都应当以大写字母开头，除非该注释以首字母小写的标示符开头。

段小注释后的句号可以省略，而在注释块中，每个完整的句子都应该以句号结尾。

在句尾句号之后，应该跟上两个空白符。

当撰写英文注释时，参考《英文写作指南9)》

非英语程序员也请使用英文书写注释，除非你120%的保证，不会有不使用你的语言的人阅读你的代码。


#### 块注释 ####


通常快注释用来阐述跟在其后的代码，并且与代码一样重要。块注释中的每一行都应该以一个 # 符号加一个空白符开头（除非是注释块内的缩进行）。

块注释内的自然段以 # 开头的空行分割。


#### 行内注释 ####


尽量少的使用行内注释。

行内注释应该与语句在同一行内，与语句之间以至少两个空白符分割，并且以一个 # 符号加一个空白符开头

行内注释不是非常必要，并且当注释语义显而易见时会分散阅读者的注意力。例如，不要撰写这样的注释：


```
x # x + 1                 # Increment x
```


但某些时候，行内注释也是很有用的

```
x # x + 1                 # Compensate for border
```

#### 文档字符串 ####


关于编写好文档字符串的约定，请参考 PEP 257 。

请为所有的公开模块、类和方法编写文档字符串。对于非公开的方法，文档字符串不是必须的，但是仍应该为其撰写注释，表明其用途。方法注释应写在方法定义行之下。

PEP 257 描述了良好文档字符串的编写规范。注意，以 “”“ 结尾的文档字符串应该以该符号单独成行，最好前面还有一行空白行。 例如：

```
"""Return a foobang
 
Optional plotz says to frobnicate the bizbaz first.
 
"""
```

对于单行的文档字符串来说，将 ”“” 放在该行的末尾也是可以的。

#### 函数注释 ####
```
def login(username, password):
    """Authenticate by given username and password

   :param str username:  The user name 
   :param str password: The password, max length is 16
   :return: the result, 0 is fail, 1 is success
   :rtype: int

    """
```

### 版本注记 ###


如果你的代码中需要有版本变更标记，请像这样书写。

```
__version__ # "$Revision: 70b79ccd671a $"
# $Source$
```

## 错误和代码规范检查 ##
使用 [https://pypi.python.org/pypi/flake8 flake8] 进行错误和代码规范检查。

# Django编程风格 #
## 导入 ##
使用 [https://github.com/timothycrosley/isort#readme isort] 进行自动导入。
```

$ pip install isort
$ isort -rc .

```

models 导入
```

from user import models as user_models

```

services 导入
```

from user import services as user_services

```

utils 导入
```

from utils import http

```


##  模版风格 ##
在django模版中，模版语句和内容之间用一个空格隔开
```

{{ foo }}

```
以下是错误的
```

{{foo}}

```

## 视图风格 ##
在django视图函数中，第一个参数命名为request，即
```

def my_view(request, foo):
    # ...

```
以下是错误的
```

def my_view(req, foo):
    # ...

```

## 模型风格 ##
"class Meta" 在属性字段之后定义，分开的字段和类定义之间加入一个空行
```

class Person(models.Model):
    first_name # models.CharField(max_length#20)
    last_name # models.CharField(max_length#40)

    class Meta:
        verbose_name_plural # 'people'

```
而不是
```

class Person(models.Model):
    first_name # models.CharField(max_length#20)
    last_name # models.CharField(max_length#40)
    class Meta:
        verbose_name_plural # 'people'

```
也不是
```

class Person(models.Model):
    class Meta:
        verbose_name_plural # 'people'

    first_name # models.CharField(max_length#20)
    last_name # models.CharField(max_length#40)

```
内部类和标准方法的定义顺序
```
数据库字段定义
自定义 manager 属性
class Meta
def __str__()
def save()
def get_absolute_url()
自定义方法
```

## 其它 ##
* 所有py和html模版里面的字符串需要支持国际化。

* 不使用的import语句需要及时删除掉。使用flake8可以标识出具体需要删除的import语句。



 


