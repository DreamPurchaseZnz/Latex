# Latex


## spacing between the items 

```
\begin{itemize}
  \setlength\itemsep{1em}
  \item one
  \item two
  \item three
\end{itemize}
```

----------------------------------------------------------------------------------------------------------------------------------
## parbox and minipage
A parbox is a box whose contents are created in paragraph mode

```
\parbox[position][height][inner-pos]{width}{text}              
```
For larger pieces of text, including ones containing a paragraph-making environment, you should use a minipage environment
```
\begin{minipage}[position]{width}        
  text
 \end{minipage}
```
Footnotes in a minipage environment are handled in a way that is particularly useful for putting footnotes in figures or tables.

----------------------------------------------------------------------------------------------------------------------------------

----------------------------------------------------------------------------------------------------------------------------------
# Latex2e Help
[help](http://herbert.the-little-red-haired-girl.org/html/latex2e/Top.html)
```
Overview What is LaTeX?
Commands                                 # Commands within a LaTeX document.
Parameters                               # The command line.
Command Index                            # An alphabetical list of LaTeX commands.
Concept Index                            # An alphabetical list of concepts.
```

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
```
Counters                    # Internal counters used by LaTeX
Cross References            # Automatic referencing
Definitions                 # Define your own commands etc
Document Classes            # Some of the various classes available
Environments                # Such as enumerate & itemize
Footnotes                   # How to produce footnotes
Layout                      # Controlling the page layout
Lengths                     # The length commands
Letters                     # The letter class
Line & Page Breaking        # How to insert pagebreaks etc.
Making Paragraphs           # Paragraph commands.
Margin Notes                # Putting remarks in the margin.
Math Formulae               # How to create mathematical formulae.
Modes                       # Paragraph, Math or LR modes.
Page Styles                 # Various styles of page layout.
Sectioning                  # How to section properly.
Spaces & Boxes              # All the associated commands.
Special Characters          # Special reserved characters.
Splitting the Input         # Dealing with big files by splitting.
Starting & Ending           # The formal start & end layouts.
Table of Contents           # How to create a table of contents.
Terminal Input/Output       # User interaction.
Typefaces                   # Such as bold, italics etc.
```
### Counters
Everything latex numbers for you has a counter associated with it. The name of counter is the same as the name of the environment or command that produces the nubmer. 
```
 part            paragraph       figure          enumi
 chapter         subparagraph    table           enumii
 section         page            footnote        enumiii
 subsection      equation        mpfootnote      enumiv
 subsubsection
```

Below is a list of the counters used in Latex standard document classes to control numbering. Counters in a document can be inremented,reset, accessed and referenced.
```
\addtocounter                             # Add a quantity to a counter.
\alph{counter}                            # Print value of a counter using letters, a, b; Alph, A, B,C,..
\arabic{counter}                          # Print value of a counter using numerals, 1, 2,...
\fnsymbol                                 # Print value of a counter using symbols, value is in the range of 9.
\newcounter                               # Define a new counter.
\refstepcounter                           # Add to counter, resetting subsidiary counters.
\roman{counter}                           # Print value of a counter using roman numerals, i, ii;Roman, I, II, III...
\setcounter                               # Set the value of a counter.
\stepcounter                              # Add to counter, resetting subsidiary counters.
\usecounter                               # Use a specified counter in a list environment.
\value                                    # Use the value of a counter in an expression.
```
#### setcounter
The \setcounter command sets the value of the counter to that specified by the value argument. Syntax:
```
\setcounter{counter}{value}
```
For example
```
\begin{enumerate}
\setcounter{enumi}{3}                     # sets the value of the item counter in the list to 3 
\item Something
\end{enumerate}
```
#### counter manipulation
```
\stepcounter{counter}
```
Two counters are used in the following code segment.
```
\section{Another section}
This is a dummy section with no purpose whatsoever but to contain text. 
This section has assigned the number \thesection.                          # the value of current section counter
 
\stepcounter{equation}                                                     
\begin{equation}
\label{1stequation}
\int_{0}^{\infty} \frac{x}{\sin(x)}
\end{equation}
```

The \value command produces the value of the counter named in the mandatory argument
```
\value{counter}
```
It can be used where LaTeX expects an integer or number, such as the second argument of a \setcounter or \addtocounter command, or in:
```
\hspace{\value{foo}\parindent}
```

#### define a counter

The \newcounter command defines a new counter named foo. The counter is initialized to zero.

The optional argument \[counter\] causes the counter foo to be reset whenever the counter named in the optional argument is incremented.
```
\newcounter{foo}[counter]
```
#### refer the step counter
```
\refstepcounter{<ctr>}
```
Like \stepcounter but you can use LATEX's referencing system to add a \label and later \ref the counter. The printed reference will be the current expansion of \the<ctr>.
  
### Cross reference

One reason for numbering things like figures and equations is to refer the reader to them, as in "See Figure 3 for more details"
```
\label Assign             # a symbolic name to a piece of text.
\pageref                  # Refer to a page number of the place where the corresponding 
                            label command appears.
\ref                      # Refer to a section, figure or similar and produce the number of the 
                            corresponding sectional unit.
```
#### label
```
\label{key}
```
if appearing in the ordinary text, this command will assigns to the key the number of current sectional unit.

if one appears inside a numbered environment, it will assigns that number to the key.

To avoid create two labels with the same name, it is common to use labels consisting of a prefix and suffix seperated by colon.
And the prefix conventionally used are:
```
cha for chapters
sec for lower-level sectioning commands
fig for figures
tab for tables
eq for equations
```

### Definition
```
\newcommand                  # Define a new command.
\newenvironment              # Define a new environment.
\newtheorem                  # Define a new theorem-like environment.
\newfont                     # Define a new font name
```
#### newcommand
```
 \newcommand{cmd}[args]{definition}
 \newcommand{cmd}[args][default]{definition}
 \renewcommand{cmd}[args]{definition}
 \renewcommand{cmd}[args][default]{definition}
```

```
cmd              # command name
args             # an integer from 1-9 denoting the number of arguments of the command being defined.
default          # If present, the first argument is optional. The default value is default.
definition       # The text to be substituted for every occurence of cmd; 
                   #n  in cmd is replaced by text of the nth argument when the substitution takes place.
```
```
\newcommand{\wbalTwo}[2][Wikimedia]{
  This is the Wikibook about LaTeX
  supported by {#1} and {#2}!}
  
% in the document body:
\begin{itemize}
\item \wbalTwo{John Doe}
\item \wbalTwo[lots of users]{John Doe}
\end{itemize}
```

#### newenvironment
```
\newenvironment{nam}[args]{begdef}{enddef}
\newenvironment{nam}[args][default]{begdef}{enddef}
\renewenvironment{nam}[args]{begdef}{enddef}
```
```
nam             # the name of environment
args            # the number of arguments.
default         # the first arguments is optional
begdef          # when \begin{name} is encoutered, the material
                  specified in the begdef is processed before text
enddef          # Vice versa
```
```
\newenvironment{king}
{ \rule{1ex}{1ex}\hspace{\stretch{1}} }
{ \hspace{\stretch{1}}\rule{1ex}{1ex} }

\begin{king}
My humble subjects \ldots
\end{king}
```
```
\newenvironment{topics}{
\newcommand{\topic}[2]{ \item{##1 / ##2\} }
Topics:
\begin{itemize}
}
{
\end{itemize}
}
```
#### newtheorem
```
\usepackage{amsthm}
\newtheorem{env_name}{printed output}[within]
\newtheorem{env_name}[numbered_like]{printed output}
```
Often the counters are determined by section,for example "Theorem 2.3" refers to the 3rd theorem in the 2nd section of a document
```
env_name                        # name, it must not be the same name of an existing environment or counter.
printed output                  # the text printed at the begining of the environment
within                          # the counter of this new environment will be reset 
                                  every time a new within environment is used.
numbered_like                   # the even though a new environment is created, 
                                  it will use the same counter as the numbered_like environment.
```
The \newtheorem command may have at most one optional argument.
```
\newtheorem{mydef}{Definition}

\begin{mydef}
Here is a new definition
\end{mydef}
```
### Document classes
Valid document classes include:
```
article
slides
book
report
letter
```
They are selected with the following command:
```
\documentclass [options] {class}
```
Options: Selecting the typeface (10pt is default)
```
10pt, 11pt, 12pt
```
Options: selecting the paper size
```
a4paper, a5paper, b5paper, letter paper, legal paper, executivepaper
```
Miscellaneous options
```
landscape                   # selects landscape format. Default is portrait.
titlepage, notitlepage      # selects if there should be a separate title page.
leqno                       # equation number on left side of equations. Default is right side.
fleqn                       # displayed formulas flush left. Default is centred.
openbib                     # use "open" bibliography format.
draft, final                # mark/do not mark overfull boxes with a rule. Default is final.
```
These options are not available with the slides class:
```
oneside, twoside            # selects one- or twosided layout. Default is oneside, except for the book class.
openright, openany          # determines if a chapter should start on a right-hand page. Default is openright for book.
onecolumn, twocolumn        # one or two columns. Defaults to one column.
```
If you specify more than one option, they must be seperated by a comma.
### Environment
latex provides a number of different paragraph-making environments
```
\begin{environment-name}
        .
\end{environment-name}
```
```
array                     # Math arrays.
center                    # Centred lines.
description               # Labelled lists.
enumerate                 # Numbered lists.
eqnarray                  # Sequences of aligned equations.
equation                  # Displayed equation.
figure                    # Floating figures.
flushleft                 # Flushed left lines.
flushright                # Flushed right lines.
itemize                   # Bulleted lists.
letter                    # Letters.
list                      # Generic list environment.
minipage                  # Miniature page.
picture                   # Picture with text, arrows, lines and circles.
quotation                 # Indented environment with paragraph indentation.
quote                     # Indented environment with no paragraph indentation.
tabbing                   # Align text arbitrarily.
table                     # Floating tables.
tabular                   # Align text in columns.
thebibliography           # Bibliography or reference list.
theorem                   # Theorems, lemmas, etc.
titlepage                 # For hand crafted title pages.
verbatim                  # Simulating typed input.
verse                     # For poetry and other things.
```
#### array
math array are produced with the array environment, it has a mandatory argument 
decribing the number of columns and alignment within them

```
\begin{array}{col1col2...coln}
column 1 entry & column 2 entry ... & column n entry \\  
 .
 .
 .
\end{array}
```
NOTE: 1) Each column col is specifed by a single letter that tells how items in that row should be formatted
```
l             flush left
c
r
```
2) Column entries must be seperated by an &. Each row of the array must be terminated with the string \\

3) Note that the array can only be used in math mode. So normally it is used inside an equation environment.

#### center
```
 \begin{center}                       # centered within the left and right margin
 Text on line 1 \\                    # each line must terminate with the string \\
 Text on line 2 \\
 .
 .
 .
 \end{center}
```
\center: the declaration form of the center environment. Usually it is used in the quote, figure, table or parbox environment. 
The declaration is terminated with blank line or \end command
#### discription
```
 \begin{description}                 # make labeled lists.
 \item [label] First item            # the label is bold face and flushed right.
 \item [label] Second item
 .
 .
 .
 \end{description}
```
#### enumerate
It produces a numbered list; Enumerations can be nested within one another, up to four levels deep.

They can be nested within other paragraph-making environments
```
\begin{enumerate}                  
 \item First item
 \item Second item
 .
 .
 .
 \end{enumerate}
```
#### eqnarray
The environment is used to display a sequence of equations or inequalities.
```
 \begin{eqnarray}
 math formula 1 \\
 math formula 2 \\
 .
 .
 .
 \end{eqnarray}
```
It is very much like a three column environment with consecutive rows seperated by \\ and the consecutive items with a row seperated
by an &

An equation number is placed on every line unless that line has a \nonumber command. The command \lefteqn is used to splitting long formulas across lines.
#### equation
The equation environment centres your equation on the page and places the equation number on the right margin.
```
 \begin{equation}
  math formula
 \end{equation}
```
#### figure
Figure are objects that are not part of the normal text and usually floated to a convenient place.
```
 \begin{figure}[placement]

  body of the figure

 \caption{figure title}
 \end{figure}
```
The placement determines where Latex will try to place your figure. There are four places
```
h (Here)            # at the position in the text where the figure environment appears.
t (Top)             # at the top of a text page.
b (Bottom)          # at the bottom of a text page.
p (Page of floats)  # on a separate float page, which is a page containing no text, only floats
```
The standard report and article use the default placement tbp.

The caption command allows you to title your figure.
#### flushleft and flushright
```
 \begin{flushleft}
 Text on line 1 \\
 Text on line 2 \\
 .
 .
 .
 \end{flushleft}
```
The flush environment allows you to create a paragraph consisting of lines that are flushed left, to the left-hand margin.

#### itemize
The itemize environment produces a "bulleted" list.
```
 \begin{itemize}
 \item First item
 \item Second item
 .
 .
 .
 \end{itemize}
```
#### list
```
 \begin{list}{label}{spacing}
 \item First item
 \item Second item
 .
 .
 .
 \end{list}
```
#### minipage
```
 \begin{minipage}[position]{width}
  text
 \end{minipage}
```
the minipage environment is similar to a \parbox command. It is useful for putting footnotes in figure and tables. A \footnote or \footnotetext command puts the footnote at the bottom of the minipage instead of the bottom of the page.
#### picture
The picture environment allows you create just about any kind of picture you want containing text, lines, arrows and circles.

A coordinate specifies a length in multiples of the unit length \unitlength. A position is a pair of coordinates, which are specified in the usual way with respect to an origin, which is normally at the lower-left corner of the picture.

```
\begin{picture}(width,height)(x offset,y offset)
  .
  .
  picture commands
  .
  .
 \end{picture}
```
The width and height specify the size of the picture. And the x_offset, y_offset specify the origin of the coordinates.

Everything that appears in a picture is drawn by the \put command. 
```
\put (11.3,-.3){...}              # reference point
```
```
\circle[*]{diameter}                                # Draw a circle; * refers to solid circle
\dashbox{dash_length}(width,height){...}            # Draw a dashed box.
\frame{}                                            # Draw a frame around an object.
\framebox                                           # (picture) Draw a box with a frame around it.
\line(x slope,y slope){length}                      # Draw a straight line.
\linethickness                                      # Set the line thickness.
\makebox                                            # (picture) Draw a box of the specified size.
\multiput                                           # Draw multiple instances of an object.
\oval                                               # Draw an ellipse.
\put                                                # Place an object at a specified place.
\shortstack                                         # Make a pile of objects.
\vector                                             # Draw a line with an arrow.
```
#### quotation
The quotation environment are indented on the right and the left. The texts are justified at both margin.

Leaving a blank line between text produce a new paragraph.
```
 \begin{quotation}
  text
 \end{quotation}
```
The syntax is same as that of quote command

#### tabbing
```
\begin{tabbing}
 text \= more text \= still more text \= last text \\
 second row \>  \> more \\
 .
 .
 .
 \end{tabbing}
```
The \hspace command is useful for controlling horizontal space in the tabbing environment

it is best suited for cases where the width of each column is constant and known in advance
```
\=                        # (set tab) 
\>                        # (advance to next tab stop only at this line) 
\<                        # (put things to the left margin)
\+                        # (indent; move margin right)
                            Moves the left margin of the next 
                            and all the following commands one tab stop to the right. 
\-                        # (unindent; move margin left) 
\'                        # Moves everything that you have typed so far in the current column, 
                            i.e. everything from the most recent \>, \<, \', \\, or \kill command, 
                            to the right of the previous column, flush against the current column's tab stop.
\`                        # Allows you to put text flush right against any tab stop, 
                            including tab stop 0. However, it can't move text to the right of the last column 
                            because there's no tab stop there. 
                            The \` command moves all the text that follows it, up to the \\ or \end{tabbing} command 
                            that ends the line, to the right margin of the tabbing environment. 
                            There must be no \> or \' command between the \` and the command that ends the line.
\\                        # (end of line; newline) 
\kill                     # (ignore preceding text; use only for spacing) 
\pushtabs                 # save all the tab stop positions
\poptabs	                # restore the tab stop positions
\a	                      # \accent
```
An example is as follows:
```
  \begin{tabbing}
        function \= fact(n : integer) : integer;\\                 |-\-
                 \> begin \= \+ \\                                 \-|-\-\
                       \> if \= n $>$ 1 then \+ \\                 \-\-|-\-\
                                fact := n * fact(n-1) \- \\        \-\-|-\-\
                          else \+ \\                               \-|-\-\-\
                                fact := 1; \-\- \\                 \-\-|-\-\
                    end;\\                                         |-\-\-\-\
        \end{tabbing}
```
```
\begin{tabbing}
	if \= (condition) \{ \\ % inserts a tab just after the "if"-command.
	\> then statement \=\\ % go to the defined tab and set a new one
	\}\\
	else \{ \\
	\> else statement     \> next tab is here\\
	\}\\
\end{tabbing}
```
#### table
```
\begin{table}[placement]

  body of the table

 \caption{table title}
 \end{table}
```
The position argument
```
h : Here - at the position in the text where the table environment appears.
t : Top - at the top of a text page.
b : Bottom - at the bottom of a text page.
p : Page of floats - on a separate float page, which is a page containing no text, only floats.
```
#### tabular
These environments produce a box consisting of rows of items, aligned vertically in columns.
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

```
width            # specifies the width of the tabular* environment.
                   There must be rubber space between columns that 
		   can stretch to fill out the specified width.

```
options-pos, specifies the vertical position. default is alignment on the center of the environment
```
t - align on top row
b - align on bottom row
```
options-col, specifies the column formatting.
it consists of the following specifier, corresponding to the sequence of columns and itercolumn material
```
l                      # A column of left-aligned items.
r                      # A column of right-aligned items.
c                      # A column of centred items.
|                      # A vertical line the full height and depth of the environment.
@{text}                # This inserts text in every row. 
                         An @-expression suppresses the intercolumn space normally inserted between columns;
			 any desired space between the inserted text and the adjacent items must be included in text. 
			 An \extracolsep{wd} command in an @-expression causes an extra space of width wd to 
			 appear to the left of all subsequent columns, until countermanded by another \extracolsep command. 
			 Unlike ordinary intercolumn space, this extra space is not suppressed by an @-expression. 
			 An \extracolsep command can be used only in an @-expression in the cols argument.
p{wd}                  # Produces a column with each item typeset in a parbox of width wd, 
                         as if it were the argument of a \parbox[t]{wd} command. 
			 However, a \\ may not appear in the item, except in the following situations:
			 inside an environment like minipage, array, or tabular.
			 inside an explicit \parbox.in the scope of a \centering, \raggedright, or \raggedleft declaration. 
			 The latter declarations must appear 
			 inside braces or an environment when used in a p-column element.
*{num}{cols}           # Equivalent to num copies of cols, where num is any positive integer and 
			 cols is any list of column-specifiers, which may contain another *-expression.
```
```
\begin{tabular}{r@{.}l}
  3   & 14159 \\
  16  & 2     \\
  123 & 456   \\
\end{tabular}
```
These commands can be used inside a tabular environment
```
\cline{i-j}                        # Draw a horizontal line spanning 
			             beginning in column i and ending in column j
\hline                	           # Draw a horizontal line spanning all columns.
\multicolumn{cols}{pos}{text}      # Make an item spanning several columns； cols specifies the number to span.
				     pos specifies the formatting, flush right or left.
\vline                             # Draw a vertical line, it can be used in the@expression.
```
```
\begin{tabular}{ |l|l| }
  \hline
  \multicolumn{2}{|c|}{Team sheet} \\
  \hline
  GK & Paul Robinson \\
  LB & Lucas Radebe \\
  DC & Michael Duberry \\
  DC & Dominic Matteo\\
  \hline
\end{tabular}
```
#### thebibliography




## Paremeters

The input file specification indicates the file to be formatted.

TeX uses ".tex" as a default file extension.

You can specify command options by supplying a string as parameters to the command
```
latex  \scrollmode\input foo.tex            # will process "foo.tex" without pausing after every error
```

Output file are always created in the current directory.







