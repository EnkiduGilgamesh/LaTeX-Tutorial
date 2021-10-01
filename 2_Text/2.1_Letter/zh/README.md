# 2.1 文字和符号

- [2.1 文字和符号](#21-文字和符号)
  - [2.1.1 空格](#211-空格)
  - [2.1.2 字体](#212-字体)
    - [2.1.2.1 预设字体](#2121-预设字体)
    - [2.1.2.2 更多字体](#2122-更多字体)
  - [2.1.3 强调](#213-强调)
  - [2.1.4 字号](#214-字号)

## 2.1.1 空格

宏包 **ctex** 会在中文和英文之间自动插入一个空格。

为了避免中文和西文之间默认的空格，可以将中文装入一个盒子中。

```latex
\mbox{条目}-a 和条目-b。
```

也可以使用如下命令。

```latex
\CJKsetecglue{} % 空白参数，表示中文与西文之间的内容为空
```

## 2.1.2 字体

### 2.1.2.1 预设字体

中文没有西文那么多的变体，许多字体都是独立的。一般只使用不同的字体族区分中文。在 **xeCJK** 宏包下，中文和西文字体的选择命令是分开的。

```latex
 {\CJKfamily{zhhei}这是黑体}\\
{\CJKfamily{zhkai}这是楷体}
```

此外还有 `zhsong`, `zhfs`。不同的系统下，这些字体族可能会有差异。

**xeCJK** 宏包还预定义了一些字体命令。

```latex
{\songti 宋体} \quad {\heiti 黑体}\\
{\fangsong 仿宋} \quad {\kaishu 楷书}
```

**ctex** 宏包还定义了一套组合的字体，使文章中实现像西文一样的粗体、意大利体等效果。比如 Windows 系统下，`rm` 是宋体，`bf` 是黑体，`it` 是楷体，`sf` 是幼圆，`tt` 是仿宋。可以通过以下方式使用它们：

```latex
{\CJKfamily{rm}这是宋体}\、
\textbf{粗体} \quad \textit{斜体}   % 等同于 \bfseries, \itshape 命令
```

NOTE: 可以在下面的文件中更改 ctex 宏包的预定义：
".../texlive/2021/texmf-dist/tex/latex/ctex/fontset/ctex-fontset-windows.def"

在文件中，ctex 宏包通过使用下面的命令为某个字体的变体指定代替的其他字体。

```latex
\setCJKmainfont[BoldFont=SimHei, ItalicFont=KaiTi, BoldItalicFont=LiSu]{SimSun}
```

西文中也有类似的选项。

使用 `\renewcommand\CJKrmdefault{font}` 可以将全文使用的 rm 字体族替换为你制定的字体族。使用 `\renewcommand\CJKfamilydefault{\CJKsfdefault}`，可以将全文默认的字体族修改为 sf 字体族。和西文的命令类似。

### 2.1.2.2 更多字体

下面的命令可以修改预设的字体

```latex
\setCJKmianfont[optiions]{font1}         % rm
\setCJKsansfont[optiions]{font2}         % sf
\setCJKmonofont[optiions]{font3}         % tt
```

也可以自定义字体

```latex
\setCJKfamilyfont{defined_name}[options]{font4}
```

## 2.1.3 强调

使用 xelatex 编译时，**CJKfntef** 宏包提供了更加丰富的下划线形式

```latex
\usepackage{CJKfntef}
...
\CJKunderdot{下加点}\newline
\CJKunderline{下划线}\newline
\CJKunderdblline{双下划线}\newline
\CJKunderwave{波浪线}\newline
\CJKsout{横删除线}\newline
\CJKxout{斜删除线}
```

**CJKfntef** 宏包也有指定某个宽度，让文字在这个宽度下分散对齐的命令

```latex
\begin{CJKfilltwosides}{5cm}
    分散对齐。
\end{CJKfilltwosides}
```

传统的 `emph{}` 命令也被保留。但是在使用 **CJKfntef** 宏包后，这个命令会被更改成下划线形式，同样 `normalem` 命令或调用 `normalem` 会使用原来的定义。

在 ctex 文档类中，可以在选项中使用 fntef 调用 **CJKfntef** 宏包。

更多关于 **CJKfntef** 宏包的信息，访问网站：
"https://www.ctan.org/tex-archive/languages/chinese/CJK/cjk-4.8.4/texinput/#CJKfntef.sty"

## 2.1.4 字号

在 **ctex** 宏包中，字号有 0~8 和 -0~-6 这几类，分别代表 初号、一号到八号和小初号、小一号到小六号。

```latex
{\zihao{0} 初号}\\
{\zihao{-0} 小初号}\\
{\zihao{1} 一号}\\
{\zihao{-1} 小一号}\\
{\zihao{4} 四号}\\
{\zihao{8} 八号}
```

**ctex** 的文档类提供了两个默认字体大小的选项，c5size 和 cs4size.

```latex
\documentclass[c5size]{ctexart}
```
