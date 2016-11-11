## TJUThesisLatexTemplate
 
Latex template for TJU thesis. Forked from code.google.com/p/tjuthesis.
 
Modified for the new format requirements of the 2016 Master's thesis of Tianjin University.
 
---
 
## 说明
 
天津大学硕士学位论文LaTex模板。
 
模板源自[code.google.com/p/tjuthesis](code.google.com/p/tjuthesis)，此版本根据《天津大学关于博士、硕士学位论文统一格式的规定（试行版）》（2016.10.24），针对**全日制工程硕士学位论文**格式进行修改。
 
博士以及其他类型的硕士学位的封面、扉页等部分有点区别，细节参考《天津大学关于博士、硕士学位论文统一格式的规定（试行版）》，可自行修改。
 
查看最新学位论文格式可以进入[天津大学学位管理系统](http://121.193.130.234:7001/Degree/)，查看“学位论文格式规定”条目下的官方文件。
 
---
 
## 改动
 
#### 样式修改
 
+ 扉页修改为全日制工程硕士的格式
+ 扉页，论文标题的字体修改为宋体加粗
+ 修改正文小四字体为20pt行间距
+ 修改论文中英文标题的行距为1.25倍
+ 修改“独创性声明”与下面的间隙，以及一些格式微调
+ 修改“学位论文版权使用授权书”与下面的间隙
+ 修改扉页下面“学位论文作者签名”与“签字日期”的缩进
+ 修改文档格式，章节仅从奇数页开始
+ 修改正文字间距，每行大概为35个中文字符
+ 修改了目录格式
+ 修改了各级标题的段前段后间距
+ 参考文献bib中的中文文献需要注意加上language条目（非空就可以，不然中文参考文献的格式会不正确）
+ 修改documentclass为正反面，章节从奇数页开始
+ 独创性声明、目录、摘要都修改为从奇数页开始
+ 修改页边距：上：27.5mm；下25.4mm；左：35.7mm；右：27.7mm。页眉距边界15.0mm；页脚距边界17.5mm
+ 参考文献字体修改为小四
+ 参考文献英文中的et al修改为非斜体
 
#### 最近更新
 
+ 从[天津大学学位管理系统](http://121.193.130.234:7001/Degree/)下载了官方的格式规定文档（参考文献格式规定的起止页码间的符号为“-”，而信息学院转发的文档中的符号为“~”）。
 
---
 
## 如何使用
 
#### LaTex基础
 
[一份不太简短的 LaTeX 介绍](http://www.latexstudio.net/archives/6058)
 
[Documentation](http://www.latex-project.org/help/documentation/)
 
[Documentation - ShareLaTeX](https://www.sharelatex.com/learn)
 
#### 从旧版本更新到此版本
 
如果已经使用了之前的latex模板，可以通过以下步骤更新为此版本的格式：
 
1. 使用此版本下的以下文件替换（覆盖）旧版本的同名文件：

    + ./TJUThesis.bst
    + ./setup/format.tex
    + ./setup/package.tex
 
2. 修改文件./tjumain.tex

    复制旧版本./tjumain.tex中正文部分的多个`\include{body/yourchapter}`（当前论文的各个章节），分别填入此版本./tjumain.tex的相应位置，然后替换旧版本的./tjumain.tex。（如有需要可以注释掉47行：`\nocite{*}`）
 
3. 修改文件./preface./cover.tex

    将旧版本中文件./preface./cover.tex的各项目（标题、姓名、摘要...）依次填入此版本的同名文件的相应位置，然后替换旧版本的./preface./cover.tex。（非工程硕士自行修改）
 
4. 重新编译。
 
#### 自定义修改样式
 
由于文档中有些格式并没有严格要求或者有不同的理解，如需更改样式，可以参考这里给出的一些提示：
 
+ 文档要求”双面打印，且各章节从奇数页开始“。此版本的摘要、封面、扉页等都从奇数页开始，如有空白的偶数页，页眉页脚设置为空。主要涉及以下代码：
    - `\documentclass[12pt,openright,twoside]{book}`
    - `\clearpage{\pagestyle{empty}\cleardoublepage}`
 
+ 目录页的页眉页脚有点麻烦，貌似格式要求是没有页眉然后罗马数字的页码。主要涉及以下代码：
    - `\AtBeginDocument{\addtocontents{toc}{\protect\thispagestyle{only_foot}}}`
    - `\pagestyle{only_foot}`
    - `\tableofcontents`
    - `\thispagestyle{only_foot}`
 
+ 参考文献这次要求是GB/T 7714-2005（此版本已修改为非斜体的et al），需要注意的是中文参考文献，google scholar中的中文参考文献的bibTex大多没有language条目，而latex中根据language条目是否非空来判断增加“ ，等 ”或者“ ,et al ”，因此，需要在参考文献bib文件中的所有中文文献中增加"language={not_empty}"
 
+ 格式要求图片与正文的间隔是一行，但是此模板中的所有图片内容都在`\end{figure}`上通过`\vspace{\baselineskip}`额外增加了一行的空隙，可以考虑去掉这一行。
 
 