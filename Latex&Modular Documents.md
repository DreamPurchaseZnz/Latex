# LaTeX/Modular Documents

Create a clear structure of the whole project this way:

1. create a directory only for the project. We'll refer to that in the following parts as the root directory

2. create two other directories inside the root, one for LaTeX documents, the other one for images. 
Since you'll have to write their name quite often, choose short names. A suggestion would be simply tex and img.
3. create your document (we'll call it document.tex, 
but you can use the name you prefer) and your own package (for example mystyle.sty); 
this second file will help you keep the code cleaner.

```
./document.tex
./mystyle.sty
./tex/
./img/
```
## Getting LaTeX to process multiple files
### Using the different paths

When the LaTeX compiler finds a reference to an external file in the base file, it will look for it in the same directory. However, you can in principle refer to any file on your system, using both absolute and relative paths.

An absolute path is a full path- and filename with every element specified. So, filename.tex might have the full path,
```
\input{/home/user/texfiles/filename.tex}
```
```
\input{./filename.tex}
```

### Including full Latex Documents in another latex document

So you want to include the 13 individual documents in one LaTeX document. LaTeX provides \include and \input commands, but these would require that the content of the individual files, i.e. the stuff between \begin{document} and \end{document}, is put in a file of its own. You cannot just \input the full problem sheet document, as there must be only one \documentclass command, and a few preamble commands are invalid within the document.

```
% arara: pdflatex: { synctex: on } 
% arara: pdflatex: { synctex: on } 
\documentclass[oneside]{scrbook} 

\title{A Sample Thesis} 
\author{A.N. Other} 
\date{July 2013} 
\titlehead{A Thesis submitted for the degree of Doctor of Philosophy} 
\publishers{School of Something\\University of Somewhere} 

\begin{document} 
\maketitle 

\frontmatter 
\tableofcontents 
\listoffigures 
\listoftables 

\chapter{Acknowledgements} 

I would like to thank my supervisor, Professor Someone. This 
research was funded by the Imaginary Research Council. 

\chapter{Abstract} 

A brief summary of the project goes here. 

\mainmatter 

\include{intro} 

\include{techintro} 

\include{method} 

\include{results} 

\include{conc} 

\backmatter 

\end{document} 
```
Listing 3 (intro.tex):
```
\chapter{Introduction} 
\label{ch:intro} 
```
Listing 4 (techintro.tex):
```
\chapter{Technical Introduction} 
\label{ch:techintro} 
```
Listing 5 (method.tex):
```
\chapter{Method} 
\label{ch:method} 
```







