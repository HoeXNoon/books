#### 一。python 之所以功能强大，是因为它丰富的工具集和系统语言
```
（1）动态类型：
    Python在运行过程中随时跟踪对象的种类，不需要代码中关于复杂的类型和大小的声明，事实上Python中没有类型和变量声明这回事，因为Python代码不是约束数据的类型，它往往自动的应用了一种广义上的对象。
    Python强大我认为还有一点就是它的自省，自省是指这种能力：检查某些事物以确定它是什么、它知道什么以及它能做什么。自省向程序员提供了极大的灵活性和控制力。简单来说就是运行时能够获得对象的类型。
（2）自动内存管理
    Python自动进行对象分配，当对象不再使用时，将自动撤销对象（'垃圾回收'），
    当需要时自动扩展或收缩，Python能够代替你进行底层的内存管理。
（3）大型程序的支持
    Python 包含了模块、类和异常等工具，这些工具允许你把系统组织为组件，使用OOP重用并定制代码，并以一种优雅的方式处理事件和错误
（4）内置对象类型
    Python提供了常用的数据结构作为语言的基本组成部分。例如：列表（list）、字典（dictionary）、字符串（string）。我们将会看到，它们灵活并易于使用，例如，内置对象可以根据需求扩展或收缩，可以任意地组织复杂的信息等。
（5）内置工具
    为了对以上对象类型进行处理，Python自带了许多强大的标准操作，包括合并（concatenation）、分片（slice）、排序（sort）和映射（mapping）等
（6）库工具
    Python预置了许多预编码的库工具，从正则表达式匹配到网络都支持
（7）第三方工具
    数据处理的：http://www.sohu.com/a/232660207_464033
    常用的第三方库： http://www.cnblogs.com/jiangchunsheng/p/9275881.html

```
#### 二。Python解释器简介
```
当我们编写Python代码时，我们得到的是一个包含Python代码的以.py为扩展名的文本文件。要运行代码，就需要Python解释器去执行.py文件。
由于整个Python语言从规范到解释器都是开源的，所以理论上，只要水平够高，任何人都可以编写Python解释器来执行Python代码（当然难度很大）。事实上，确实存在多种Python解释器。

CPython
当我们从Python官方网站下载并安装好Python 2.7后，我们就直接获得了一个官方版本的解释器：CPython。这个解释器是用C语言开发的，所以叫CPython。在命令行下运行python就是启动CPython解释器。
CPython是使用最广的Python解释器。教程的所有代码也都在CPython下执行。

IPython
IPython是基于CPython之上的一个交互式解释器，也就是说，IPython只是在交互方式上有所增强，但是执行Python代码的功能和CPython是完全一样的。好比很多国产浏览器虽然外观不同，但内核其实都是调用了IE。

CPython用>>>作为提示符，而IPython用In [序号]:作为提示符。

PyPy
PyPy是另一个Python解释器，它的目标是执行速度。PyPy采用JIT技术，对Python代码进行动态编译（注意不是解释），所以可以显著提高Python代码的执行速度。
绝大部分Python代码都可以在PyPy下运行，但是PyPy和CPython有一些是不同的，这就导致相同的Python代码在两种解释器下执行可能会有不同的结果。如果你的代码要放到PyPy下执行，就需要了解PyPy和CPython的不同点。

Jython
Jython是运行在Java平台上的Python解释器，可以直接把Python代码编译成Java字节码执行。

IronPython
IronPython和Jython类似，只不过IronPython是运行在微软.Net平台上的Python解释器，可以直接把Python代码编译成.Net的字节码。

小结
Python的解释器很多，但使用最广泛的还是CPython。如果要和Java或.Net平台交互，最好的办法不是用Jython或IronPython，而是通过网络调用来交互，确保各程序之间的独立性。
本教程的所有代码只确保在CPython 2.7版本下运行。请务必在本地安装CPython（也就是从Python官方网站下载的安装程序）。
此外，教程还内嵌一个IPython的Web版本，用来在浏览器内练习执行一些Python代码。要注意两者功能一样，输入的代码一样，但是提示符有所不同。另外，不是所有代码都能在Web版本的IPython中执行，出于安全原因，很多操作（比如文件操作）是受限的，所以有些代码必须在本地环境执行代码。

```
##### 字节码编译 ".pyc"就是编译过来的".py"源代码
#### 三。Python虚拟机（PVM）
```
PVM就是迭代运行字节码指令的一个大循环，一个接一个地完成操作，它是实际运行脚本的组件，也就是所谓Python解释器的最后一步
```
#### 经常出现的困惑与解答
```http
1. 什么是Python解释器？
  Python解释器是运行Python程序的程序。
2. 什么是源代码？
  源代码是为程序所写的语句：它包括了文本文件（通常以.py为后缀名）的文本。
3. 什么是字节码？
  字节码是Python将程序编译后所得到的底层形式。Python自动将字节码保存到后缀为.pyc的文件中。
4.什么是PVM？
  PVM是Python虚拟机，它是Python运行时引擎解释编译得到的代码。
5.请列出两个Python标准执行模块的变体的名字。
  Psyco（实时编译器，加快执行速度）、Shedskin（C++转换器）以及forzen biinaries（冻结二进制文件） 是执行模块的所有变体。
6. CPython、Jython以及IronPython有什么不同？
  CPython是Python语言的标准实现。Jython和IronPython分别是Python程序的Java和.net的实现；它们都是Python的编译器的替代实现

```


