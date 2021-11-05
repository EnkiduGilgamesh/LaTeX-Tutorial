# 4.4 Long Formula

- [4.4 Long Formula](#44-long-formula)
  - [4.4.1 Multiple formulas](#441-multiple-formulas)
  - [4.4.2 Split Formula](#442-split-formula)
  - [4.4.3 Combine fomulas](#443-combine-fomulas)

## 4.4.1 Multiple formulas

In **equation** environment, the wrapping around command `\\` doesn't work. The environment **gather** and **gather&#42;** has only one difference from **equation** which is that the `\\` command works as usual.

```latex
\begin{gather}
    a+b = b+a \\
    a\times b = b\times a
\end{gather}
```

Every line of formula in gather has its own tag which represent the chapter or section it lays, whereas none of the lines will be followed with tags in gather* environment. The optional command `\notag` will hide the tag for the appointed line.

```latex
\begin{gather}
    a+b = b+a \notag \\
    a\times b = b\times a
\end{gather}
```

Environment gather is always align at the center. Environment **Align** and **Align&#42;** can make lines align at other positions we appoint by using the sympol `&`.

```latex
\begin{align}
    x &= t+\cos t+1 \\
    y &= 2\sin t
\end{align}
```

In every line of environment align, we can also put multiple formulas.

```latex
\begin{align*}
    x &= t & x &= \cos t & x &= t \\
    y &= 2t & y&= \sin(t+1) & y &= \sin t
\end{align*}
```

Notice that the `&` is strongly recommended to closely use in front of binary operator, or it will make a wrong spacing. The two examples below show how to solve special situation if needed.

```latex
\begin{align}
        & (a+b)(a^2-ab+b^2) \notag \\
    ={} & a^3-a^2b+ab^2+a^2b-ab^2+b^3 \notag \\
    ={} & a^3 + b^3
\end{align}

\begin{align}
    &\mathrel{\phantom{=}}
        (a+b)(a^2-ab+b^2) \notag \\
    &= a^3-a^2b+ab^2+a^2b-ab^2+b^3 \notag \\
    &= a^3 + b^3
\end{align}
```

In some situations, we want to insert some text in the formula. We can use `\intertext{}` command to do it. The command do not break the alignment between its two side lines and will wrap around automatically.

```latex
\begin{align*}
    x^2 + 2x &= -1
    \intertext{Transpose it and then get:}
    x^2 + 2x + 1 &= 0
\end{align*}
```

Package **mathtools** also provides command `\shortintertext{}` to insert text. Differently, the short-command will get a more compact line spacing between the text and the formula.

Environment **subequations** is similar to equation environment, but it will treat all the formula in it as one formula when tagging.

TODO: Page 265-266 example

```latex

```

## 4.4.2 Split Formula

When a formula is too long to put into one single line, we always want to split it. In some situations, the align environment is qualified to do this work.

Howerver, if we want to tag the long line formula, it will become disgusted to edit every line.

The environment **multline** is made from equation environment for this situation. In multiline, the wrapping around command `\\` still works, and the first line of the formula aligns at left, the last line aligns at right and other lines align at center.

```latex
\begin{multline}
    a+b+c \\
     +d+e+f \\
     +g+h+i \\
      +j+k+l
\end{multline}
```

The leftmost and the rightmost of the fomula both have a spacing from the two sides margins of the page which we can control through `\multlinegap` and `\multlinetaggap`. Also, we can make the middle lines align left or right through `\shoveleft` and `\shoveright`.

Environment **split** is used in equation or gather to split the formula into multiple lines. In particular, if the environment tags the formula, the tag will appears in the middle of the multiple lines.

```latex
\begin{equation}
\begin{split}
    \cos 2x &= \cos^2 x - \sin^2 x \\
            &= 2\cos^2 x - 1
\end{split}
\end{equation}
```

When we are writting article, it usuallly hard to know if a formula is too long without we compile it.

Package **breqn** provides environment **dmath** and 
**dmath&#42;** to wrap around the formula intelligently. For more information about breqn package, reference "./rsc/breqn.pdf".

## 4.4.3 Combine fomulas

It is very common to combine multiple formulas into one formula in mathematics.

Environment **cases** in equation is often used to conbine formulas.

```latex
\begin{equation}
    D(x) = \begin{cases}
        1, & \text{if } x \in \mathbb{Q}; \\
        0, & \text{if } x \in mathbb{R}\setminus\mathbb{Q}.
    \end{cases} 
\end{equation}
```

Package **mathtools** provides **dcase** environment to compose these case formulas. And **cases** package is made to do more things with them. For more information about cases package, reference to "./rsc/cases.pdf".

Package **amsmath** provides some environments for more common situations in case formula, such as **gathered**, **aligned**, and **alignedat**.

Environment **gathered** combines multiple formula into one single formula aligning them at center.

```latex
\[
    \left. \begin{gathered}
        S \subseteq T \\
        S \supseteq T
    \end{gathered} \right\}
    \implies S = T
\]
```

Package **mathtools** uses environment **lgathered** and **rgathered** to do the similar thing whose difference from above is that they align at left or at right.

Package **mathtools** also provides an environment named **multlined** in order to make the multiple-lined formula a block.

```latex
\usepackage{mathtools}

\newcommand\Set[2]{
    \left\{ #1\ \middle\vert\ #2 \right\}
}

\[
    \Omega = \Set{x}{\begin{multlined}
         x^7+x^6+x^5 \\
        +x^4+x^3+x^2 \\
        +x+1=0 \end{multlined}
    }
\]
```

Most of the environments aligns at center in vertical defaultly. Option parameters `[t]` and `[b]` can make them align at the first line or the last line.
