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
## new command creation
```
\newcommand{\suma}{\Large$+$}
```
----------------------------------------------------------------------------------------------------------------------------------
## math operation
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

## Paremeters

The input file specification indicates the file to be formatted.

TeX uses ".tex" as a default file extension.

You can specify command options by supplying a string as parameters to the command
```
latex  \scrollmode\input foo.tex            # will process "foo.tex" without pausing after every error
```

Output file are always created in the current directory.







