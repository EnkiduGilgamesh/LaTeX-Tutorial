# Math Environment Introduction

The original purpose to design the $\TeX$ system is to help compose complex math formula.

Boxes will arrange by a special way in math environment, even the most simple formula looks different from the normal text. It's not a good habit that we don't use math environment when we meet math formula for convenience.

There are two main ways to go into math environment, the inline formula and the displayed formula.

The inline fomula:

```latex
The Commutative law is $a+b=b+a$, for example $1+2=2+1$. \par
% or
\(a+b=b+a\)\par
% or
\begin{math}a+b=b+a\end{math}
```

Command `\ensuremath` can get the defined command displayed like in math environment, even if it is already in math environment.

```latex
\usepackage{ntheorem}
\renewcommand\qedsymbol{\ensuremath{\Box}}
\qedsymbol and $\qedsymbol$
```

FIXME: Command `\Box` not provided in base Latex2e

The displayed formula:

```latex
The Commutative law is
$$
    a*b=b*a
$$
% or
The Associative law is:
\[
    (a*b)*c=a*(b*c)
\]
% or
The Distributive law is:
\begin{displaymath}
    a*(b+c)=a*b+a*c
\end{displaymath}
```

NOTE: `\[...\]` is recommanded to be used.

Environment **equation** will automatically numbers the equations  in it with the section number. And it can also add labels to the equations.

```latex
\begin{equation}
    a+b=b+a \label{eq:commutative}
\end{equation}
```

Package **amsmath** is a very powerful package that provides many functions about math environment. In latter chapters and the rest part of this chapter, the command below is defaultly used. See more details about this package, see "./rsc/amsmath.pdf".

```latex
\usepackage{amsmath}
```

Chinese character and even other kinds of western language can not be used in math environment. Package **amsmath** solves it.

NOTE: Space does not work in math environment, so we can use it to make the input code more beatiful and structured.

```latex
$\text{被减数}-\text{减数}=\text{差}$
```
