# Some common usages

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
