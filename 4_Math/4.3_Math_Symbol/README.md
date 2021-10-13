# 4.3 Math Symbol

- [Math Symbol](#math-symbol)

Math symbols is a very abundant component of math system in $\LaTeX$.

Roughly, they can be divied into 8 parts, common symbol, math operator, binaty operator, relation character, open character, close character, punctuation and variable. open character and close character constitute a pair of bracket.

## 4.3.1 Letter and Common Symbols

The math environment can change its font like common text. There are several fonts can be selected.

| | | | |
| --- | --- | --- | --- |
| \mathnormal | \mathit | \mathrm | \mathbf |
| \mathsf | \mathtt | \mathcal | |

```latex
$\mathrm{e}$
```

NOTE: Font `\mathnormal` is the default font used with a different distance between letter from common text, whereas the other fonts which use the same fonts with common text directly have the same distance.

```latex
$xyz$ is different from $\mathit{xyz}$.
```

NOTE: Generally, variables in math use italic font, whereas constants use upshaped font such as e, i, etc.

```latex
\newcommand\mi{\mathrm{i}}
\newcommand\me{\mathrm{e}}
```

Some math font package like **amsmath**, **bbold**, **bbm**, **mathrsfs**, **euscript**, **asmsymb**, **eufrak**, **amsfonts** provide more fonts to choose in math environment.

For **asmymb** package, see "./rsc/amsfonts.pdf".

Hartke's documentation "./rsc/hartke.pdf" sums the usual fonts that can be freely used in math.

TODO: Page 237

The Greek letter can be directly used in $\LaTeX$ with its build-in commands.

The lower-case letter:

| Command | Letter | Command | Letter |
| --- | --- | --- | --- |
| \alpha | $\alpha$ | \beta | $\beta$ |
| | | | |

The capital letter:

| Command | Letter | Command | Letter |
| --- | --- | --- | --- |
| \Gamma | $\Gamma$ | \Delta | $\Delta$ |
| | | | |

TODO: Page 238

Package **upgreek** can get upright shaped greek lettter. Just add two letters `up` in front of a common command. So do other packages like **txfonts**, **fourier**, **mathdesign**.

```latex
\usepackage{\upgreek}
$\upalpha$
```

Accent in math is absolutely different from common text.

| Command | Accent | Command | Accent |
| --- | --- | --- | --- |
| \acute | $\acute a$ | \grave | $\grave a$ |
| | | | |

TODO: Page 239

Package **accrnts** can generate a customized accent.

```latex
\usepackage{accents}
$\accentset{*}{A}$, $\accentset{@}{A}$, 
$\underaccent{\check}{A}$, $\underaccent{\hat}{A}$, 
$\undertilde{abc}$
```

NOTE: This package must be used after **amsmath** and with `no-math` option in **fontspec** if they are used.

Some common symbols in math.

| Command | Symbol | Command | Symbol |
| --- | --- | --- | --- |
| \hbar | $\hbar$ | \imath | $\imath$ |
| | | | |

TODO: Page 241

Command `\boldmath` is used to change math fonts to bold series. But it will change the math font permanently in a group. The package **amsmath** provides a flexible method.

```latex
{\boldmath$a^2+b^2=c^2$}\\
$\boldsymbol{v} = (0,1)$
```

For some symbols that have no bold series, we can use `\hm` and `\bm` provided by package **bm** to get them. Package **amsmath** also provides a method to get a fake bold.

```latex
\usepackage{bm}
\[
    \hm\int > \bm\int > \int    
\]
$\pmb\sum$                   % fake bold
```

TODO: Page 242-243 math operator

## 4.3.2 Math Operator

Large operator:

| Command | Operator | Command | Operator |
| --- | --- | --- | --- |
| \sum | $\sum$ | \prod | $\prod$ |
| | | | |

TODO: Page 244

Single character operator:

TODO: Page 245

Name operator without limits:

| Command | Operator | Command| Operator |
| --- | --- | --- | --- |
| \log | $\log$ | \lg | $\lg$ |
| | | | |

TODO: Page 246

Name operator with limits:
| Command | Operator | Command| Operator |
| --- | --- | --- | --- |
| \lim | $\lim$ | \limsup | $\limsup$ |
| | | | |

NOTE: For these operator, the superscript and subscript are in their just upper and under.

TODO: Page 246

Package **amsmath** provide a method to define a new operator.

```latex
\DeclareMathOperator{\card}{card}        % without limits
\DeclareMathOperator*{\esssup}{ess\,sup} % with limits
```

It can also used temporarily without definition.

```latex
\[
    \operatorname*{Prod}_{\{1,\ldots,n\}}(\bar X) =
    \operatorname{card}(\varnothing)/n=0.    
\]
```

TODO: \mathod and \mathord Page 246
and commath

```latex

```

## 4.3.3 Binaty Operator

Binaty operator makes a different distance from the letters on two sides from common letter from letter.

For example: $0-2=-2$

The first negative sign is a binaty operator but second is not.

NOTE: `\setminus` and `\backslash` are two different symbols.

For example: $H\backslash G/K$ and $H\setminus G/K$

Binaty operator in $\LaTeX$:

| Command | Operator | Command| Operator |
| --- | --- | --- | --- |
| \triangleleft | $\triangleleft$ | \triangleright | $\triangleright$ |
| | | | |

Binaty operator in AmS:

| Command | Operator | Command| Operator |
| --- | --- | --- | --- |
| \dotplus | $\dotplus$ | \smallsetminus | $\smallsetminus$ |
| | | | |

TODO: Page 249

The negative binaty symbol can be just gotten by add `\not` in front of the positive symbol command.

For example: $s\not\in T$, the operator's command is `\not\in`.

Some binaty symbol and its negative symbol:

| Command | Operator | Command | Negative Operator |
| --- | --- | --- | --- |
| = | $=$ | \neq or \ne | $\ne$ |
| | | | |

TODO: Page 250

Arrow symbol in $\LaTeX$

| Command | Arrow | Command | Arrow |
| --- | --- | --- | --- |
| \leftarrow or \gets | $\gets$ | \nleftarrow | $\nleftarrow$ |
| | | | |

Arrow symbol in AmS

| Command | Arrow | Command | Arrow |
| --- | --- | --- | --- |
| \leftleftarrows | $\leftleftarrows$ | \rightrightarrows | $\rightrightarrows$ |
| | | | |

TODO: Page 252 and 253

Command `\stackrel` can put symbol onto a binaty operator.

```latex
\newcommand\defeq{\stackrel{\text{d}}{=}}
$f(x) \defeq ax^2+bx+c$
```

Command `\xleftarrow` and `\xrightarrow` provided by **amsmath** are flexible arrows.

```latex
\[
    A \xleftarrow{0<x<1} B
    \xrightarrow[0\leq 0]{x\geq 1} C    
\]
```

Package **extarrows** provides more flexible arrows.

| | | | |
| --- | --- | --- | --- |
| \xleftarrow | \xrightarrow | \xlongleftarrow | \xlongrightarrow |
| | | | |

Some logic arrows are also usually used.

```latex
$x=y \implies x+a=y+a$\\
$x=y \impliedby x+a=y+a$\\
$x=y \iff x\le y \And x\ge y$
```

The effects are:

$x=y \implies x+a=y+a$

$x=y \impliedby x+a=y+a$

$x=y \iff x\le y \And x\ge y$

TODO: \mathbin and \mathrel Page 253-256

## 4.3.4 Bracket

The main kinds of brackets are (), [], {}, and <>.

They are:

| Command | Bracket | Command | Bracket |
| --- | --- | --- | --- |
| ( | $($ | ) | $)$ |
| | | | |

TODO: Page 256

Package **amsmath** defines more precise symbols of absolute value, `\lvert`, `\rvert` and `\lVert`, `\rVert` which can replace the build-in `\vert` and `\Vert`.

```latex
\newcommand*\abs[1]{\lvert#1\rvert}
$\abs{x+y} \le \abs{x} + \abs{y}$
```

TODO: What is \newcommand*

A more broad conception in math is **delimiter**. It is displayed as the brackets on the left and right of a math element. One of the features of delimiter is that it can change its size with the element's size in it.

We can get the delimiter simply by using `\left` or `\right` commands before the symbols we want to use as a delimiter. Notice that the left must be paired with the right without they being the same symbol.

```latex
\[
    \partial_x \partial_y \left[
    \frac12 \left( x^2+y^2 \right)^2 + xy
    \right]
\]
```

The code would be like:

$$
    \partial_x \partial_y \left[
    \frac12 \left( x^2+y^2 \right)^2 + xy
    \right]
$$

```latex
\[ \left. 
    \int_0^x f(t,\lambda) \, \mathrm{d}t
        \right|_{x=1}, \quad
    \lambda \in
        \left[\frac12, \infty\right).
\]
```

The code would be like:

$$
    \left. 
    \int_0^x f(t,\lambda) \, \mathrm{d}t
        \right|_{x=1}, \quad
    \lambda \in
        \left[\frac12, \infty\right).
$$

Besides, we can also append a "middle" delimiter by command `\middle`.

```latex
\[
    \Pr \left( X>\frac12 
    \middle\vert Y=0 
    \right) 
    = \left.
    \int_0^1 p(t)\, \mathrm{d}t
    \middle/ (N^2+1) \right.
\]
```

The code would be like:

$$
    \Pr \left( X>\frac12
    \middle\vert Y=0
    \right)
    = \left.
    \int_0^1 p(t)\, \mathrm{d}t
    \middle/ (N^2+1) \right.
$$

We can also adjust the size of delimiter manually. Command `\big`, `\Big`, `\bigg`, and `\Bigg` represent different size. The types of different sides are `\bigl`, `\bigr` and `\bigm`.

```latex
\[
    \biggl( \sum_{i=1}^n A_i \biggr) \cdot
    \biggl( \sum_{i=1}^n B_i \biggr) > 0    
\]
```

The code would be like:

$$
    \biggl( \sum_{i=1}^n A_i \biggr) \cdot
    \biggl( \sum_{i=1}^n B_i \biggr) > 0  
$$

## 4.3.5 Punctuation

Only very few punctuations can use in math. They are:

| | | | | |
| --- | --- | --- | --- | --- |
| , | ; | ! | ? | $\colon$(\colon) |

NOTE: In math environment, the ":" directly input by keyboard is regarded as binaty operator in math which has the same distance from the elements on the left and right(Of cource, no distance will be displayed if two operators are adjacent).

$$
a\mathrm{:}b = ac\mathrm{:}bc\\
a:b = ac:bc
$$

Howerver, the `\colon` is just like the ":" in common text with a different distance between the elements on the left and right.

$$
a\colon b
$$

NOTE: Wrapping around is not allowed after punctuation in math environment.

In math environment, there are different types of dots.

| Command | Dots | Command | Dots | Command | Dots |
| --- | --- | --- | --- | --- | --- |
| \ldots | $\ldots$ | \cdots | $\cdots$ | \vdots | $\vdots$ |
| \ddots | $\ddots$ | \iddots | $\iddots$ | | |
| \dotsc | $\dotsc$ | \dotsb | $\dotsb$ | \dotsm | $\dotsm$ |
| \dotsi | $\dotsi$ | \dotso | $\dotso$ | | |

Different dots have different location in a line and satisfy different situations.

```latex
\[
    (1,\ldots,n) \qquad (1+\cdots n) \qquad a=\cdots z
\]
```

$$
    (1,\ldots,n) \qquad (1+\cdots +n) \qquad a=\cdots =z
$$

Command `\dots` in package **amsmath** can change the type intelligently.

## 4.3.6 Math Fonts

Math symbols were early used in some fonts with TrueType and OpenType fornat. Because of their using significant defferent standards and lower quality than $\TeX$ itself, they were seldom used in $\TeX$.

Since Unicode 3.2 published in 2002 with a huge amount math symbols' and letters' encoding, some fonts with Unicode math encoding has appeared. The earliest work was done by Microsoft who designed Cambria Math font with math symbols inheriting the advantages of $\TeX$ typography and used in Word.

Thanks to Microsoft's work, it has been able to use OpenType math fonts. Package **unicode-math** implement XeLaTeX and LuaLaTeX using math fonts. See "./rsc/unicode-math.pdf".

The most breathtaking part of math fonts is that we can now input math sympol directly through Unicode encoding which makes documentation more readable.

Some open-source math fonts are listed underneath:

| Math Font | Text Font suitable | Math Font | Text Font suitable|
| --- | --- | --- | --- |
| Asana Math | Palatino | Latin Modern Math | Lation Modern Roman |
| Neo Euler | Palatino | TeX Gyre Pagella Math | TeX Gyre Pagella |
| TeX Gyre Termes Math | TeX Gyre Termes | XITS Math | XITS |
| Cambria Math | Cambria |

```latex

```

```latex

```

```latex

```

```latex

```

```latex

```

```latex

```

```latex

```

```latex

```

```latex

```

```latex

```

