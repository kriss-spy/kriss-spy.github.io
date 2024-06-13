# install
Tex system: MikTex, proText, Texlive
editor: Texmaker, WinEdit, TexWorks...

//i chose texstudio, and it has dark mode!

若使用中文，在前置区中加入命令：
`\usepackage [UTF8]{ctex}`
# manual
[The Not So Short Introduction to LaTex](https://mirrors.concertpass.com/texarchive/info/lshort/english/lshort.pdf)
[chinese version](https://mirror.las.iastate.edu/texarchive/info/lshort/chinese/lshort-zh-cn.pdf)
# resources
https://www.latex-project.org/
https://www.ctan.org/
https://ctan.org/pkg/latex2e-help-texinfo
https://mirrors.rit.edu/CTAN/info/latex2e-help-texinfo/latex2e.html
http://tug.ctan.org/tex-archive/macros/latex2e/base/source2e.pdf
manual integrated in editors
# LaTeX 使用（基础）
```latex title example1.tex
example1.tex

% example1.tex

\documentclass{report}

\begin{document}

This is my first {\LaTeX} typesetting example.\
This is my first\LaTeX{} typesetting example.\
This is my first\LaTeX\ typesetting example.\
I am Mr. Edward G.J. Lee, G.J. is a abbreviation of my name.\
I am Mr\ Edward G.J. Lee, G.J. is a abbreviation of my name.\
Please see Appendix A. We will be there soon.\
Please see Appendix A. We will be there soon.

\end{document}

```
Latex 文件：后缀为 .tex 为纯文字文档，

可以用任何编辑器编辑

sooner or later I will turn to vscode (
## LaTeX 排版命令
Latex 特殊专用符号
1. \ ： 排版指令由 “\”开头；
2. ％ ：注解。
3. $：进入、离开数学模式
4. ｛｝：命令作用范围；
5. ～：产生一个空白；
6. \\ ： 换行

Latex 文稿中，空一个和多个空白都会被认为一个英文空白；

Latex 用空白行来分隔各个段落，但是空一行和多行都认为是一个空白行

## LaTeX 基本文本结构
```latex
\documentclass{article}
    Preamble区
    % Preamble区一些会影响整个文章的指令或者宏命令集
\begin{document}
    文本区
\end{document}
```

常用 class ： article, report, book

常用 options ： 10pt, a4paper, twocolumn
```latex
\documentclass[options]{class}

\documentclass[12pt, a4paper, oneside, draft]{report}
To typeset the docement as a report to be in 12pt typer on A4, but printed one-sided in draft mode
```
### Document Classes

|   |   |
|---|---|
|article|For articles in scientific journals, presentations, short reports, program documentation, invitations, ...|
|IEEEtran|For articles with the IEEE Transactions format.|
|proc|A class for proceedings based on the article class.|
|report|For longer reports containing several chapters, small books, thesis, ...|
|book|For real books.|
|slides|For slides. The class uses big sans serif letters.|
|memoir|For changing sensibly the output of the document. It is based on the book class, but you can create any kind of document with it|
|letter|For writing letters.|
|beamer|For writing presentations.|

### Document Class Options

|   |   |
|---|---|
|10pt, 11pt, 12pt,…|Sets the size of the main font in the document. If no option is specified, 10pt is assumed.|
|a4paper, letterpaper,...|Defines the paper size. The default size is letterpaper;|
|fleqn|Typesets displayed formulas left-aligned instead of centered.|
|leqno|Places the numbering of formulas on the left hand side instead of the right.|
|titlepage, notitlepage|Specifies whether a new page should be started after the document title or not. The article class does not start a new page by default, while report and book do.|
|twocolumn|Instructs LaTeX to typeset the document in two columns instead of one.|
|twoside, oneside|Specifies whether double or single sided output should be generated. The classes article and report are single sided and the book class is double sided by default.|
|landscape|Changes the layout of the document to print in landscape mode.|
|openright, openany|Makes chapters begin either only on right hand pages or on the next page available. This does not work with the article class, as it does not know about chapters. The report class by default starts chapters on the next page available and the book class starts them on right hand pages.|
|draft|makes LaTeX indicate hyphenation and justification problems with a small square in the right-hand margin of the problem line so they can be located quickly by a human. It also suppresses the inclusion of images and shows only a frame where they would normally occur.|

### Preable 区
```latex
\documentclass{article}
\usepackage{color} % color package used in the article.
\linespread{1.36} % 将行距变成原来的1.36 倍
\parindent=0pt % 调整段落内缩的程度，这里调整成0

\begin{document}
This is blue color.\\
\textcolor{blue}{This is blue color.}
\end{document}
```
编译结果：
![[appendix/Pasted image 20240611214506.png]]

## 文档结构
章节标题由指令控制，不必理会字型、大小， Latex 会自动处理

章节标题内容直接写入指令的大括号里

Book/report: 深度标号 2； article：深度标号为 3

|   |   |   |
|---|---|---|
|深度标号|指令|作用|
|-1|\part{}|部，最大结构|
|0|\chapter{}|章， article 文章里无章|
|1|\section{}|节|
|2|\subsection{}|小节|
|3|\subsubsection{}|次小节|
|4|\paragraph{}|段落|
|5|\subparagragh{}|小段落|

## 章节标题与交叉引用
```latex
% example2.tex \documentclass{report} 
\usepackage[colorlinks=true]{hyperref}

\begin{document}

This is the first experience of \LaTeX. \chapter{Aesop Fables}\label{Ch:1} 
\section{The Ant and the Dove}

An ant went to the bank of a river …

\section{The Dog in the Manger}

A dog lay in a manger, and by his growling…

\chapter{The Eagle and the Arrow}

An eagle… Please see Section \ref{Ch:1}.

\end{document}
```
![[appendix/Pasted image 20240611215929.png]]
## 加入 title page
```latex
% example3.tex

\documentclass{report}

  \title{Aesop Fables} 
  \author{Aesop\thanks{Thanks to the reader.}
      \and Nobody\thanks{Thanks to nobody.}}
  \date{\today}

\begin{document}

  \maketitle

  This is the first experience of \LaTeX. \chapter{Aesop Fables} \section{The Ant and the Dove}

\end{document}
```
1. title page: 包括 title, author, date, thanks；若无\maketitle 就没有 title page 。
2. 在 report/book 中, title page 自 成 一 页 ； 在 article 中 , title page 和文本连在一起；
3. 要修改的地方是 preamble 区及文本区的\maketitle
4. title page 不编码。
5. 作者用\and 指令连接。 若没有\date{\today}指令， 日期固定为今天

## 加入目录
```latex
% example4.tex
\documentclass{report}
\title{Aesop Fables}
\author{Aesop\thanks{Thanks to the reader.}
\and Shan\thanks{Thanks to Kevin.}}
\date{\today}
\begin{document}
\maketitle
\tableofcontents
This is the first experience of \LaTeX.
\section{Aesop Fables}
\section{The Ant and the Dove}
\end{document}
```
要编译 2 次, 产生 example4.toc，再真正加入目录。

目录顺序： (abstract,) Table of Contents, List of Figures, List of Tables．

## 加入摘要
```latex
\begin{abstract}
  missing
  missing
  % or use \input{abstract.tex}
\end{abstract}
```
abstract 只有 article/report 才有， 

report 的摘要自成一页，不编页码， 且不会放入目录； 

article 的摘要和正文相连，在文章标题后。
## 加入脚注
脚注由阿拉伯数字编号，至于页底

report/book 类， 编号每章会从头算起， article 则会连续

脚注 Footnote
```latex
A Dove\footnote{Pigeon, an emblem of peace.}
```
边注 Marginal note
```latex
A Dove\marginpar{Pigeon, an emblem of peace.}
```

## 字形调整
### 字族 （ font family）
默认为 Knuth 教授所设计的 Computer Modern fonts。

例： cmr Computer Modern Roman； cmss Computer Modern Sans Serif； cmtt Computer Modern Typewriter

### 字型系列 （ font series）
字型的 weight（ 胖瘦）及 width（ 长扁） 。例如粗、细字体，一般用 medium， 粗体是 bold。m： medium； b: bold； bx: Bold extended； sb: Semi-bold； c: Condensed

### 字形 （ font shape）： 字的形状。
n : 正常字（ normal），指 upright; it Italic sl Slanted sc Small Caps

### 字型大小（ font size）
预设 10pt（ 10 point）

![[appendix/Pasted image 20240613101244.png]]

也 可 当 成 环 境 来 用 ， 如 \begin{itshape}, \end{itshape}， \itshape， 以后文字都用 italic， 直至另一个改变字型的指令出现

### 相对字形大小的调整
10pt 时各种字型大小指令、 实际例子、及其大小；
![[appendix/Pasted image 20240613102752.png]]
```latex
\begin{small}
    文字
\end{small}
```
## 纸张大小
```latex
\documentclass[12pt, a4paper]{report}
```
![[appendix/Pasted image 20240613103717.png]]

## 项目标签环境 (item labe)
### 项目式条列环境 (itemize)
//源代码中，缩进只是增强可读性，决定列表分级的是\begin 和\end 的结构
```latex
\documentclass[10pt]{article}
\usepackage[UTF8]{ctex}
\begin{document}

\begin{itemize}
\item 第一大项，这是第一大项。
\item 第二大项，这是第二大项。
	\begin{itemize}
	\item 第一小项，这是第一小项。
	\item 第二小项，这是第二小项。
	\end{itemize}
\item 第三大项，这是第三大项。
\item 第四大项，这是第四大项。
\end{itemize}

\end{document}
```
![[appendix/Pasted image 20240613103940.png]]
### 枚举环境环境 (enumerate)
将上页命令中 itemize 改为 enumerate
![[appendix/Pasted image 20240613104735.png]]
### 条列环境 (description)
改成 description， 文字用方括号括住，则以粗体文字来起头
![[appendix/Pasted image 20240613104839.png]]

## tabular 表格

```latex
\documentclass[10pt]{article}
\begin{document}

\begin{tabular}[t]{lll}
\hline
column1 & column2 & column3 \\
\hline
item1 & item2 & item3 \\
itemA & itemB & itemC \\
\hline
\end{tabular}

\end{document}
```
![[appendix/Pasted image 20240613104944.png]]
- `[t]` 表示 top， `[b]` 表示 bottom， `[c]` 代表 center；

- `lll` 指定各列内容在小方框内的置放位置，
`l` 标示靠左（left） ， `r` 表示靠右（right） ，
c 表示置中（center） 。 在 `{lll}` 中加上 bar`|` 会画纵线， 例如 `{|l|l|l|}` 就变成传统的大方框、 小方框表格。 而两个 bar 就会画双纵线。
- `\hline` 画一横线， `\hline\hline` 画双横线； 。
- 最常用， 作为一个整体处理， 不能被分割。
- 有表格线， 列间符号是&， 要指定列內文字的位置。

1. `p{宽度}`：指定列宽，指定了宽度后，里面文字自动换行。

2. `@{文字、符号或指令}`：让指定列各行都出现某个文字、符号或都在某个指令作用下。置于首尾的话，会让横线和文字切齐（预设不对齐，横线两端会多出栏位位间距的部份）。 @{} 如无参数，作用是去掉两列多余表格线。

3. `\multicolumn{列}{左右位置}{文字內容}`：跨列排版， 例如一小段文字跨两列。左右位置可使用 l r c 之一。

4. `\cline{a-b}`： a-b 指的是要画横线的列数， 例如\cline{2-3} 就是画第二列至第三列的横线。

5. `\arrayrulewidth`：调整表格线条的粗细， 预设为 0.4pt。使用方法： \arrayrulewidth=1.5pt 即可， 要注意在进入 tabular 环境前设好。

6. `\tabcolsep`：调整两列间距。所设指是实际列间距一半，预设是 6pt。 使用方法和 `\arrayrulewidth` 一样。

7. `\doublerulesep`：调整画双线时， 两线间间距， 预设值是 2pt。使用方法和 `\arrayrulewidth` 一样。

8. `\arraystretch`：调整表格上下行距。 这要由 `\renewcommand` 来重设，因为在 LATEX 定义出的一个常数值，而这个 `\arraystretch` 是这些常数值的倍数，需要重新改变他才能改变预设倍数。例如： example16.tex 中的使用方法。

### 表格浮动环境
```latex
\begin{table}[置放位置选项] % 进入浮动表格环境
\caption{表格标题}
\begin{tabular}{表格参数}
表格内容
\end{tabular}
\end{table}
```
tabular 表格，不能被分割，当表较大时 LATEX 就会起新页去置放，看起
来很不自然

使用浮动环境， LATEX 把前后位置经过整体计算，再决定图
表应放在哪儿。

`\caption{}` 指定表格标题，编译后会自动标上‘Table n:’ ， 后接 caption 的內容，
n 会自动编号。 

① h(here) 置于下指令处 ② t(top) 置于一页的顶端 ③
b(bottom) 置于本页底部， 如空间不够会置于次页 ④ p(page) 单独占一页

```latex
\documentclass{article}
\usepackage[colorlinks=true]{hyperref}
\usepackage{graphicx}

\begin{document}
\section{Experiment Result}
The proposed method is able to automatically recover a better PSF and reconstruct images of a higher quality according to the Peak
Signal to Noise Ratio (PSNR), see Table.\ref{tab:results}.

\begin{table}[htb]
\caption{Experiment Results}
\label{tab:results}
\begin{center}
\begin{tabular}[t]{lll}
\hline
column1 & column2 & column3 \\
\hline
item1 & item2 & item3 \\
itemA & itemB & itemC \\
\hline
\end{tabular}
\end{center}
\end{table}

\end{document}
```

![[appendix/Pasted image 20240613145242.png]]

## 图形
插入图片方法：
```latex
\usepackage{graphicx}； % 用\includegraphics 指令：
...
\begin{document}
...
\begin{figure} % 进入浮动环境
\includegraphics[参数]{图片名称}
...
\caption{标题}
\label{引用标志}
\end{figure}
...
```
### includegraphics 指令选项
1. Width：图像宽度， 会自动伸缩， 例如 [width=5in]； [width=0.75\textwidth]

2. Scale：按比例缩放， 无单位， 缩放倍数。 例： [scale=.5]

3. Bb：设定（ bounding box） ， bb=98 98 468 430， 左下角坐标是 (98, 98)， 而右上角坐标是 (468, 430)， 以纸张的左下角为 (0, 0)

4. Clip：修剪图的四周指定边缘。

5. Trim：去除的部份长度。 如： \includegraphics[trim=7 7 7 7, clip]{some}除去四周 7bp(big point) 。 图文件尽量不加扩展名。

6. Angle：逆时针旋转角度。 例： [angle=90, height=1in]

7. Orgin：旋转中心。

8. Height：图形高度。

9. totalheight：图形总高度， 即 height 再加上 depth 的值

### 案例：插图与交叉引用
```latex
\documentclass{article}
\usepackage[colorlinks=true]{hyperref}
\usepackage{graphicx}

\begin{document}
\section{Experiment Result}
The proposed method is able to automatically recover a better PSF and reconstruct images
of a higher quality according to the Peak Signal to Noise Ratio (PSNR), see
Fig.\ref{fig:SadScientist}.

\begin{figure}[h]
	\centering
	\includegraphics[width=3in]{1.jpg}
	\caption{SadScientist}
	\label{fig:SadScientist}
\end{figure}

\end{document}
```
![[appendix/Pasted image 20240613145530.png]]

默认使用工作目录下的图片，通过名称引用

### 指定图像文件搜索路径
1. LATEX 预设路径是当前目录。

2. `\graphicspath{{path1}{path2}{path3}...}`

3. `\graphicspath{{images/}}` 指定搜索路径为工作目录下的 images 目录

4. `\includegraphics{}` 直接将绝对路径写进去， 不建议，可读性差，移植性不好。

# LaTeX 使用（数学的排版）
## 数学公式排版
LaTeX 本身具有排版数学式子的能力

专业场合， 需要更强功能。 AMS-LATEX 是美国数学协会（ American Mathematical Society, AMS） 所发展的一个增强 LATEX 数学式子编辑的宏命令集， 分成两个部分： amscls 及 amsmath， 前者提供符合 AMS 的文件
规格的文稿类别， 后者可加强原来 LATEX 的数学模式。

Math mode: inline mode and display mode

数学式需进入数学模式处理。

- 数学模式下，大部分文字、符号采用斜体字，空间另作安排，额外的空白会被忽略；
- 在数学模式中要输入一般的正常文字， 要退出数学模式，或者由 `\mbox{}` 或 `\textmr{}` 包围起来。

## inline mode
1. `$数学式子$`
2. `\begin{math}数学式子\end{math}`
3. `\(数学式子\）`
```latex
\documentclass[10pt]{article}
\begin{document}
$f(x,y)=3x+4y$
$f(x, y) = 3x+ 4y$ % 空白不作用
\( \sin (2x) = -\sin x \cos x \)
\begin{math} f(x,y) = 3(x+y)y / (2xy-7) \end{math}
\end{document}
```
![[appendix/Pasted image 20240613151916.png]]

## display mode
1. `\begin{displaymath} 数学式子\end{displaymath}`

2. `\[数学式子\]`

无编号

1. `$$数学式子$$`

2. `\begin{equation}数学式子\end{equation}`

这种使用方式，亦会独立成一行，而且有编号。 equation* 则无编号。

数学式后如果有标点符号， 在 inline mode 中， 标点不应纳入数学模式中； 反之， 在 display mode 中， 标点符号则要纳入数学模式中。

基本语法省略，和 obsidian 大致相同
for reference: https://oeis.org/wiki/List_of_LaTeX_mathematical_symbols
## 具体语法
### 希腊字母
![[appendix/Pasted image 20240613152353.png]]
### Trigonometric functions
![[appendix/Pasted image 20240613152711.png]]
### hyperbolic functions
![[appendix/Pasted image 20240613152721.png]]
### relation operators
![[appendix/Pasted image 20240613152919.png]]
![[appendix/Pasted image 20240613153050.png]]
### binary operators
![[appendix/Pasted image 20240613153106.png]]
### negated binary operators
![[appendix/Pasted image 20240613153434.png]]
### Set and/or logic notation
![[appendix/Pasted image 20240613153450.png]]
### arrows
![[appendix/Pasted image 20240613155707.png]]
### other symbols
![[appendix/Pasted image 20240613155910.png]]
## AMS 数学环境：定理
- `\usepackage{amsmath,amsthm,amssymb}` % 引 入 AMS 数学环境

- `amsthm` 中 `\theoremstyle` 定义了 `plain`、`definition` 及 `remark` 三种 style。 预设的是 `plain`， 即定理名称用粗体，内文是 `italic`。 `\theoremstyle{remark}` % 内文使用正常字体。

- 证明可以直接使用 `amsthm` package 的 `proof` 环境

### 定理
`\newtheorem` 指令定义 `Theorem`, `Lemma`, `Definition` 等环境；

`\newtheorem{环境名称}{定理名称}[章节层次]`

```latex
\documentclass{article}
\usepackage{amsthm}
\newtheorem{lem}{Lemma}
\begin{document}
\begin{lem} Text text ... \end{lem}
\end{document}
```

![[appendix/Pasted image 20240613160549.png]]

`\newtheorem*` 不产生序号

### AMS 定理
```latex
\documentclass{article}
\usepackage{amsthm}
\theoremstyle{remark} % 定理内文字用正体
\newtheorem{defi}{Definition} % 在preamble 取定义好环境名称
\begin{document}
\begin{defi}
Let $f$ be continuous on the half-open interval $[a, b)$ and suppose $\lim_{x\rightarrow b^-}|f(x)|=\infty$.
Then, \[\int_a^bf(x)dx=\lim_{t\rightarrow b^-}\int_a^tf(x)dx\] provided this limit exists and is finite, in which
case we say the integral converges. Otherwise, we say it diverges.
\end{defi}
\end{document}
```
![[appendix/Pasted image 20240613161426.png]]

### proofs
```latex
\begin{proof}
missing
\end{proof}
```

### 复杂公式输入
利用 Mathtype 软件的 Cut and Copy preferences 功能直接生成 Latex 命令

# LaTeX 使用（参考文献）
## 参考文献 (Bibliography, Reference)
### the bibliography 环境
- `[标记]`： 可选参数，如无，引用
后用阿拉伯数字标记，外加方括
号；如果有加入的话，引用后使
用所加入的标记。
- `{键值}` ： 引用时的关键字，
- 引用： `\cite{键值}`

```latex
\begin{thebibliography}
\bibitem[标记一]{键值一} 参考文献一
\bibitem[标记二]{键值二}参考文献二
...
\end{thebibliography}
```

```latex
\documentclass{article}
\begin{document}
This is my first paper\cite{KDEt}.

\begin{thebibliography}{}
\bibitem{KDEt} Knuth, D.E., \textit{The \TeX{}~book}, Reading, Massachusetts: Addison-Wesley, 1989.
\end{thebibliography}

\end{document}
```
![[appendix/Pasted image 20240613170302.png]]

## BibTeX 简介
参考文献按一定格式写于 *.bib 文件，在文稿中以 `\bibliogrphy` 指令来引入;

在 latex 编译文稿后，再利用 bibtex 编译一次文稿，最后再使用 latex 重新编译。

```latex
\begin{document}
\bibliographystyle{plain} % 指定style
...
\bibliography{your.bib} % *.bib可以省略
...
\end{document}
```

### *.bib 文件格式
```bib
@book{ KDEt,
author = "Knuth, Donald E.",
year = "1989",
title = "The {\TeX}book",
publisher = "Addison-Wesley",
address = "Reading, Massachusetts",
volumn = " ",
edition = " ",
month = " ",
series = " ",
note = " ",
}
```

- 参考文献格式由 `*.bst` 控制；
- 引用使用`\cite` 指令
- 要全部 `*.bib` 里面的资料都印出来， 可以用`\nocite{*}`指令

获得 Bibtex 的途径：
1. 从 Google Scholer 获得;
2. 从各种数据库获得；
3. 从各种文献管理软件中获得

BibTEX 的参考文献格式由*.bst（ bibliography style） 控
制， 上面所引用的是plain 是引用plain.bst这种格式， 这是
最基本的格式

-  plain 依字母的顺序印出， 比较顺序为author, year, title
-  unsrt 依引用的先后次序印出
- abbrv 与plain 相同， 但first name, month, title, journal
以缩写印出
- alpha 引用处显示[作者年份] 来取代数目


```latex title:Mytext.tex
\documentclass{article}
\begin{document}
And finally take a look a more ordinary looking
scientific reference \cite{Homer_2007}.
\bibliographystyle{plain}
\bibliography{Mybib}
\end{document}
```

```bib title:Mybib.bib
@ARTICLE{Homer_2007,
AUTHOR = "Homer Simpson and Mickey Mouse",
TITLE = "On the theory of everything",
JOURNAL = "Journal of the most useful theories",
YEAR = "2007",
volume = "5",
number = "2",
pages = "123-456"
} 

@MISC{Bibliography_howto,
author = {Tutorial team for the Indian TEX Users Group},
title = {Online tutorials on LaTeX},
howpublished = "\url{http://www.tug.org.in/tutorials.html}"
}
```

![[appendix/Pasted image 20240613171559.png]]

# LaTeX使用（交叉引用）
LATEX 提供了三组交叉引用指令：
- `\label{名称}` % 置于被引用处，以一个名称标记；
- `\ref{名称}` % 引用`\label` 所标记处的章节
- `\pageref{名称}` % 引用`\label` 所标记处的页码


```latex
请参考图\ref{fig:struct}，第\pageref{fig:struct}页
```

1. 有些编辑器有交叉引用时， 要编译两次才能正常显示。
2. 能编号的章节、图表、列举项目、公式、定理才能交叉引用。
3. 图表的参照`\label` 要在`\caption` 后，不能在前。
