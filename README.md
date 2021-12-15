# LaTex 的安装与使用

[TOC]

## 1. 本地环境

- Tex 发行版： Tex Live 2021
- 编辑器： VSCode

## 2. LaTex 简介—— Tex 家族

- TeX - pdfTeX - XeTeX - LuaTeX ：**排版引擎** ；
- LaTeX ：一种 **格式** ，基于 TeX 格式定义了很多更方便使用的控制命令，上述四个引擎都有对应的程序将 LaTeX 格式解释成引擎能处理的内容；
- CTeX, MiKTeX, TeX Live ：TeX 的 **发行** 。

### 2.1. TeX - LaTeX

[TeX](https://en.wikipedia.org/wiki/TeX) ：由高德纳（Donald Ervin Knuth ）教授设计并实现的 **排版引擎** （ typesetting system ），同时也是该引擎使用的标记语言（ [Markup Language](en.wikipedia.org/wiki/Markup_language) ）的名称。这里的引擎指能够实现断行、分页等操作的程序，标记语言指一种将控制命令和文本结合起来的格式，主体是其中的文本而控制命令则实现一些特殊效果。

[LaTeX](https://en.wikipedia.org/wiki/LaTeX) ：由 L. Lamport 教授开发的基于 TeX 的 **排版系统** 。LaTeX 利用 TeX 的控制命令，定义了许多新的控制命令并封装成一个 **可执行文件** 。这个可执行文件会去解释 LaTeX 新定义的命令成为 TeX 的控制命令，并最终交由 TeX 引擎进行排版。

> 实际上， LaTeX 基于一个叫做 plain TeX 的格式。 plain TeX 是高德纳教授为了方便用户，自己基于原始的 TeX 定义的格式，但实际上 plain TeX 的命令仍然十分晦涩。至于原始的 TeX 直接使用的人就更少了，因此 plain TeX 格式逐渐就成为了 TeX 格式的同义词，尽管他们事实上是不同的。

因此在 TeX - LaTeX 组合中，

1. 最终进行断行、分页等操作的，是 TeX 引擎；
2. LaTeX 实际上是一个工具，它将用户按照它的格式编写的文档解释成 TeX 引擎能理解的形式并交付给 TeX 引擎处理，再将最终结果返回给用户。

### 2.2. pdfTeX - pdfLaTeX

TeX 系统生成的文件是 dvi 格式，虽然可以用其他程序将其转换为例如 pdf 等更为常见的格式，但是毕竟不方便。

> dvi 格式是为了排版而产生的，它本身并不支持所谓的「交叉引用」，pdfTeX 直接输出 pdf 格式的文档，这也是 pdfTeX 相对 TeX 进步（易用性方面）的地方。

为了解决这个问题，Hàn Thế Thành 博士在他的博士论文中提出了 [pdfTeX](en.wikipedia.org/wiki/PdfTeX) 这个对 TeX 引擎的扩展。二者最主要的差别就是

- pdfTeX ： **直接输出 pdf 格式文档** ；
- TeX 引擎： **输出 dvi 格式的文档** 。

pdfLaTeX** 这个程序的主要工作依旧是将 LaTeX 格式的文档进行解释，不过此次是将解释之后的结果交付给 pdfTeX 引擎处理。

### 2.3. XeTeX - XeLaTeX

高德纳教授在实现 TeX 的当初并没有考虑到中日韩等字符的处理，而只支持 ASCII 字符。这并不是说中日韩字符就无法使用 TeX 引擎排版了，事实上 TeX 将每个字符用一个框包括起来（这被称为盒子）然后将一个个的盒子按照一定规则排列起来，因而 TeX 的算法理论上适用于任何字符。ASCII 字符简单理解，就是在半角模式下你的键盘能直接输出的字符。

在 XeTeX 出现之前，为了能让 TeX 系统排版中文，国人曾使用了 天元、CCT、CJK 等手段处理中文。其中 天元和CCT 现在已经基本不用，CJK 因为使用时间长且效果相对较好，现在还有人使用。

不同于 CJK 等方式使用 TeX 和 pdfTeX 这两个不直接支持 Unicode 字符的引擎，[XeTeX](https://en.wikipedia.org/wiki/XeTeX) 引擎直接支持 Unicode 字符。也就是说现在不使用 CJK 也能排版中日韩文的文档了，并且这种方式要比之前的方式更加优秀。

XeLaTeX 和 XeTeX 的关系与 pdfLaTeX 和 pdfTeX 的关系类似

使用 XeTeX 引擎需要使用 [UTF-8 编码](https://en.wikipedia.org/wiki/UTF-8)。

### 2.4. LuaTeX

LuaTeX 是正在开发完善的一个 TeX 引擎

### 2.5. CTeX - MiKTeX - TeX Live

之前介绍了 TeX, LaTeX, pdfTeX, pdfLaTeX, XeTeX, XeLaTeX, LuaTeX 等，他们都是 TeX 家族的一部分。但是作为一个能够使用的 TeX 系统，仅仅有他们还是不够的。CTeX, MiKTeX, TeX Live 都是被称为 **「发行」** 的 **软件合集** 。他们包括了上述各种引擎的可执行程序，以及一些文档类、模板、字体文件、辅助程序等等。其中 CTeX 是建立在 MiKTeX 的基础之上的。

### 2.6. WHY LaTeX ?

[Why should I use LaTeX?](https://tex.stackexchange.com/questions/1756/why-should-i-use-latex)

## 3. Tex 发行版选择-- Tex Live 的安装

TeX Live 是 TUG (TeX User Group) 维护和发布的 TeX 系统，可说是「官方」的 TeX 系统。推荐任何阶段的 TeX 用户，都尽可能使用 TeX Live，以保持在跨操作系统平台、跨用户的一致性

[TexLive 官网](https://tug.org/texlive/)，跳转到 download 页面，选择对应操作系统的文件下载

或者 [Acquiring TeX Live as an ISO image](https://tug.org/texlive/acquire-iso.html) ，点击 `download from a nearby CTAN mirror` 进入随机的镜像网站或者点击 'mirror list' 手动选择镜像网站

这里我下载了 `texlive2021.iso`

### 3.1. Windows 下的安装

- 下载的压缩包，右键在打开方式中选择 *Windows 资源管理器* 打开
- 以管理员身份运行 `install-tl-windows.bat`
- 可以自定义安装路径
- 下面使用 VSCode 进行 LaTex 的编写，故取消安装 TeXworks 前端的选项
- 更多定制需求点击 Advanced
- 检测是否安装成功：打开 powershell ，输入命令 `xelatex -v` ，若输出版本信息表示安装成功

```powershell
XeTeX 3.141592653-2.6-0.999993 (TeX Live 2021/W32TeX)
kpathsea version 6.3.3
Copyright 2021 SIL International, Jonathan Kew and Khaled Hosny.
There is NO warranty.  Redistribution of this software is
covered by the terms of both the XeTeX copyright and
the Lesser GNU General Public License.
For more information about these matters, see the file
named COPYING and the XeTeX source.
Primary author of XeTeX: Jonathan Kew.
Compiled with ICU version 68.2; using 68.2
Compiled with zlib version 1.2.11; using 1.2.11
Compiled with FreeType2 version 2.10.4; using 2.10.4
Compiled with Graphite2 version 1.3.14; using 1.3.14
Compiled with HarfBuzz version 2.7.4; using 2.7.4
Compiled with libpng version 1.6.37; using 1.6.37
Compiled with pplib version v2.05 less toxic i hope
Compiled with fontconfig version 2.13.93; using 2.13.93
```

## 4. 使用 VSCode 编写+编译 LaTex 环境配置

### 4.1. WHY VSCode ?

### 4.2. 环境配置

安装扩展 LaTeX Workshop

#### 4.2.1. 修改 settings.json 文件

Ctrl+Shift+P 输入 json 找到 `Preference: Open Settings (JSON)` 这一项，点击打开 `settings.json` ，在配置中加入如下代码

**NOTE**: 在最后一行代码后加上代码需要首先在最后加上`,`

```json
    "latex-workshop.latex.autoBuild.run": "never",
    "latex-workshop.showContextMenu": true,
    "latex-workshop.intellisense.package.enabled": true,
    "latex-workshop.message.error.show": false,
    "latex-workshop.message.warning.show": false,
    "latex-workshop.latex.tools": [
        {// 编译工具和命令
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOCFILE%"
            ]
        },
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOCFILE%"
            ]
        },
        {
            "name": "latexmk",
            "command": "latexmk",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdf",
                "-outdir=%OUTDIR%",
                "%DOCFILE%"
            ]
        },
        {
            "name": "bibtex",
            "command": "bibtex",
            "args": [
                "%DOCFILE%"
            ]
        }
    ],
     "latex-workshop.latex.tools": [
        {// 编译工具和命令
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOCFILE%"
            ]
        },
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOCFILE%"
            ]
        },
        {
            "name": "latexmk",
            "command": "latexmk",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdf",
                "-outdir=%OUTDIR%",
                "%DOCFILE%"
            ]
        },
        {
            "name": "bibtex",
            "command": "bibtex",
            "args": [
                "%DOCFILE%"
            ]
        }
    ],
    "latex-workshop.latex.recipes": [
        {//编译链
            "name": "XeLaTeX",
            "tools": [
                "xelatex"
            ]
        },
        {
            "name": "XeLaTeX*2",
            "tools": [
                "xelatex",
                "xelatex"
            ]
        },
        {
            "name": "PDFLaTeX",
            "tools": [
                "pdflatex"
            ]
        },
        {
            "name": "BibTeX",
            "tools": [
                "bibtex"
            ]
        },
        {
            "name": "LaTeXmk",
            "tools": [
                "latexmk"
            ]
        },
        {
            "name": "xelatex -> bibtex -> xelatex*2",
            "tools": [
                "xelatex",
                "bibtex",
                "xelatex",
                "xelatex"
            ]
        },
        {
            "name": "xelatex -> biber -> xelatex*2",
            "tools": [
                "xelatex",
                "biber",
                "xelatex",
                "xelatex"
            ]
        },
        {
            "name": "pdflatex -> bibtex -> pdflatex*2",
            "tools": [
                "pdflatex",
                "bibtex",
                "pdflatex",
                "pdflatex"
            ]
        },
        {
            "name": "pdflatex -> biber -> pdflatex*2",
            "tools": [
                "pdflatex",
                "biber",
                "pdflatex",
                "pdflatex"
            ]
        },
    ],
    "latex-workshop.view.pdf.viewer": "tab",
    "latex-workshop.view.pdf.ref.viewer":"auto",
    "latex-workshop.latex.clean.fileTypes": [
        "*.aux",
        "*.bbl",
        "*.blg",
        "*.idx",
        "*.ind",
        "*.lof",
        "*.lot",
        "*.out",
        "*.toc",
        "*.acn",
        "*.acr",
        "*.alg",
        "*.glg",
        "*.glo",
        "*.gls",
        "*.ist",
        "*.fls",
        "*.log",
        "*.fdb_latexmk",
        
    ],
    "latex-workshop.latex.autoClean.run": "onFailed",
    "latex-workshop.latex.recipe.default": "lastUsed",
    "latex-workshop.view.pdf.internal.synctex.keybinding": "double-click"
```

##### 4.2.1.1. 配置代码解读

```json
"latex-workshop.latex.autoBuild.run": "never"
```

设置何时使用默认的(第一个)编译链自动构建 LaTeX 项目，即什么时候自动进行代码的编译。有三个选项：

1. `onFileChange` : 在检测任何依赖项中的文件更改(甚至被其他应用程序修改)时构建项目，即当检测到代码被更改时就自动编译tex文件；

2. `onSave` : 当代码被保存时自动编译文件；

3. `never` : 从不自动编译，即需编写者手动编译文档

```json
"latex-workshop.showContextMenu": true
```

启用上下文LaTeX菜单。此菜单默认状态下停用，即变量设置为false，因为它可以通过新的 LaTeX 标记使用（新的 LaTeX 标记能够编译文档，详见下文）。只需将此变量设置为true即可恢复菜单。即此命令设置是否将**编译文档的选项**出现在 *鼠标右键* 的菜单中。

此项设置为 true ，点击鼠标右键多出两个选项：

- Build LaTex project : 进行 tex 文件的编译
- SyncTeX from cursor : 进行正向同步，即从代码定位到编译出来的 pdf 文件相应位置

```json
"latex-workshop.intellisense.package.enabled": true
```

启用宏包补全

此项设置为 true ，能够从使用的宏包中自动提取命令和环境，从而补全正在编写的代码。

```json
"latex-workshop.message.error.show"  : false,
"latex-workshop.message.warning.show": false
```

文档编译是否显示出错和警告的弹窗。

设置为 false，因为这些错误和警告信息会在终端中显示。

```json
    "latex-workshop.latex.tools": [
        {// 编译工具和命令
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOCFILE%"
            ]
        },
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOCFILE%"
            ]
        },
        {
            "name": "latexmk",
            "command": "latexmk",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdf",
                "-outdir=%OUTDIR%",
                "%DOCFILE%"
            ]
        },
        {
            "name": "bibtex",
            "command": "bibtex",
            "args": [
                "%DOCFILE%"
            ]
        }
    ]
```

*定义* 在 *recipes 编译链* 中被使用的 **编译命令**，此处为默认配置。

- name : 命令的标签，用作下文 recipes 的引用
- command : 在该拓展中的编译命令。
- args : 调用命令时添加的命令行参数

###### 更改配置

`%DOCFILE` 可以更改为 `%DOC` 

- `%DOCFILE` 表明编译器访问 *没有扩展名的根文件名* 
- `%DOC` 表明编译器访问 *没有扩展名的根文件完整路径*

使用 `%DOCFILE` 可以将文件所在路径设置为中文，但不建议这么做，因为毕竟涉及到代码，当其余编译器引用时该 tex 文件仍需要根文件完整路径，且需要为英文路径

更多参数信息可以访问 github 中 LaTeX-Workshop 的 [Wiki](https://github.com/James-Yu/LaTeX-Workshop/wiki/Compile#placeholders): 


```json
     "latex-workshop.latex.tools": [
        {// 编译工具和命令
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOCFILE%"
            ]
        },
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOCFILE%"
            ]
        },
        {
            "name": "latexmk",
            "command": "latexmk",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdf",
                "-outdir=%OUTDIR%",
                "%DOCFILE%"
            ]
        },
        {
            "name": "bibtex",
            "command": "bibtex",
            "args": [
                "%DOCFILE%"
            ]
        }
    ],
    "latex-workshop.latex.recipes": [
        {//编译链
            "name": "XeLaTeX",
            "tools": [
                "xelatex"
            ]
        },
        {
            "name": "XeLaTeX*2",
            "tools": [
                "xelatex",
                "xelatex"
            ]
        },
        {
            "name": "PDFLaTeX",
            "tools": [
                "pdflatex"
            ]
        },
        {
            "name": "BibTeX",
            "tools": [
                "bibtex"
            ]
        },
        {
            "name": "LaTeXmk",
            "tools": [
                "latexmk"
            ]
        },
        {
            "name": "xelatex -> bibtex -> xelatex*2",
            "tools": [
                "xelatex",
                "bibtex",
                "xelatex",
                "xelatex"
            ]
        },
        {
            "name": "xelatex -> biber -> xelatex*2",
            "tools": [
                "xelatex",
                "biber",
                "xelatex",
                "xelatex"
            ]
        },
        {
            "name": "pdflatex -> bibtex -> pdflatex*2",
            "tools": [
                "pdflatex",
                "bibtex",
                "pdflatex",
                "pdflatex"
            ]
        },
        {
            "name": "pdflatex -> biber -> pdflatex*2",
            "tools": [
                "pdflatex",
                "biber",
                "pdflatex",
                "pdflatex"
            ]
        },
    ],
```

*定义* **recipes 编译链**

- name : 标签，也就是出现在工具栏中的链名称；
- tools : name 标签所对应的编译顺序，其内部编译命令来自上文 latex-workshop.latex.recipes 中内容。

PDFLaTeX 编译模式与 XeLaTeX 区别如下：

1. PDFLaTeX 使用的是TeX的标准字体，所以生成PDF时，会将所有的非 TeX 标准字体进行替换，其生成的 PDF 文件默认嵌入所有字体；而使用 XeLaTeX 编译，如果说论文中有很多图片或者其他元素没有嵌入字体的话，生成的 PDF 文件也会有些字体没有嵌入。

2. XeLaTeX 对应的 XeTeX 对字体的支持更好，允许用户使用操作系统字体来代替 TeX 的标准字体，而且对非拉丁字体的支持更好。

3. PDFLaTeX 进行编译的速度比 XeLaTeX 速度快。

##### 4.2.1.2. WHY recipes ?

编译链的存在是为了更方便编译，因为如果涉及到.bib文件，就需要进行多次不同命令的转换编译，比较麻烦，而编译链就解决了这个问题。

```json
"latex-workshop.view.pdf.viewer": "tab"
```

设置默认 pdf 查看器

1. tab : 使用 vscode 内置浏览器
2. browser : 使用电脑默认浏览器
3. external : 使用外部 pdf 查看器

```json
"latex-workshop.view.pdf.ref.viewer":"auto"
```

设置PDF查看器用于在 \ref 命令上的[View on PDF]链接，此命令作用于 \ref 引用查看。

1. auto : 由编辑器根据情况自动设置

2. tabOrBrowser : 使用 vscode 内置 pdf 查看器或使用电脑默认浏览器

3. external : 使用外部 pdf 查看器

```json
    "latex-workshop.latex.clean.fileTypes": [
        "*.aux",
        "*.bbl",
        "*.blg",
        "*.idx",
        "*.ind",
        "*.lof",
        "*.lot",
        "*.out",
        "*.toc",
        "*.acn",
        "*.acr",
        "*.alg",
        "*.glg",
        "*.glo",
        "*.gls",
        "*.ist",
        "*.fls",
        "*.log",
        "*.fdb_latexmk"
    ]
```

设置编译完成后要清除掉的辅助文件类型，若无特殊需求，无需进行更改。

```json
"latex-workshop.latex.autoClean.run": "onFailed"
```

设置什么时候对上文设置的辅助文件进行清除。其变量有：

1. onBuilt : 无论是否编译成功，都选择清除辅助文件；
2. onFailed : 当编译失败时，清除辅助文件；
3. never : 无论何时，都不清除辅助文件。

由于 tex 文档编译有时需要用到辅助文件，比如编译目录和编译参考文献时，如果使用onBuilt命令，则会导致编译不出完整结果甚至编译失败；

而有时候将 tex 文件修改后进行编译时，可能会导致 pdf 文件没有正常更新的情况，这个时候可能就是由于辅助文件没有进行及时更新的缘故，需要清除辅助文件了，而never命令做不到这一点；

onFailed，同时解决了上述两个问题。

```json
"latex-workshop.latex.recipe.default": "lastUsed"
```

设置 vscode 编译 tex 文档时的默认编译链。

1. first : 使用latex-workshop.latex.recipes中的第一条编译链，可以根据需要更改编译链顺序； 
2. lastUsed : 使用最近一次编译所用的编译链。

```json
"latex-workshop.view.pdf.internal.synctex.keybinding": "double-click"
```

用于 **反向同步**（从编译出的 pdf 文件指定位置跳转到 tex 文件中相应代码所在位置）的内部查看器的快捷键绑定。

1. ctrl-click : 默认选项，使用 Ctrl/cmd + 鼠标左键单击

2. double-click : 使用鼠标左键双击

### 4.3. 样例项目

Demo 代码请参考 [demo.tex](./Demo/demo.tex)

展示了一些基本功能

## 5. 在线编辑器 Overleaf

[Overleaf 官网](https://overleaf.com/)

[Overleaf 中文官网](https://cn.overleaf.com/)

### 5.1. 设置中文环境

```LaTex
\usepackage[chinese]{babel}
\usepackage{ctex}
```

menu / 菜单 -> 编译器选择 `XeLaTex`

## 6. LaTex 使用

### 6.1. 引用参考文献- BibTex

使用 BibTex 作为 Latex 文档引用的参考文献格式管理库

1. 创建 BibTex 文件
   相同目录下新建一个后缀名为 `.bib` 的文件，即创建了一个 BibTex 参考文献库，如：`ref.bib`
2. 添加引用文章的内容
   将要引用的文献的 BibTex 复制到 `ref.bib` 文件中
   获取参考文献的 BibTex 推荐 [Google Scholar](https://scholar.google.com/)，查找到文献后点击 `Cite` -> `BibTex` 得到 BibTex ，格式如下

   ```BibTex
    @inproceedings{yerlanova2021high,
        title={High performance computers: from parallel computing to quantum computers and biocomputers},
        author={Yerlanova, G and Serik, M and Kopyltsov, A},
        booktitle={Journal of Physics: Conference Series},
        volume={1889},
        number={3},
        pages={032032},
        year={2021},
        organization={IOP Publishing}
        }
   ```

3. 添加 cite 包；
   在 LaTex 文档里面添加包引用

   ```LaTex
   \usepackage{cite}
   ```

4. 添加引用配置；
   在 LaTex 文档里需要显示参考文献的位置添加

    ```LaTex
    \bibliographystyle{plain}
    \bibliography{ref}
    ```

    `\bibliography{ref}` 命令指定之前生成的 BibTex 参考文献库名称

    `\bibliographystyle{plain}` 命令指定参考文献的呈现方式，常见的预设样式的可选项有8种：

    - plain，按字母的顺序排列，比较次序为作者、年度和标题；
    - unsrt，样式同plain，只是按照引用的先后排序；
    - alpha，用作者名首字母+年份后两位作标号，以字母顺序排序；
    - abbrv，类似plain，将月份全拼改为缩写，更显紧凑；
    - ieeetr，国际电气电子工程师协会期刊样式；
    - acm，美国计算机学会期刊样式；
    - siam，美国工业和应用数学学会期刊样式；
    - apalike，美国心理学学会期刊样式；

5. 添加引用；
   在 LaTex 文档里面添加引用格式

   ```LaTex
   \cite{yerlanova2021high}
   ```

   花括号里面的内容为相关文献的引用格式的第一行内容

6. 生成 PDF。
   编译链 "xelatex -> biber -> xelatex*2" 或 "xelatex -> bibtex -> xelatex*2"

## 7. LaTex 问题

> Q1: biblatex 报错 I found no \bibstyle & \bibdata & \citation command

新版本的 BibLaTeX 默认使用 Biber 而非 BibTeX 进行处理参考文献

解决方案：

1. 添加宏包时注明使用 biblatex ；

```LaTex
\usepackage[backend=bibtex]{biblatex}
```

2. 或将编译器改为 Biber ，即编译文档时使用编译链 "xelatex -> biber -> xelatex*2"
