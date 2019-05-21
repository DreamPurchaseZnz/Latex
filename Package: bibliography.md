# Bibliography
## Introduction
LATEX supports bibliographies out of the box, either embedding the references in your document or storing them in an external file. This article explains how to manage bibliography with the thebibliography environment and the BibTeX system.

Standard bibliography commands in LATEX have a similar syntax to that of lists and items.
```
\begin{document}
 
\section{First section}
 
This document is an example of \texttt{thebibliography} environment using 
in bibliography management. Three items are cited: \textit{The \LaTeX\ Companion} 
book \cite{latexcompanion}, the Einstein journal paper \cite{einstein}, and the 
Donald Knuth's website \cite{knuthwebsite}. The \LaTeX\ related items are
\cite{latexcompanion,knuthwebsite}. 
 
\medskip
 
\begin{thebibliography}{9}
\bibitem{latexcompanion} 
Michel Goossens, Frank Mittelbach, and Alexander Samarin. 
\textit{The \LaTeX\ Companion}. 
Addison-Wesley, Reading, Massachusetts, 1993.
 
\bibitem{einstein} 
Albert Einstein. 
\textit{Zur Elektrodynamik bewegter K{\"o}rper}. (German) 
[\textit{On the electrodynamics of moving bodies}]. 
Annalen der Physik, 322(10):891–921, 1905.
 
\bibitem{knuthwebsite} 
Knuth: Computers and Typesetting,
\\\texttt{http://www-cs-faculty.stanford.edu/\~{}uno/abcde.html}
\end{thebibliography}
 
\end{document}
```
## Bibliography management with Bibtex
BibTeX is a widely used bibliography management tool in LATEX, with BibTeX the bibliography entries are kept in a separate file and then imported into the main document.

Once the external bibliography file is imported, the command \cite is used just as in the introductory example.
```
Ths document is an example of BibTeX using in bibliography management. Three items 
are cited: \textit{The \LaTeX\ Companion} book \cite{latexcompanion}, the Einstein
journal paper \cite{einstein}, and the Donald Knuth's website \cite{knuthwebsite}. 
The \LaTeX\ related items are \cite{latexcompanion,knuthwebsite}. 
 
\medskip
 
\bibliographystyle{unsrt}
\bibliography{sample}
```

This uses the following commands:
```
\bibliography{sample}
```
Imports the BibTeX file "sample.bib" to display the bibliography. To import several .bib files just write them comma-separated inside the braces, the file extension is not necessary.
```
\bibliographystyle{unsrt}
```
Sets the bibliography style to be used in this document. The information displayed depends on the bibliography style used, even if the entry contains information about the date, author, title, publisher, and abstract, the style used might only print the title and the author. See Bibtex bibliography styles which contains examples of the default bibliography styles in LATEX.
```
\cite{einstein}
```
This will print a number of text, depending on the bibliography style, to reference the bibliography entry whose label is passed to the command. In this case, the label einstein produces [2].
## The bibliography file
Bibliographic references are usually kept in a bibliography file whose extension is .bib, this file consists of a list of records and fields. Each bibliography record holds relevant information for a single entry.
```
@article{einstein,
    author =       "Albert Einstein",
    title =        "{Zur Elektrodynamik bewegter K{\"o}rper}. ({German})
        [{On} the electrodynamics of moving bodies]",
    journal =      "Annalen der Physik",
    volume =       "322",
    number =       "10",
    pages =        "891--921",
    year =         "1905",
    DOI =          "http://dx.doi.org/10.1002/andp.19053221004"
}
 
@book{latexcompanion,
    author    = "Michel Goossens and Frank Mittelbach and Alexander Samarin",
    title     = "The \LaTeX\ Companion",
    year      = "1993",
    publisher = "Addison-Wesley",
    address   = "Reading, Massachusetts"
}
 
@misc{knuthwebsite,
    author    = "Donald Knuth",
    title     = "Knuth: Computers and Typesetting",
    url       = "http://www-cs-faculty.stanford.edu/\~{}uno/abcde.html"
}
```
This file contains records in a special format, for instance, the first bibliographic reference is defined by:
```
@article{...}
```
This is the first line of a record entry, @article denotes the entry type and tells BibTeX that the information stored here is about an article. Besides the entry types shown in the example (article, book and misc) there are a lot more, see the reference guide.
```
einstein
```
The label einstein is assigned to this entry, is an identifier that can be used to refer this article within the document.
```
author = "Albert Einstein",
```
This is the first field in the bibliography entry, indicates that the author of this article is Albert Einstein. Several comma-separated fields can be added using the same syntax key = value, for instance: title, pages, year, URL, etc. See the reference guide for a list of possible fields.
The information in this file can later be used within a LATEX document to include these references, as shown in the next subsection.

## Bibliographic information file
BibTeX uses a style-independent text-based file format for lists of bibliography items, such as articles, books, and theses. BibTeX bibliography file names usually end in .bib. A BibTeX database file is formed by a list of entries, with each entry corresponding to a bibliographical item. Entry types correspond to various types of bibliographic sources such as article, book, or conference.

An example entry which describes a mathematical handbook would be structured as an entry name followed by a list of fields, such as author and title:
```
@Book{abramowitz+stegun,
 author    = "Milton {Abramowitz} and Irene A. {Stegun}",
 title     = "Handbook of Mathematical Functions with
              Formulas, Graphs, and Mathematical Tables",
 publisher = "Dover",
 year      =  1964,
 address   = "New York City",
 edition   = "ninth Dover printing, tenth GPO printing"
}
```
If a document references this handbook, the bibliographic information may be formatted in different ways depending on which citation style (APA, MLA, Chicago etc.) is employed. The way LaTeX deals with this is by specifying *\cite* commands and the desired bibliography style in the LaTeX document. If the command \cite{abramowitz+stegun} appears inside a LaTeX document, the bibtex program will include this book in the list of references for the document and generate appropriate LaTeX formatting code. When viewing the formatted LaTeX document, the result might look like this:
```
Abramowitz, Milton and Irene A. Stegun (1964), Handbook of mathematical
functions with formulas, graphs, and mathematical tables. New York: Dover.
```
Depending on the style file, BibTeX may rearrange authors' last names, change the case of titles, omit fields present in the *.bib* file, format text in italics, add punctuation, etc. Since the same style file is used for an entire list of references, these are all formatted consistently with minimal effort required from authors or editors.

The types of entries and fields used in virtually all BibTeX styles BibTeX are listed below.

### Entry types
A BibTeX database can contain the following types of entries:

article
```
An article from a journal or magazine.
Required fields: author, title, journal, year, volume
Optional fields: number, pages, month, doi, note, key
```
book
```
A book with an explicit publisher.
Required fields: author/editor, title, publisher, year
Optional fields: volume/number, series, address, edition, month, note, key, url
```
booklet
```
A work that is printed and bound, but without a named publisher or sponsoring institution.
Required fields: title
Optional fields: author, howpublished, address, month, year, note, key
```
conference
```
The same as inproceedings, included for Scribe compatibility.
```
inbook
```
A part of a book, usually untitled. May be a chapter (or section, etc.) and/or a range of pages.
Required fields: author/editor, title, chapter/pages, publisher, year
Optional fields: volume/number, series, type, address, edition, month, note, key
```
incollection
```
A part of a book having its own title.
Required fields: author, title, booktitle, publisher, year
Optional fields: editor, volume/number, series, type, chapter, pages, address, edition, month, note, key
```
inproceedings
```
An article in a conference proceedings.
Required fields: author, title, booktitle, year
Optional fields: editor, volume/number, series, pages, address, month, organization, publisher, note, key
```
manual
```
Technical documentation.
Required fields: title
Optional fields: author, organization, address, edition, month, year, note, key
```
mastersthesis

```
A Master's thesis.
Required fields: author, title, school, year
Optional fields: type, address, month, note, key
```
misc
```
For use when nothing else fits.
Required fields: none
Optional fields: author, title, howpublished, month, year, note, key
```
phdthesis
```
A Ph.D. thesis.
Required fields: author, title, school, year
Optional fields: type, address, month, note, key
```
proceedings
```
The proceedings of a conference.
Required fields: title, year
Optional fields: editor, volume/number, series, address, month, publisher, organization, note, key
```
techreport
```
A report published by a school or other institution, usually numbered within a series.
Required fields: author, title, institution, year
Optional fields: type, number, address, month, note, key
```
unpublished
```
A document having an author and title, but not formally published.
Required fields: author, title, note
Optional fields: month, year, key
```
### Field types
A BibTeX entry can contain various types of fields. The following types are recognized by the default bibliography styles; some third-party styles may accept additional ones:

address
```
Publisher's address (usually just the city, but can be the full address for lesser-known publishers)
```
annote
```
An annotation for annotated bibliography styles (not typical)
```
author
```
The name(s) of the author(s) (in the case of more than one author, separated by and)
```
booktitle
```
The title of the book, if only part of it is being cited
```
chapter
```
The chapter number
```
crossref
```
The key of the cross-referenced entry
```
doi
```
digital object identifier
```
edition
```
The edition of a book, long form (such as "First" or "Second")
```
editor
```
The name(s) of the editor(s)
```
howpublished
```
How it was published, if the publishing method is nonstandard
```
institution
```
The institution that was involved in the publishing, but not necessarily the publisher
```
journal
```
The journal or magazine the work was published in
```
key
```
A hidden field used for specifying or overriding the alphabetical order of entries
(when the "author" and "editor" fields are missing).
Note that this is very different from the key (mentioned just after this list)
that is used to cite or cross-reference the entry.
```
month
```
The month of publication (or, if unpublished, the month of creation)
```
note
```
Miscellaneous extra information
```
number
```
The "(issue) number" of a journal, magazine, or tech-report, if applicable. 
Note that this is not the "article number" assigned by some journals.
```
organization
```
The conference sponsor
``` 
pages
```
Page numbers, separated either by commas or double-hyphens.
```
publisher
```
The publisher's name
```
school
```
The school where the thesis was written
```
series
```
The series of books the book was published in (e.g. "The Hardy Boys" or "Lecture Notes in Computer Science")
```
title
```
The title of the work
```
type
```
The field overriding the default type of publication
(e.g. "Research Note" for techreport, "{PhD} dissertation" for phdthesis, "Section" for inbook/incollection)
```
volume
```
The volume of a journal or multi-volume book
```
year
```
The year of publication (or, if unpublished, the year of creation)
In addition, each entry contains a key (Bibtexkey) that is used to cite or
cross-reference the entry. This key is the first item in a BibTeX entry, and is not part of any field.
```

## Adding the bibliography in the table of contents

There are two ways of including the bibliography in the table of contents, either manually adding it or using the package tocbibind (recommended).

To add it manually just insert the next line right before the command \begin{thebibliography} or \bibliography
```
\addcontentsline{toc}{chapter}{Bibliography}
```
for books and reports or
```
\addcontentsline{toc}{section}{References}
```
for articles. If you're also using the hyperref package, it is advisable to add \phantomsection before these \addcontentsline calls, so that hyperlinks will target the correct page. If you prefer to use tocbibind see the next example.
```
\documentclass[a4paper,10pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[english]{babel}
 
\usepackage[nottoc]{tocbibind}
 
\begin{document}
 
\tableofcontents
 
\section{First Section}
This document ...
 
\bibliographystyle{unsrt}
\bibliography{sample}
 
\end{document}
```
Adding the line
```
\usepackage[nottoc]{tocbibind}
```
to the preamble will print the "References" or "Bibliography" in the table of contents, depending on the document type. Be careful, it will also add other elements like the Index, Glossary and list of Listings to the table of contents.






