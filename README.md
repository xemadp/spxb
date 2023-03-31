# SIMPLEX BIBLIOTHECA
This is a simple bash script that creates an html file
listing different books ( PDFS and EPUBS for now) and 
their cover images using a template html file.

## Requirements
This script needs the following programs to function:

- imagemagick ( convert command )
- [epub-thumbnailer](https://github.com/marianosimone/epub-thumbnailer)

Both of these programs are needed to generate the book covers.

Make sure you have them installed.

Another Requirement is the template.html to be present, more on that [below](https://github.com/xemadp/spxb#template).

## Installing 
``` bash
git clone https://github.com/xemadp/spxb
cd spxb
chmod +x spxb
```

## USAGE
This pretty much explains it:

```
USAGE: spxb OPTION DIR
OPTIONS:
        spxb gc DIR => creates covers from books present in the DIR directorty
        spxb gp DIR => creates bibliotheca.html from books present in the DIR directorty
        spxb b DIR => creates covers and bibliotheca.html from books present in the DIR directorty
        spxb supports pdfs and epub files for now.
```

## Template
The template.html file is needed to be present in the directory spxb
is executed from, The overall format of the template is pretty straight 
forward since the output file bibliotheca.html
is going to be a set of repeated html blocks that
contain books and their covers
the template.html file needs to have a section
that begins with
```
%CONTENT BEGIN%
```
and ends with
```
%CONTENT END%
```
and contains the following terms:
- %COVER% - this term will be replaced with the directory address of the books cover
- %BOOKNAME% - this term will be replaced with the books name, without the format (e.g .pdf)
- %BOOKDIR% - this term will be replaced with the directory address of the book

This constitutes the repeated blocks in which the books will go.
refer to the default [template](https://github.com/xemadp/spxb/blob/master/template.html) to get a more clear idea.

## Example
Lets say you have a directory such as ~/Books that you keep your books in
in order to create bibliotheca.html you should be in a directory that template.html is present in,
and do as such:
``` bash
spxb b ~/Books
```
This will create the needed covers directory and also the bibliotheca.html file.

If covers are already present and you for some reason lost bibliotheca.html do this:
``` bash
spxb gp ~/Books
```

If the reverse happens ( bibliotheca.html exists and covers/ directory is deleted) do as such:
``` bash
spxb gc ~/Books
```
