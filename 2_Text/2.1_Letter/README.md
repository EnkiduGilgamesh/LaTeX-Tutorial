# 2.1 Letter and Symbol

- [2.1 Letter and Symbol](#21-letter-and-symbol)
  - [2.1.1 Letter](#211-letter)
    - [2.1.1.1 Accent](#2111-accent)
    - [2.1.1.2 Other Letter](#2112-other-letter)
    - [2.1.1.3](#2113)
    - [2.1.1.3 Ligature](#2113-ligature)
  - [2.1.2 Punctuation](#212-punctuation)
    - [2.1.2.1 Common Punctuation](#2121-common-punctuation)
    - [2.1.2.2 Special Punctuation](#2122-special-punctuation)
    - [2.1.2.3 Other Symbol](#2123-other-symbol)
  - [2.1.3 Blank](#213-blank)
  - [2.1.4 Wrap Around](#214-wrap-around)
  - [2.1.5 Font](#215-font)
    - [2.1.5.1 Basic Fonts](#2151-basic-fonts)
    - [2.1.5.2 NFSS System](#2152-nfss-system)
    - [2.1.5.3 More Font](#2153-more-font)
    - [2.1.5.4 Math Font](#2154-math-font)
    - [2.1.5.5 Flaw in Font](#2155-flaw-in-font)
    - [2.1.5.6 Important to Know](#2156-important-to-know)
  - [2.1.6 Emphasize](#216-emphasize)
  - [2.1.7 Font Size](#217-font-size)
  - [2.1.8 Line Space](#218-line-space)
  - [2.1.9 Horizontal Space](#219-horizontal-space)
  - [2.1.10 Box](#2110-box)

## 2.1.1 Letter

### 2.1.1.1 Accent

Accent is a usual way to indicate the stress or special pronunciation in English.

$\LaTeX$ provides many kinds of letters' accents. The table underneath shows some examples that are build-in command:

|  |  |  |  |  
| --- | --- | --- | --- |
| \\&#95;o | \'o | \^o | \"o |
| \~o | \=o | \aa | \SS |
| \t{oo} | H{o} | \i | \ae |

See more details in the given code in "./Letter.tex".

### 2.1.1.2 Other Letter

TODO: how to input and output other letters

```latex
\textgreek{abcde}

{\fontencoding{OT2}\selectfont ABCDE}
```

### 2.1.1.3

### 2.1.1.3 Ligature

Some letters will have ligature between each other when output using a certain font. Also, there are two simple ways that we can use to avoid it manually.

```latex
differ find flight difficult ruffle\\
dif{}fer f{}ind f\/light dif\/f\/icult ruffle
```

For pictograph, like Chinese, see "./zh/README.md"

## 2.1.2 Punctuation

### 2.1.2.1 Common Punctuation

For common punctuation, we can input them directly. They are:

|  |  |  |  |
| --- | --- | --- | --- |
| , | . | ; | : |
| ! | ? | \` | ' |
| ( | ) | [ | ] |
| - | / | * | @ |
| \| | < | > | + |
| = |

NOTICE: The punctuations above are all DCB case. For SBC case, see "./zh/README.md".

In LaTeX, we cannot input `"` directly, we input double `&#95;` for the former `"` and doule `'` for the latter `"` instead. And when `"` and `'` are close to each other, use `\,` to split them. For example:

```latex
`` ''\\
``\, ` '\, ''
```

Different number or `-` will generate different puncatuation. For example:

```latex
X-ray, 1--2, APP---Application
```

TODO: English writing rule

The Command `\dots` and `\ldots` will generate an ellipsis with wider distance between dots which has a better looking than directly using three dots punctuation.

```latex
Good: One, two, Three\dots\\
Bad: One, two, Three...

One, two, Three\dots.
% Another dots that used to be full stop could follow \dots. 
```

### 2.1.2.2 Special Punctuation

Some symbol or punctuation are occupied by LaTeX command, so they cannot iniput directly. The `\` is called escape character. Symbols following it will not be treat as the build-in definition, but treat as themselves.

```latex
\# \quad \$ \quad \% \quad \&\\
\{ \quad \} \quad \_\\
\~{} \quad \^{} \quad       % Symbol "~" and "^"
\textbackslash              % Symbol "\"
```

### 2.1.2.3 Other Symbol

Some symbols are listed underneath.

| Command | Symbol | Command | Symbol |
| --- | --- | --- | --- |
| \S | § | \dag | † |
| \ddag | ‡ | \P | ¶ |
| \copyright | © | \textregistered | ® |
| \texttrademark | ™ | \pounds | £ |
| \textbullet | • |

Package **textcomp** provides more symbols, such as:

| Command | Symbol | Command |Symbol |
| --- | --- | --- | --- |
| \texteuro | € | \textperthousand | ‰ |

NOTICE: Use `\usepackage{textcomp}` firstly.

Package **tipa** provides symbols of phonetic, while package **dingbat**, **bbding**, **pifont** provide symbols of instruction and decoration.

The file "./rsc/symbols-letter.pdf" provide a relatively overall liist of symbols.

NOTE: Some package just provide symbol command, some package provide alternative font to their symbol, while some package change the holistic font set of the artical. So please read related documentation of your package before using.

We can also use encoding of a symbol to input it.

```latex
\symbol{90} \quad           % Decimalism
\symbol{"5A} \quad          % Hexadecimal
\symbol{'132} \quad         % Octonary
\symbol{`Z}                 % Symbol itself
```

NOTE: If the symbol is special punctuation in 2.2, an escape character is also needed in front.

NOTICE: Chinese character is only allowed in **xelatex** environment.

## 2.1.3 Blank

In $\LaTeX$, A series of space is equal to a click of space. For example, `A   B` is equal to `A B`.

The space after a macro command will be ignored. There are 4 ways to avoid the ignoring situation.

```latex
\TeX ing            % 1
and \TeX\ ing       % 2
and \TeX{} ing      % 3
and {\TeX} ing.     % 4
```

In English writing, there are generally 5 situations that are not allowed wrap around between two words.

| Situation | Case |
| --- | --- |
| Name and its sort | Question 1 |
| Given name | Donald E Knuth |
| Acronym of name | Mr. Knuth |
| Short equation after its name | function $f(x)$ |
| Sequence | 1, 2, and 3 |

However, blank generating by click the space key could be interrupted them if a line is feeded. Using `~` to link two words can prevent them to be interrupted. For example:

```latex
Question~1\\
Donald~E Knuth\\
Mr.~Knuth\\
function~$f(x)$\\
1,~2, and 3\\
```

It is also needed to be noticed that, in $\LaTeX$ writing, the space must be used after ", . ; :", or the line would not wrap around correctly.

The book named *The Elements of Typographic Style by Robert Bringhurst* (I shared in "./rsc") discuss more details in English writing rules.

In $\LaTeX$, the width of the space at the end of a sentence following a dot is different from that in the sentence.

But sometimes, a dot could be used in the middle of a sentence following a samll letter like situation **4** or at the end of a sentence following a capital letter like situation **3**. In these situations, $\LaTeX$ can not distinguish if it is the end of a sentence. So, we use command `\@.` replacing `.` in the situation **3** and use `\` before a sapce in the situation **4**. For example:

```latex
A sentence. Another Sentence. \newline             % 1
U.S.A. means United States of America. \newline    % 2
Roman number XII\@. Yes. \newline                  % 3
Thinker et al.\ made the double play.              % 4
```

While you compiling Chinese documentation, a space while automatially add between Chinese and English ignoring how many space you have typed in these space. See more ddetails in "./zh/Letter_zh.tex"

The command \phantom will generating a blank boxas wide as the paremeter.

```latex
There is a phantom in the box. \\
There is a \phantom{phantom} in the box.
```

## 2.1.4 Wrap Around

In $\LaTeX$, just wrap around one time would be ignored, this peculiarity is set to help the code more legible. To begin a new paragraph, you need at least wrap around two times with a blank line in the middle.

Another way to begin a new line is to use command `\\` or `\newline` at the end of a line. Command `\\` have a parameter which set the vertical distance between two lines. For example:

```latex
This is a line. 

This is another line. \newline
This is a line. \\[5pt]
This is another line. \\[5pt]{}
[] are the beginning of this line. 
```

Command `\linebreak` have an option which specify the urgency of the line break of linebreak and be defaultly set to 4, ranging from 0 the lowest to 4 the highest meaning that the line break must occur being contrary to the command `\nolinebreak`. So the `\linebreak` or `\linebreak[4]` look like distributing the line from the left to the right margins. For example:

FIXME: How the `\linebreak[1~3]` works

>Terminates the current line and formats it in the same way as the preceding line. If that line is justified, this line would be justified as well. The optional argument \<value> takes integer values between 0 and 4 inclusive to specify the urgency of the line break; 4 means it must occur.
by the way: \linebreak has the same behaviour as \pagebreak for the vertical adjustment.

```latex
This is a line. 

This is another line. \newline
This is a line. \linebreak
This is another line. 
```

## 2.1.5 Font

### 2.1.5.1 Basic Fonts

In $\LaTeX$, every font is divided into three orthometrics dimensions--family, shape and series. The font's each style can be regarded as a combination of the three orthometrics.

There are two ways to change the font style which are font declaration and box command with parameter as the explaination in annotation. They are:

| Command | Command | Font |
| --- | --- | --- |
| {\rmfamily } | \textrm{} | Roman font |
| {\sffamily } | \textsf{} | Sanserif font |
| {\ttfamily } | \texttt{} | Typewriter font |
| {\upshape } | \textup{} | Upright shape |
| {\itshape } | \textit{} | Italic shape |
| {\slshape } | \textsl{} | Slanted shape |
| {\scshape } | \textsc{} | Small capital shape |
| {\mdseries} | \textmd{} | Medium series |
| {\bfseries} | \textbf{} | Bold extended series |

See their style in my given code.

NOTE: Since some fonts may not have all shape or series, these two command may have different effect.

The command above can be mixed to use, for example:

```latex
{\rmfamily\slshape\mdseries Mixed font I}\\
\textsf\textit\textbf{Mixed font II}
```

Chinese fonts usaully have no other variant, so different type of fonts are used to replace the variant in a font family. See more details in "./zh/Letter_zh.tex".

Command `{\normalfont }` and `\textnormal{}` are used to change the font back to normal which is `\rmfamily\mdseries\upshape` in general situation. For example:

```latex
{\sffamily \textbf{There is a \textit{complex example, but \textnormal{a normal one} is in} it}}
```

We can replace the rmfamily font:

```latex
\renewcommand\rmdefault{cmfib}
```

After this command, whenever we use `\rmfamily` or `\textrm{}`, we will choose font cmfib instead. The command is usually used in the preamble of a file.

Also we can change the artical's using default font family from rm into sf:

```latex
\renewcommand\familydefault{\sfdefault}
```

More details about English font can be found in "./rsc/hartke.pdf" and [The LaTeX Font Catalogue](https://tug.org/FontCatalogue/)

### 2.1.5.2 NFSS System

Like dividing font into three dimensions, $\LaTeX$ publish its own method to locate a font, NFSS(New Font Selection Scheme) which also dividing font into many orthometric properties, such as encoding, family, series, shape, size and so on.

The whole command to choose a font in NFSS is:

```latex
{\fontencoding{OT1}\fontfamily{pzc}\fontseries{m}\fontshape{n}\fontsize{14}{17} %
\selectfont PostScrip New Century Schoolbook}\\
% or
{\usefont{T1}{pbk}{db}{n} PostScrip Bookman Demibold Normal. }
```

NOTE: The first parameter in fontsize is letter's size, and the second one is line spacing.

### 2.1.5.3 More Font

To use other fonts, the simpleest way is to use font package, such as **times**, **mathptms**, **txfonts** and so on.

The package **fontspec** contains commands that can use other font to replace the default font in latex.

```latex
\usepackage{fontspec}
\setmainfont{font1}       % change the \rmfamily
\setsansfont{font2}       % change the \sffamily
\setmonofont{font3}       % change the \ttfamily
```

NOTE: In Chinese environment, because of CJK package, the commands are different, see in "./zh/Letter_zh.tex".

Package **fontspec** can also define new font famlily if needed.

```latex
\newfontfamily\inkfamily{Ink Free}
{\inkfamily Hello!}
```

NOTE: Different font may need different encoding.

For example, if you want to use font package ccfonts and euler for better harmony of text and math part, you need to use T1 encoding.

```latex
\usepackage[OT1,T1]{fontenc}
```

The multiple parameters are the encoding ways of the article, with the final one the default one.

### 2.1.5.4 Math Font

Generally LaTeX using italic font in math parts of the article. And commands `\mathrm{}`, `/mathsf{}`, `/mathtt{}`, and so on can change the math parts font, which is configured defualtly as the same with `\text**{}`.

```latex
\begin{equation}
    AB^2 = BC^2 + AC^2. 
\end{equation}
\begin{equation}
    \mathrm{AB^2 = BC^2 + AC^2. }
\end{equation}
```

Some math font packages can change the math parts font, but whether it is useful to above commands depanding the package whether loads "no-math" module in fontspec.

If it doesn't, like package ccfonts, and you want to change the configuration of these command like \mathrm{}, just manually load the module by command `\usepackage[no-math]{fontspec}`

TODO: Situation may go complex when we use both English which not support Unicode and Chinese in one article, See the book in Page 74 for some help.

### 2.1.5.5 Flaw in Font

The right part of a slanted letter may be too close to next letter. The methods underneath can revise this problem.

```latex
{\itshape M}M \quad \textit{M}M \quad {\itshape M\/}M\\
\textit{M\nocorr}M\newline         % Forbid the revise.
```

Bold letters may be also too close to the puntuation following it.

```latex
`{\bfseries leaf}' \quad `{\bfseries leaf\/}' \quad `\textbf{leaf}'
```

Command `\nocorrlist{}` can set a punctuation that are forbiden the revise. `\nocorrlist{}` is defualt set with "," and "." in it which is the same as `\newcommand\nocorrlist{,.}`.

### 2.1.5.6 Important to Know

NOTE: $\LaTeX$ only use one encoding in one time. That may make mistakes when you use fonts in different encoding.

If you need different encodings, you need change it manually.

There is an example: in Greek and fontspec package. $\XeLaTeX$ uses Unicode encoding, while the command `\textipa` in **tipa** package which outputs IPA works in ASCII.
So when you compile command `\textipa{}`, the compiler will change the IPA's encoding from ASCII into Unicode, which can not output by default font Latin Modern because it lack these endoing.

To solve this problem, you just need use font containing IPA in Unicode, such as Linux Libertine O, Times New Roman and so on. for example,

```latex
\setmainfont{CMU Serif}
```

There is another way is use `\newcommand` to define a new command, please see more details in book Page 75.

There is a useful package named **fonttable** which can output the symbol table in specific font with its NFSS.

```latex
{\xfonttable{OT1}{lmr}{m}{n}}
```

## 2.1.6 Emphasize

In $\LaTeX$, basical command to emphasize is actually to use italic shape in upright or on the contrary.

```latex
This word is \emph{emphsized} in the sentence. \\
\textit{This word is \emph{emphsized} in the sentence. }
```

We can use `\newcommand` to define our own style to emphasize our text.

```latex
\newcommand\Emph{\textbf}
This word is \Emph{emphsized} differently in the sentence. 
```

Underline is another usual way to emphsize.

```latex
This is an \underline{Emphasized} \underline{word}. 
```

Howerver, if we observe the underline carefully, we can find that the underline command does not support wraping around text, and not align under the text.

Package **ulem** provides a better underline command.

```latex
\usepackage{ulem}
This is an \uline{Emphasized} \uline{word}. \\
This is a very \uline{very very very very very very very very very very very very very veryvery very very very} long sentence. 
```

NOTE: The **ulem** package will change the original `\emph` command into underline style.

To avoid this, we can use `normalem` option when we use **ulem** package, or just use `\normalem` to replace `\emph`.

```latex
\usepackage[normalem]{ulem}
% or
This word is \normalem{emphsized} in the sentence.
```

Furthermore, the **ulem** package supports the colorful highlight. See "./rsc/ulem.pdf".

CJK package provides its own command to emphaisze which is more friendly in Chinese Situation. See "./zh/Letter_zh.tex".

## 2.1.7 Font Size

In $\LaTeX$, there are 11 kinds of units to represent the length. They are:

| Unit | Meaning | Length |
| --- | --- | --- |
| pt | point | 0.3527mm |
| pc | pica | 12pt |
| in | inch | 72.27pt |
| bp | big point | 1in=72bp |
| cm | centimeter | |
| mm | millimeter | |
| dd | didot point | 1157dd=1238pt |
| cc | cicero | 12dd |
| sp | scaled point | 65536pt=1pt |
| em | whole body | Width of M (chaging with the font size and font) |
| ex | x-height | Height of x(chaging with the font size and font) |

At past, font size was regarded as one of the coordinates in NFSS, as we see in *2.1.5.2 NFSS System*. But now, fonts are usually vectors, which can change its size at will.

Font size is described by length units in $\LaTeX$.

```latex
{
    \fontsize{24.88pt}{36pt} \selectfont 
    A very huge
    line
}
```

The first parameter defines the font size and the second parameter defines the line space which will be explained in *2.1.8 Line Space*.

There are some simple declaration command provided to change the font size.

| | | | |
| --- | --- | --- | --- |
| \tiny | \scriptsize | \footnotesize | \small |
| \normalsize | \large | \Large | \LARGE |
| \huge | \Huge | | |

In different document class options, the \normalsize could be configured differently. Standard class have 10pt, 11pt, 12pt normalsize to option with command above defineing different size of font.

And command above will change the line space, too, in order to make the composing more beautiful.

NOTE: Command `\quad` is as wide as the font size's length, in other words, as wide as the letter's height.

In Chinese environment, package **ctex** provides another kind of command, which is more intuitive, `\zihao{}` to change the font size. See in "./zh/Letter_zh.tex".

## 2.1.8 Line Space

Every line has its own base line, and the distance between two adjacent base lines is the line space.

![2021-10-01-Line_Space](https://i.loli.net/2021/10/01/ybIRsgBFfL3JCXi.jpg)

Defaultly, line space in paragraph is 1.2 times as long as the **font size**.

To change the line space, the basical command can be used like underneath, the parameters defines the times to **default line space**.

```latex
{
    \linespread{1.5} \selectfont
    A different\\
    line space
}
```

NOTE: In Chinese environment, the default line space is 1.3 times as long as the **font size**.

Package **setspace** provides some command to define space line easily.

Among them, the command `\setstretch{}` used frequently is equal to `\linespread{}\selectfont`.

```latex
\usepackage{setspace}
...
 {\setstretch{1.5} A different\\
    line space. }
A normal\\
line space. 
```

NOTE: It should be noticed that other command like \singlespacing, \onehalfspacing reprensent the line space times to font size, instead of the default space line.

These commands can also used as environment, for example:

```latex
\begin{spacing}{1.5}
    A different\\
    line space
\end{spacing}
\begin{doublespace}
    A different\\
    line space
\end{doublespace}
```

The default line space is controlled by the value of `\baselineskip`. Actually, `\fontsize` and `\linespread` indirectly controlled the `\baselineskip`.

`\lineskiplimit` is a limit value set by users whose function is that when two adjancent lines' line space smaller than it, the line space will use the value `\lineskip`, which is also set by us, instead.

```latex
\setlength\lineskiplimit{2.5bp}
\setlength\lineskip{2.5bp}
```

This function can be very useful when math fraction appears in your article.

## 2.1.9 Horizontal Space

Line Space is the vertical distance between line and line, while horizontal space is between letter and letter in the same line.

Some commands can represent different horizontal space between two letters.

| | |
| --- | --- |
| \thinspace | \\, |
| \negthinspace | \enspace |
| \nobreakspace | |

These commands are not allowed to wrap around.

| | |
| --- | --- |
| \quad | \qquad |
| \enskip | \ (a space following) |

These commands are allowed to wrap around.

```latex
A\thinspace B\negthinspace C\\
A\quad B\enskip C
```

Command `\hspace{}` can adjust the horizontal distance precisely through the length parameter.

```latex
Space\hspace{1cm}1\, cm
```

NOTE: `\hspace{}` is allowed to wrap around. And it will ignore the distance when its left has no text, while `\hspace*{}` will not.

```latex
\hspace{1cm} 1\, cm\\       % The left blank will be ignored
\hspace*{1cm} 1\, cm
```

`\hspace{}` can generate a length ranging in a designated scale which commonly called **glue** or **rubber length**.

```latex
\newcommand\test{longggggggggg\hspace{2em plus 1em minus 0.25em}}       % 1.75em~3em
\test\test\test\test\test\test\test\test
```

`\fill` is a special rubber length parameter in `\hspace`, which ranging from zero to infinite. The command `\hspace{\fill}` can be written like `\hfill` as its abbreviation.

```latex
left\hspace{\fill}middle\hfill right
```

Parameter `\stretch{}` can generate a rubber length which elastic force is parameter times as strong as the \hfill.

```latex
left\hspace{\stretch{2}} middle\hspace{\stretch{3}} right
```

Commands `\dotfill` and `\hrulefill` are similar to `\hfill` in function, and their differences with it are that the former uses dot and the latter uses underline replacing the blank.

```latex
left\dotfill middle\hrulefill right
```

Command `\parindent` can control the indent at the far left of one line. It usually used in environment and need to coordinate with `\setlength`. For example:

```latex
{
    \setlength\parindent{24em}
    Paragraph indent can be very wide in \LaTeX .\par
     Para\par
    \addtolength\parindent{2em}Para\par
    \addtolength\parindent{2em}Para
}
```

FIXME: Why this command above did not work?

There is a useful technique that is to set a definition of a designated length, so that you can just change your definition to change the global length. The mylen is defined in Introduction.

```latex
\setlength\mylen{2em}
...
{
    Para\par
    \addtolength\parindent{\mylen}Para\par
    \addtolength\parindent{\mylen}Para
}
```

## 2.1.10 Box

Box is the fundamental unit $\LaTeX$ deal with. Everything, containing a letter, a line, a paragraph, a graph, a table, a page and so on, can be regarded as a box.

On horizon, the letter boxes constitude a line box, and on vertical, the line boxes contitude a page box.

A text box is like this:

![2021-10-01-Text_Box](https://i.loli.net/2021/10/01/imURaMVOJpzkSYb.jpg)

Command `\mbox{}` is the most simple command which will generate a box with text put into. The text in it is the same as outer text, but the blank before or after it could be affected in some special situation, and most commonly, it do not allowed wrap around which is the function every box does.

```latex
\mbox{Text in box cannot be broken. }
```

We can also custom a special box. Command `\makebox[][]{text}`, the simplest way, has three parameters. The first one represents the width, the second one represents the alignment, with c-center, l-left, r-right, s-stretch optionally. The horizontal space between word and word could be adjust according to our parameters.

```latex
This is a\,\makebox[1em]{text}\,in box. \par
\makebox[5cm][s]{Some stretched text}
```

The \makebox can even generate a 0-width box to make overlap effect. The command `\llap` and `\rlap` are professionally used to do the same. the former one left alignment and the latter one right alignment.

```latex
\makebox[0pt][l]{word}text\par
Some text\llap{word}\par
\rlap{word}Some text
```

Command `\fbox` and `\framebox` can generate box with framwork. Their grammer is similar to `\mbox` and `\makebox`.

```latex
\fbox{framed}\par
\framebox[3cm][s]{A framed box}
```

NOTE: The space between framework and text is configured by `\fboxsep` which is defaultly 3pt. And the thickness of the framework is configured by `\fboxrule` which is defaultly 0.4pt.

```latex
{
    \setlength\fboxsep{0pt}
    \setlength\fboxrule{0.1pt}
    \fbox{tight}
}\par
{
    \setlength\fboxsep{1em}
    \setlength\fboxrule{1pt}
    \fbox{loose}
}
```

We can define a box environment, so that we can use it repeatedly. So saving box is usually used to saving some complex content.

```latex
\newsavebox\mybox
\sbox\mybox{text text}
...
\usebox\mybox \fbox{\usebox\mybox}
```

TODO: Command `\settowidth<length_variable>{text}`, `\settoheight<length>{text}`, `\settodepth<length>{text}` can respectively get the text parameter's width, height, and depth.

And command `\wd<box_variable>`, `\ht<box>`, `\dp<box>` can respectively get the box parameter's width, height, and depth.

```latex
\framebox[\wd\mybox]{text}
```

Some special parameter represent the text natural properties. They are `\width`, `\height`, `\depth`, `\totalheight`(the sum of height and depth).

```latex
\framebox[2\width]{frame}       % double width
```
