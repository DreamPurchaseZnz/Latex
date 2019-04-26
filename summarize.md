














{chapter 2}
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
```



