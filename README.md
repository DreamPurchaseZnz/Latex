# Latex
## Spacing between the items 
```
\begin{itemize}
  \setlength\itemsep{1em}
  \item one
  \item two
  \item three
\end{itemize}
```


## tabular
```
\begin{tabular}[pos]{cols}
 column 1 entry & column 2 entry ... & column n entry \\
 .
 .
 .
 \end{tabular}

                or

 \begin{tabular*}{width}[pos]{cols}
 column 1 entry & column 2 entry ... & column n entry \\
 .
 .
 .
 \end{tabular*}
```



## parbox and minipage
A parbox is a box whose contents are created in paragraph mode

```
\parbox[position][height][inner-pos]{width}{text}               # the text and width are mandatory arguments
```
For larger pieces of text, including ones containing a paragraph-making environment, you should use a minipage environment
```
\begin{minipage}[position]{width}        # You may use other paragraph-making environments inside a minipage.
  text
 \end{minipage}
```
Footnotes in a minipage environment are handled in a way that is particularly useful for putting footnotes in figures or tables.

## New command
```
\newcommand{\suma}{\Large$+$}
```

## Math operation
```
multline
align
gather
```
---------------------------------------------basic-------------------------------------------------------------------------------------
# Latex2e Help
[help](http://herbert.the-little-red-haired-girl.org/html/latex2e/Top.html)


## overview of latex and local guide

The LaTeX command typesets a file of text using the TeX program and the LaTeX Macro package for TeX

- A "Device Independent", or '.dvi' file: for device command translation
- A "transcript" or "log" file: contain summary information and diagnostic messages for any errors discovered in the input file
- An "auxiliary" or "aux" file: this is used by Latex itself, for things such as sectioning

## command

A latex command begins with the command name, which consists of a "\" followed by either
- a string of letters
- a single non-letter

Arguments  contained in square brackets \[\], are optional while arguments contained in braces \{\} are required

Note: Latex is case sensitive.









