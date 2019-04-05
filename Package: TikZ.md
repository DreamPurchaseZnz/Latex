# TikZ

[Tikz help](https://stuff.mit.edu/afs/athena/contrib/tex-contrib/beamer/pgf-1.01/doc/generic/pgf/version-for-tex4ht/en/pgfmanual.html#pgfmanualse30.html)

[A very minimal introduction to TikZ-NP:26](https://cremeronline.com/LaTeX/minimaltikz.pdf)

[tikzpgfmanual-NP:405](https://www.bu.edu/math/files/2013/08/tikzpgfmanual.pdf)

[excellent tutorial](http://www.flutterbys.com.au/stats/tut/tut17.1a.html)

-----------------------------------------------------------------------------------------------------------------------
## Layered Graphics
```
\usepackage{pgfbaselayers} % LATEX
```
This package provides a commands and environment for composing a picture from multiple layers

Fisrtly, declare a new layer except the main layer by default.
```
\pgfdeclarelayer{<name>}
```
Then tell the PGF which layers will be part of the actual picture and which will be their ordering. It is possible to
have more layers declared than are actually used.
```
\pgfsetlayers{<layer list>}
```
for example:
```
\pgfdeclarelayer{background} 
\pgfdeclarelayer{foreground} 
\pgfsetlayers{background,main,foreground}

```
### using the layers
You can use the pgfonlayer environment to tell the PGF that certain command should instead be added to the given layer.
```
\begin{pgfonlayer}{<layer name>}
  <environment contents>
\end{pgfonlayer}
```

You can not add anything to the main layer using this environment


-------------------------------------------------------------------------------------------------------------------------
## Matrix of nodes and alignment
A matrix of nodes is a TikZ matrix in which each cell contains a node, we can load the package
```
\usetikzlibrary{matrix}
```
The matrix have the following syntax
```
\path node[matrix] {}
          \matrix (name) [style] {                  # for short
1) Each row (including the last one) is ended by the command \\
2) The character & is used to seperate cells
3) Inside each cell you must place commands for drawing a picture, which is ended with semicolon ";"
4) It is not necessary to specify beforehand how many rows and columns there are going to be.
}
```
where the style can be
```
matrix of nodes
matrix of math nodes                        # math mode will be switched on in all nodes
nodes in empty cells                        # if True, a node will be put in empty cells.
```

### matrix of nodes
It provides each node in matrix with the specified name, where the name is set to <matrix name>-<row number>-<column number>
```
\begin{tikzpicture}
\matrix (magic) [matrix of nodes]
	{
	8 & 1 & 6 \\
	3 & 5 & 7 \\
	4 & 9 & 2 \\
	};
	\draw[thick,red,->] (magic-1-1) |- (magic-2-3);       # node name
\end{tikzpicture}
```
You may wish to add options to certain nodes in the matrix, this can be achieved in three ways
- Fisrt method
```
\tikzstyle{row 2 column 3}=[red]                             # use the tikzstyle
\matrix [matrix of nodes]
{
8 & 1 & 6 \\
3 & 5 & 7 \\
4 & 9 & 2 \\
};	
```
- Special syntax

```
\begin{tikzpicture}
\matrix [matrix of nodes]
{
8 & 1 & 6 \\
3 & 5 & |[red]| 7 \\              # if a cell start with a vertical bar
                                    then everything between this bar and the next bar 
				    is passed on the node command
4 & 9 & 2 \\
};
\end{tikzpicture}
```
Note that the & character alse takes an optional argument, which is an exra column skip

```
\begin{tikzpicture}
\matrix [matrix of nodes]
{
8 &[1cm] 1 &[3mm] |[red]| 6 \\
3 & 5 & |[red]| 7 \\
4 & 9 & 2 \\
};
\end{tikzpicture}
```

- Rewrite the \node 
```
\begin{tikzpicture}
\matrix [matrix of nodes]
{
8 & 1 & 6 \\
3 & 5 & \node[red]{7}; \draw(0,0) circle(10pt);\\
4 & 9 & 2 \\
};
\end{tikzpicture}
```
### Matrix options
Setting and Adjusting Column and Row Spacing

```
every matrix/.style
every cell
cells
nodes                                   # this option adds the option to "every node"
column sep=<spacing list>                
row sep
colunm <number>                         # Used for every cell in column <number>
every odd column
every even column
row
every odd row
every even row
row <row number> column <number>
execute at end cell
execute at begin cell
execute at empty cell
matrix anchor
anchor

ampersand replacement                  # column seperator setting
```

```
\begin{tikzpicture}
\matrix [nodes={fill=blue!20,minimum size=5mm}]
{
\node {8}; & \node{1}; & \node {6}; \\
\node {3}; & \node{5}; & \node {7}; \\
\node {4}; & \node{9}; & \node {2}; \\
};
\end{tikzpicture}
```




-------------------------------------------------------------------------------------------------------------------------

## Introduction

At least 70% of the figures found in the economic literature can be drawn with the commands I present here.


## Load package
Load the tikz package
```
\documentclass{standalone}
\usepackage{tikz}
```
Load the tikz libraries of your own choice
```
\usetikzlibrary{list of libraries}
```
Examples for libraries are
```
 "arrows",              # for example use the arrow head type, >=stealth                     
 "Positioning"          # for example the syntax: right=4pt of node name, compared with 
                                                  right of = node name
 "automata",
 "backgrounds", 
 "calendar", 
 "chains", 
 "matrix",
 "mindmap", 
 "patterns", 
 "petri", 
 "shadows", 
 "shapes.geometric", 
 "shapes.misc",
 "spy", "trees".                                   
```
## Get a canvas
The basic structure of tikzpicture enviroment is as follows:
```
\begin{tikzpicture} [options]
instructions
\end{tikzpicture}
```
or 
```
\tikz [option] {tikz commands}
```
There are approximately 750 options that can be applied to graphical elements 

Some of the commen options that are applied at the environment level so that they can affect all elements therein 
```
scale=(factor)                     # Rescaling the graphic by X
xscale, yscale
```

If you want to apply the float format, you can set it up as
```
\begin{figure}
	\begin{tikzpicture}
		code
	\end{tikzpicture}
	\caption{Title}
\end{figure}
```
### about the options
In my opinions, the options is equal to .style. And the style file is similar to the enviroment of variables, where we can refer some instructions. There are there feasible way to define such a enviroment
- firstly, we can dirctly define the tikzpicture option
```
\begin{tikzpicture}[
	state/.style={
	rectangle,
	rounded corners,
	draw=black, very thick,
	minimum height=2cm,
	inner sep= 0.5cm,
	text centered]
\end{tikzpicture}
```
- Secondly use the \tikzset
```
\tikzset{
	state/.style={
	rectangle,
	rounded corners,
	draw=black, very thick,
	minimum height=2cm,
	inner sep= 0.5cm,
	text centered
}}
```
- Thirdly use the \tikzstyle
```
\tikzstyle
```

Notice that we must take care to name a new instruction. Or it will conflict with the current instruction exist in the environment.
``` 
\tikzset{
out/.style={thick, circle},}
```
The system will throw you a error, the key requires a value. It means the out is a key of the current instruction.

## Coordinates
```
Cartesian:(x,y)
Polar:(length, angle)
```
### relative coordinates
Coordinates relative to the precious position can be specified 
by appending either "++"(incremental) or "+"(non-incremental) before brackets
```
++(x,y)                       # Update the reference point with the current point
+(x,y)                        # Donnot send the new reference location as the current point
```

## Basics elements 
basic elements are paths and nodes

### Path 
Path is a series of line segments between coordinates and by default a path is invisible

```
\path [option] specifications
```
Abbrevaitions
```
\draw = \path [draw]
\fill = \path [fill]
\shade = \path [shade]
\pattern = \path[pattern]
```
Options can be as follows: 

#### Geometric Actions
```
rotate
xshift
yshift
scaling
xscale
yscale
```
#### Color
```
draw
fill
color-color
opacity
```
#### line width
```
line width
= ultra thin,
very thin
thin
semithick
thick
very thick
ultra thick
```
####  line sype
```
solid
dashed
dotted
dashdotted
densely dotted
loosely dotted
double
dash phase = phase
dash pattern = <pattern>
```
####  Arrow heads and tails
```
->
-stealth
-latex
```
#### round corners


### Node
A node is a text element placed at a coordinate and 
optionally may have a simple shape (such as a rectangle or circle or elipse) drawn around it

By default, the shape around a node is stretched such that it just slightly bigger than the contents.
A node has a number of anchors as well as a label that can be used to refer to the node (or any of its anchors).

A node have the following syntax
```
\node [options](name){text}                 
```
where the name is the node's label and the optional text is the text elment to be appear at the node

Nodes can be also defined along path/line by using the node operator
```
begin{tikzpicture}
draw [help lines] (-2,-2) grid (2,2);
path [draw] (-1,1) node (NodeA) {Node A} --
	(1,-1) node (NodeB) {Node B} -- (-1,-1.5);
end{tikzpicture}
```
#### option-shapes
```
rectangle
circle
elipse
diamond
cyclinder
cloud
signal
cloud callout
rectangle callout
rounded rectangle
```
#### seperation 
```
inner sep=<>
outer sep=dimension
```
```
\node [draw,inner sep=10pt] at (1,-1) (NodeB) {Node B};
\node [draw,outer sep=5pt] at (1,-1) (NodeB) {Node B};
```
#### anchor location
```
anchor= <direction> where directions is one of 
north
west
east
south
or combination
```
```
<direction>= of <node>
where direction is one of "above", "below", "left", "right" or a combination
```
```
\draw [help lines] (-2,-2) grid (2,2);
  \node [draw] at (-1,1) (NodeA) {Node A};
  \node [draw] at (-1,1.5) (NodeA) {Node A};
  \node [draw,right=1pt of NodeA] (NodeB) {Node B};
  \node [draw,node distance=1pt,below=of NodeA] (NodeC) {Node C};
  \node [draw] at (-1,0) (NodeC) {Node C};
  \node [draw,below right=1pt of NodeC,anchor=west]  (NodeD) {Node D};
  \node [draw] at (-1,-1) (NodeE) {Node E};
  \node [draw,anchor=west] at (NodeE.east)  (NodeF) {Node F};
```
#### Minimum height and/or width
```
minimum size=<dimension>, 
minimum width=<dimension>, 
minimum height=<dimension>
```
This provides a way of ensuring that the size of the node is not solely dependent on the size of the node contents.

### Continously draw node
```
\draw 
node at (0,0)[right=-3mm]{a}
node [input, name=input1] {b} 
node [sum, right of=input1] (suma1) {c}
node [block, right of=suma1] (inte1) {d}
node at (6.8,0)[block] (Q1) {e}
node [block, below of=inte1] (ret1) {f};
```

## Draw lines and curves

There are three way to connect the nodes 
```
1) --                  # Line-to operations 
2) to 
3) edge                # If many edge operation in a row, the start coordinate keep same
4) ..control (x,y)..   # Curve to operation
```
**The line-to operation** extends the current path from the current point in a straight line to the given
coordinate. 
The “current point” is the endpoint of the previous drawing operation or the point specified
by a prior move-to operation.
```
\path     --                     # two minus sign
\path     -|                     # first horizontal, then vertical
\path     |-
```
```
\begin{tikzpicture}[line width=10pt]
\draw (0,0) --(1,1) (1,1) --(2,0);
\draw (3,0) -- (4,1) -- (5,0);
\useasboundingbox (0,1.5); % make bounding box higher
\end{tikzpicture}
```
**The curve-to operation** allow you extend a path using Bezier curve
```
\path ...  ..controls<c> and <d>..                # two control point
```

**The edge operation** works like a to operation that is added after the main path have been drawn, much like a node is added after the main path have drawn.
It's syntax
```
\path .... edge [<option>] <nodes>.... 
```

if there are several edge operation in a row, the start coordinate is the same for all of them 
as their target coordinates are not.
```
\begin{tikzpicture}
	\foreach \name/\angle in {a/0,b/90,c/180,d/270}
		\node (\name) at (\angle:1.5) {$\name$};
	\path[->] (b) edge node[above right] {$5$} (a)
		      edge (c)
	   	      edge [-,dotted] node[below,sloped] {missing} (d)
		  (c) edge (a)
		      edge (d)
		  (d) edge [red] node[above,sloped] {very}
		     		 node[below,sloped] {bad} (a);
\end{tikzpicture}
```




### simple straight lines
by default, coordinates are in centimeters

Lines can be drawn by either using the draw path option or the \draw keyword.
```
draw [help lines] (-2,-2) grid (2,2)
\draw (0,0) --(1,2);                    # draws a line between the points (0,0) and (1,2)
\draw (0,0) --(1,2) -- (2,3) -- (1,0);
```
A path can be closed with operation
```
-- cycle 
```

Points can be connected by an "elbow" including only a horizontal and vertical line rather than a single straight line.
```
draw (-1.5,2) |- (0.0,-0.5);
draw (-1,0.8) -| (1.5,-1.5);
```

### Bezier curved paths/lines
Bezier curves are specified by including operation between points
```
.. control(x,y)..              # the coordination of control define the Bezier Curves handles
```
```
 \begin{tikzpicture}
  \draw [help lines] (-2,-2) grid (2,2);
  \draw (-1.5,0) .. controls (-1,1) .. (1,-0);
  \draw (-1.5,-0.5) .. controls (-1,-1) and (0,-1) .. (1,-0.5);
  \end{tikzpicture}
```

You can put several lines on the same graph

Notice the semi-colon ";" at end of lines, it is these colons that mark the end of instructions. You can see below examples where one
instruction is spread over several lines without changing the output
```
\draw (0,0) --(1,2) -- (2,3) -- (1,0); \draw (3,0) -- (1.5,0.5);
```
### other curves
It also possible to create parabola curved paths/lines by
```
(in,out) looseness
(in,out) (min,max) distance
(in,out) control
```
Exit and entry angles can be repectively defined by the out and in options.

Also 
```
bend right/left
```
indicate the direction and the angle of a bend in a path or line.

### scaling picutres
You can blow up the picture, by adding an option "scale" to the environment
```
\begin{tikzpicture}[scale=3]
\draw (0, 0) -- (1, 2) 
\end{tikzpicture}
```
you can scale only one dimension
```
[xscale=1, yscale=0.5]
```
### Arrows and the like
You can decorate the lines.

We can put the arrows or bars on one or both extremities
```
\draw [->] (0,0) -- (2,0);
\draw [<-] (0, -0.5) -- (2,-0.5);
\draw [|->] (0,-1) -- (2,-1);
```
When we draw several segments, the arrows are placed at the extremities of the first and the last segments.
```
\draw [<->] (0,2) -- (0,0) -- (3,0);
\end{tikzpicture}
```
### change the thickness of lines
Other decoration include changing the thickness
```
\draw [ultra thick] (0,1) -- (2,1);
\draw [thick] (0,0.5) -- (2,0.5);
\draw [thin] (0,0) -- (2,0);
```
You can use: ultra thin, very thin, thin, semithick, thick, very thick and ultra thick, also, you can use custom widths
```
\draw [line width=12] (0,0) -- (2,0);
\draw [line width=0.2cm] (4,.75) -- (5,.25);
```
### Dashes and dots
You can also make dotted and dashed lines
```
\draw [dashed, ultra thick] (0,1) -- (2,1);
\draw [dashed] (0, 0.5) -- (2,0.5);
\draw [dotted] (0,0) -- (2,0);
```
### Colors
And finally you can color you line
```
\draw [gray] (0,1) -- (2,1);
\draw [red] (0, 0.5) -- (2,0.5);
\draw [blue] (0,0) -- (2,0);
```
You have direct access to the following colors: red, green, blue, cyan, magenta, yellow, black, gray, darkgray, 
lightgray, brown, lime,
olive, orange, pink, purple, teal, violet, and white. And you can define the colors.

### Pictures in the middle of the text
```
wherever \begin{tikzpicture} \draw [yellow, line width=6]
(0,0) -- (.5,0); \end{tikzpicture} you want
```

### Curves
You are not limited to straight lines
```
\begin{tikzpicture}
\draw [blue] (0,0) rectangle (1.5,1);
\draw [red, ultra thick] (3,0.5) circle [radius=0.5];;
\end{tikzpicture}
```
##### Arc paths/lines
An arc is defined by three parameters separated by colons
```
(out angle;in angle;radius length)
```
```
\draw [gray] (6,0) arc [radius=1, start angle=45, end angle= 120];
draw [help lines] (-2,-2) grid (2,2);
draw (-1.5,0.5) arc (10:300:-0.75cm);
draw (-1.5,-1) arc (10:300:-0.75cm and 0.75cm);             # collapse
draw (0,0) arc (10:300:-1cm and -0.5cm);

```

If you want a precise curve you can do it by computing lots of points in program such as Mathematica and putting them in TikZ.
```
\draw[orange] (0.6, 1.0385) --
(0.61, 1.06372) -- (0.62, 1.08756) -- (0.63, 1.11012) -- (0.64,......
```
There are a number of ways by which you can do curves without plotting all the points
```
\draw[very thick] (0,0) to [out=90,in=195] (2,1.5);
```
Note that I had to replace the "-" by "to", notice how the angles work:

- when the curve goes out of (0, 0), you put a needle with one extremity on the starting point and the other one facing right and you
  turn it counterclockwise until it is the tangent to the curve.

You can put several instructions in the same TikZ instruction.
```
\draw [<->,thick, cyan] (0,0) to [out=90,in=180] (1,1)
to [out=0,in=180] (2.5,0) to [out=0,in=-135] (4,1) ;
```

### Ploting functions
TikZ also have a math engine which enable you to plot functions
```
\draw [domain] plot (\x, {function})              # brace around the function
```
```
\begin{tikzpicture}[xscale=13,yscale=3.8]
\draw [<->] (0,0.8) -- (0,0) -- (0.5,0);
\draw[green, ultra thick, domain=0:0.5] plot (\x, {0.025+\x+\x*\x});
\end{tikzpicture}
```
Many mathematical functions are possible, you will probably have enough with 
```
factorial(\x), 
sqrt(\x), 
pow(\x, y), exp(\x), ln(\x),
log10(\x), log2(\x), abs(\x)
mod(\x,y),round(\x), floor(\x), ceil(\x)
sin(\x)                                       # it assumes that x is in degrees
sin(\x r)                                     # x is expressed in radians
cos(\x)
min(\x, y)
```
In mathematical expression the following variables can be useful: e, which is equal to 2.718 and pi which is equal to 3.14
```
\draw [help lines, <->] (0,0) -- (6.5,0);
\draw [help lines, ->] (0,-1.1) -- (0,1.1);
\draw [green,domain=0:2*pi] plot (\x, {(sin(\x r)* ln(\x+1))/2});
\draw [red,domain=0:pi] plot (\x, {sin(\x r)});
\draw [blue, domain=pi:2*pi] plot (\x, {cos(\x r)*exp(\x/exp(2*pi))});
```

## Filling up areas
### Fill up simple area
You can also fill paths when they are closed
```
\draw [fill=red,ultra thick] (0,0) rectangle (1,1);
\draw [fill=red,ultra thick,red] (2,0) rectangle (3,1);                    # draw a line around shape in red
\draw [blue, fill=blue] (4,0) -- (5,1) -- (4.75,0.15) -- (4,0);
\draw [fill] (7,0.5) circle [radius=0.1];
\draw [fill=orange] (9,0) rectangle (11,1);
\draw [fill=white] (9.25,0.25) rectangle (10,1.5);
```
if you don't want to see the outline at all, replace the \draw by \path
```
\path [fill=gray] (0,0) rectangle (1.5, 1)
\draw [fill=yellow] (2, 0) rectangle (3,3)
```
### Filling up a arbitrary areas
```
\draw [ultra thick] (0,0) to [out=87,in=150] (1,1) -- (.85,.15) -- (0,0);
\draw [ultra thick, fill=purple] (2,0) to [out=87,in=150] (3,1) -- (2.85,.15) -- (2,0);
\path [fill=purple] (4,0) to [out=87,in=150] (5,1) -- (4.85,.15) -- (4,0);
```

## Putting labels in pictures
```
\node[option] (node name) at (x,y) {Tex content of node}
\path (x,y) node [option] (node name) {Tex content of node}
```
When you do a picture, in 99% of cases you also need to put labels, Let's start by seeing how we would place some text in the pic
```
\begin{tikzpicture}
\draw [thick, <->] (0,2) -- (0,0) -- (2,0);
\node at (1,1) {yes};                         # Notice how the "yes" is positioned; 
                                                the center of its "baseline" is at (1,1)                      
\end{tikzpicture}
```

Sometime you want a label to be situated relative to a point, TkiZ has neat commands for this.
```
\draw [thick, <->] (0,2) -- (0,0) -- (2,0);
\draw[fill] (1,1) circle [radius=0.025];
\node [below] at (1,1) {below};
\node [above] at (1,1) {above};
\node [left] at (1,1) {left};
\node [right] at (1,1) {right};
```
And also you can mix and match
```
\draw [thick, <->] (0,1) -- (0,0) -- (1,0);
\draw[fill] (1,1) circle [radius=0.025];
\node [below right, red] at (.5,.75) {below right};
\node [above left, green] at (.5,.75) {above left};
\node [below left, purple] at (.5,.75) {below left};
\node [above right, magenta] at (.5,.75) {above right};
```
This makes it possible to label axes and points
```
\draw [thick, <->] (0,1) -- (0,0) -- (1,0);
\node [below right] at (1,0) {$x$};
\node [left] at (0,1) {$y$};
\draw[fill] (.4,.6) circle [radius=.5pt];
\node[above right] (.4,.6) {$A$};
```
You can avoid some typing by mixing nodes in the middle of paths
```
\draw [thick, <->] (0,1) node [left] {$y$} -- (0,0) -- (1,0) node [below right] {$x$};
\draw[fill] (.4,.6) circle [radius=.5pt] node[above right] (.4,.6) {$A$};
```
The above two code segment have given the same result. Note that the node is put after the point to which it is attached 
and that we suppress the \ in \node

Sometime you may want to put a whole text several lines in your nodes, that can be done by using the standard Latex \\ for indicating
a new line but you much tell Tikz how to align things
```
\begin{tikzpicture}[xscale=1.3]
\draw [thick] (0,0) -- (9,0);
\draw (0,-.2) -- (0, .2);
\draw (3,-.2) -- (3, .2);
\draw (6,-.2) -- (6, .2);
\draw (9,-.2) -- (9, .2);
\node[align=left, below] at (1.5,-.5)%
{This happens\\in period 1\\and is aligned\\ left};
\node[align=center, below] at (4.5,-.5)%
{This happens\\in period 2\\and is centered};
\node[align=right, below] at (7.5,-.5)%
{This happens\\in period 2\\and is right\\aligned};
\end{tikzpicture}
```

## Integration with Beamer
TikZ works very well with Beamer (They are written by the same person). In particular, it is very easy to uncover figures processively
```
\begin{frame}
a few lines
\begin{center}
\begin{tikzpicture}
\draw [blue, ultra thick] (-1,2) -- (6,3);
\uncover<1>{\draw [green,thick] (-4,3) -- (2,2.5);}
\uncover<2>{\draw [red,thick] (0,0) -- (0,5);}
\end{tikzpicture}
\end{center}
and something under.
\end{frame}
```
## Hints and tricks

- It takes some time to draw figures, and it is normal to make mistakes. Proceed by trial and error, compiling your code often

## Examples
```
% EPC flow charts
% Author: Fabian Schuh
\documentclass{minimal}

\usepackage{pgf}
\usepackage{tikz}
\usepackage[utf8]{inputenc}
\usetikzlibrary{arrows,automata}
\usetikzlibrary{positioning}


\tikzset{
	state/.style={
		rectangle,
		rounded corners,
		draw=black, very thick,
		minimum height=2em,
		inner sep=2pt,
		text centered,
	},
}

\begin{document}

	\begin{tikzpicture}[->,>=stealth']
	
	% Position of QUERY 
	% Use previously defined 'state' as layout (see above)
	% use tabular for content to get columns/rows
	% parbox to limit width of the listing
	\draw[help lines] (-3, -8) grid (10, 8);
	
	
	\node[state] (QUERY) 
	{\begin{tabular}{l}
		\textbf{Query}\\
		\parbox{4cm}{\begin{itemize}
			\item Start
			\item Parameter $Q$
			\item Zufallszahl aus \mbox{$[0, 2^Q-1]$} in Slotzähler $SC$
			\end{itemize}
		}\\[4em]
		\textbf{QueryAdjust}\\
		\parbox{4cm}{\begin{itemize}
			\item Variiere Q
			\item neue Zufallszahl
			\end{itemize}
		}
		\end{tabular}};
	
	% State: ACK with different content
	\node[state,    	% layout (defined above)
	text width=3cm, 	% max text width
	yshift=2cm, 		% move 2cm in y
	right of=QUERY, 	% Position is to the right of QUERY
	node distance=6.5cm, 	% distance to QUERY
	anchor=center] (ACK) 	% posistion relative to the center of the 'box'
	{%
		\begin{tabular}{l} 	% content
		\textbf{Ack}\\
		\parbox{2.8cm}{Bestätigen mit $RN_{16}$}
		\end{tabular}
	};
	
	% STATE QUERYREP
	\node[state,
	below of=ACK,
	yshift=-2cm,
	anchor=center,
	text width=3cm] (QUERYREP) 
	{%
		\begin{tabular}{l}
		\textbf{QueryRep}\\
		\parbox{2.8cm}{Dekrementiere Slotzähler}
		\end{tabular}
	};
	
	% STATE EPC
	\node[state,
	right of=ACK,
	node distance=5cm,
	anchor=center] (EPC) 
	{%
		\begin{tabular}{l}
		Antwort: \textbf{EPC}\\
		\parbox{4cm}{Mit nächstem \mbox{\textbf{QueryRep}} als "`inventoried"' markieren.}
		\end{tabular}
	};
	
	% draw the paths and and print some Text below/above the graph
	\path (QUERY) 	edge[bend left=20]  node[anchor=east,above]{$SC_n=0$}
	node[anchor=north,below]{$RN_{16}$} (ACK)
	(QUERY)     	edge[bend right=20] node[anchor=south,above]{$SC_n\neq 0$} (QUERYREP)
	(ACK)       	edge                                                     (EPC)
	(EPC)       	edge[bend left]                                          (QUERYREP)
	(QUERYREP)  	edge[loop below]    node[anchor=south,below]{$SC_n\neq 0$} (QUERYREP)
	(QUERYREP)  	edge                node[anchor=left,right]{$SC_n = 0$} (ACK);
	
	\end{tikzpicture}
\end{document}
```



