# 2.4 页面设计

## 2.4.1 文档类

ctex 文档类有 ctexart, ctexrep, ctexbook.

它们的选项有如下：

| 类型 | 选项 | 说明 |
| --- | --- | --- |
| 字号 | c5size | 正文 5 号字 |
|  | c4size | 正文 4 号字 |
| 章节 | sub3section | \paragraph 标题单独占用一行 |
|  | sub4section | \paragraph 和 \subparagraph 标题单独占用一行 |
| 编码 | GBK |  |
|  | UTF8 |  |
| 字库 | nofonts | 不设定 |
|  | winfonts |  |
|  | adobefonts |  |
|  | ... |  |
| 排版 | cap | 中文标题、编号、日期 |
|  | nocap | 保留英文标题、编号、日期 |
|  | punct | 启用标点压缩（默认） |
|  | nopunct | 关闭标点压缩 |
|  | indent | 首行缩进 |
|  | noindent | 无缩进 |
| 宏包兼容 | fancyhdr | 调用 fancyhdr 宏包并兼容 |
|  | hyperref | 调用 hyperref 宏包并与之兼容 |
|  | fntef | 调用 fntef 宏包并与之兼容 |
