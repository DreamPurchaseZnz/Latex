# TikZ

[A very minimal introduction to TikZ-NP:26](https://cremeronline.com/LaTeX/minimaltikz.pdf)

[tikzpgfmanual-NP:405](https://www.bu.edu/math/files/2013/08/tikzpgfmanual.pdf)

## Introduction

At least 70% of the figures found in the economic literature can be drawn with the commands I present here.


## Setup a picture
Load the tikz package
```
\usepackage{tikz}
```
Load the tikz libraries of your own choice
```
\usetikzlibrary{list of libraries}
```
Examples for libraries are
```
 "arrows", "automata", "backgrounds", 
 "calendar", "chains", "matrix",
 "mindmap", "patterns", "petri", 
 "shadows", "shapes.geometric", 
 "shapes.misc", "spy", "trees".                                   
```

Start drawing
```
\begin{tikzpicture} [options]
instructions
\end{tikzpicture}
```
or 
```
\tikz [option] {tikz commands}
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
## Basics 
basic elements are paths and nodes

-Path
```
\path [option] specifications
```
Abbrevaitions
```
\draw = \path [draw]
\fill = \path [fill]
\shade = \path [shade]
etc.
```
-Node: typically a rectangle or circle or another simple shape with some text
or even with text only.

```
\node [options](name){text}
```


## Draw lines and curves
### simple straight lines
by default, coordinates are in centimeters
To draw a line
```
\draw (0,0) --(1,2);                    # draws a line between the points (0,0) and (1,2)
\draw (0,0) --(1,2) -- (2,3) -- (1,0);

```
You can put several lines on the same graph

Notice the semi-colon ";" at end of lines, it is these colons that mark the end of instructions. You can see below examples where one
instruction is spread over several lines without changing the output
```
\draw (0,0) --(1,2) -- (2,3) -- (1,0); \draw (3,0) -- (1.5,0.5);
```


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
The arc is of radius 1, starts at the point (6, 0) leaving it at an angle of 45 degrees and stops when its slope is 120 degrees
```
\draw [gray] (6,0) arc [radius=1, start angle=45, end angle= 120];
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

