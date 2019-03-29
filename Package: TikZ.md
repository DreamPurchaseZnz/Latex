# A very minimal introduction to TikZ

## Introduction

At least 70% of the figures found in the economic literature can be drawn with the commands I present here.


## Setup a picture
When you want to do a picture, just write it as 
```
\usepackage{tikz}                    # in the preamble
\begin{tikzpicture}
  code
\end{tikzpicture}
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

## Draw lines and curves
### simple straight lines
by default, coordinates are in centimeters
To draw a line
```
\draw (0,0) --(1,2);                    # draws a line between the points (0,0) and (1,2)
\draw (0,0) --(1,2) -- (2,3) -- (1,0);

```
You can put several lines on the same graph
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
You have direct access to the following colors: red, green, blue, cyan, magenta, yellow, black, gray, darkgray, lightgray, brown, lime,
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

```


## Putting labels in pictures


## Integration with Beamer


## Hints and tricks


## Examples



## Conclusion
