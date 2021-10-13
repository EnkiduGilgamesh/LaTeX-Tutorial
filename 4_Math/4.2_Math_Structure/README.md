# Math Structure

- [Math Structure](#math-structure)
  - [4.2.1 Superscript and Subscript](#421-superscript-and-subscript)
  - [4.2.2 Line and Brace](#422-line-and-brace)
  - [4.2.3 Fraction](#423-fraction)
  - [4.2.4 Square Root](#424-square-root)
  - [4.2.5 Matrix](#425-matrix)

## 4.2.1 Superscript and Subscript

Superscript and subscript are very easy.

```latex
$A_{ij}=2^{i+j}$
```

They can be used in nested way.

```latex
$A_i^k = B^k_i$\par
$A_{i_k} = B^{k_i}$\par
$3^{3^{3^{\cdot^{\cdot^{\cdot^3}}}}}$
```

The symbol `'` is a special superscript. It can't be followed of follow other supersscript.

```latex
$a = a'$, $b_0' = b_0''$\par
${c'}^2 = (c')^2$
```

Command `\circ` can represent the angle symbol in math.

```latex
$A=90^\circ$
% or
\newcommand\degree{^\circ}
$A=90\degree$
```

For math operator, the superscript and subscript are usually just under them. But some operator are not, like integral operator.

```latex
\DeclareMathOperator\dif{d\!} % in introduction
...
\[
    \max_n f(n) = \sum_{i=0}^n A_i
\]
\[
    \int_0^1 f(t) \dif t = 
    \iint_D g(x,y) \dif x \dif y
\]
```

But for inline formula, the superscript and subscript for these operator are like the normal.

Package **amsmath** provides some options to change the position of the superscript and subscript.

The Command `\limits` make the script just upper or above whereas the `nolimits` is on the contrary.

```latex
\[
    \iiint\limits_D \mathrm{d}f =
    \max\nolimits_D g   
\]

$\sum\limits_{i=0}^n A_i$ is worse than
$\sum_i^n A_i$.
```

Package **mathtools** can add superscript and subscript in front of letter or symbol. The command is `\prescript{super}{sub}{element}`

```latex
\usepackage{mathtools}
$\prescript{n}{m}{H}_i^j < L$ is better than 
${}^n_mH_i^j < L$
```

A more complex situation can seek help from **amsmath**:

```latex
\[
    \sideset{_a^b}{_c^d} \sum_{i=0}^n A_i = 
    \sideset{}{'} \prod_k f_i
\]
```

Like `\sideset`, `\overset` and `\underset` add scripts to just upper adn just under.

```latex
$\overset{*}{\underset{\dag}{X}}$
```

Tensor algebra:

```latex
\usepackage{tensor}
$M\indices{^a_b^{cd}_e}$ \qquad
$\tensor[^a_b^c_d]{M}{^a_b^c_d}$
```

Another way without the support from the **tensor** to do the same is:

```latex
$A_m{}^n$ is worse than $A_m^{\phantom{m}n}$
```

Package **mhchem** helps us write chemical equation. See "./rsc/mhchem.pdf".

## 4.2.2 Line and Brace

Display line under or above equation or letters:

```latex
$\overline{a+b} =
 \overline a + \overline b$\\
$underline a = (a_0,a_1,a_2,\dots)$

$\overline{\underline{\underline a} +
 \overline{b}^2 - c^{\underline n}$
```

Package **amsmath** provides over and under arrow.

```latex
$\overleftarrow{a+b}$\\
$\underrightarrow{a+b}$\\
$\overleftrightarrow{a+b}$
```

The `\vec` command is similar to a right arrow, and it is usaually used on a single letter.

```latex
$\vec x = \overrightarrow{AB}$
```

Brace:

```latex
$\overbrace{a+b+c} = \underbrace{1+2+3}$

\[
    ( \overbrace{a_0,a_1,\dots,a_n}^{totally n elements} ) = 
    ( \underbrace{0,0,\dots,0}_{n},1 )
\]
```

Bracket(**mathtools needed**):`\underbracket[width_of_line][height]{text}`

```latex
\[
    \underbracket{\overbracket{1+2}+3}_3    
\]
```

TODO: interlaced brace in page 229

## 4.2.3 Fraction

Fraction:

```latex
Equation: $\frac 13 + \frac 2x = \frac{2+x}{2x}$
```

NOTE: Fraction's height depends on the environment it is in. But we can adjust it manually.

Command provided by **amsmath** `\tfrac` (text style) means the fraction is as high as the text, and `\dfrac` (display style) means the fraction is as high as the font.

```latex
\[
    \tfrac 12 f(x) =
    \frac{1}{dfrac 1a + dfrac 1b +c}
\]
```

Continued fraction is a special fraction and specially displayed by `\cfrac`. The command followed by a parameter which means the alignment method. They are l, c, r, and it is defaultly c.

```latex
\[
    \cfrac{1}{1+\cfrac{2}{1+\cfrac{3}{1+x}}} = 
    \cfrac[r]{1}{1+\cfrac[c]{2}{1+\cfrac[l]{3}{1+x}}}    
\]
```

Another style of fraction is like a/b. The package **xfrac** provides the style.

```latex
\usepackage{xfrac}
$\sfrac 1a + b$ and $1/a + b$
```

Sometimes, binomial is used to represent fraction. Package **amsmath** provides the style.

```latex
\[
    (a+b)^2 = \binom 20 a^2 + \binom 21 ab + \binom 22 b^2
\]
```

Similarly, the `\binom` also has optional commands `tbinom` and `dbinom`.

A more generalized fraction can be defined by `\genfrac` in **amsmath**. Its total command is `\genfrac{left_bracket}{right_bracket}{line_width}{size}{molecule}{denominator}`. The size can be 0, 1, 2, 3

```latex
\[
    \genfrac{[}{]}{0pt}{}{n}{1} = (n-1)!, \qquad n > 0 
\]
```

It is not usually used directlly, but we can define a new style fraction command by it.

```latex
\newcommand\stiring[2]{\genfrac{[}{]}{0pt}{}{#1}{#2}}
\newcommand\dstiring[2]{\genfrac{[}{]}{0pt}{0}{#1}{#2}}
\newcommand\tstiring[2]{\genfrac{[}{]}{0pt}{1}{#1}{#2}}

\[
    \stiring{n}{1} = (n-1)!, \qquad n > 0 
\]
```

## 4.2.4 Square Root

Square root:

```latex
$\sqrt 4 = \sqrt[3]{8} =2$
```

It also can be nested.

```latex
\[
    \sqrt[n]{\frac{x^2 + \sqrt 2}{x + y}}    
\]
```

Package **amsmath** provides two commands to adjust the position of the root  `\uproot` and `\leftroot`. They both followed by a parameter which is a integer.

```latex
\[
    \sqrt[\uproot{16}\leftroot{-2}n]{\frac{x^2 + \sqrt 2}{x + y}}    
\]
```

The height of the square root depands on the content in it. If we want to make the height the same, we can do like:

```latex
$\sqrt{\sqrt 12} < \sqrt{\vphantom{\frac 12} 2}$
% or
$\sqrt b \sqrt y$ \qquad 
$\sqrt{\mathstrut b} \sqrt{\mathstut y}$
```

## 4.2.5 Matrix

There are several different matrix environment in $\LaTeX$, in which the brackets around the element are defferent.

| | | |
| --- | --- | --- |
| matrix | bmatrix | vmatrix |
| pmatrix | Bmatrix | Vmatric |

Since matrix module has been enhanced by **amsmath**, the package is recommanded to be used if we want to make matrix in article.

```latex
\[
    A = \begin{pmatrix} 
    a_{11} & a_{12} & a_{13} \\
    0 & a_{22} & a_{23} \\
    0 & 0 & a_{33}
    \end{pmatrix}    
\]
```

Use dots in matrix.

```latex
\[
    A = \begin{bmatrix} 
    a_{11} & \dots & a_{1n} \\
     & \ddots & \vdots \\
    0 &  & a_{nn}
    \end{pmatrix}    
\]

\[
    \begin{bmatrix}
    1 & \frac 12 & \dots & \frac 1n \\
    \hdotsfor{4} \\
    m & \frac m2 & \dots & \frac mn
    \end{bmatrix}
\]
```

Package **mathdots** enhances the command `\ddots`, `\vdots` and provide some new dots command like `\iddots` which means insert ddots.

Matrix also can be used nested.

```latex
\[
    \begin{bmatrix}
    \begin{matrix} 1 & 0 \\ 
                   0 & 1 \end{matrix}
    & \text{\Large 0} \\
    \text{Large 0} & \begin{matrix}
                     1 & 0 \\
                     0 & 1 \end{matrix}
    \end{bmatrix}
\]
```

For inline matrix, we can use `\smallmatrix`, but we need add `()` manually.

```latex
The matrix \begin{math}
\left( \begin{smallmatrix}
x & -y \\
y & x \end{smallmatrix} \right) \end{math}
```

Multiple scripts for operator:

```latex
\[
    \sum_{\substack{0<i<n \\ 0<j<i}} A_{ij}    
\]

\[
    \sum_{\begin{subarray}{l}   % l,r,c
    i<10 \\ j<100 \\ k<1000
    \end{subarray}} X(i,j,k)    
\]
```

The maximum of columns is 10 which is controlled by counter `MaxMatrixCols`.

```latex
\setcounter{MaxMatrixCols}{15}
```

Package **mathtools** provides **matrix\***, **pmatrix\*** etc. environment that can set the alignment methods for matrix. More details about **mathtools** see "./rsc/mathtools.pdf".

```latex
\usepackage{mathtools}
\[
    \begin{pamatrix*}[r]
    10 & -10 \\ -20 & 3
    \end{pmatrix*}    
\]
```

We can make a matrix with the colomn and row numbers.

```latex
\[
    \bordermatrix{
        & 1 & 2 & 3 \cr
      1 & A & B & C \cr
      2 & D & E & F \cr
    }    
\]
```
