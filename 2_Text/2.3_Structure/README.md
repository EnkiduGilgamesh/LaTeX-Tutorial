# 2.3 Structure

- [2.3 Structure](#23-structure)
  - [2.3.1 Title Page](#231-title-page)
  - [2.3.2 Chapter](#232-chapter)
  - [2.3.3 Append Index](#233-append-index)
  - [2.3.4 Matters](#234-matters)
  - [2.3.5 Multiple Files](#235-multiple-files)
  - [2.3.6 Chapter's Style](#236-chapters-style)
  - [2.3.7 Grammar Check](#237-grammar-check)

## 2.3.1 Title Page

In *article* the title is not in a single page, where in *book* or report is in the contrary.

The options `titilepage` or `notitlepage` of document class can control title page whether to display in a single page.

$\LaTeX$ does not provide any methods to change the title page's style. Since the title only be used once, we can change it manually. Below is an example:

```latex
\begin{titlepage}
    \vspace*{\fill}
    \begin{center}
        \normalfont
        {\Huge\bfseries Article Structure}

        \bigskip
        {\Large\itshape Wenren Muyan}

        \medskip
        \today
    \end{center}

    \vspace*{\fill}

    \begin{center}
        {\huge\bfseries Perface}
        
        \vspace{2em}

        This article is about the construct of LaTeX. 
    \end{center}

    \vspace{\stretch{3}}
    
\end{titlepage}
```

The package **titling** provides methods to change the style through `\maketitle`. See them in "./rsc/titling.pdf".

## 2.3.2 Chapter

LaTeX has 7 ranks chapters. They are:

| Rank | Name | Comment |
| --- | --- | --- |
| -1 | part | the highest |
| 0 | chapter | the highest in report and book |
| 1 | section | the highest in article |
| 2 | subsection | |
| 3 | subsubsection | |
| 4 | paragraph | no number, no display in content |
| 5 | subparagraph | no number, no display in content |

Chapter and section are actually equal to each other.

Command `\chapter*` means that this chapter has no number and no display in content. The same as the other rank of chapters.

The whole command is `\chapter[title_in_content]{title_in_page}`, with the option `title_in_content` displaying in content.

TODO: counter secnumdepth, tocdepth

## 2.3.3 Append Index

The chapters in append index will sort by letters and do not show in content. Command `\appendix` represents the beginning of append index.

```latex
\appendix
\chapter{Reference} %\section{Reference}
```

Package **appendix** can change the style of the append index, see in "./rsc/appendix.pdf"

## 2.3.4 Matters

For book, it can be divided into front matter, main matter and back matter using command `\frontmatter`, `\mainmatter`, and `\backmatter`.

The three commands above will all clear the page to begin a new page by implicitly using command `\clearpage` or `\cleardoublepage`.

In front page, the page number will use lower case of roman number and the chapers will not be numbered. In main matter, the page number wll use Arabic numbers. In back matter, the chapters will not be numbered.

## 2.3.5 Multiple Files

When the project is too long, it's inconvenient to compile all your work in one single file.

Command `\include{file_name}` will put the code in the selected file to the command's position, before and after this action the command `\clearpage` or `\cleardoublepage` will be used. This command can be only used in document, and not be nested. The file name does not need to followed by an extension.

```latex
\begin{document}
    \section{A}
    ...
    \include{fileI}
    \include{fileII}
\end{document}
```

Command `\includeonly` used in preamble can choose parts in the parts you include, so the compiler will ignore other includeing parts when displaying the PDF. Note that the other parts actually will be compiled.

Another command `\input{file_name.extension}` just copy what in the selected file to the command's position. It can be used in any place of the file including the preamble and it can be also nested.

```latex
\input{configuration.tex}

\begin{document}
    ...
\end{document}
```

In the file input, command `\endinput` marks the end of the inputting. Hence, we can put comments in the rest of the file without the comment symbol.

```latex
...
\endinput

This will not be input.
```

## 2.3.6 Chapter's Style

The chapter's style is defaultly fixed. So, we need package **titlesec** to change it. See how to do it in "./rsc/titlesec.pdf".

In package **ctex**, the `\CTEXsetup` can change the style of the chapter. See "./zh/Chapter_zh.tex".

## 2.3.7 Grammar Check

Package **syntonly** provides a command `\syntaxonly` which is used in preamble and makes the compiler only check the grammar of the file and not output div or pdf file.

```latex
\usepackage{syntonly}

\syntaxonly
```
