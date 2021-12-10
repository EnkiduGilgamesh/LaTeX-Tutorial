# 3 Cross Reference

- [3 Cross Reference](#3-cross-reference)
  - [3.1 Label](#31-label)
  - [3.2 Cite](#32-cite)
  - [3.3 Other tools](#33-other-tools)
  - [3.4 Cite external files](#34-cite-external-files)

Cross Reference is one of important autotools in $\LaTeX$, through which we can cite an object's number, page, title and other message by its label without navigating where it is.

## 3.1 Label

The first step to use cross reference is to set label for objects in proper place. For instance

```latex
\section{Language} \label{sec:lang}
```

The `sec:lang` is the name of the label, in which we can put whatever we love, but most importantly, the labels must be dinstinct so we can reuse it easily. It is strongly recommanded that use a prefix like the instance.

Generally, these objects have an ability to be automatically numbered. For objects generating by a single command, like `section`, `item`, etc. just put the label very behind them; for objects like `environment`, put the label in the environment. For footnote, the label should be put into footnote, but not put behind it. In addition, some special environments define `label` in their own way, so we can't directly put the label in environment, such as the `lstlisting` environment provided by `listing` package. These special usage of `label` will mentioned in their documentation, refer to them before using it.

## 3.2 Cite

After setting label, the following step is to cite the label. The instance below shows how we can do it.

```latex
\begin{align}
    c^2 &=a^2+b^2
    \label{eq:gougu-formula} \\
    5^2 = 3^2 + 4^2
    \label{eq:gougu-example}
\end{align}

Gougu formula (\ref{eq:gougu-formula}) has been mentioned in Page~\pageref{eq:gougu-formula}. 
```

The **Cross Reference** funtion relies on the **auxiliary file** that is **.aux** file. Hence, to generate a proper cite, the source file need to be compile at least two times.

## 3.3 Other tools

Many packages extends the function of Cross Reference.

Package `amsmath` provides command `\eqref` for users which can generate the whole style of the equation number.

Package `nameref` can get the name of the cited objects. Notice that if the object doesn't have a title, it may cause errors.

```latex
\usepackage{nameref}
See \nameref{fig:xref}
```

Package `lastpage` permits using `\label{LastPage}` in the last page, so we can get the number of the lastpage when we cite the label.

```latex
Page~\thepage of \pageref{LastPage}
```

Furthermore, package `hyperref` provides `\autoref` to recognize the object automatiaclly. Refer to "./rsc/hyperref-doc.pdf".

## 3.4 Cite external files

Package `xr` realize citing external `.aux` file.

```latex
\usepackage{xr}
\externaldocument[ch:]{chinese}
See \ref{ch:fig:popular}
```

The `ch:` is prefix which is optional and mainly prevent conflict between label name of the source files and external files.
