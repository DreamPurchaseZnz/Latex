# Some common usages
There are some beautiful examples, but I can only list weblinks and codes here for convenience 
because the github is not easy to present diagrams.

[Nested structure](http://www.texample.net/tikz/examples/system-combination/)



## Manually listing objects
```
% Bootstrap resampling
% Germain Salvato-Vallverdu - mai 2009
% http://germain.salvato-vallverdu.perso.sfr.fr
\documentclass[11pt,a4paper,landscape]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[francais]{babel}
\usepackage[top=3cm,left=2cm,right=2cm,bottom=3cm]{geometry}

\usepackage{tikz}
\usetikzlibrary{shadows} 

\usepackage{hyperref}
\hypersetup{%
pdfauthor={Germain Salvato-Vallverdu},%
pdftitle={bootstrap method},% 
pdfkeywords={Tikz,latex,bootstrap,uncertaintes},%
pdfcreator={PDFLaTeX},%
pdfproducer={PDFLaTeX},%
}

\title{Bootstrap method}
\author{Germain Salvato-Vallverdu}

\pagestyle{empty}

\begin{document}
\sffamily


\begin{center}

\begin{tikzpicture}[scale=1.4]

% style
\tikzstyle{rboule} = [circle,scale=0.7,ball color=red!40]
\tikzstyle{gboule} = [circle,scale=0.7,ball color=green!40]
\tikzstyle{bboule} = [circle,scale=0.7,ball color=blue!40]
\tikzstyle{nboule} = [circle,scale=0.7,ball color=black!40]
\tikzstyle{sample} = [->,thin]

% complete element space
\path[draw,<-,thick] (0,5.6) -- (4,5.6);
\path (6,5.6) node {Complete element space};
\path[draw,->,thick] (8,5.6) -- (12,5.6);

\path ( 0.00,5.25) node[bboule] (i01) {};
\path ( 0.25,5.25) node[rboule] (i02) {};
\path ( 0.50,5.25) node[gboule] (i03) {};
\path ( 0.75,5.25) node[bboule] (i04) {};
\path ( 1.00,5.25) node[rboule] (i05) {};
\path ( 1.25,5.25) node[bboule] (i06) {};
\path ( 1.50,5.25) node[bboule] (i07) {};
\path ( 1.75,5.25) node[rboule] (i08) {};
\path ( 2.00,5.25) node[bboule] (i09) {};
\path ( 2.25,5.25) node[rboule] (i10) {};
\path ( 2.50,5.25) node[bboule] (i11) {};
\path ( 2.75,5.25) node[bboule] (i12) {};
\path ( 3.00,5.25) node[nboule] (i13) {};
\path ( 3.25,5.25) node[rboule] (i14) {};
\path ( 3.50,5.25) node[bboule] (i15) {};
\path ( 3.75,5.25) node[bboule] (i16) {};
\path ( 4.00,5.25) node[rboule] (i17) {};
\path ( 4.25,5.25) node[rboule] (i18) {};
\path ( 4.50,5.25) node[bboule] (i19) {};
\path ( 4.75,5.25) node[bboule] (i20) {};
\path ( 5.00,5.25) node[rboule] (i21) {};
\path ( 5.25,5.25) node[bboule] (i22) {};
\path ( 5.50,5.25) node[rboule] (i23) {};
\path ( 5.75,5.25) node[bboule] (i24) {};
\path ( 6.00,5.25) node[bboule] (i25) {};
\path ( 6.25,5.25) node[rboule] (i26) {};
\path ( 6.50,5.25) node[rboule] (i27) {};
\path ( 6.75,5.25) node[gboule] (i28) {};
\path ( 7.00,5.25) node[rboule] (i29) {};
\path ( 7.25,5.25) node[bboule] (i30) {};
\path ( 7.50,5.25) node[bboule] (i31) {};
\path ( 7.75,5.25) node[nboule] (i32) {};
\path ( 8.00,5.25) node[bboule] (i33) {};
\path ( 8.25,5.25) node[rboule] (i34) {};
\path ( 8.50,5.25) node[gboule] (i35) {};
\path ( 8.75,5.25) node[bboule] (i36) {};
\path ( 9.00,5.25) node[bboule] (i37) {};
\path ( 9.25,5.25) node[rboule] (i38) {};
\path ( 9.50,5.25) node[bboule] (i39) {};
\path ( 9.75,5.25) node[rboule] (i40) {};
\path (10.00,5.25) node[bboule] (i41) {};
\path (10.25,5.25) node[rboule] (i42) {};
\path (10.50,5.25) node[bboule] (i43) {};
\path (10.75,5.25) node[bboule] (i44) {};
\path (11.00,5.25) node[rboule] (i45) {};
\path (11.25,5.25) node[nboule] (i46) {};
\path (11.50,5.25) node[rboule] (i47) {};
\path (11.75,5.25) node[bboule] (i48) {};
\path (12.00,5.25) node[bboule] (i49) {};

% title initial sample
\path (3.5,3.75) node[anchor=east] 
	{\parbox{0.15\textwidth}{\centering initial sample with N elements}};

% labels
\path (3.5,3)   node[anchor=east] {1};
\path (3.5,2.5) node[anchor=east] {2};
\path (3.5,2.0) node[anchor=east] {3};
\path (3.5,1.5) node[anchor=east] {4};
\path (3.5,0.5) node[anchor=east] {$N_b$};

\path (3.5,1) node[anchor=east] {$\vdots$};
\path[draw,dashed] (4,1) -- (8.25,1);
%
\path[draw,<->,thick] (2.9,0.5) -- (2.9,3) node[anchor=east,pos=0.5] 
	{\parbox{0.1\textwidth}{\centering $N_b$ \textit{bootstrap} samples}};

% initial sample
\path ( 3.75,3.75) node[bboule] (j01) {};               
\path ( 4.00,3.75) node[bboule] (j02) {};               
\path ( 4.25,3.75) node[rboule] (j03) {};               
\path ( 4.50,3.75) node[rboule] (j04) {};               
\path ( 4.75,3.75) node[rboule] (j05) {};               
\path ( 5.00,3.75) node[nboule] (j06) {};               
\path ( 5.25,3.75) node[bboule] (j07) {};               
\path ( 5.50,3.75) node[rboule] (j08) {};               
\path ( 5.75,3.75) node[bboule] (j09) {};               
\path ( 6.00,3.75) node[bboule] (j10) {};               
\path ( 6.25,3.75) node[bboule] (j11) {};               
\path ( 6.50,3.75) node[rboule] (j12) {};               
\path ( 6.75,3.75) node[gboule] (j13) {};               
\path ( 7.00,3.75) node[rboule] (j14) {};               
\path ( 7.25,3.75) node[gboule] (j15) {};               
\path ( 7.50,3.75) node[bboule] (j16) {};               
\path ( 7.75,3.75) node[rboule] (j17) {};               
\path ( 8.00,3.75) node[rboule] (j18) {};               
\path ( 8.25,3.75) node[bboule] (j19) {};               
\path ( 8.50,3.75) node[rboule] (j20) {}; 

% arrows from the complete space to the initial sample
\path[sample] (i01.south) edge[out=-60,in=120] (j01.north west);
\path[sample] (i04.south) edge[out=-60,in=120] (j02.north west);
\path[sample] (i05.south) edge[out=-60,in=120] (j03.north west);
\path[sample] (i08.south) edge[out=-60,in=120] (j04.north west);
\path[sample] (i10.south) edge[out=-60,in=120] (j05.north west);
\path[sample] (i13.south) edge[out=-60,in=120] (j06.north west);
\path[sample] (i16.south) edge[out=-90,in=90] (j07.north);
\path[sample] (i18.south) edge[out=-90,in=90] (j08.north);
\path[sample] (i20.south) edge[out=-90,in=90] (j09.north);
\path[sample] (i24.south) edge[out=-90,in=90] (j10.north);
\path[sample] (i25.south) edge[out=-90,in=90] (j11.north);
\path[sample] (i27.south) edge[out=-90,in=90] (j12.north);
\path[sample] (i28.south) edge[out=-90,in=90] (j13.north);
\path[sample] (i34.south) edge[out=-90,in=90] (j14.north);
\path[sample] (i35.south) edge[out=-90,in=90] (j15.north);
\path[sample] (i37.south) edge[out=-90,in=60] (j16.north east);
\path[sample] (i40.south) edge[out=-90,in=60] (j17.north east);
\path[sample] (i42.south) edge[out=-90,in=60] (j18.north east);
\path[sample] (i44.south) edge[out=-90,in=60] (j19.north east);
\path[sample] (i47.south) edge[out=-90,in=60] (j20.north east);
%
% bootstrap 1
\path ( 3.75, 3.0) node[bboule] {};                    
\path ( 4.00, 3.0) node[bboule] {};                    
\path ( 4.25, 3.0) node[bboule] {};                    
\path ( 4.50, 3.0) node[gboule] {};                    
\path ( 4.75, 3.0) node[rboule] {};                    
\path ( 5.00, 3.0) node[bboule] {};                    
\path ( 5.25, 3.0) node[gboule] {};                    
\path ( 5.50, 3.0) node[bboule] {};                    
\path ( 5.75, 3.0) node[rboule] {};                    
\path ( 6.00, 3.0) node[rboule] {};                    
\path ( 6.25, 3.0) node[bboule] {};                    
\path ( 6.50, 3.0) node[rboule] {};                    
\path ( 6.75, 3.0) node[rboule] {};                    
\path ( 7.00, 3.0) node[rboule] {};                    
\path ( 7.25, 3.0) node[bboule] {};                    
\path ( 7.50, 3.0) node[nboule] {};                    
\path ( 7.75, 3.0) node[rboule] {};                    
\path ( 8.00, 3.0) node[rboule] {};                    
\path ( 8.25, 3.0) node[gboule] {};                    
\path ( 8.50, 3.0) node[gboule] (b1) {};                    
                                                       
% bootstrap 2
\path ( 3.75, 2.5) node[bboule] {};                    
\path ( 4.00, 2.5) node[bboule] {};                    
\path ( 4.25, 2.5) node[rboule] {};                    
\path ( 4.50, 2.5) node[nboule] {};                    
\path ( 4.75, 2.5) node[rboule] {};                    
\path ( 5.00, 2.5) node[bboule] {};                    
\path ( 5.25, 2.5) node[bboule] {};                    
\path ( 5.50, 2.5) node[rboule] {};                    
\path ( 5.75, 2.5) node[rboule] {};                    
\path ( 6.00, 2.5) node[rboule] {};                    
\path ( 6.25, 2.5) node[bboule] {};                    
\path ( 6.50, 2.5) node[rboule] {};                    
\path ( 6.75, 2.5) node[rboule] {};                    
\path ( 7.00, 2.5) node[rboule] {};                    
\path ( 7.25, 2.5) node[rboule] {};                    
\path ( 7.50, 2.5) node[rboule] {};                    
\path ( 7.75, 2.5) node[bboule] {};                    
\path ( 8.00, 2.5) node[bboule] {};                    
\path ( 8.25, 2.5) node[bboule] {};                    
\path ( 8.50, 2.5) node[bboule] (b2) {};                    
                                                       
% bootstrap 3
\path ( 3.75, 2.0) node[rboule] {};                    
\path ( 4.00, 2.0) node[bboule] {};                    
\path ( 4.25, 2.0) node[rboule] {};                    
\path ( 4.50, 2.0) node[rboule] {};                    
\path ( 4.75, 2.0) node[bboule] {};                    
\path ( 5.00, 2.0) node[bboule] {};                    
\path ( 5.25, 2.0) node[bboule] {};                    
\path ( 5.50, 2.0) node[bboule] {};                    
\path ( 5.75, 2.0) node[rboule] {};                    
\path ( 6.00, 2.0) node[rboule] {};                    
\path ( 6.25, 2.0) node[gboule] {};                    
\path ( 6.50, 2.0) node[gboule] {};                    
\path ( 6.75, 2.0) node[rboule] {};                    
\path ( 7.00, 2.0) node[rboule] {};                    
\path ( 7.25, 2.0) node[nboule] {};                    
\path ( 7.50, 2.0) node[bboule] {};                    
\path ( 7.75, 2.0) node[rboule] {};                    
\path ( 8.00, 2.0) node[bboule] {};                    
\path ( 8.25, 2.0) node[rboule] {};                    
\path ( 8.50, 2.0) node[nboule] (b3) {};

% bootstrap 4
\path ( 3.75, 1.5) node[nboule] {};
\path ( 4.00, 1.5) node[bboule] {};
\path ( 4.25, 1.5) node[rboule] {};
\path ( 4.50, 1.5) node[gboule] {};
\path ( 4.75, 1.5) node[bboule] {};
\path ( 5.00, 1.5) node[gboule] {};
\path ( 5.25, 1.5) node[bboule] {};
\path ( 5.50, 1.5) node[rboule] {};
\path ( 5.75, 1.5) node[bboule] {};
\path ( 6.00, 1.5) node[rboule] {};
\path ( 6.25, 1.5) node[gboule] {};
\path ( 6.50, 1.5) node[nboule] {};
\path ( 6.75, 1.5) node[bboule] {};
\path ( 7.00, 1.5) node[rboule] {};
\path ( 7.25, 1.5) node[rboule] {};
\path ( 7.50, 1.5) node[rboule] {};
\path ( 7.75, 1.5) node[rboule] {};
\path ( 8.00, 1.5) node[bboule] {};
\path ( 8.25, 1.5) node[bboule] {};
\path ( 8.50, 1.5) node[gboule] (b4) {};
%
% bootstrap N
\path ( 3.75, 0.5) node[nboule] {};
\path ( 4.00, 0.5) node[gboule] {};
\path ( 4.25, 0.5) node[rboule] {};
\path ( 4.50, 0.5) node[rboule] {};
\path ( 4.75, 0.5) node[bboule] {};
\path ( 5.00, 0.5) node[rboule] {};
\path ( 5.25, 0.5) node[bboule] {};
\path ( 5.50, 0.5) node[gboule] {};
\path ( 5.75, 0.5) node[bboule] {};
\path ( 6.00, 0.5) node[bboule] {};
\path ( 6.25, 0.5) node[gboule] {};
\path ( 6.50, 0.5) node[rboule] {};
\path ( 6.75, 0.5) node[rboule] {};
\path ( 7.00, 0.5) node[gboule] {};
\path ( 7.25, 0.5) node[bboule] {};
\path ( 7.50, 0.5) node[bboule] {};
\path ( 7.75, 0.5) node[bboule] {};
\path ( 8.00, 0.5) node[rboule] {};
\path ( 8.25, 0.5) node[bboule] {};
\path ( 8.50, 0.5) node[gboule] (bN) {};

% arrows
\path[sample] (j20.east) edge [out=0, in=60] (b1.east);
\path[sample] (j20.east) edge [out=0, in=60] (b2.east);
\path[sample] (j20.east) edge [out=0, in=60] (b3.east);
\path[sample] (j20.east) edge [out=0, in=60] (b4.east);
\path[sample] (j20.east) edge [out=0, in=60] (bN.east);

\end{tikzpicture}

\end{center}

\vspace{\baselineskip}

\begin{center}

\begin{tikzpicture}

\definecolor{monred}{rgb}{0.79 0.0 0.1}
%
\tikzstyle{rec} = [rectangle,rounded corners,ultra thick,draw=monred!90,fill=white] 
%
\node[rec,text=black!80,inner sep=3mm,drop shadow] (th)
	{\parbox{0.6\textwidth}{
	When N tend to infinity, the distribution of average values computed from bootstrap samples
	is equal to the distribution of average values obtained from ALL samples with N elements
	which can be constructed from the complete space. Thus the width of the distribution gives
	an evaluation of the sample quality.}};
%
\node[rec,text=monred!95,anchor=south west,xshift=3mm,yshift=-1mm] 
	at (th.north west) {\small Theorem \scriptsize (B. Efron, Ann. Statist. 1979)};

\end{tikzpicture}

\end{center}

\end{document}
```


## For each method
```
% Author: Robert Felty
% Source: http://blog.robfelty.com/2007/02/14/pgf-gallery
% Model structure from Rumelhart \& McClelland (1986, p .222)%

\documentclass{article}
\usepackage{tikz}
\usetikzlibrary{arrows}
\begin{document}

% Declare layers
\pgfdeclarelayer{background}
\pgfsetlayers{background,main}

% Styles
\tikzstyle{information text}=[text badly centered,font=\small,text width=3cm]
\begin{tikzpicture}[scale=.8,cap=round]
    % The graphic
    \begin{scope}[>=stealth', line width=1pt]
        \draw[->] (1,.9) node[below, information text]
            {Phonological representation of root form } -- (1,1.8);
        \draw[->] (5,-.2) node[below,information text]
            {Wickelfeature representation of root form } -- (5,.8);
        \draw[->] (11,-.2) node[below,information text]
            {Wickelfeature representation of past tense } -- (11,.8);
        \draw[->] (16,0.9) node[below,information text]
            {Phonological representation of past tense } -- (16,1.8);
    \end{scope}
    \draw (3,6) node[information text] { Fixed Encoding Network };
    \draw (8,6) node[information text, text width=4cm, ]
        { Pattern Associator Modifiable Connections };
    \draw (13.5,6) node[information text] { Decoding/Binding Network };
    % draw the nodes
    \foreach \x in {1,16}
        \foreach \y in {2,3,4} {
        \filldraw[fill=white] (\x,\y) circle (0.1);
        }
    \foreach \x in {5,11}
        \foreach \y in {1,2,3,4,5} {
            \filldraw[fill=white] (\x,\y) circle (0.1);
        }
    % The lines connecting the nodes are drawn in the background layer.
    % This way we can hide the lines behind the nodes and don't worry
    % about the width of each node.    
    \begin{pgfonlayer}{background}
        % we add the lines for the nodes starting in y 2,3, and 4
        \foreach \xa / \xb in {1 / 5, 5 / 11 , 11 / 5 , 16 / 11}
            \foreach \ya / \yb / \yc / \yd / \ye in {2 / 3 / 4 / 5 / 1, 
            3 / 4 / 5 / 1 / 2, 4 / 5 / 1 / 2 / 3} {
                \draw (\xa,\ya) -- (\xb,\ya);
                \draw (\xa,\ya) -- (\xb,\yb);
                \draw (\xa,\ya) -- (\xb,\yc);
                \draw (\xa,\ya) -- (\xb,\yd);
                \draw (\xa,\ya) -- (\xb,\ye);
            }
        % add remaining lines from y1 to y5
        \foreach \xa / \xb in {5 / 11 , 11 / 5}
            \foreach \ya / \yb in {1 / 5, 5 / 1} {
            \draw (\xa,\ya) -- (\xb,\ya);
            \draw (\xa,\ya) -- (\xb,\yb);
        }
    \end{pgfonlayer}
\end{tikzpicture}

\end{document}
```


## Nested blocks
```
\documentclass{article}

\usepackage{tikz}
\usetikzlibrary{shapes,arrows}
\usepackage{amsmath,bm,times}
\newcommand{\mx}[1]{\mathbf{\bm{#1}}} % Matrix command
\newcommand{\vc}[1]{\mathbf{\bm{#1}}} % Vector command

\begin{document}
\pagestyle{empty}

% We need layers to draw the block diagram
\pgfdeclarelayer{background}
\pgfdeclarelayer{foreground}
\pgfsetlayers{background,main,foreground}
%
%% Define a few styles and constants
\tikzstyle{sensor}=[draw, fill=blue!20, text width=5em, 
    text centered, minimum height=2.5em]
\tikzstyle{ann} = [above, text width=5em]
\tikzstyle{naveqs} = [sensor, text width=6em, fill=red!20, 
    minimum height=12em, rounded corners]
\def\blockdist{2.3}
\def\edgedist{2.5}
%
\begin{tikzpicture}
    \node (naveq) [naveqs] {Navigation equations};
    % Note the use of \path instead of \node at ... below. 
    \path (naveq.140)+(-\blockdist,0) node (gyros) [sensor] {Gyros};
    \path (naveq.-150)+(-\blockdist,0) node (accel) [sensor] {Accelero-meters};
    
    % Unfortunately we cant use the convenient \path (fromnode) -- (tonode) 
    % syntax here. This is because TikZ draws the path from the node centers
    % and clip the path at the node boundaries. We want horizontal lines, but
    % the sensor and naveq blocks aren't aligned horizontally. Instead we use
    % the line intersection syntax |- to calculate the correct coordinate
    \path [draw, ->] (gyros) -- node [above] {$\vc{\omega}_{ib}^b$} 
        (naveq.west |- gyros) ;
    % We could simply have written (gyros) .. (naveq.140). However, it's
    % best to avoid hard coding coordinates
    \path [draw, ->] (accel) -- node [above] {$\vc{f}^b$} 
        (naveq.west |- accel);
    \node (IMU) [below of=accel] {IMU};
    \path (naveq.south west)+(-0.6,-0.4) node (INS) {INS};
    \draw [->] (naveq.50) -- node [ann] {Velocity } + (\edgedist,0) 
        node[right] {$\vc{v}^l$};
    \draw [->] (naveq.20) -- node [ann] {Attitude} + (\edgedist,0) 
        node[right] { $\mx{R}_l^b$};
    \draw [->] (naveq.-25) -- node [ann] {Horisontal position} + (\edgedist,0)
        node [right] {$\mx{R}_e^l$};
    \draw [->] (naveq.-50) -- node [ann] {Depth} + (\edgedist,0) 
        node[right] {$z$};
%    
    % Now it's time to draw the colored IMU and INS rectangles.
    % To draw them behind the blocks we use pgf layers. This way we  
    % can use the above block coordinates to place the backgrounds   
    \begin{pgfonlayer}{background}
        % Compute a few helper coordinates
        \path (gyros.west |- naveq.north)+(-0.5,0.3) node (a) {};
        \path (INS.south -| naveq.east)+(+0.3,-0.2) node (b) {};
        \path[fill=yellow!20,rounded corners, draw=black!50, dashed]
            (a) rectangle (b);
        \path (gyros.north west)+(-0.2,0.2) node (a) {};
        \path (IMU.south -| gyros.east)+(+0.2,-0.2) node (b) {};
        \path[fill=blue!10,rounded corners, draw=black!50, dashed]
            (a) rectangle (b);
    \end{pgfonlayer}
\end{tikzpicture}


\end{document}
```
