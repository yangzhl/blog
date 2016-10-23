###常见问题
Tex, LaTex, pdflatex, xelatex, xetex等的区别和关系
```
TeX：一种宏语言。
Plain Tex： Tex中的一个最基本的宏集合与TeX的基础语言构成的一种格式。
LaTex： Tex中的一个宏集合，构成一种与 Plain TeX 不一样的格式。

Tex程序：把Tex语言转换为排版的程序，也叫Tex。为区别，称这个 TeX 程序叫Knuth TeX。

tex命令：Tex程序中的编译命令。tex命令默认用Plain TeX格式进行排版。也就是说tex命令后面默认跟的tex文件应该是用Plain Tex格式写的。

latex命令：tex命令加上某一个选项使用，就会用LaTeX 格式进行排版，也就是说此时后面跟的tex文件应该是用LaTex格式写的。为方便，就把tex 命令与对应编译选项合成为一个命令，叫latex命令。

ε-TeX 程序：Knuth TeX程序的一个扩展，也是一个程序，一般写成 eTeX。增加了少量的几个命令，但一般来说是与Knuth TeX程序没有太多区别的。

实现：在文中的意思就是指“程序”的意思。如文中：eTeX 程序和 Knuth TeX 都是TeX语言的一个实现（也就是说，eTeX 程序和 Knuth TeX 都是把TeX语言转换为排版的程序。程序作用于tex文本文件，把tex文件编译成dvi文件）。

pdfTeX程序：Tex语言的又一个实现，也就是把Tex语言转换为排版的又一个程序。它会把 TeX 语言写的代码直接编译成 PDF 文件。

pdftex命令：pdfTex程序中的命令，用来编译用Plain TeX格式写的tex文件。

pdflatex命令：pdfTex程序中的命令，用来编译用LaTeX格式写的tex文件。

XeTeX程序：TeX语言的新的实现，即把Tex语言转换为排版的一个新程序。支持Unicode 编码和直接访问操作系统字体。

xetex命令：XeTeX程序中的命令，用来编译用Plain TeX格式写的tex文件。

xelatex命令：XeTeX程序中的命令，用来编译用LaTeX格式写的tex文件。

其中“实现”这个概念比较别扭，不知是不是计算机中的概念，反正非计算机专业的人读起来不知道“实现”是什么意思，不知道“TeX语言的一个实现”是什么意思。如果把“TeX语言的一个实现”写成是把TeX语言转换为排版的一个程序，这个程序作用于tex文本文件，把tex文件编译成某些文件，如dvi，pdf文件（比如pdfTex程序把tex文件编译成pdf文件）。那就好理解多了。
```
总的来说Tex是一种宏语言，而又存在两种编码格式：LaTeX和Plain Tex.
因此衍生出了好多的程序分别用来编译这两种不同的格式，较好的区分方式为，以*LaTeX命名的一般用来编译LaTeX格式文件是没有问题的，但是如果用*tex程序来编译可能出错，这种是用来编译plain tex的格式


 #####用LaTeX生成的东西无法用PDF直接查看的原因
 要查看console（控制台）的编译信息，在最后会生成关于最后的output的信息，会告诉你是生成dvi还是生成pdf，pdflatex直接生成pdf格式的，LaTeX生成DVI格式的文件，点击dvi pdf 可以把生成的dvi转化为pdf
 
####winedt按下enter键无法插入新的行？
解决办法，按下insert 键，就是写着**Ins(Num Lk)**



