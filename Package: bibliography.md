# Bibliography

### Bibliographic information file
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
Abramowitz, Milton and Irene A. Stegun (1964), Handbook of mathematical functions with formulas, graphs, and mathematical tables. New York: Dover.
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
A hidden field used for specifying or overriding the alphabetical order of entries (when the "author" and "editor" fields are missing). Note that this is very different from the key (mentioned just after this list) that is used to cite or cross-reference the entry.
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
The "(issue) number" of a journal, magazine, or tech-report, if applicable. Note that this is not the "article number" assigned by some journals.
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
The field overriding the default type of publication (e.g. "Research Note" for techreport, "{PhD} dissertation" for phdthesis, "Section" for inbook/incollection)
```
volume
```
The volume of a journal or multi-volume book
```
year
```
The year of publication (or, if unpublished, the year of creation)
In addition, each entry contains a key (Bibtexkey) that is used to cite or cross-reference the entry. This key is the first item in a BibTeX entry, and is not part of any field.
```













