# `handlecsv`

`handlecsv` is a module that enables document merging in ConTeXt.

It can import data from CSV—comma separated values—files and merge them into high–quality PDF documents.

The main case for automated document generation is mail–merging.

## Minimal Sample

Imagine you need a list full of lines following the pattern:

> [Name] [Surname] was born on [Birth Date].

The data to be merged are stored in the file `a.csv`, which contains:

```
"Name";"Surname";"Birthdate"
"John";"Smith";10/03/02
"Jane";"Amr";03/03/92
```

The source code to generate the required list is:

``` tex
\usemodule[handlecsv]
\setheader
\opencsvfile{a.csv}
\starttext
\startbuffer[loop]
\cA\ \cB\ was born on \cC.\crlf
\stopbuffer
\doloop{\ifnotEOF\getbuffer[loop]\nextrow\else\exitloop\fi}
\stoptext
```

The resulting content in the PDF document will be:

>John Smith was born on 10/03/02.
>
>Jane Amr was born on 03/03/92.

## Issues

If you have anything to say about `handlecsv`, please [open an issue](https://github.com/ousia/handlecsv/issues/new).

Issue reporting requires a _GitHub_ account. And please, don’t forget that all commments in all issues are public by default.

## License

`handlecsv` is released under the [GNU General Public License version 3](https://gnu.org/licenses/gpl-3.0.html).
