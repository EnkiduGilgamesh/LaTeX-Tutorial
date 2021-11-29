# 2.3 文档结构

## 2.3.1 标题样式设置

宏包 **ctex** 提供了 `\CTEXsetup` 命令来修改标题样式。

对照下列例子

```latex
\CTEXoptions[today=old]                     % samll, old
\CTEXsetup[name={第,章},                    % 章节名前后的字
        number={\chinese{section}},         % 数字的格式
        format={\raggedleft\bfseries},      % 章节全局格式
        nameformat={\sffamily},             % 章节名和编号格式，不包括后面标题
        numberformat={\itshape},            % 编号格式，不包括章节名和标题
        titleformat={\ttfamily},            % 标题格式，不包括章节名和编号
        %aftername={\\\vspace{2ex}},         % 章节名和编号与标题之间的内容，仅对 part 和 chapter 有效
        beforeskip={2cm},                   % 章节标题前的垂直距离
        afterskip={5cm},                    % 章节标题后的垂直距离
        indent={4em}                        % 章节标题的缩进长度
    ]{section}                              % 对象类型
```
