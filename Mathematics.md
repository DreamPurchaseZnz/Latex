# Mathematics
## List of LaTeX symbols
[List of LaTeX symbols](https://latex.wikia.org/wiki/List_of_LaTeX_symbols)

LaTeX symbols have either names (denoted by backslash) or special characters. They are organized into seven classes based on their role in a mathematical expression. This is not a comprehensive list. Refer to the external references at the end of this article for more information

#### Class 0 (Ord) symbols: Simple / ordinary ("noun")
Latin letters and Arabic numerals

#### Class 1 (Op) symbols: prefix operator (extensible)

Named operators: sin, cos, etc.Edit
If your favorite operator, say, "foo", isn't listed, then you won't be able to use \foo(x) in your LaTeX equation. But don't fret. You can get the same result with 
```
\operatorname{foo}(x)
```
If your made-up operator needs displayed limits, as in \lim or \max, then use 
```
\operatorname*{foo}
```
as in the example in the following table.

```
\operatorname{foo}_0^1
```

#### Class 2 (Bin) symbols: binary operator ("conjunction")
```
+ - x /
```
#### Class 3 (Rel) symbols: relation / comparison ("verb")
<, =, >, and variants

#### Class 4 (open; left) and class 5 (close; right) symbols (extensible)

#### Class 6 (Pun) symbols: postfix / punctuation

## Aligning equations with amsmath
The amsmath package provides a handful of options for displaying equations. You can choose the layout that better suits your document, even if the equations are really long, or if you have to include several equations in the same line.
### writing a single equation

To display a single equation, as mentioned in the introduction, you have to use the equation* or equation environment, depending on whether you want the equation to be numbered or not. Additionally, you might add a label for future reference within the document.
```
\begin{equation} \label{eu_eqn}
e^{\pi i} + 1 = 0
\end{equation}
 
The beautiful equation \ref{eu_eqn} is known as the Euler equation
```
### displaying long equations

For equations longer than a line use the multline environment. Insert a double backslash to set a point for the equation to be broken. The first part will be aligned to the left and the second part will be displayed in the next line and aligned to the right.

Again, the use of an asterisk * in the environment name determines whether the equation is numbered or not.
```
\begin{multline*}
p(x) = 3x^6 + 14x^5y + 590x^4y^2 + 19x^3y^3\\ 
- 12x^2y^4 - 12xy^5 + 2y^6 - a^3b^3
\end{multline*}
```
### splitting and aligning an equation
Split is very similar to multline. Use the split environment to break an equation and to align it in columns, just as if the parts of the equation were in a table. This environment must be used inside an equation environment. For an example check the introduction of this document.
```
\begin{align*} 
2x - 5y &=  8 \\ 
3x + 9y &=  -12
\end{align*}
```
### grouping and centering equations

If you just need to display a set of consecutive equations, centered and with no alignment whatsoever, use the gather environment. The asterisk trick to set/unset the numbering of equations also works here.
```
\begin{gather*} 
2x - 5y =  8 \\ 
3x^2 + 9y =  3a + c
\end{gather*}
```


## Cross-referencing an equation
To reference to a given label you can use the standard command \ref or any other reference command provided by some packages. I like to use \eqref to reference to equations.

The environment equation doesn't allow any line breaks. So the syntax will be:
```
\begin{equation}
 a^2+b^2=c^2\label{eq:1}
\end{equation}
```
The environment align allows line breaks and so every line can get a label
```
\begin{align}
  x^2+y^2&=2r^2 \label{eq:1} \\
  d^2+h^2&=4r^2 \label{eq:2}
\end{align}
```
To reference to a given label you can use the standard command \ref or any other reference command provided by some packages. I like to use 
```
\eqref 
```
to reference to equations.


## Matrix
```
\begin{matrix}
\begin{pmatrix}             # paraphasis
\begin{bmatrix}
\begin{vmatrix}
\begin{Vmatrix}
```
## 


## math environment
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
## Reference
[wiki](https://en.wikibooks.org/wiki/LaTeX/Mathematics)

[User’s Guide for the amsmath Package](http://texdoc.net/texmf-dist/doc/latex/amsmath/amsldoc.pdf)

