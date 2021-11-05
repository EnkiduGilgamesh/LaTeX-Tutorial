# 4.5 Precise Adjustment

- [4.5 Precise Adjustment](#45-precise-adjustment)
  - [4.5.1 Tag Control](#451-tag-control)
  - [4.5.2 Formula Size](#452-formula-size)
  - [4.5.3 Inline Wrapping Around](#453-inline-wrapping-around)
  - [4.5.4 Spacing](#454-spacing)
  - [4.5.5 Some Reference](#455-some-reference)

## 4.5.1 Tag Control

The global option **leqno**, **reqno** can control the location of formula's tag be put into left or right side. And the options **centertags**, **tbtags** of package **amsmath** can control the location to the center or the top.

```latex
\documentclass[fleqn, leqno]{article}
\usepackage[tbtags]{amsmath}
```

Package **amsmath** also provides `\tag{}` for us to edit the tag manually. And the `\tag*` can get a tag without brackets `()`.

```latex
\begin{equation*}
    a^2 + b^2 = c^2 \tag{$\star$}
    \sum_{k=1}^n \frac{1}{k} = \ln n + \mathrm{C} \tag*{[Euler]}
\end{equation*}
```

Package **mathtools** can modify the tag globally through the steps blow:

```latex
\usepackage{mathtools}

\newtagform{bracket}[\textit]{[}{]}
\usetagform{bracket}

\begin{equation}
    \sum_{k=1}^n \frac{1}{k} = \ln n + \mathrm{C}
\end{equation}
```

The counter of formula is named **equation** which we can redefine it.

```latex
\renewcommand\theequation{
    \thechapter.\roman{equation}
}

\begin{equation}\label{eq:euler}
    \chi = V + F - E = 2
\end{equation}
```

The sub equation environment **subequations** defines its own tag form, which uses counter equation as its sub tag and counter **parentequation** as its parent tag. If we want to redefine it, we need to redefine it in subequations environment.

```latex
\newenvironment{mysubeqn}
{\begin{subequations}
    \renewcommand\theequation{\theparentequation-
    -\roman{equation}}}
{\end{subequations}}

\begin{mysubeqn}
\begin{gather}
    \zeta(2) = \frac{\uppi^2}{6} \\
    \zeta(s) = \prod_{p\text{ prime}} \frac{1}{1-p^{-s}}
\end{gather}
\end{mysubeqn}
```

Generally in book and report, the tag's counter is associated with the chapter in which way the counter will reset to 0, whenever go into a new chapter.

Package **chngcntr** can cancel this association.

```latex
\usepackage{chngcntr}
\counterwithout{equation}{chapter}
```

## 4.5.2 Formula Size

The most simple and direct way to change the size of formula is like blow:

```latex
{\Large
\[
    F(x) \equiv 0
\]
}
```

In equation, there are four kinds of size we can choose.

| Command | Display |
| --- | --- |
| `\displaystyle` | $\displaystyle \sum$ |
| `\textstyle` | $\textstyle \sum$ |
| `\scriptstyle` | $\scriptstyle \sum$ |
| `\scriptscriptstyle` | $\scriptscriptstyle \sum$ |

In most symbols and characters, the displaystyle and the textstyle are the same.

**All these kinds of size will be influenced by the normal text size**.

```latex
\newcommand\D{\displaystyle}
\[
    \mathop{\text{\Large$\D\sum_i$}}
    \dfrac{\D\int f_i(x)\,\mathrm{d}x}
          {\D\oint g_i(x)\,\mathrm{d}x}    
\]
```

Command `\DeclareMathSizes` can declare the size the math text's four kinds of size. And the command `\defaultscriptratio` and `\defaultscriptscriptratio` can declare the ratio between script style or script-script style with the normal text.

```latex
\DeclareMathSizes{10.54}{10.54}{6.32}{6.32}
\defaultscriptratio{0.6}
\defaultscriptscriptratio{0.4}
```

## 4.5.3 Inline Wrapping Around

Inline math formula is only allowed to wrap around after **binary operator**, for example `+`, `=`, etc. In other word, the wrapping around will never appear after a camma, bracket or letter.

In addition, we can use `\*` to remind compiler the position in multipy calculation that the wrapping around will most possibly happend, and a symbol $\times$ will automatically generate in the wrapping-around place.

```latex
$F(x,y,z)\* G(x,y,z)
```

We can also redifine the multipy symbol ourselves.

```latex
\renewcommand\*{
    \discretionary{\,\mbox{$\cdot$}}{}{}
}
```

Defaultly, $\LaTeX$ doesn't allow to break page in multiple lines of formula. But we can simply use command `\allowdisplaybreaks` to get the allowance. We can also use command `\displaybreak` to break the page manually.

## 4.5.4 Spacing

Math environment has its customized length unit named **mu**(math unit) which is as long as $1/18$ em. The command `\mspace{}` can directly set a blank box with appointed length.

A more convenient way to set spacing is to use commands blow:

| Command | Length | Spacing | Controled by |
| --- | --- | --- | --- |
| `\,` | 3mu | $a\,b$ | `\thinmuskip` |
| `\:` or `\>` | 4+2(-4)mu | $a\:b$ | `\medmuskip` |
| `\;` | 5+5mu | $a\;b$ | `\thickmuskip` |
| `\!` | -3mu | $a\!b$ | `\thinmuskip` |

These commands are often used to precisely adjust the formula to make it more good-looking.

In addition, the command `\,` can also work in normal text. Others can work if package **amsmath** is used.

These commands are not direct length command. They are controled by the length listed in table.

Technically, the spacing can help us creat customized math symbols like the example blow:

```latex
\newcommand\lowint{
    \mspace{2mu}\underline{\vphantom{\int}\mspace{7mu}}
    \mspace{-9mu}\int
}

\[
    \lowint_a^b f(x)\,\mathrm{d}x = \inf_P s(P).    
\]
```

Command `\quad` and `\qquad` are also able and often used in math environment.

When we use **fleqn** option of document, the fixed indent spacing of formula is under `\mathindent` command's control.

Command `\abovedisplayshortskip` and `\abovedisplayskip` control the above distance between math formula and normal text, whereas `\belowdisplayshortskip` and `\belowdisplayskip` controls the below. Their default value are listed below:

| Command | Value |
| --- | --- |
| `\abovedisplayshortskip` | 12pt plus 3pt minus 9pt |
| `\abovedisplayskip` | 0pt plus 3pt |
| `\belowdisplayshortskip` | 7pt plus 3pt minus 9pt |
| `\belowdisplayskip` | 12pt plus 3pt minus 9pt |

**Notice the length above will not change with font size changed**. It may be necessary in some situations for us to modify the length if the font size is changed.

```latex
\zihao{7}
\setlength\abovedisplayskip{2pt plus 1pt minus 3pt}
```

Command `\jot` controls the distance between lines which is defaultly set **3pt**. Similarly, it will not change with font size changed. Alternatively, we can use `\\[]` to set the distance wherever we need.

Command `\mathsurround{}` sets the additional distance between inline formula and normal text.

Command `\skew` controls the accent's position. It has 3 parameters with the first one being the right-moving distance measured in mu, the second one the accent symbol command and the third one the letter.

```latex
$\ddot{h} \iff \skew{-2}{\ddot}{h}$
```

The **phantom** and **vphantom** is an useful and also powerful tool to make some special indent and alignment.

```latex
\begin{equation*}
\begin{split}
    f(x) &= \left(\vphantom){\frac1x}
    x+2+3+4\right. \\
         & \left. \phantom{=\biggl(x+{}}
    5+6+7+\frac1x \right)^2 \\
         &= g(x)
\end{split}
\end{equation*}
```

Command `\smash` is contrast with phantom. It displays appointed content like them has no height and depth.

```latex
\[
    \underline{
        \smash{\int f(x)\,\mathrm{d}x}
    }
\]
```

Package **amsmath** extends the `\smash` command with tow options `t` and `b` which mean only ignore the box's height and depth.

```latex
$\sqrt{A_{n_k}} \qquad
\sqrt{\smash[b]{A_{n_k}}}$
```

When we make a tree, the `\smash` command is a very useful tool.

```latex
\vspace{\baselineskip}
\[
    \text{Real Number} \begin{cases}
      \text{Rational Number}\smash[t]{\begin{cases}
        \text{Integer}\smash{\begin{cases}
          \text{Odd } \\
          \text{Even}
        \end{cases}}
        \text{Fraction} 
        \end{cases} \\[4ex]
      \text{Irrational}\smash[b]{\begin{cases}
        \text{Algebraic Irrational} \\
        \text{Transcendental Number}
      \end{cases}}
      \end{cases}}
    \end{cases}
\]
```

## 4.5.5 Some Reference

The "./rsc/amsldoc.pdf" is a official document of **amsmath** from the *American Mathematical Society*.

The "./rsc/mathmode.pdf" introduces math tools for $\LaTeX$ in detail and provides many classic examples for readers.

The "./rsc/Gai.pdf" also gives math edit examples. And it also introduces some art principle for math.

The book "./rsc/The LaTeX companion.pdf" is a winderful textbook for $\LaTeX$ in which the writer introduces math part in Chapter 8.

For International Standard of scientific documentation, reference [ISO/TC 12: Quantities and units](https://www.iso.org/committee/46202.html#:~:text=Standardization%20of%20units%20and%20symbols%20for%20quantities%20and,between%20the%20various%20units.%20ISO%2FTC%2012%20-%20Secretariat)
