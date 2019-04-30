# Glossary

Many technical documents use terms or acronyms unknown to the general population. 
It is common practice to add a glossary to make such documents more accessible.

## Jump start

Place 
```
\usepackage{glossaries}                # after \usepackage{hyperref} if present 
\makeglossaries 
```
in your preamble. Then define any number of 
```
\newglossaryentry 
\newacronym 
```
glossary and acronym entries in your preamble (recommended) 
or before first use in your document proper. 

Finally add a 
```
\printglossaries 
```
call to locate the glossaries list within your document structure. 

Then pepper your writing with 
```
\gls{mylabel} 
```
macros (and similar) to simultaneously insert your predefined text and build the associated glossary. 
File processing must now include a call to makeglossaries followed by at least one further invocation of latex or pdflatex.

## Defining terms
```
\newglossaryentry{<label>}
{<settings>}
```
<label> is a unique label used to identify an entry in glossary, <settings> are comma separated key=value pairs used to define an entry.

```
\newglossaryentry{computer}
{
  name=computer,
  description={is a programmable machine that receives input,
               stores and manipulates data, and provides
               output in a useful format}
}
```
## Defining acronyms
```
\newacronym{<label>}{<abbrv>}{<full>}
```
where <label> is the unique label identifying the acronym, <abbrv> is the abbreviated form of the acronym and <full> is the expanded text. For example:

  
  
  
  
  
