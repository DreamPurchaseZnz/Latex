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
## New command
```
\newcommand{\suma}{\Large$+$}
```
----------------------------------------------------------------------------------------------------------------------------------
## Math operation
```
multline
align
gather
```
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
\alph                                     # Print value of a counter using letters.
\arabic                                   # Print value of a counter using numerals.
\fnsymbol                                 # Print value of a counter using symbols.
\newcounter                               # Define a new counter.
\refstepcounter                           # Add to counter, resetting subsidiary counters.
\roman                                    # Print value of a counter using roman numerals.
\setcounter                               # Set the value of a counter.
\stepcounter                              # Add to counter, resetting subsidiary counters.
\usecounter                               # Use a specified counter in a list environment.
\value                                    # Use the value of a counter in an expression.
```
#### Setcounter
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
#### Counter manipulation




## Paremeters

The input file specification indicates the file to be formatted.

TeX uses ".tex" as a default file extension.

You can specify command options by supplying a string as parameters to the command
```
latex  \scrollmode\input foo.tex            # will process "foo.tex" without pausing after every error
```

Output file are always created in the current directory.







