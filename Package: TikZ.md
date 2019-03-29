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



## Filling up areas


## Putting labels in pictures


## Integration with Beamer


## Hints and tricks


## Examples



## Conclusion
