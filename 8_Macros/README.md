# 8 Macros

## 8.1 The Simplest Example

In this chapter, we will talk about how to make a document class or a package.

The most simple package can be written like below:

```latex
% mypackage.sty
\newcommand\mycmd{}
```

After editing, we rename it with ".sty" or ".cls" extension and put it in the root directory. Then we can use it in ".tex" file by commands:

```latex
\documentclass{class_name} % for .cls file
\usepackage{package_name} % for .sty file
```

After including the package or class, we can directly use the command we have defined in it.

We can add commands below so that the compiler will output the message about your macros in logs.

```latex
\ProvidesPackage{package_name}[2021/11/29 v5.5 A package made by WR]
\ProvidesClass{class_name}[2021/11/29 v5.5 A class made by WR]
```

## 8. Including other Macros in Macros

Instead of common way to use class or package, in macros, we do like below to include other macros:

```latex
\LoadClass[option]{class_name}[time]
\RequirePackage[option]{package_name}[time]
```

For example:

```latex
\LoadClass[a5papar]{article}
```

After using command above, we will inherit all the property of **article** class with option **a5paper**.

## 8. Define a New Command

We have discussed command `\newcommand`, `\renewcommand` and `\providecommand` in 2.4 which are all avalible in macros file. But it must to be mentioned that they are all base on command `\def`, a primitive command used in $\TeX$.

