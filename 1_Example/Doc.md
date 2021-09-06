# LaTeX Example

[LaTeX Example](#latex-example)
  - [1 源文件](#1-源文件)
  - [2 问题记录](#2-问题记录)
    - [2.1 使用计量单位](#21-使用计量单位)
    - [2.2 Label 使用](#22-label-使用)
    - [2.3 图表位置](#23-图表位置)
    - [2.4 参考文献](#24-参考文献)
      - [2.4.1 Windows 10](#241-windows-10)
      - [2.4.2 Arch Linux](#242-arch-linux)
    - [2.5 Fontset](#25-fontset)

## 1 源文件

[EnkiduGilgamesh/LaTeX-Tutorial: My journey of LaTeX learning. (github.com)](https://github.com/EnkiduGilgamesh/LaTeX-Tutorial)

**Reference**

《LaTeX 入门》，张海洋

## 2 问题记录

### 2.1 使用计量单位

出现问题

```bash
Illegal unit of measure
```

这是因为图片宽度设置没有单位，无法判断大小。
将

```tex
\includegraphics[width=3]{xiantu.jpg}
```

改为

```tex
\includegraphics[width=3cm]{xiantu.jpg}
```

后面我又将其改为了

```tex
\includegraphics[scale=0.5]{xiantu.jpg}
```

**Reference**

[Illegal unit of measure (pt inserted)_Xovee-CSDN博客](https://blog.csdn.net/xovee/article/details/106633231)

### 2.2 Label 使用

```tex
\lable{fig:xiantu}

Undifined contron sequence
```
\lable{} 必须放在模块最后。但我确实是在最后。

可能与编译方式有关，xelatex 并不能识别这个命令。

我最后注释掉了这条语句。

**Reference**

[latex的label引用有时候不成功 - 简书 (jianshu.com)](https://www.jianshu.com/p/7213d30a6e3e)

[LaTex中编译时出现“! Undefined control sequence.”_ZoomToday-CSDN博客](https://blog.csdn.net/qq_36477513/article/details/107310936)

### 2.3 图表位置

结果中制作的表和插入的图片位置不正确。所用命令为
```tex
\begin{figure}[ht]

\begin{table}[h]
```
了解到 [] 内的选择有如下
* [h] ~ here，当前位置。将图形放置在正文文本中给出该图形环境的地方。如果本页所剩页面不够，这一参数将不起作用。
* [t] ~ top，顶部。将图形放置在页面的顶部。
* [b] ~ bottom，底部。将图形放置在页面的底部。
* [p] ~ page of its own，浮动页。将图形放置在一个允许有浮动对象的页面上。
字母按顺序组合在一起，则是按照顺序进行尝试。
例如 ht，会先尝试将图片放在此处，如若放不下，则 h 参数失效，t 参数生效。

我的图、表顺序改变的原因，就是因为 h 参数失效，图片和表插入了下一页，而后面的文本则填充到的剩余的空间。

调整方式有以下几种
1. 调整 htbp 参数；
2. 调整图片大小；
3. 使用 float 宏包中的 H 参数；
4. 手动插入空白行，以占用剩余空间。

我最后使用方法 4 解决了排版的问题。

```tex
...
如图 1.
\\[5pt]
```
第二行的命令是插入一个 5pt 高度的空白行。类似的命令有
```tex
~\\             %插入一个空白行
```
或使用命令进入新的一页
```tex
\newpage
```


**Reference**

[技能提升之Latex控制图片位置_LeonSUST的博客-CSDN博客_latex 双栏 图片通栏 控制位置](https://blog.csdn.net/LeonSUST/article/details/89332744)

[latex的Table参数_知至-CSDN博客](https://blog.csdn.net/kmsj0x00/article/details/82772000)

[latex自定义插入空行或者空格_CSer-CSDN博客_latex空行](https://blog.csdn.net/weixin_44489823/article/details/104952110)

[Latex入门的基本操作——换行、分段和换页 - 简书 (jianshu.com)](https://www.jianshu.com/p/7c0ad8e52faf)

**Extension**

[\莲枝专栏--“图片又飘到下一页去了！” - LaTeX科技排版工作室 (latexstudio.net)](https://www.latexstudio.net/archives/4683.html)

### 2.4 参考文献

#### 2.4.1 Windows 10

参考文献存放在 .bib 文件中，在 .tex 文件中，命令
```tex
\bibliographystyle{plain}
\bibliography{math}
```
第一行，表示对参考文献进行排序方式；第二行则是表示引用 math.bib 文件中的参考文献。

编写 bib 文件后出现问题
```
"message": "I found no \\citation commands",
```

不知是否是 Biblatex 使用 Biber 而不是 Bibtex 导致其无法识别。使用命令更改
```
\usepackage[backend=bibtex]{biblatex}
```
仍然出现相同的问题。
若改为 Biber 则出现
```
Package biblatex:"\'bibliographystyle' invalid"
```

尝试调整 ```\bibliographystyle{plain}``` 至最后（与书中不同），仍然和上述情况相同。

我再次翻阅了书籍，发现要在文本中插入 ```\cite{}``` 来表示对参考文献的引用。问题得以解决。

#### 2.4.2 Arch Linux

编译后 pdf 中没有参考文献。

查看 .log 看到
```
Info: Could not resolve font "FZKai-Z03/B"
Info: Could not resolve ...
```
起初认为是错误原因，下载相关字体，却发现已经安装。

怀疑是 fontset 中字体名称与系统不匹配导致。打开 fontset 配置文件，见 2.5. 同时使用命令查看中文字体列表，见 [Linux | Configure Your Arch](https://app.yinxiang.com/shard/s59/nl/27057169/e47c9fb8-3871-4512-9011-1417369bcf32).

发现字体名称为 "FZKai\-Z03"。将 fontset 配置中字体改为这个名字后，编译失败了。字体列表中的 \ 应该是一个转义符。

我更换了一个 fontset=windows 后，发现情况和 fontset=founder 类似（安装了所需字体后）。提示也只是 Info，于是我认为这并不是原因。

我突然想起 《LaTeX 入门》中讲解过 .bib 文件百编译的问题，由于我使用命令行进行编译，文献所依赖的 .bib 文件并没有被编译。翻阅书籍后，我找到解决方法。
```
$ xelatex "filename.tex"
$ bibtex "filename.aux"
$ xelatex "filename.tex"
```
1. 第一次编译生成 bibtex 需要的 .aux 文件；
2. 第二次编译通过 .aux 中的信息， bibtex 从文献数据库中选取在 .tex 文件中用到的文献进行编译；
3. 第三次编译即可将参考文献信息写入，但此时顺序可能会出错；
4. 第四次编译可以将参考文献的顺序调整至于正文出现顺序一致。

**Reference**

[LaTeX编译参考文献“I found no \citation commands---while reading file”问题_ya6543的博客-CSDN博客](https://blog.csdn.net/ya6543/article/details/112542915)

[在LaTeX中如何引用参考文献 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/265479955)

[LATEX插入参考文献（两种方法）_feiba54的博客-CSDN博客_latex 插入参考文献](https://blog.csdn.net/qq_39540454/article/details/107604031)

### 2.5 Fontset

Fontset 指定 CTEX 宏集加载的字库。
可以自己写一份配置文件，命名为 ctex-fontset-⟨name⟩.def，然后调用。

我设置 ```fontset=founder``` 后，编译文件，出现以下问题
```
Warning: There were undifined references. 
Warning: Ciation 'Kline' undifined.
...
```
检查日志文件，发现下面记录
```
/* -------- Gougu.log --------- */
/* ------------------------------ */

error: pdflatex.exe (file FZKTK.TTF): cannot open TrueType font file for reading
```
我猜测是因为缺少字库中所需的字体，导致其无法通过编译。

安装缺少字体后，成功通过了编译。

Linux 下，fontset 配置文件在路径 /usr/local/...（查看 .log） 下，如果找不到某种字体，可以更改其中的配置。

**Reference**

[latex编译错误(pdflatex.exe (file simsun.ttf):cannot open TrueType font&_华东_新浪博客 (sina.com.cn)](http://blog.sina.com.cn/s/blog_92d2c5e10101cktw.html)

[fontset=zy是什么意思？ - LaTeX 工作室 - 专职专业 LaTeX 服务网站问答社区 (latexstudio.net)](https://ask.latexstudio.net/ask/question/3426.html)