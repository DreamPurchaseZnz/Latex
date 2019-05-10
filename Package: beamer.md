# Beamer
## Beamer theme gallery
[Beamer theme gallery](http://www.deic.uab.es/~iblanes/beamer_gallery/index.html)


## Basic format
```
\documentclass{beamer}
\title{A first example}

\author{author}
\date{\today}

\begin{document}
	\frame{\titlepage}
	
	\begin{frame}
		\frametitle{First slide}
		Hello, the world
	\end{frame}
	
\end{document}
```
## Basic code

### documentclass
```
\documentclass[option]{beamer}
```
Options are:
```
8pt&9pt (too small), 10pt, 11pt, 12pt, 14pt, 17pt, 20pt (huge)
handout     # no overlays
draft       # graphics, headlines, footlines are replaces by 
              gray rectangles to speed up compiling
```
```
\usepackage{pgfpages}
\pgfpagesuselayout{2 on 1}[a4paper,border shrink=5mm]
(alternative: '4 on 1' )
```
The beamer class automatically loads some other LATEXpackages, e.g.
xcolor, amsmath, amsthm, hyperref.
### The frame
A frame defines one page (slide) of the presentation
```
\begin{frame}[option]
\frametitle{Basic Code II - The Frame} 
\framesubtitle{Subtitle}              % Bookmark info
Frame content
\end{frame}
```
Options are:
```
plain          #  no headlines, footlines, sidebars
b, c or t      #  vertically align at bottom, center or top
fragile        #  require for verbatim environment
shrink=0..100  # shrink everything by n percent
```
### section and subsection
You can structure the presentation using the usual LATEXcommands
\section and \subsection before the frame environment
```
\section[short title]{long title}
\subsection[short title]{long title}
\begin{frame}
```
each call of them creates

- a new entry into the Table of Contents
- insert a new entry into the navigation bars (in many themes)
- does not generate a frame heading or any text on the slide

the version \section\*[]{} adds only an entry in the navigation
bars, but not in the Table of Contents

###  Special frame
#### Title
```
\title[short version]{A long Title \\ over several lines}
\subtitle[short version]{Subtitle}
\date[2009]{Event, \today}
\author[M. Smith]{Michael Mike Smith}
\institute[Uni Warwick]{University of Warwick}
\logo{\includegraphics[scale=0.1]{logo}}
\titlegraphic{\includegraphics[scale=0.1]{graphics}}
\begin{document}
\frame{\titlepage} % <-- generate frame with title
```
short versions of title, authors, : : : are used for head- and footlines

several authors with several affiliations
```
\author[author1 et al.]{author1\inst{1} \and author2\inst{2}}
\institute[Location1 and Location 2]{
\inst{1} Location long 1 \and
\inst{2} Location long 2}
```

#### Table of contents
```
\frame{
\frametitle{Outline}
\tableofcontents[pausesections]
}
```
\[pausesections\] is optional ! create pause between the sections.

Note: You can automatically print the table of contents at the beginning
of each section by adding the following code in the preamble:
```
\AtBeginSection[] {
\begin{frame}
\frametitle{Outline}
\tableofcontents[currentsection]
\end{frame}
}
```

## Changing the way thinks look: Themes

For the appearance of the presentation you can select predefined themes
of the Beamer class. Thereby, Beamer classifies five Categories:

Categories of Themes:

- Presentation Themes: slide template
- Color Themes*: color scheme of slide template
- Font Themes*: defines the fonts
- Inner Themes*:defines inside of slide like of bullets, boxes, ect.
- Outer Themes*: defines outside of slide like head- and footline

(* are optional if you don't like the default settings of Presentation themes)

### themes
Specifies the slide template of the entire presentation:
```
usetheme[...]{Berkeley}
```
Presentation Themes (many are named after cities):
```
AnnArbor Antibes Bergen Berkeley Berlin
Boadilla boxes CambridgeUS Copenhagen Darmstadt
default Dresden Frankfurt Goettingen Hannover
Ilmenau JuanLesPins Luebeck Madrid Malmoe
Marburg Montpellier PaloAlto Pittsburgh Rochester
Singapore Szeged Warsaw
```
### color themes
Specifies the color themes of the slide template either complete or
just for inner and outer elements:
```
\usecolortheme[...]{beaver}
```
Color Themes (many are named after animals):
```
complete:  albatross, beetle, crane, dove, fly, 
                      seagull, wolverine,beaver
inner:     lily, orchid, rose
outer:     whale, seahorse, dolphin
```

### inner themes
Specifies the typesetting of elements within the frame such as:
```
title and part pages
itemize, enumeration & description environment
block, theorem & proof environment
figures and tables
footnotes
bibliography entries
```
```
\useinnertheme[...]{circles}
```
Inner Themes:
```
circles 
default 
inmargin 
rectangles 
rounded
```
### Outer Themes
Specifies the the navigational elements such as:
```
head- and footline
sidebars
logo
frame title
```
```
\useouthertheme[...]{split}
```
Outer Themes:
```
default infolines miniframes sidebar smoothbars
smoothtree split tree
```

### Font Themes
Specifies the the fonts used in a presentation:
```
\usefonttheme[...]{serif}
```
Font Themes:
```
default professionalfonts serif
structureitalicserif structuresmallcapsserif structurebold
```
### Note
- All themes can be further customized by options \[...\] which can be found in the documentation included in the distribution of Beamer.
) 
- The color/inner/outer & font themes are optional which can be selected if you don't like the default settings) 
- More detailed adjustments are possible ! check the documentation


## Structuring a Presentation: Environments
### lists
Usual LATEX environments are available
```
Itemize - environment
Enumerate - environment
Description - environment
```

### mathematics blocks
Usual math LATEX environments are available

```
Theorem
Definition
Lemma
Corollary
Proof
Example
```
### blocks
Beamer offers additional block environments

A Block
```
\begin{block}{A Block}
...
\end{block}
```
A Alertbox
```
\begin{alertblock}{A Alertblock}
...
\end{block}
```
A Exampleblock
```
\begin{exampleblock}{A Exampleblock}
...
\end{block}
```
## Creating Overlays

Overlays control the order in which parts of the frame appear
- Helpful to focus the attention of the audience to the information that is currently being discussed.
- Don't overuse it: otherwise you'll end up to continuously run back to the computer to click to uncover the next part of your talk.

### pause
Pause command 
An easy (but unexible) way to create overlays is the \pause command.
If you use this command somewhere in the frame, only the text on the
frame up to the \pause command is shown on the first slide. On the
second slide, everything up to the second \pause, and so forth.

Can be used inside environments, mathematical equation & texts.

```
\begin{enumerate}
\item Shown from first slide on.
\pause
\item Shown from second slide on.
\pause
\item Shown from third slide on.
\pause
\item Shown from fourth slide on.
\end{enumerate}
```
### Overlays specifications

Overlays specifications are given in pointed brackets <...> which
can be written behind certain commands

These specifications indicate which slide the corresponding
information should appear on, as explained in the following:

```
<2>             # display on slide 2.
<1->            # display from slide 1 on.
<1-3>           # display from slide 1 to slide 3.
<-3, 5-6, 8->   # display on all slides except slides 4 and 7.
```
Overlay Specification can be used with these commands
```
\textbf<2>{Sample} Sample
\textit<2>{Sample} Sample
\textsl<2>{Sample} Sample
\alert<2>{Sample} Sample
\textrm<2>{Sample} Sample
\textsf<2>{Sample} Sample
\color<2>{green}{Sample} Sample
\structure<2>{Sample} Sample
```
Note: Effect of each command will only appear on the second slide

### Special commands with overlay specifications

The following commands have special overlay specifications which affect
the text within the brackets fg or behind the command

Special commands with Overlay Speciffications I
```
\onslide<>{}                 # Text will only be shown on the specified slides. 
                               On non-specified slides, text still occupies the space.
\only<>{}                    # Text only appears on speciffied slides. 
                               On non-specified slides text will occupy no space.
\uncover<>{}                 # Text will only be shown on specified slides. 
                               On non-specified slides, text still occupies the space and appears transparent
			       if transparency effects are enabled.
\visible<>{}                 # Text will be shown on specified slides. 
                               On the other slides, text is not shown but occupies still the space.
\invisible<>{}               # Opposite to \visible.
```

```
\alt<n>{default text}{alternative text}
```
The default text is shown on the specified slides, otherwise the alternative text.
```
\temporal<>{before slide}{default text}{after slide}
```
This command takes three text arguments. The first text appears if the current slide is before the specified slides, the default text
appears while currently on the specified slides, the last text appears
after the specified slides have appeared.

### Overlay Specifications - Environments
Environments can also be equipped with overlay specifications
```
\begin{theorem}<1->
There exists an infinite set.
\end{theorem}
\begin{proof}<3->
This follows from the axiom of
infinity.
\end{proof}
\begin{example}<2->
The set of natural numbers is
infinite.
\end{example}
```
For each of the basic commands \only, \uncover, \invisible and
\alt there exists \environment versions": onlyenv, altenv, visibleenv,
uncoverenv & invisibleenv.

### Transparency effects
By default, covered items are not shown during a presentation
Transparency Effects
Transparency effects can be specified in a quite general way by using the
command in the preamble: 
```
\setbeamercovered{options}
```
Options are:
```
invisible                 # default - covered text is completely transparent
transparent               # covered text is typeset in a transparent way
                            (opaqueness can be specified - check documentation)
dynamic                   # covered text is transparent in dynamic way, i.e. the longer
                            it will take till the text is uncovered, the stronger the transparency.
highly dynamic            # same effect as dynamic, but the effect is stronger.
: : :
```
## Including Graphics

Standard LATEX figure environment can be used
```
\includegraphics[options]{filename}
```
Options are:
```
scale=<value>: scale the picture by <value>
height=<len>: scale the picture so that the width is <len>
width=<len>: scale the picture so that the width is <len>
angle=<x>: rotate the picture by <x> degrees
draft: Don't display image, print lename in a box of the same size.
: : :
```
Beamer also supports the pgf package
```
\pgfdeclareimage[options]{image name}{filename}
\pgfuseimage{image name}
\pgfimage[options]{image name}
```
the commands \includegraphics, \pgfuseimage, and
\pgfimage can be combined with overlay specification

## Structuring a Presentation: Columns, Spaces & Alignments

### columns
To structure the frame you can use
```
LATEX minipage environments
Beamer columns environments
```
```
\begin{columns}
\begin{column}[]{.5\textwidth}
\begin{block}{Block 1} Contents of Block 1\end{block}
\end{column}
\begin{column}[]{.5\textwidth}
\begin{block}{Block 2} Contents of Block 2\end{block}
\end{column}
\end{columns}
```

### Alignments & Spacings

A frame can be assigned a left, center, or right alignment with the
flushleft, center and flushright environments
```
\begin{center}
The center-aligned text goes here.
\end{center}
```
- A vertical or horizontal space can be indicated by using
```
\vspace{0.5cm} and \hspace{0.5cm}, respectively.
```
- Several units can be used, e.g, 
```
mm, cm, in, pt, : : : .
```
- Also negative values can be used to squeeze text or graphics
together: 
```
\vspace{-0.5cm}
```
### Tips for Professional Tables
Simple tables can be created in Beamer with the tabular environment:
```
\begin{tabular}[position]{table spec}
...
\end{tabular}
```
The following symbols are available to describe the table columns:
```
l               # left-justified column
c               # centered column
r               # right-justified column
p{width}        # paragraph column with text vertically aligned at the top
|               #vertical line
||              # double vertical line
```
LATEX won't wrap the text in a column if it is too wide for the page. With p{width} you can dene the width of the column and the
text will be wrap-around.

## Other useful thinks:
Adding notes to the pdf 
```
\documentclass[notes]{beamer}
```
Drawing figures using e.g.:
- the LATEX picture environment
- pstricks package: cannot use pdflatex with this

Animations, Sounds & Multimedia ! \usepackage{multimedia}

Adding a Bibliography & Appendix
















## reference
[beamer class](http://tug.ctan.org/macros/latex/contrib/beamer/doc/beameruserguide.pdf)

[Overleaf beamer](https://www.overleaf.com/learn/latex/Beamer)

[University of Warwick, The beamer class for latex](https://warwick.ac.uk/fac/sci/physics/research/cfsa/people/pastmembers/wuensch/workshoplatex/beamertutorialkwuensch.pdf)

[fun with beamer to create the perfect presentation](http://web.mit.edu/rsi/www/pdfs/beamer-tutorial.pdf)

