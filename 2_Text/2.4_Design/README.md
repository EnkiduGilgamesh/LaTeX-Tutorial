# 2.4 Design

- [2.4 Design](#24-design)
  - [2.4.1 Document](#241-document)
    - [2.4.1.1 Basic Classes](#2411-basic-classes)
    - [2.4.1.2 Paper design](#2412-paper-design)
    - [2.4.1.3 Page Style](#2413-page-style)
  - [2.4.2 Multiple Columns](#242-multiple-columns)
  - [2.4.3 Command Definition](#243-command-definition)
    - [2.4.3.1 Newcommand](#2431-newcommand)
    - [2.4.3.2 Renewcommand](#2432-renewcommand)
    - [2.4.3.3 Providecommand](#2433-providecommand)
  - [2.4.4 Environment Definition](#244-environment-definition)

## 2.4.1 Document

### 2.4.1.1 Basic Classes

Basic document classes include article, report and book.

Document class options are:

| Types | Options | Specification
| --- | --- | --- |
| Paper | a4paper | 21.0cm*29.7cm |
|  | a5papar | 14.8cm*21.0cm |
|  | b5paper | 17.6cm*25.0cm |
|  | letterpaper | 8.5in*11in |
|  | leagalpaper | 8.5in*14in |
| Direction | landscape | Horizontal paper |
| Side | oneside | One side paper |
|  | twoside | Two sides paper |
| Text Size | 10pt |  |
|  | 11pt |  |
|  | 12pt |  |
| Column | onecolumn | One column design |
|  | twocolumn | Two columns design |
| Tiltle | titlepage | Title in a single page |
|  | notitlepage | Title in the first page |
| Chapter | openright | Chapter begins in odd number page |
|  | openany | Chapter begins in any page |
| Formula | leqno | The number of formula is in the left |
|  | fleqn | Formulas align in the left with a steady indent |
| Drafts | draft | Overflowing box will be display as a black block |
|  | final | Final draft |
| Reference | openbib | Reference will be seperated into several parts |

Basic classes' default options are:

| Document Class | Default options |
| --- | --- |
| article | letterpaper, 10pt, oneside, onecolumn, notitlepage, final |
| report | letterpaper, 10pt, oneside, onecolumn, titlepage, final, openany |
| book | letterpaper, 10pt, twoside, onecolumn, titlepage, final, openright |

For Chinese, ctex provides ctexart, ctexrep and ctexbook classes which is similar to English classes. See more details in "./zh/Design_zh.tex"

For example

```latex
\documentclass[leagalpaper, landscape, 12pt, twocolumn]{article}
```

### 2.4.1.2 Paper design

![Page Design](https://github.com/EnkiduGilgamesh/PicBed/blob/main/Image_LaTeX/20210927-Page_Design.jpg?raw=true)

The graphic is drawed by package **layout**.

These parameters can affect each other, so that we need to set them very carefully. For example, if we need to set the distance of right margin, we need to calculate it through the equation underneath:

$$
1 in+hoffset+oddsidemargin+textwidth+right\_margin=paperwidth
$$

Package **geometry** make it easier.

```latex
\usepackage{geometry}

\geometry{a4paper, left=3cm, right=3cm}
```

See more details in "./rsc/geometry.pdf".

### 2.4.1.3 Page Style

Page style contains page number, footer, and header.

Set the style of page number simplily by using command `\pagenumbering{}`, for example:

```latex
\pagenumbering{roman}
```

It is equal to the command underneath which uses the counter:

```latex
\renewcommand\thepage{\roman{page}}
```

We can also set the page style by using the predefined options.

| Options | Specification |
| --- | --- |
| empty | No page footer and header |
| plain | No page header, and page footer is centering page number |
| headings | No page footer, and page header is chapter name and page number |
| myheadings | No page footer, and page header and number are custom text |

```latex
\pagestyle{headings}
\thispagestyle{plain}
```

When using myheadings, we can change the page style like underneath:

```latex
\markright{page_header}         % one side page
\markboth{left_page_header}{right_page_header} % two sides page
```

Package **fancyhdr** provide more options to change the page style. See more details in "./rsc/fancyhdr.pdf"

## 2.4.2 Multiple Columns

Except the twocolumn options in document class, we can use `\twocolumn` and `\onecolumn` to switch the number of columns. These commands always start a new page with the configuration. Also, we can put a title in the beginning of the multiple page.

```latex
\twocolumn[\maketitle]
\chapter{...}

\onecolumn
```

In multiple page, the command `\newpage` and `\pagebreak` means going into next column, while `\clearpage` and `\cleardouble` page means going into next page.

The distance between two columns is controlled by `\colunmsep` and the width of a column is controlled by `\columnwidth`, which value is equal to $(textwidth-columnsep)/2$ and is not recommendated to be modified.

The width of the vertical line is controlled by `\columnseprule` whose default value is 0pt meaning that there is not a line.

Defaultly, only when one column is full of text, the next column will be used, which makes the unbalanced of two columns. Package Balance provide a simple command `\balance` to make it balanced with `\nobalance` in contrast.

```latex
\usepackage{balance}
\balance
```

Package **multicol** provide more powerful functions of multiple columns, package **flowfram** can make arbitrary columns in any area of one page which is loved by magazine and newspaper, and package grid can set steady height and width just like putting all the letter in grids to make the alignment better. See more details in "./rsc/balance.pdf", "./rsc/flowfram.pdf" and "./rsc/grid.pdf".

## 2.4.3 Command Definition

### 2.4.3.1 Newcommand

We can use `\newcommand` to define a new command. Its grammer is underneath:

```latex
\newcommand\thecommand[number_of_parameters][default_first_parameter]{definition}
```

For example:

```latex
\newcommand\PRC{People's Republic of \emph{China}}
\newcommand\love[2]{#1 loves #2 very much}
\newcommand\hate[3][hate]{#2 #1 #3}
```

For the second command, when we use `\love{Peter}{Jane}`, it will ouputs:
> Peter loves Jane very much

And for the third command, we can use custom text in **[]** to replace the default parameter:

```latex
\hate[don't like]{I}{it}
```

The output will be:
> I don't like it

NOTE: There is only one default parameter allowed.

### 2.4.3.2 Renewcommand

`\renewcommand` is used to redifine a existing command in $\LaTeX$. Its grammer is the same as `\newcommand`.

The command difinition could be nested, for example:

```latex
\newcommand\Emph[1]{\emph{#1}}
\newcommand\setEmph[1]{
    \renewcommand\Emph[1]{
        #1{##1}
    }
}
```

In this example, `\Emph` defines a new command which is equal to to `\emph` originally. But when we use `\setEmph\textbf`, the `\Emph` will be changed and it will be equal to `\textbf` after changed.

NOTE: The #\#1 means the parameter is the internal parameter.

### 2.4.3.3 Providecommand

`\providecommand` will check if the command is defined firstly. If it has been defined, it will not work.

## 2.4.4 Environment Definition

The environment definition also contains `\newenvironment` and `\renewenvironment`. Their grammers are:

```latex
\newenvironment{envname}[num_of_par][default_par]{fomer_def}{latter_def}
```

For example

```latex
\newenvironment{Abstract}[1][Abstract]
    {\small
     \begin{center}\bfseries #1\end{center}
     \begin{quotation}}
    {\end{quotation}}
```

NOTE: The parameter can be only used in fomer_def, and is not allowed to be used in latter_def. So we can do like the example underneath:

```latex
\newenvironment{Quotation}[1]
    {\newcommand\quotesource{#1}
     \begin{quotation}}
    {\par\hfill From \textit{\quotesource}
     \end{quotation}}
```
