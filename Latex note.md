# 第一章 latex基本概念
## 1.1 概述
---
* 具有专业的排版输出能力，产生的文档看上去就像“印刷品”一样。
* 具有方便而强大的数学公式排版能力，无出其右者。
* 绝大多数时候，用户只需专注于一些组织文档结构的基础命令，无需（或很少）操心文档的版面设计。
* 很容易生成复杂的专业排版元素，如脚注、交叉引用、参考文献、目录等。
* 强大的可扩展性。世界各地的人开发了数以千计的LATEX 宏包用于补充和扩展LATEX 的功能。
*　能够促使用户写出结构良好的文档——而这也是LATEX 存在的初衷。
* LATEX 和TEX 及相关软件是跨平台、免费、开源的。无论用户使用的是Windows，macOS（OS X），GNU/Linux 还是FreeBSD 等操作系统，都能轻松获得和使用这一强大的排版工具，并且获得稳定的输出。
---

安装:
`texlive`:
[官网](https://tug.org/texlive/)
编辑器:
[tex studio](https://www.texstudio.org/)
在线:[overleaf](https://www.overleaf.com/)
vscode/vim

---
## 1.2 第一次使用
下面为最短的latex源代码示例
```tex
\documentclass{article}
\begin{document}
``Hello world!'' 
\end{document}
```
---

## 1.3 latex 命令和代码结构
LATEX 中命令以反斜线`\ `开头，为以下两种形式之一：
• 反斜线和后面的一串字母，如`\LaTeX` 。它们以任意非字母符号（空格、数字、标点等）为界限。
• 反斜线和后面的单个非字母符号，如`\$` 。
---
## 1.4 宏包和文档类
### 文档类
```
\documentclass[⟨options⟩]{⟨class-name⟩}
```
options:
*  `10pt`, `11pt`, `12pt `指定文档的`基本字号`。默认为`10pt`。
* `a4paper`, `letterpaper`, … 指定`纸张大小`，默认为`美式信纸letterpaper`。可指定选项还包括a5paper，b5paper，executivepaper 和legalpaper。
* `twoside`, `oneside` 指定`单面/双面排版`。
	双面排版时，奇偶页的页眉页脚、页边距不同。
	article和report 默认为oneside，
	book 默认为twoside。
* `onecolumn`, `twocolumn `指定单栏/双栏排版。
	默认为`onecolumn`。
* `openright`, `openany` 指定新的一章\chapter 是在奇数页（右侧）开始，还是直接紧跟着上一页开始。
	report 默认为openany，book 默认为openright。对article 无效。
*  `landscape` 指定横向排版。默认为纵向。
* `titlepage` ` notitlepage` 指定标题命令 `\maketitle `是否生成单独的标题页。article 默认为notitlepage，report 和book 默认为titlepage。
* `fleqn `令行间公式左对齐。默认为居中对齐。
* `leqno `将公式编号放在左边。默认为右边。
* `draft`/ `final `指定草稿/终稿模式。草稿模式下，断行不良（溢出）的地方会在行尾添加一个黑色方块；插图、超链接等功能也会受这一组选项影响，默认为final
### 宏包
```
\usepackage[⟨options⟩]{⟨package-name⟩}
```
```
% 一次性调用三个排版表格常用的宏包
\usepackage{tabularx, makecell, multirow}
```

## 1.5 用到的文件一览
![[Pasted image 20230712201645.png]]

---
## 1.6 文件的组织方式
编写长篇文档时,将每章的内容单独写在一个文件夹
在源代码中插入文件
```
\include{⟨filename⟩}%不带tex扩展名

\include{chapters/file} % 相对路径

\include{/home/Bob/file} % *nix（包含Linux、macOS）绝对路径
\include{D:/file} % Windows 绝对路径，用正斜线
```
---
## 1.7 latex和tex相关概念
**`引擎`** :全称为排版引擎，是编译源代码并生成文档的程序，如pdfTEX、XƎTEX 等。有时也称为编译器。
**`格式`**:是定义了一组命令的代码集。LATEX 就是最广泛应用的一个格式，高德纳本人还编写了一个简单的plain TEX 格式，没有定义诸如`\documentclass` 和`\section`等等命令。
**`编译命令`**:是实际调用的、结合了引擎和格式的命令。如xelatex 命令是结合XƎTEX 引擎和LATEX 格式的一个编译命令
![[Pasted image 20230712202012.png]]

| 特性/引擎 | TeX | pdfTeX | XeTeX | LuaTeX |
|:---|:---:|:---:|:---:|:---:|
| Unicode支持 | 不支持 | 不支持 | 支持 | 支持 |
| 现代字体 (TrueType, OpenType) 支持 | 不支持 | 不支持 | 支持 | 支持 |
| 直接生成PDF | 不支持 | 支持 | 支持 (通过xdvipdfmx) | 支持 |
| 微型调整（间距等） | 不支持 | 支持 | 有限的支持 | 支持 |
| 内建脚本语言 | 不支持 | 不支持 | 不支持 | 支持 (Lua) |
| 多语言排版 | 不支持 | 不支持 | 支持 | 支持 |

下面是对各引擎适用场合的总结：

- **TeX**：适合于基本的文本和数学排版，尤其是如果只使用拉丁字符和无需特别高级特性的情况下。
- **pdfTeX**：在TeX的基础上添加了直接生成PDF以及一些微调的特性，适合大部分的日常文档制作。
- **XeTeX**：具有广泛的Unicode和现代字体支持，适合需要多语言或者特别字体支持的复杂排版任务。
- **LuaTeX**：集成了Lua脚本语言，使得用户可以进行高度的自定义，适合对文档排版有特别要求或者需要高级自定义的用户。

# 第二章 用latex排版文字
## 2.1 语言文字和编码
* AS2
* UTF-8

## 2.2 排版中文
ctex宏包
```tex
\usepackage{ctex}
```

`\documentclass{ctexart}
源码保存为UTF-8编码,使用xelatex或lualatex编译
## 2.3 latex中的字符
连续两个换行是为一个空行
`\par`分段
`%`  注释
特殊字符使用`\`转义
## 2.4 断行和断页
手动断行 `\newline`
手动断页`\new page ` `\clear page`
判断`\linebreak` `page break`
# 第三章 文档元素
## 3.1 章节和目录
划分章节:
```tex
\chapter{title}   \section{title}    \subsection{title}
\subsubsection{title}    \paragraph{title}  \subparagraph{title}
```
• article 文档类带编号的层级为`\section ` ` \subsection `  `\subsubsection` 三级；
• report / book 文档类带编号的层级为`\chapter` ` ` `\section ` ` \subsection `三级。
目录
```tex
\table of contents`
```
这个命令会生成单独的一章（report / book）或一节（article），标题默认为“Contents”
```tex
\addcontentsline{toc}{⟨level⟩}{⟨title⟩}
```
将正文和附录分开 `\appendix`


## 3.2 标题页
```tex
\title{name}     \author{name}    %必须
\date{date}%可选
```
## 3.3 交叉应用
`\lable{label-name}`
`\ref{label-name}`
`\pageref{label-name}`
![[Pasted image 20230714144147.png]]

## 3.4 脚注和编注
`\footnote{这是脚注}`
``` tex
\footnotemark
\footnotetext{脚注内容}
```
边栏
``` 
\marginpar{编注} 
```

## 3.5 特殊环境
### 3.5.1 列表
```tex
\begin{enumerate}
\item...
\end{enumerate}
```
```
\begin{itemize}
\item
...
\end{itemize}
```
关键字description
```tex
\begin{description}
\item[item title]
\end{description}
```
### 3.5.2 对齐环境
```tex
\begin{center}
...
\end{center}

\beginn{flushleft}
...
\begin{flushleft}

\begin{flushright}
...
\end{flushright}

```
or
```
\centering

\reggedright

\redgedleft

```
### 3.5.3 引用环境quote
```tex
\begin{quote}
...
\end{quote}
```
另外quatation:首行缩进
### 3.5.4 摘要环境 
abstract
### 3.5.5 代码环境
verbatim
```latex
\usepackage{listings}

\begin{lstlisting}[language=C++]
#include <iostream>

int main() {
    std::cout << "Hello, World!";
    return 0;
}
\end{lstlisting}

```
参数设定
```tex
%全局设定列表参数
\lstset{language=Python, %设置语言为python,启用python的语法高亮
		basicstyle=\ttfamily\small,%设置代码的基本样式为打字机字体,大小为小
		showstringspaces=false,
	 %是否在字符串中显示空格。设置为 `false`，表示不显示字符串中的空格。
		numbers=left, 
		numberstyle=\tiny, 
		breaklines=true, 
		frame=single}
```
简短代码或关键字
`\verb|...`

## 3.6 表格
tabular环境
~~~tex
\begin{tabular}{|c|c|c|}
\hline
列1 & 列2 & 列3 \\
\hline
1 & 2 & 3 \\
4 & 5 & 6 \\
\hline
\end{tabular}
~~~
使用longtable包允许创建跨页的长表格:
```tex
\usepackage{longtable}

\begin{longtable}{|c|c|}
\hline
1 & 2 \\ 
3 & 4 \\ 
% ... more rows ...
\hline
\end{longtable}

```
## 3.7 图片
调用graphicx宏包
`\includegraphics{filername}`
[[插入多幅图形]]

## 3.8 盒子
水平盒子
 ```tex
 \mbox{}
\makebox [width][align]{...}
```
![[Pasted image 20230714151444.png]]
带框的水平盒子
```
\fbox{...}
\framebox[width][align]{...}
```
![[Pasted image 20230714151412.png]]

垂直盒子
```tex
\parbox{width}{...}
or
\begin{minipage}
\end{minipage}
```
![[Pasted image 20230714151344.png]]

标尺盒子
`\rule{width}{height}`
![[Pasted image 20230714151251.png]]

## 3.9 浮动体
两类浮动体环境table and figure
```
\begin{table}
...
\end{table}
```
![[Pasted image 20230714151512.png]]

加标题,并且自动编号
`\caption{...}`
各自生成单独的章节
```tex
\listoftables
\listoffigures
```
# 第四章 排版数学公式
```
\usepackage{amsmath}
```
## 4.1 数学公式排版
 1. **行内公式** 
eg:    `$a^2+b^2=c^2$`
 $a^2+b^2=c^2$
  2. **行间公式** 
  环境:euqtion,euqtion*,displaymath
```
\begin{eqution}
 `a^2+b^2=c^2`
\end{eqution}```
```
## 4.2 数学模式

1. 输入的空格被忽略.需要人为引入间距时,可输入`\quad`等命令
2. **不允许有空格**
 3. 所有字母被当作变量处理,如要输入正题文本使用`\text
## 4.3 数学符号
希腊字母就是英文名称
`\alpha` α     `\beta` β  
省略号 `\dots \cdots`  $\dots$
```
\frac{分子}{分母}    %分式
\sqrt{...}   %一般分式
\sqrt[n]{...}   %n次方根
\binom{}{}     %二项式解构
```
![[Pasted image 20230714151728.png]]
巨算符包括积分号`\int`$\int$和求和号`\sum`$\sum$
箭头:
$$
\leftarrow \Leftarrow \leftrightarrow
$$×`\times`
÷`\div`
$$\nabla \quad \partial $$

## 4.4 多行公式
```
\begin{align}
a=&b+c\\
=&d+e
\end{align}   %自动编号 可用命令\nolag
```
![[Pasted image 20230714151827.png]]
不需要按等号对齐时
```
\begin{gather}
a=b+c\\
d=e+f+g\\
h+i=j+k\notag\\
l+m=n
\end{gather}
```
![[Pasted image 20230714151900.png]]
## 4.5 数组和矩阵
array环境
分类函数:
cases环境

## 4.6 定理和证明
```latex
\newtheorem{definition}{定义}[section]
\newtheorem{theorem}{定理}[section]
\newtheorem{lemma}[theorem]{引理}
\newtheorem{corollary}[theorem]{推论}
```
**证明环境**:```
```tex
\usepackage{amsthm}
\begin{proof}
\end{prove}
```
## 符号表
![[Pasted image 20230713095213.png]]
![[Pasted image 20230713095244.png]]
![[Pasted image 20230713095316.png]]
# 第五章 排版样式设定
修改排版样式

## 5.1 字体和字号
![[Pasted image 20230713095425.png]]
![[Pasted image 20230713095516.png]]
![[Pasted image 20230713095610.png]]
#  第六章 特色工具和功能
## 参考文献和bibtex工具
在正文中引入参考文献
```
\cite{}
```
参考文献本身内容
```
\begin{thebibliography}
\bibitem{}
\end{thebibliography}
```
**bibtex数据库**
BIBTEX 是最为流行的参考文献数据组织格式之一。它的出现让我们摆脱手写参考文献条目的麻烦。我们还可以通过参考文献样式的支持，让同一份 BIBTEX 数据库生成不同样式的参考文献列表。
BIBTEX 数据库以 .bib 作为扩展名，其内容是若干个文献条目，每个条目的格式为：
```
@<type>{citation,
	<key1>=<value1>
	<key2>=<value2>
}
```
eg:    
```bib
@article{Alice13,
title = {Demostration of bibliography items},
author = {Alice Axford and Bob Birkin and Charlie Copper and Danny Dannford},
year = {2013},
month = {Mar},
journal = {Journal of \TeX perts},
volume = {36},
number = {7},
pages = {114-120}}
```
现在利用bibtex数据库生成参考文献和引用:
1. 准备一份bibtex文件,假设文件名为books.bib,和latex源代码位于同一目录
2. 在正文应用参考文献
3.` \bibliography`
## 使用超链接
```tex
\usepackage{hyperref}
...
\href{www.example.com}{这是一个超链接}
...
\url{...}
```

# 第七章 绘图功能
tikz:坐标和路径
```
\tikz ...
\begin{tikzpicture}
...
\end{tikzpicture}


\coordinate(s) at (0,1)
\draw (s) --(1,1)
```
绘图命令和参数
```
\draw ...
\fill ...
\filldraw ..
```
`color/draw/fill color `
`thick= thin/semithick/length`
`solid/dashed/datted/dash dot/dash dot dot`
`round corners = `radius`/sharp corners `路徑轉向出繪製為圆角/直角
`scale/xshift/yshift/xslant/rotate` 设定图形的缩放,位移和旋转文字结点
```
\node (name at (coordinate) {text});
```
```
\begin{tikzpicture}\
\node (A) at (0,0) {A};
\node (B) at (1,0) {B}
\draw (A)--(B)--(C)
\end {tikzpicture}
```
结点形状:shape = ractangle/circle
文字颜色:text = `color`
文字字体:node font = `font command`  
向外或向内额外距离:inner sep = `length`/outer sep = `length`
结点最小大小/高度/宽度: mininum size/height/width = `length`
[[彩色盒子]]


# 第八章  自定义latex 命令和功能
## 8.1 自定义命令和环境
定义新命令
```
\newcommand{\name} {definitions}
```
定义环境:
```
\newenvironment {name} {before} {after}
```
## 8.2 编写自己的宏包和文档类
编写简单宏包
```
\ProxidesPackage {package name}
```
在宏包中调用其他宏包
```
\RequirePackage {package name}
```
 编写自己的文档类     以`.cls`作为扩展名
 ```
\ProvideClass {class name}
\LoadClass {package name}
```
## 8.3 计数器
定义一个计数器
```
\newcounter{countr name}
```
修改计数器的数值
```
\setcountr {name} {number} 
\addcounter {name} {number}
\stepcounter {counter name}
```
## 宏包介绍
[[常用宏包介绍]]
