# Using Curl

These notes come from the curl manpage.

## General form

`curl [options] url`

## Examples

`curl http://example.com/file.txt`	downloads file.txt to stdout

`curl -o myFile.txt http://example.com/file.txt`	downloads the file 'file.txt' to myFile.txt


## Specifying multiple files/urls

Braces {} allow multiple url parts. Square brackets [] allow sequences of alphanumerics.

- ftp://file{one,two,three}.txt	- multiple file parts
- ftp://file[1-100].txt	- numeric range
- ftp://file[001-100].txt	- numeric range with formatting
- ftp://file[a-z].txt	- range of alpha
- ftp://file[1-1000:10]	- step counter

Combining these patterns:

- http://example.com/archive[1996-2001]/vol[1-4]/part{a,b,c}.html

This will download parta.html, partb.html and partc.html files from the volumes 1-4 of archives from 1996-2001!


## Useful Options

Use a space between options (although single-dash forms don't require the space).

`--progress-bar` or `-#`	displays transfer progress as a bar

`--silent` or `-s`	does not display a progress bar/meter

`--append` or `-a`	append to target file instead of erasing it.

`-l, --location`	follow redirects

`-0, --output <file>`	write to file instead of stdout


