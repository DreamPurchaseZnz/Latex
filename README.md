```
\documentclass[10]{ctexart} % book,report,letter

%\usepackage{ctex}

\title{\heiti 我的文档}
\author{nianzu.zheng}
\date{\today}
\usepackage{graphicx}
\graphicspath{{figures/}}% 图片在当前目录下的figures目录下

\usepackage{amsmath}
\usepackage{amssymb}
\usepackage{dirtree}% 用于生成列表
\usepackage{listings}%用于展示程序

\usepackage[style=numeric,backend =biber]{biblatex}
\addbibresource{reference_lib.bib}
%\bibliographystyle{plain}
%\usepackage{multirow}

% 定义为新命令
\newcommand\degree{_\circ}
\newcommand\myorder[2][打]{#1#2}
\renewcommand\abstractname{内容简介}


%正文区（文稿区）
\begin{document}
	
	\maketitle

	let $f(x) $ is defined by the formula
	$$f(x)=x^3+x^2-1$$
	 Then $f(x)$ can be seen as the quality factor. All the factor should be considered, or it will lead to a bad consequence.
	$\angle C=90\degree$
	% 带标号的Equation公式
    \begin{equation}
    AB^2=BC^2+AC^2
    \end{equation}
    for short% 不带标号的Equation公式

    %----------------------------------------------
    \begin{lstlisting}
    >>>a=[1,2,3,4,5,6,7]
    >>>b=filter(lambda x:x>5, a)
    >>>print b
    >>>[6,7]

    \end{lstlisting}
    %------------------------------------------------

    \begin{equation*}
    a^2+b^2=c^2
    \end{equation*}

    \textbf{列表运算}%
    \dirtree{%
    .1 list..
    .2 count.
    .2 index.
    .2 reverse.
    }




    % 第二部分 字体族、字体大小、字体系列、字体形状
    \textrm{罗马族} \textsf{无衬线字体} \texttt{打字机字体}

    \rmfamily Good morning.
    I’m very glad to stand here and give you my informative speech. To begin with, let me show you a series of pictures.As is\newline depicted in the picture we can see something
    {\sffamily
    	it can be used for\par
    	
     	Search and Rescue\par
     	    	
    	Atmospheric science research\par
    	
    	Aerial package delivery }

    % 使用matlab所生成的图像
    \begin{figure}
      \centering
      \includegraphics[scale=1]{peaks1.eps}
      \caption{山峰}\label{peaks1}
    \end{figure}


    Well, there is such a kind of invention that contains all the functions above. And I am quite sure that all of you have ever heard about it. Guess what it is? {\ttfamily (wait)}

    % 字体系列设置
    \mdseries
    \textbf{Right!} That is my topic today---\textit{unmanned aerial vehicle }or \textsl{UAV for short} ， what at started as a platform for hobbyists is poised to become a multibillion-dollar industry.

    % 中文字体及字号
    {\zihao{-5} {\songti 具体行文思路}}


    {\Large Today} at first I want to introduce you the following parts.

    %第三部分篇章结构
    \tableofcontents
%    \chapter{chapter 1}
    \section{Introduction}
    \subsection {UAV }
    \subsection {UAV and MAV }
    \section{What the UAV is}

     Firstly, just as I mentioned, I will explain what it is UAV are aircrafts capable of flight without a pilot on board.  Such vehicles can be controlled remotely by an operator at a  ground control station, or can fly autonomously {\textit{[ɔ:'tɒnəməslɪ]}}  based on pre-programmed flight plans or more complex dynamic automation {\textit{[ˌɔtəˈmeʃən]}} systems. Compared to manned aircraft, UAVs are often preferred for missions that are too "dull, dirty or dangerous" for humans. Well, since we has known what it is, let's move on to the second part.

  %  \chapter{chapter 2}
    \section{Several categories}% 空格的键入
     The second part is its categories.\kern 1pc T here are several categories of  UAV such as Fixed wing 、Flapping Wing and Rotary Wing. I will introduce these types in detail
    In the civilian field, fixed-wing UAVs , like airplane ,are offen used for long-distance, long-range and high altitude missions.
    However Flapping-wing UAVs is trying to duplicate the way birds or insects fly. Most of them are still under development.\copyright

    \LaTeX{} X{}关键词
    `UAV'  ``无人机''



    \section{Applications.}
    Last but not the least, due to some unique abilities of Rotary wings such as small size, and easy control, Rotary wings UAVs have been widely used in the world see as \ref{fig-uav}


    % 图示 % shif+alt+ctrl + rightarrow  注释
    \begin{figure}
    	\centering
    	\includegraphics[scale=0.2]{Desert}% angle=-30度
         \caption{picture of UAV}\label{fig-uav}
    \end{figure}

    And finally come to its Applications
    UAVs combined with traditional industries has a huge application areas and broad prospects for development; as an  aerial platform, the functions depends on what it carries, And there are some potential applications ,Such as agriculture、traffic、environment protection 、Land Resources and so on.see on table \ref{tab-result}

    % 表格 浮动体
    \begin{table}
    	\centering
    	\caption{Index}\label{tab-result}
    	\begin{tabular}{c ||c| c }
    		\hline
    		\ & RMSEP & RPD\\
    		\hline\hline
    		PSO & 1&10\\
    		\hline
    		ASFA & 2 & 100\\
    		\hline
    		
    	\end{tabular}
    \end{table}

    I prefer to talk about traffic
    Traffic jam is normally seen in each city of China ,especially in the event of traffic accident.It will not only cause adjacent road  paralysis ,but also cause the law enforcement and rescue vehicles could not reach the accident spot, which will cause the situation worse. however ,UAV can fly at low attitude and arrive at the accident spot very quickly  taking the photos for evidence at first time and sending feedback of the overall transportation situation by transmit the pictures it take
    In this way people will know what’s happening in the accident spot and then take measures in time to deal with traffic accident
    \section{End}
    All in all, through my brief introduction about UAVs, I hope that all of you can have a clear picture of it now.
    That’s all, thanks for your listening.



    %矩阵排版
    \[ % 数学环境下
    \begin{matrix}
           0 & 1\\
           1 & 0
    \end{matrix}\qquad
    \]
    \[ A =
    \begin{vmatrix}
           a_{11} & \dots & a_{1n}\\
           \vdots & \ddots& \vdots\\
           a_{n1} & \dots & a_{nn}
    \end{vmatrix}_{n\times n}
    \]
   % 小矩阵
   Small matrix  such as
   \begin{math}
   \left( %手动加入小括号
   \begin{smallmatrix}
   x & y \\ y & x
   \end{smallmatrix}
   \right)
   \end{math}

   \begin{math}
   	\begin{array}{|c c|}
        x &y\\
        y& x
   	\end{array}	
   \end{math}

    %公式部分
    $ a=b$
    交换律 \[a+b=b+a\]

    \begin{math} a=b+c  \end{math}


    $$ \lim_{x \rightarrow0}\left(1+\frac{1}{n}\right)^{n}$$
    % \left 右侧
    $$\left.\frac{\partial y}{\partial x}\right|_{x=4}$$
    $$ \mathop{lim}_{x \rightarrow 0}$$  % 将几个字母作为一个字母处理

    % 多行公式的排版
    % 带编号
    \begin{gather}
        a+b = b+a\\
        ab=ba\\
        c =d    \\
        d= e^2
    \end{gather}
    % 不带编号
    \begin{gather*}
        a+b = b+a\\
        ab=ba
    \end{gather*}

    % align 和align* 环境（用&对齐）
    % from\cite{article1} we can get the following rules
    %带编号
    %\bibliography{reference_lib}



    %公式对齐方式
    例子1
    \begin{equation}
    \begin{split}
         a^2+b^2+c^2 &=c^2+c^2\\
         & = 2c^2
    \end{split}
    \end{equation}
    例子2
    \begin{equation}
    \begin{split}
       z & =2 +4+5+7 \\
         & =6+12 \\
         & = 18
    \end{split}
    \end{equation}

    \begin{align}
       z & =2 +4+5+7 \nonumber \\ %\nonumber 去除编号
         & =6+12 \\
         & = 18
    \end{align}

    \begin{equation}
      \begin{gathered}
       z  =2 +4+5+7 \\ %\nonumber 去除编号
       z  =6+12 \\
       z  =18
    \end{gathered}
    \end{equation}
 %  分段函数 case函数
     \[ I_A(a)=\begin{cases}
                0, & \mbox{if } a \in A\\
                1, & \mbox{otherwise}  a\notin A
              \end{cases} \]
    \begin{equation}
         f(x) = \begin{cases}
         x^2，& \text{if } x > 0\\
         -x^2,& \text{if } x < 0
         \end{cases}
     \end{equation}


    %\begin{thebibliography}{widestlabel}
    %\bibitem{article1}郑念祖.\emph{基于聚类的样本选择方法研究}[J].计算机科学.2014(06)
    	%\bibitem{book1} nianzu.zheng .\emph{Research on sampling based on clustering 3rd Edition}Cambridge University press,New York,2027.
    %\end{thebibliography}
    \nocite{*} % 显示未引用的文献
    \printbibliography[title = {参考文献}]

\end{document}


%所有命令都是以“\”开头的
%注释以“%”开头
%空格：LaTeX中空格用来隔开单词(英语一类字母文字)，多个空格等效于一个空格；中文的空格则用“~”表示。
%换行：命令“\\”或“\newline”。
%分段：命令“\par”或空出一行
%换页：命令“\newpage”或者“\clearpage”

%知耻而后勇
% 对中文的编译采用XElatex （知耻而后勇）
%编译不通过：忘记引用宏包，命令拼写错误，括号未配对等
%搜索：英文优于中文，Google优于Baidu
%处理中文时，一定要记得要用XeLaTeX编译，并保存成UTF-8格式
%如果下载的文件WinEdt打开时提示错误，请用记事本打开，复制内容到Winedt中，再保存成UTF-8格式即可
%写一些，就编译一次，容易定位错误位置


%快捷键系类
%Alt+C：在剪贴板原有复制文本后增加新的被选择的文本。
%Ctrl+Shift+Alt+Right/Left：对选中文本增加或者删除Comment标记。
%Ctrl+Enter：自动完成LaTeX标准命令，cool。
%Shift+Enter：对光标所在位置的单词进行英语语法检查
%Alt+F12：对选中文本进行LaTeX语法检查（强烈推荐）。
%查找：
%Ctrl+Shift+Backspace/Delete： Moving Ring Backward/Forward。
%Ctrl+Shift+F12：括号匹配。
%编译：
%Ctrl+Shift+X：（生成DVI文件）
%Ctrl+Shift+D：DVI --> PS
%Ctrl+Shift+G：查看PS文件
%Ctrl+Shift+B：编译bib文件
%Ctrl+Shift+C：编译选中的文本
%shit+enter 自动完成LaTeX标准命令
%\(re)newcommand {name}[num]{definition}
                 %name，是你想要定义的命令的名称
                       %num，可选，用于制定命令所需参数的数目
                             %definition，命令的定义，也是要执行的操作

% tab键可以产生代码缩进
%处理一个较大的文件，一个有效的方法是把它分成几个部分，然后分别用input 或者 include命令导入.
%\input 连续不分页
%\include 开始新的一页

%#——\#
%$——\$
%%——\%
%{——\{
%}——\}
%~——\~{}
%\——$\backslasb$
%^——\^{} 注意报错为 miss % inserted

%生成空格, 则可以使用下面的命令:
%两个quad空格 a \qquad b 两个m的宽度
%quad空格 a \quad b 一个m的宽度
%大空格 a\ b 1/3m宽度
%中等空格 a\;b 2/7m宽度
%小空格 a\,b 1/6m宽度
%紧贴 a\!b 缩进1/6m宽度

%用于绘制列表     \usepackage{detree}
%\textbf{列表运算}%
%\dirtree{%
%.1 list..
%.2 count.
%.2 index.
%.2 reverse.
%}


%\begin{figure/table}[!htbp]
%其中htbp是可选的，它们分别代表
%!-忽略“美学”标准
%h-here
%t-top
%b-bottom
%p-page-of-its-own


% 大于等于号是  \geqslant     小于等于号 \leqslant  水平的横线\le | \leq  \ge  \geq

%-----------设置section样式-------------------------------------------
%\makeatletter %使\section中的内容左对齐
%\renewcommand{\section}{\@startsection{section}{1}{0mm}
%  {-\baselineskip}{0.5\baselineskip}{\bf\leftline}}
%\makeatother
% NAME  表示所定义的节标题的名称（不要带反斜杠），比如section和subsection。
%  LEVEL      是一个数字，可以定义节标题的命令层次。这个数决定了定义的节标题是否编号（若是小于等于   secnumdepth则被编号）也决定了标题是否会被编进目录（若是小于等于tocdepth则被编号）。
%  INDENT     : 定义节标题到版心左边的距离。此度量若是负数则标题进入边空。
%  BEFORESKIP： 是一个长度，其绝对值表示标题到上文之间的距离。若是此距离为负数，则标题后面的第一个段落不缩进。此度量最好是一个可以被伸长和缩短的长度。另外标题总是另起一段的。因而parskip已被加入到标题与上下文的距离。
%  AFTERSKIP :是一个长度，其绝对值表示独立显示的标题到下文之间的垂直间距或者是段内显示的标题到下文之间的距离。此度量若是负的，则定义的标题是段内显示的。对于独立显示的标题，parskip也已被加进标题与下文的距离。 STYLE ：决定标题的内容形式。可以是任意影响文本排版结构的命令如加入尺寸\huge \large \bfseries 对齐命令等

%\verb|\balance| ->表示圈住一个命令
%\texttt{ddd}
%verbatim环境可原样输出其中的文本，忽视TeX命令。verbatim*会将空格以└┘的形式输出。
%对简短的抄录，可使用\verb|文字|和\verb*|文字|。

%There are several options for \verb|\bibliographystyle|:

%plain	normal style - listed in ABC order and labeled numerically
%unsrt	same as plain except entries appear in order of citation
%alpha	same as plain except entry labels are used
%abbrv	same as plain except uses abbreviations for first names,	month names, and journal name


%@BOOK{<some abbreviation that you make up>,
%	    AUTHOR = "author",
%	    TITLE = "book title",
%	    PUBLISHER = {publishing company},
%	    ADDRESS = {where published},
%	    YEAR = year published}


一些有用的变量是：

%页面设置
%\columnsep: 列间距
%\topmargin: 页眉到页边的距离
%\topskip: 页眉与正文的距离
%\textheight: 正文的高度
%\textwidth: 文本的宽度
%\oddsidemargin: 奇数页的左面页边距
%\evensidemargin : 偶数页的左面页边距
%段落
%\parindent: 段落缩进距离
%\parskip: 段落间的距离
%浮动图表
%\floatsep: 浮动对象之间的距离
%\textfloatsep: 最后一个浮动对象顶端或第一个浮动对象底端与正文之间的距离
%\intextsep : 文中浮动顶端与底端所留的距离
%\dbltextfloatsep 是在双列输出时用 \textfloatsep 的数值
%\dblfloatsep 是在双列输出时用 \floatsep 的数值
%\abovecaptionskip: 标题上方的距离
%\belowcaptionskip: 标题下方的距离
%数学公式
%\abovedisplayskip: 公式前的距离
%\belowdisplayskip: 公式后面的距离
%\arraycolsep: 在一个array中列之间的空白长度
%列表
%\topsep: 第一个item和前面版落间的距离
%\partopsep: 当在一个新页开始时加到 \topsep 的额外空间
%\itemsep: 连续items之间的距离


% 设置页边距的方法：
%\usepackage{geometry}
%\geometry{left=2.5cm,right=4cm}

%对边缘进行标注的方法
%%\usepackage{marginnote}
%\usepackage{todonotes}

% 用于产生参考文献，需要编译三遍
%Here is an example file, which requires biber, and can be compiled with xelatex. Use the following commands: xelatex <filename>.tex, biber <filename>.bcf, xelatex <filename>.tex --- where '<filename>' is whatever you called the example file. (Note I don't have complicated UTF8 needs for my bibliography, so I added one entry full of gibberish; but compare the junkentry input with the image given below to see that biber handles the material properly, whereas bibtex would choke and produce the wrong gibberish.)

%当存在大量的包时 ，可以将这些设置放在另外一个tex 文件中，并以input的格式调用
%\input{structure.tex} % Specifies the document structure and loads requires packages
```
