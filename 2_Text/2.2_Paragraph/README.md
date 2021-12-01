# 2.2 Paragraph

- [2.2 Paragraph](#22-paragraph)
  - [2.2.1 Indent](#221-indent)
  - [2.2.2 Alignment](#222-alignment)
  - [2.2.3 Hyphenation](#223-hyphenation)
  - [2.2.4 Paragraph Width](#224-paragraph-width)
  - [2.2.5 Paragraph Shape](#225-paragraph-shape)
  - [2.2.6 Text Environment](#226-text-environment)
  - [2.2.7 Enumerate Environment](#227-enumerate-environment)
    - [2.2.7.1 Introduction](#2271-introduction)
    - [2.2.7.2 Enumerate](#2272-enumerate)
    - [2.2.7.3 Custom Counter](#2273-custom-counter)
    - [2.2.7.4 Itemize](#2274-itemize)
    - [2.2.7.5 Description](#2275-description)
    - [2.2.7.6 List Environment](#2276-list-environment)
  - [2.2.8 Theorem Environment](#228-theorem-environment)
  - [2.2.9 Verbatim Environment](#229-verbatim-environment)
  - [2.2.10 Code Environment](#2210-code-environment)
  - [2.2.11 Tabbing Environment](#2211-tabbing-environment)
  - [2.2.12 Vertical Box](#2212-vertical-box)
    - [2.2.12.1 Vspace](#22121-vspace)
    - [2.2.12.2 Minipage](#22122-minipage)
    - [2.2.12.3 Parbox](#22123-parbox)
    - [2.2.12.4 Rule Box](#22124-rule-box)
    - [2.2.12.5 Strut](#22125-strut)
    - [2.2.12.6 Raise Box](#22126-raise-box)
  - [2.2.13 Page Turning](#2213-page-turning)
  - [2.2.14 Footnote](#2214-footnote)
  - [2.2.15 Margin Paragraph](#2215-margin-paragraph)

## 2.2.1 Indent

Indent is the width that the the leftmost text of a line is away from the lefr margin.

In $\LaTeX$, the first line of the first paragraph has no indent, while other paragraphs' first lines' indent is as wide as 2em.

Command `\indent` and `\parindent` makes a box that is as wide as an indent. Command `\noindent` makes the paragraph no indent.

```latex
The first line. \par
The second line. \par
\noindent The third line. \par
\indent The forth line. \par
\indent\indent The fifth line. \par
```

## 2.2.2 Alignment

The paragraph defaultly distributes evenly between two margins.

Command `\raggedleft` makes paragraph not align at left margin, so it means that the paragraph will align at right. The command `\raggedright` is on the contrary.

```latex
\raggedleft I am at the right margin. \par
\raggedright I am at the left margin.
\centering I am at the center.  
```

Another way to change the alignment is to use environment.

```latex
\begin{flushright}              % Align at right
    Hello!\par
    I am at the right margin. 
\end{flushright}
\begin{center}                  % Align at center
    Hello!\par
    I am in the center. 
\end{center}
```

## 2.2.3 Hyphenation

Hyphenation would be used when a long word can not put into the left space of a line.

Use the \- command to tell the compiler where you want to use a hyphenation, so the compiler will try to make hyphenation there.

```latex
The is a very very very very very very very very 
long sentence with a long\-longlonglong word. 
```

NOTE: The hyphenation is only used in distributed alignment.

Package **Ragged2e** can use hypenation in other alignment environment. The package also provides `justify` environment and `\justifying` declaration command to go back to distributed alignment.

TODO: \sloppy, \fussy

```latex

```

Package **microtype** can adjust the distance between letters in words to improve the wrapping around in $\pdfTeX$. Now, it can support $\XeLaTeX$, too. More details about this package, see "./rsc/microtype.pdf".

## 2.2.4 Paragraph Width

To control the width of paragraphs, we need to indirectly control the width of left and right skipped space.

```latex
{
    \setlength\leftskip{10cm}
    \setlength\rightskip{2cm}
    The leftskip is the distance to the left margin, 
    and the rightskip is the distance to the right margin. 
}
```

FIXME: Why no effect?It is globally?

## 2.2.5 Paragraph Shape

A special indent is hanging indent, which can be controlled by command `\hangindent` telling the compiler the indent length, and `\hangafter` telling the comiler the amount of the lines that will use the hangindent.

```latex
{
    \hangindent=5pc \hangafter=-2           % The value of the commands can be positive or negative. 
    Donald Knuth’s TEX, a computerized typesetting system, provides nearly
    everything needed for high-quality typesetting of mathematical notations
    as well as of ordinary text. It is particularly notable for its flexibility, its
    superb hyphenation, and its ability to choose aesthetically satisfying line
    breaks. Because of its extraordinary capabilities, TEX has become the
    leading typesetting system for mathematics, science, and engineering and
    has been adopted as a standard by the American Mathematical Society. 
}
```

Package **lettrine** can generate Drop Capital effect.

```latex
\usepackage{lettrine}
...
{
    \lettrine{O}ver this period of one hundred years, the CPC has united and 
    led the people in toppling the “three mountains” of imperialism, feudalism 
    and bureaucrat-capitalism, creating the People’s Republic of China (PRC), and 
    completing the New Democratic Revolution and the Socialist Revolution. The 
    political and institutional foundations were thereby laid down to ensure 
    the rights and freedoms of the people. Through successes and setbacks, 
    China has pioneered reform and opening up, set the goal of socialist modernization, 
    and ushered in a new era of building socialism with Chinese characteristics. 
    The Chinese nation has stood up, become better off, and grown in strength. 
    Now, it is embarking on a new journey to build a modern socialist country in all respects.
}
```

TODO: How to let the Drop Cap not in margin?

Command `\parshape` can compose much special shaped paragraph. Donald E. Knuth's book *Computers & Typesetting, Volume A: The TeXbook* tells how to use it specificly. Or see "./rsc/teximpat.pdf"

Package **shapepar** provide some simple APIs of \parshape, and predefines some shapes that can be directly used. For more details, see "./rsc/shapepar.pdf"

```latex
\usepackage{shapepar}
...
\heartpar{
    Green, green the reed,
    Dew and frost gleam.
    Where’s she I need?
    Beyond the stream.
    Upstream I go,
    The way is long.
    Downstream I go,
    She’s thereamong.
    White, white the reed,
    Dew not yet dried.
    Where’s she I need?
    On the other side.
    Upstream I go,
    Hard is the way.
    Downstream I go,
    She’s far away.
    Bright, bright the reed,
    Dew and frost blend.
    Where’s she I need?
    At river’s end.
    Upstream I go,
    The way does wind.
    Downstream I go,
    She’s far behind.
}
```

## 2.2.6 Text Environment

$\LaTeX$ has predefined quote, quotation, verse, and abstract text environment.See the examples:

```latex
\begin{abstract}        % Used in the beginning of the article
    This article is about Paragraph and Environment.
\end{abstract}
```

NOTE: The abstract environment name is configured by \abstractname.
TODO: How to set your own abstact name?

```latex
In the film \textit{The Shawshank Redemption}, Reid said, 
\begin{quote}           % no indent
    Some birds are not meant to be caged; their feathers are just too bright. 
\end{quote}
```

```latex
There are such paragraphs in \textit{The Communist Party of China and Human Rights Protection -- A 100-Year Quest}
\begin{quotation}       % indent
    The year 2021 marks the centenary of the Communist Party of China (CPC). 
    Over the past century, the CPC has invested a huge effort in human rights 
    protection, adding significantly to global human rights progress.

    A hundred years ago, the CPC came into being – its mission to salvage the 
    country and save the Chinese people at a perilous time of domestic upheaval 
    and foreign aggression. This was an epoch-changing moment. Under the leadership 
    of the CPC, the Chinese people embarked on a new journey towards prosperity, 
    national rejuvenation, and wellbeing.
\end{quotation}
```

```latex
The \textit{Where is She?} is a Chinese classical poemtry in \textit{the Book of Songs}
\begin{verse}
    Green, green the reed,
    Dew and frost gleam.
    Where’s she I need?
    Beyond the stream.
    Upstream I go,
    The way is long.
    Downstream I go,
    She’s thereamong.
    
    White, white the reed,
    Dew not yet dried.
    Where’s she I need?
    On the other side.
    Upstream I go,
    Hard is the way.
    Downstream I go,
    She’s far away.
    
    Bright, bright the reed,
    Dew and frost blend.
    Where’s she I need?
    At river’s end.
    Upstream I go,
    The way does wind.
    Downstream I go,
    She’s far behind.
\end{verse}
```

## 2.2.7 Enumerate Environment

### 2.2.7.1 Introduction

In $\LaTeX$, there are three kinds of enumerate environment. They are **enumerate**, **itemize**, **description**. They are used like:

```latex
The first situation is: 
\begin{enumerate}               % number
    \item The first
    % The command \item have a parameter to configure personalized number or keyword. 
    \item The second
    \begin{itemize}             % no number
        \item The first
        \item The second
        \begin{description}     % customer text
            \item[1st] One
            \item[2nd] two
            \item[3rd] Three
        \end{description}
        \item The third
    \end{itemize}
    \item The third
    \item[3a] The A part of the  third                       % manual number
    \item[\dag] The most important part of the third                       % special symbol
\end{enumerate}
```

NOTE: Enumerate environment can be nested in four levels.

### 2.2.7.2 Enumerate

The number of the enumerate is controlled by a group of counters:

+ Whenever enter a new enumerate environment, the counter will be reset to 0
+ Whenever meet a `\item` without parameter, the counter plus 1
+ There are four default counter in LaTeX, whose name are enumi, enumii, enumiii, enumiv

Command `\the` or `label` with conuter_name behind will outout the value of the counter and for the latter one, a dot will follow the number with lable command. Actually, the enumerate environment use it to output the number.

```latex
\theenumi \\
\labelenumi
```

There are several styles that conter number can change to.

| | | |
| --- | --- | --- |
| \arabic | \roman | Roman |
| \alph | \Alph | \fnsymbol |

Different levels of counters will defaultly use different styles of counter number, which are set ahead of time.

TODO: sum the styles of different levels of counter

We can manully choose one of styles for a counter when we use enumerate environment.

```latex
{
    \renewcommand\theenumi{\roman{enumi}}
    \begin{enumerate}
        \item The first
        \item The second
    \end{enumerate}
}
```

Except the enumerate environment, the pages, sections, and so on also use counter. For example:

```latex
This sentence is in Page \thepage.
```

### 2.2.7.3 Custom Counter

It would be needed to define your own counter.

```latex
\newcounter{mycnt}
\setcounter{mycnt}{0}                                             % set the origin value
\renewcommand\themycnt{\arabic{mycnt}}
\stepcounter{mycnt}The counter's value is \themycnt . \par        % the counter plus 1
\stepcounter{mycnt}The counter's value is \themycnt . \par
\addtocounter{mycnt}{2}The counter's value is \themycnt . \par    % the counter plus 2
\addtocounter{mycnt}{-3}The counter's value is \themycnt . \par   % the counter subtract 1
```

The `\newcounter` could be followed by another counter name as its parameter. That means when the counter used in parameter increases, the newcounter will be reset to zero. That is how counter subsection, subsubsection... work.

```latex
\newcounter{enumv}[enumiv]
```

The command `\value{counter}` will return the value of the certain counter as a parameter.

TODO: An example

Package **amsmath** extends the function of counter, so that it will be more friendly in math equation. Package **chngcntr** provides function similar to amsmath. See more details in "./rsc/amsmath.pdf" and "./rsc/chngcntr.pdf".

Further, the counter can be used in complex condition control and loop. Package **ifthen**, and **calc** provide some function of them. See more details in "./rsc/ifthen.pdf" and "./rsc/calc.pdf"

### 2.2.7.4 Itemize

There are also serveral styles of tags for itemize environment.

| | |
| --- | --- |
| \textbullet | \normalfont\bfseries \textendash |
| \textasteriskcentered | \textperiodcentered |

The \item actually use the \lableitemi, \labelitemii..., command to replace itself. So we can reset the command to another style like enumerate.

```latex
\renewcommand\labeliremi{\textasteriskcentered}
```

### 2.2.7.5 Description

Also, we can modify the style of description environment's number label which is defined by the \descriptionlabel.

```latex
\renewcommand\descriptionlabel[1]{\normalfont\Large\itshape\textbullet #1}
```

### 2.2.7.6 List Environment

Enumerate, itemize, description are all defined in **list** environment.

The list is usually used to define new environment, of course, it can be used directly with the similar gramer to the definition. It has many parameters. See the pictures.

![2021-10-05-List_Environment](https://raw.githubusercontent.com/EnkiduGilgamesh/PicBed/main/Image_LaTeX/2021-10-05-List_Environment.jpg)

```latex
\newenvironment{myitemize}{% define list environment myitemize
    \begin{list}{\textbullet}{%
        \setlength\topsep{0pt} \setlength\partopsep{0pt}
        \setlength\parsep{0pt} \setlength\itemsep{0pt}
    }}
    {\end{list}}

\begin{document}
    \begin{myitemize}
        \item One
        \item Two
    \end{myitemize}
\end{document}
```

There is another special environment **trivlist**  which can generate a list environment without number label.

Some environments that seems like irrelevant with enumerate, are usually defined by it. For example, the **center** enviroment is defined by it. The definition is the same as the mycenter in Introduction.

```latex
\newenvironment{mycenter}{% define trivlist environment mycenter
    \begin{trivlist}
        \centering\item[]}     
    {\end{trivlist}}

\begin{document}
    \begin{mycenter}
        One\par
        Two
    \end{mycenter}
\end{document}
```

For more standard classes' definition in $\LaTeX$, see in "./rsc/standardclasses.pdf".

The list environment is a little complex to use, and the enumerate environment configuration is not easy to change, too.

Package **enumitem** provide methods to use parameters in enumerate. See the documentation "./rsc/enumitem.pdf". A simple way to use it has given underneath.

```latex
\usepackage{enumitem}

\begin{enumerate}[
itemsep=0pt, parsep=0pt, lable=(\arabic*)]
    \item One
    \item Two
\end{enumerate}
```

FIXME: label undifined

## 2.2.8 Theorem Environment

The theorem environment will generate a title, a number and text with a certain style.

```latex
\newtheorem{thm}{Theorem}[section]

\begin{document}
    \begin{thm}[the Pythagorean theorem]
        The square of the hypotenuse of a right triangle is equal to 
        the sum of the squares of the two sides. 
    \end{thm}

    \begin{thm}
        The two sides of a triangle add up to more than the third. 
    \end{thm}
\end{document}
```

The parameter in **[]** is a counter or other theorem environment which is optional.

However, the theorem environment's style is unchangable.

The package **theorem** and **ntheorem** provide some comamnds to change the style of theorem environment. See "./rsc/ntheorem.pdf" and "./rsc/theorem.pdf". The package **thmtools** make it easier to use ntheorem and amsthm. See "./rsc/thmtools.pdf".

## 2.2.9 Verbatim Environment

It's difficult to use special symbol or punctuation in $\LaTeX$, especially when you want to use it frequently.

Verbatim can output what you put without regard them as special symbos in typewriter font.

It begin with a symbol and end with a same symbol as the beginner no matter what you use.

```latex
\verb"\/{}#$%&~!"\par
\verb!\LaTeX \& \TeX!\par
\verb*"1 2  3   4"
```

Verbatim can be also used as an environment.

```latex
\begin{verbatim}
    #!usr/bin/env perl
    $name = "guy"; 
    print "Hello, $name!\n"; 
\end{verbatim}
```

The verbatim and other environment can not be used as a parameter in other command.

We can use lrbox environment to save them as a customer box and then use the box as a parameter.

```latex
\newsavebox\verbbox  % define verbbox       
\begin{lrbox}\verbbox
    \verb"#$%^&*()"
\end{lrbox}
...
\usebox\verbbox \fbox{\usebox\verbbox}\par
```

Package **fancyvrb** provides some special commands help us do the above like underneath. Also, fancyvrb extends the verbatim so that we can modify its font, frames, color and so on. See more details in "./rsc/fancyvrb.pdf".

```latex
\usepackage{fancyvrb}

\SaveVerb{myverb}|#$@$%^&|
\fbox{\UseVerb{myverb}}\par
```

The package **cprotect** does the similar things to the fancyvrb.

```latex
\cprotect\fbox{\verb|#$@$\%^&|}\par
```

Package **verbatim** extends the verbatim environment, which also provides a command `\verbatiminput` to copy the text in the file you give to it. See more details in "./rsc/verbatim.pdf"

The package can also define a very short name to `\verb`. It should be noticed that the symbol you define may conflict with some commands you use behind.

```latex
\usepackage{verbatim}

\MakeShortVerb" % use " as the verbatim symbol
"\LaTeX"
```

## 2.2.10 Code Environment

Package **listings** provides various languages' environment with code highlighting:

```latex
\usepackage{listings}

\begin{document}
    \begin{lstlisting}[language=C]
        /* hello.c */
        # include <stdio.h>
        void main(){
            printf("Hello. \n"); 
        }
    \end{lstlisting}
\end{document}
```

We can also custom the style of the highlighting:

```latex
\lstset{
    numbers=left,               % code rows numbers
    numberstyle=\footnotesize,
    basicstyle=\sffamily,
    keywordstyle=\bfseries,
    commentstyle=\rmfamily\itshape,
    stringstyle=\ttfamily
}
```

TODO: The package can also insert an inline code.

```latex

```

The package can also set the color, the background, etc. for the code or the code block. See more details in "./rsc/listings.pdf"

## 2.2.11 Tabbing Environment

The tabbing environment is defined to help to use TAB for composing. It is used like:

```latex
\begin{tabbing}
    Style\hspace{3em} \= Author \\
    Plain \TeX \> Donald \\
    LaTeX \> Leslie Lamport
\end{tabbing}
\noindent\hfill$*$\hfill$*$\hfill$*$\hfill
\begin{tabbing}
    Style\hspace{3em} \= Author \kill
    Plain \TeX \> Donald \\
    LaTeX \> Leslie Lamport
\end{tabbing}
```

The `\kill` controls if the first row displays. Other commands used in tabbing environment show in the table below:

| | |
| --- | --- |
| \\= | set a TAB |
| \\' | the text front and latter will be centered around the current TAB |
| \\` | align right for the latter text |
| \\< | skip to the former TAB |
| \\> | skip to the latter TAB |
| \\+ | every line behind current line skips to the right one time |
| \\- | every line behind current line skips to the left one time |
| \pushtabs | save the current TAB |
| \poptabs | recover the TAB saved by \pushtabs |

The common commands above in tabbing environment are replaced by `\a=`, `\a'`, `\a` and so on.

There is a complex example.

```latex
\newcommand\kw{\textbf}
\begin{tabbing}
    
    \pushtabs
    Algorithm: Do a binary search for x in list[L, H]. \\
    \qquad\=\+\kw{interger} $L, H, M, J$\\
    \kw{while} \=\+ $L \leq H$ \kw{do} \` $L$ and $H$ are left and right margins. \\
        $M \gets \lfloor(L+H)/2\rfloor$ \` $M$ is the center dot. \\
        \kw{case} \=\+\\
            condition \= foo \+\kill
            $x > A[M]$: \' $H \gets M-1$ \\
            $x < A[M]$: \' $H \gets M+1$ \\
            \kw{else}: \' \= $j \gets M$ \` Find $x$ and return its place. \\
                \> \kw{return}$(j)$ \\
        \<\< \kw{endcase} \-\-\-\\
    $j \gets 0$\\
    \kw{return}$(j)$ \-\\
    \poptabs
    Example: \\
    $A = \{2, 3, 5, 7, 11\}$, $x = 3$\\
    \qquad\=\+ $M$\qquad \= $L$\qquad \= $H$\qquad \= \\
                None     \> 1         \> 5          \> initial value, enter the loop \\
                3        \> 1         \> 2          \> $H$ changes \\
                2        \> None      \> None       \> find $x$, output place 2. 
\end{tabbing}
```

## 2.2.12 Vertical Box

### 2.2.12.1 Vspace

The commands about vertical box, like `\vspace{length}`, `\vfill`, `\vspace{\fill}` are just like the horizontal box command. See more details in "~/LaTeX/2_Text/2.1_Letter/Letter.tex".

TODO: These commands are used in the beginning of the latter line.

```latex

```

### 2.2.12.2 Minipage

Minipage environment can generate a box with height and width, just like a mini page.

```latex
There is another 
\begin{minipage}{4em}
    paragraph box
\end{minipage}. 
```

The paragraph configured like `\parindent`, `\parskip` and so on can be used in minipage environment.

The minipage is similar to parbox.

```latex
There is a \parbox{4em}{paragraph box}. 
```

### 2.2.12.3 Parbox

Command `\parbox` and minipage has three optional parameters. And the total command is `\parbox[base_line_position][height][text_position]{width}{text}`

The *base_line_position* is the box position and it can use **c-center, t-top, b-buttom**, which is defaulty c. The *text_position* is the text in the box's position, and it can use **c, t, b**, and **s-distributed**.

```latex
\begin{minipage}[c][2.5cm][t]{5em}
    The grass grows  
\end{minipage}
\begin{minipage}[c][2.5cm][c]{8em}
    on the edge of a lonely stream,
\end{minipage}
\begin{minipage}[c][2.5cm][b]{15em}
    and there is a spring tide with the sound of deep trees. 
\end{minipage}
\begin{minipage}[c][2.5cm][s]{14em}
    \setlength\parskip{0pt plus 1pt}
    When showers fall at dusk, the river overflows; \par
    A lonely boat athwart the ferry floats at ease.
\end{minipage}
```

In *2.2.9 Verbatim*, the `\verb` can save in the lrbox, while the verbatim environment can not. We can write the verbatim in minipage, and then save it in lrbox.

```latex
\newsavebox\verbatimbox
\begin{lrbox}\verbatimbox
    \begin{minipage}{20em}
        \begin{verbatim}
            #!/bin/sh
            cat ~/${file}$
        \end{verbatim}
    \end{minipage}
\end{lrbox}
...
\fbox{\usebox\verbatimbox}\quad\fbox{\usebox\verbatimbox}
```

Package **fancyvrb** also provides `\SaveVerbatim` and `\UseVerbatim` to do the above job.

Package **varwidth** provides varwidth to generate environment with settled max width, so the width can be changed with your text input.

```latex
\usepackage{varwidth}
...
 \fbox{
    \begin{varwidth}{10cm}
        Natural \par
        width
    \end{varwidth}
}
```

### 2.2.12.4 Rule Box

Rule box is a solid box fill with ink. Its whole command is `\rule[lift_distance]{width}{height}`.

```latex
\rule{1pt}{1em}Middle\rule{1pt}{1em}\par
Left\rule[0.5ex]{2cm}{0.6pt}Right\par
\rule[-0.1em]{1em}{1em}Prove comlete. 
```

### 2.2.12.5 Strut

Strut means a placeholder, whose width or height is 0. It is similar to the `\phantom`. $\LaTeX$ has predefined `\strut` whose height is as high as current font size.

```latex
\fbox{---}\par
\fbox{\strut---}\par
\fbox{\rule{0pt}{2em}---}
```

### 2.2.12.6 Raise Box

Raise box is used to generate a box with lift distance, and we can put our text in it. That is how the `\TeX` symbol appears.

Its whole command is `\raisebox{lift_distance}{height}[depth]{text}`.

```latex
\mbox{T\hspace{-0.49em}
    \raisebox{-0.5ex}{E}
    \hspace{-0.48em}X}\quad
\TeX{}
```

## 2.2.13 Page Turning

There are several commands to do with page turning.

* `\raggedbottom` means that every page will keep their natural height.
* `\flushbottom` means that all the page will align at the buttom of the paper.
* `\pagebreak[rank]` can skip to the next page with four ranks, 0, 1, 2 and 4, with 4 in force, `\nopagebreak` on the contrary.

```latex
\pagebreak[4]
```

Command `\enlargethispage{length}` can increase the height of the page provisionally.

```latex
\enlargethispage{8em}
```

NOTE: `\newpage` can skip to the next page manually. It is actually equal to the `\paragraph` and then `\vfill` the middle text. It can not work continuously, if it needed, use a `\mbox{}` in every blank page.

```latex
\newpage
\mbox{}
\newpage
```

TODO: \clearpage, \cleardoublepage and float.

## 2.2.14 Footnote

Footnote explains details about some message you have referenced in paragraphs.

The `\footnote` uses the counter footnote, and in minipage it uses mpfootnote. But the `\footnote` has a optional parameters can replace the number.

TODO: use footnote in minipage

```latex
This is a footnote\footnote{\textbackslash footnote\{text\}}. \par
This is another foodnote\footnote[1]{The footnote number is still 1}. 
```

We can also change the footnote number to what we love.

```latex
\renewcommand\thefootnote{\fnsymbol{footnote}}
A symbol number footnote\footnote{}. \par
\renewcommand\thefootnote{\textcircled{\arabic{footnote}}} % circled number
A circled number footnote\footnote{}. 
```

The circled number is ugly, we can use package **pifont** instead. `\ding` outputs the character whose encoding is the number we put. See more details in "./rsc/psnfss2e.pdf"

```latex
\renewcommand\thefootnote{\ding{\numexpr171+\value{footnote}}}
A more beautiful circled number foootnote\footnote{}. 
```

The footnote can not used in box or table. But we could use `\footnotemark` and `\footnotetext` instead. For example:

```latex
\begin{tabular}{r|r}
    Independent variable & Dependent varible\footnotemark \\
    \hline
    $x$ & $y$
\end{tabular}
\footnotetext{$y=x^2$}
```

Footnote is not allowed to be used in section and annotation directly, because it is a **fragile command**. If we want to use it in such environments, use `\protect` in front.

```latex
\section{Footnote\protect\footnote{Footnote in the section}}
```

The line space between footnote is set by `\footnotesep`. And the line between text and footnote is set by `\footnoterule`.

Package **footmisc** provides more command to configure footnote. See "./rsc/footmisc.pdf"

## 2.2.15 Margin Paragraph

The marginpar will display in the margins.

```latex
The marginpar will display in the margins\marginpar{Marginpar}. \par
```

The text will display in the left side margin in even number page whereas in the right side margin in odd number

The marginpar have an option meaning that the text in option will display if the marginpar is in even page.

```latex
\marginpar[\hfill 左 $\rightarrow$]{$\leftarrow$ 右}
```

Command `\reversemarginpar` will exchange the position of marginpar in even and odd page, and `\normalmarginpar` will reset to the defualt position.

For further configuration about marginpar, see package **marginnote** in "./rsc/marginnote.pdf"
