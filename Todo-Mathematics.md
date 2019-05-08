# Mathematics
[wiki](https://en.wikibooks.org/wiki/LaTeX/Mathematics)

[User’s Guide for the amsmath Package](http://texdoc.net/texmf-dist/doc/latex/amsmath/amsldoc.pdf)

## math formulae
There are three environment that put Latex in math mode
```

math	                   # For Formulae that appear right in the text
displaymath	           # For Formulae that appear on their own line.
equation	           # The same as the displaymath environment 
                             except that it adds an equation number in the right margin.
```
The following short form is as follows. Both displaymath and equation are used only in paragraph mode
```
\(...\)     instead of     \begin{math}...\end{math}
```
```
\[...\]     instead of     \begin{displaymath}...\end{displaymath}
```
In fact, the math environment is so common that it has an even shorter form:
```
$ ... $     instead of     \(...\)
```

```
Subscripts & Superscripts                   # Also known as exponent or index.  _ and ^
Math Symbols                                # Various mathematical squiggles.
Spacing in Math Mode                        # Thick, medium, thin and negative spaces.
Math Miscellany                             # Stuff that doesn't fit anywhere else.
```
LaTeX provides the following four commands for use in math mode
```
\; - a thick space
\: - a medium space
\, - a thin space
\! - a negative thin space
```
```

\cdots	            # Produces a horizontal ellipsis where 
                      the dots are raised to the centre of the line.
\ddots	            # Produces a diagonal ellipsis.
\frac{num}{den}	    # Produces the fraction num divided by den.
\ldots	            # Produces an ellipsis. 
                      This command works in any mode, not just math mode.
\overbrace{text}    # Generates a brace over text.
\overline{text}	    # Causes the argument text to be overlined.
\sqrt[root]{arg}    # Produces the square root of its argument. 
                      The optional argument, root, determines what root to produce, i.e., 
		      the cube root of x+y would be typed as $\sqrt[3]{x+y}$.

\underbrace{text}   # Generates text with a brace underneath.
\underline{text}    # Causes the argument text to be underlined. 
                      This command can also be used in paragraph and LR modes.
\vdots	            # Produces a vertical ellipsis.
```

## Matrix
```
\begin{matrix}
\begin{pmatrix}             # paraphasis
\begin{bmatrix}
\begin{vmatrix}
\begin{Vmatrix}
```
