# 第一章 latex基本概念
## 1.1 概述
* 具有专业的排版输出能力，产生的文档看上去就像“印刷品”一样。
* 具有方便而强大的数学公式排版能力，无出其右者。
* 绝大多数时候，用户只需专注于一些组织文档结构的基础命令，无需（或很少）操心文档
   的版面设计。
* 很容易生成复杂的专业排版元素，如脚注、交叉引用、参考文献、目录等。
* 强大的可扩展性。世界各地的人开发了数以千计的LATEX 宏包用于补充和扩展LATEX 的功
   能。
*　能够促使用户写出结构良好的文档——而这也是LATEX 存在的初衷。
* LATEX 和TEX 及相关软件是跨平台、免费、开源的。无论用户使用的是Windows，macOS
（OS X），GNU/Linux 还是FreeBSD 等操作系统，都能轻松获得和使用这一强大的排版工
具，并且获得稳定的输出。
## 1.2 第一次使用
下面为最短的latex源代码示例
```
\documentclass{article}
\begin{document}
``Hello world!'' from \LaTeX.
\end{document}
```
## 1.3 latex 命令和代码结构
LATEX 中命令以反斜线`\ `开头，为以下两种形式之一：
• 反斜线和后面的一串字母，如`\LaTeX` 。它们以任意非字母符号（空格、数字、标点等）为
界限。
• 反斜线和后面的单个非字母符号，如`\$` 。
## 1.4 宏包和文档类
### 文档类
```
\documentclass[⟨options⟩]{⟨class-name⟩}
```
options:
* `10pt`, `11pt`, `12pt `指定文档的基本字号。默认为10pt。
* `a4paper`, `letterpaper`, … 指定纸张大小，默认为美式信纸letterpaper。可指定选项还包括a5paper，b5paper，executivepaper 和legalpaper。
* `twoside`, `oneside` 指定单面/双面排版。双面排版时，奇偶页的页眉页脚、页边距不同。article和report 默认为oneside，book 默认为twoside。
* `onecolumn`, `twocolumn `指定单栏/双栏排版。默认为onecolumn。
* `openright`, `openany` 指定新的一章\chapter 是在奇数页（右侧）开始，还是直接紧跟着上一页开始。report 默认为openany，book 默认为openright。对article 无效。
* `landscape` 指定横向排版。默认为纵向。
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
![[Screenshot 2023-03-03 200031 3.png]]
## 1.6 文件的组织方式
```
\include{⟨filename⟩}
```
```
\include{chapters/file} % 相对路径
\include{/home/Bob/file} % *nix（包含Linux、macOS）绝对路径
\include{D:/file} % Windows 绝对路径，用正斜线
```

## 1.7 latex和tex相关概念
**`引擎`** :全称为排版引擎，是编译源代码并生成文档的程序，如pdfTEX、XƎTEX 等。有时也称为
编译器。
**`格式`**:是定义了一组命令的代码集。LATEX 就是最广泛应用的一个格式，高德纳本人还编写了一
个简单的plain TEX 格式，没有定义诸如`\documentclass` 和`\section`等等命令。
**`编译命令`**:是实际调用的、结合了引擎和格式的命令。如xelatex 命令是结合XƎTEX 引擎和
LATEX 格式的一个编译命令
# 第二章 用latex排版文字
## 2.1 语言文字和编码
## 2.2 排版中文
ctex宏包
## 2.3 latex中的字符
`\par`分段
`%`  注释
特殊字符使用`\`转义
## 2.4 断行和断页
手动断行 `\newline`
手动断页`new page ` `clear page`
判断`\linebreak` `page break`
# 第三章 文档元素
## 3.1 章节和目录
划分章节:
```
\chapter{title}   \section{title}    \subsection{title}
\subsub{title}    \paragraph{title}  \subparagraph{title}
```
• article 文档类带编号的层级为`\section ` ` \subsection `  `\subsubsection` 三级；
• report / book 文档类带编号的层级为`\chapter` ` ` `\section ` ` \subsection `三级。
目录
```
\table of contents`
```
这个命令会生成单独的一章（report / book）或一节（article），标题默认为“Contents”
```
\addcontentsline{toc}{⟨level⟩}{⟨title⟩}
```
将正文和附录分开 `\appendix`


## 3.2 标题页
```
\title{name}     \author{name}     \date{date}
```
## 3.3 交叉应用
`\lable{label-name}`
`\ref{label-name}`
`pageref{label-name}`
## 3.4 脚注和编注
`\footnote{这是脚注}`
```
footnotemark
footnotetext{脚注内容}
```
边栏
```    `\marginpar{编注}` ```

## 3.5 特殊环境
### 3.5.1 列表
```
\begin{enumerate}
\item...
\end{enumerate}
```
关键字description
```
\begin{description}
\item[item title]
\end{description}
```
### 3.5.2 对齐环境
```
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
```
\begin{quote}
...
\end{quote}
```

### 3.5.4 摘要环境 
abstract
### 3.5.5 代码环境
verbatim
简短代码或关键字
`\verb|...`
## 3.6 表格
tabular环境

## 3.7 图片
调用graphicx宏包
`\lncludegraphics{filername}`
## 3.8 盒子
水平盒子
 `makebox {...}`
带框的水平盒子
```
\fbox{,,,}
\framebox{...}
```
垂直盒子
```\parbox{width}{...}

```
标尺盒子
`\rule{width}{height}`
## 3.9 浮动体

# 第四章 排版数学公式
# 第五章 排版样式设定
# 第六章 特色工具和功能
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
