# Latex

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
