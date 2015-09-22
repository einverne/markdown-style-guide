---
title: Markdown 书写风格指南
description: 在线 Markdown 书写风格指南
---

参考 [原始设计规范](http://daringfireball.net/projects/markdown/syntax),
[CommonMark](http://commonmark.org) 和其他扩展。

本项目由社区驱动, 尝试达成共识。
只有当社区达成一致时，项目维护者才将其加入此文档。

讨论将在 [GitHub issue]({{ site.github }}/issues) 展开。

本文档源代码托管在 [GitHub]({{ site.github }})。

- a
{:toc}

## 关于 {#about}

### 设计目标 {#design-goals}

-   易读

-   可移植性: 通过不同的实现，产生相同的输出或者更好的输出文本。

    移植性测试在 [Markdown Test Suite](https://github.com/karlcow/markdown-testsuite) 开展。

-   容易书写和修改

-   友好的文件差异对比

-   容易记忆，容易被编辑器实现

-   从不同的选择中抽取基本原理

    每一个需要解释的区域或者段落都会标注 `rationale`
    所以，如果你只对最后的规范感兴趣，可以跳过解释。

### 著名用户 {#notable-users}

- [GitLab](https://github.com/gitlabhq/gitlabhq/blob/master/CONTRIBUTING.md#style-guides)
- [Vim Markdown](https://github.com/plasticboy/vim-markdown/blob/master/CONTRIBUTING.md#style)

你在使用这份风格指南吗？ 将你的名字添加到我们的 [wiki]({{ site.github }}/wiki/Users).

如果你很著名? 给我们发送一个 pull request.

如果你是一个著名的用户：

-   你会在此标准遇到较大更新时得到提醒。
    在提交 pull request 之前请提前了解。

-   你对此标准的决定，制定者会有更大的考虑。

如果你的项目满足以下条件，请毫不犹豫的发送 pull request吧：

-   大量使用 Markdown . 比如说: markdown 引擎, markdown 文本编辑器, 大量 markdown 文档等等。

-   是否受到欢迎的标准。任何的流行评判标准都会考虑。 比如说，GitHub 加星数,
    Google Rank 等等. 2K+ GitHub 加星会很有说服力。

### 可选 {#options-system}

有争议的内容会给出多种可选择的风格。

每一种可选项会用小写连字符分割提示。

每一种可选项都会有以下格式的说明:

    # Option key:value

The first option header that appears in this text is the default value.

比如， 如果自动换行 `wrap` 有三种风格，我们会给出关键词 `wrap`,
并且给每一种风格一种名字，比如：

    # Option wrap:space
    # Option wrap:no
    # Option wrap:sentence

当引用此标准时，准确标明所有非默认选项的风格，并用逗号分割：

    Use the Markdown Style Guide wrap:space, code:indented

### 书写约定 {#typographic-conventions}

当这份风格指南需要多种表示空格的方式，或者在代码区块开始或结束时出现空格时，点号将被用来表示空格。

例如:

`a`, 空格, `b`:

    a b

`a`, 2 空格, `b`:

    a..b

空格, `ab`:

    .ab

`ab`, 空格:

    ab.

### 可供选择 {#alternatives}

这份指南最初从[carwin/markdown-styleguide](https://github.com/carwin/markdown-styleguide/tree/9121c77bd177a3ade6713d50ab1228782d7c02a7) fork 得来.
原始文档已经被大规模的改动，一些决定已经被修改，几乎已经找不到原文。

Miguel de Icaza (GNOME, Mono) 已经提出一份简短的风格指南
<http://tirania.org/blog/archive/2014/Sep-30.html>

### Lint tools

在 Stack Exchange 上的提问: <http://softwarerecs.stackexchange.com/questions/7138/markdown-lint-tool/>

- <https://github.com/wooorm/mdast-lint>
- <https://github.com/mivok/markdownlint>

## 通用规则 {#general-rules}

### 文件 {#file}

#### 文件扩展名 {#file-extension}

使用 `.md`.

解释: 为什么不使用 `.mkd` 或者 `.markdown`?

- 更短
- 更加流行
- 没有明显冲突

#### 文件名 {#file-name}

文件名建议使用如下的风格:

- 用小写代替大写
- 把开头 `the`, `a`, `an` 除去
- 用连字符代替标点和空格
- 用一个连字符代替连续多个连字符，当多个连字符出现时，只使用一个
- 不在文件名前后使用连字符

建议使用:

    file-name.md

不建议, 多个连续的连字符:

    file--name.md

不建议, 包围的连字符:

    -file-name-.md

解释: 为何不使用下划线和驼峰大小写？连字符是现在最流行的网址分隔符，并且 Markdown 文件在上下文中经常使用:

- 可能在同一个项目中有连字符分割的HTML文件使用Markdown相同的目录。
- 文件名会被直接使用到 URL 中. 比如: GitHub blobs.

### 空白 {#whitespaces}

#### 新行 {#newlines}

*不要* 使用连续两空行，也就是说，不要连续使用两个换行符，除非是在代码块中不得已而必须出现。

以回车换行结束文件。*不要*在文件结束时留下空行。

*不要* 在行尾留空格除非是在行尾空出两个空格插入换行符。

建议使用:

    - list
    - list

    # Header

建议, 代码区块:

    The markup language X requires you to use triple newlines to separate paragraphs:

        p1


        p2

不建议：

    - list
    - list


    # Header

解释: 多空行占用更多的竖直屏幕空间，并且会严重影响到可读性。

#### 句子结束空格 {#spaces-after-sentences}

##### 可选 space-sentence:1 {#option-space-sentence-1}

句子结束使用一个空格

不建议, 使用2个空格:

    First sentence.  Second sentence.

建议使用:

    First sentence. Second sentence.

解释: 相比于`space-sentence:2`的优点:

-   容易编辑

-   通常不是必须的，如果使用 `wrap:inner-sentence` or `wrap:sentence`

-   `space-sentence:2` 对可读性造成一种错误的感觉，因为忽略了输出的 HTML 文件。

-   更加流行

相较于 `space-sentence:2` 的优势:

- 容易查看一句话的结束

##### 可选 space-sentence:2 {#option-space-sentence-2}

不建议, 单个空格:

    First sentence. Second sentence.

建议使用:

    First sentence.  Second sentence.

### 自动换行 {#line-wrapping}

#### 可选 wrap:inner-sentence {#option-wrap-inner-sentence}

尝试将一行限制在 80 个字符以下，将长段落按照以下的逻辑分开，例如:

-   句子: 一句话结束 `.` 之后, 问句问号 `?` 或者感叹句 `!` 之后

-   [子句 clauses](http://www.oxforddictionaries.com/words/clauses):
    在单词 `and`, `which`, `if ... then`, 逗号 `,` 之后

-   [短语 phrases](http://www.oxforddictionaries.com/words/phrases)

一行中超过80个字符是可以接受的，但是记住长句子不适合阅读，并且在 `git diff` 中会很难看。

设置你的文本编辑器对 Markdown 文件一行不要超过80字符，以免忘记。

建议使用:

    This is a very very very very very very very very very very very very very long not wrapped sentence.
    Second sentence of of the paragraph,
    third sentence of a paragraph
    and the fourth one.

解释:

-   Diffs 工具看起来更好, 因为一个子句的修改在 diff 工具中显示为一行修改.

-   临时的换行不会降低对 Markdown 文件的可读性，
    因为唯一的语言特性，可以缩进表示层次结构的就是嵌套列表。

-   现在除了 GitHub 在 README 和评论中将单独一行解释成回车。
    没有其他主流的解释引擎这么做，使用换行是非常安全的。

-   一些工具对较长的一行不友好，比如 Vim 并且 `git diff` 默认并不换行.
    这些不友好都可以通过配置除去，对于git，使用 `git config --global core.pager 'less -r'` 对于Vim可以使用 `set wrap` 来自动换行.

缺点:

-   需要在写作时增加顾虑，尤其是在修改代码的时候。

-   Markdown 看起来和渲染输出不同, 输出没有换行符。

    手动的换行可以让 Markdown 比生成的文档更加易读，
    当然这样做的同时，也造成了一种虚假的可读性错觉，让人感觉没有长段落。

-   需要用户拥有使用可编程文本编辑器，类似 Vim，可以通过配置来换行。[EditorConfig gave it WONTFIX](https://github.com/editorconfig/editorconfig/issues/168)

#### 可选 wrap:no {#option-wrap-no}

不要自动换行.

解释: 很容易编辑。但是长句子的 diffs 很难阅读。

#### 可选 wrap:space {#option-wrap-space}

在超过80个字符的第一个单词换行。

解释: 源文件易读，并且文本编辑器支持。Diff 比较难读，并且修改困难。

#### 可选 wrap:sentence {#option-wrap-sentence}

解释: 和 `wrap:inner-sentence` 相似的优点, 但是规则通俗易懂:
在句号后换行。对于长句子依然面临 Diff 难以阅读的困扰。

著名事件: [ProGit 2](https://raw.githubusercontent.com/progit/progit2/5c285553c0605342339284981a9bb8a6c4e7c18e/book/01-introduction/1-introduction.asc).

### 代码 {#code}

#### Shell中美元符号 {#dollar-signs-in-shell-code}

*不要* 在 shell 代码前加 `$` 符号，除非你想要展示命令的输出。

如果目的是表明确切的语言，那么直接在代码前标明。

解释: 复制粘贴比较困难，不利于阅读。

建议使用:

    echo a
    echo a > file

不建议：

    $ echo a
    $ echo a > file

建议, 展示输出:

    $ echo a
    a
    $ echo a > file

建议, 在代码前标明代码语言:

    Use the following Bash code:

    echo a
    echo a > file

#### 标记代码内容 {#what-to-mark-as-code}

使用代码块，或者行内代码：

-   可执行文件。 比如：

        `gcc` is the best compiler available.

    注意将工具名字和项目工程名字区别开来。比如： `gcc` vs GCC.

-   文件路径

-   程序版本号

-   大写的缩写解释:

        xinetd stands for `eXtended Internet daemon`

-   其他和电脑相关的术语，想要单独标明

不要标记为代码：

-   项目名。 比如： GCC
-   函数库名。比如： libc, glibc

#### 拼写和语法 {#spelling-and-grammar}

使用正确的拼写和语法。

尽量选用英语，更准确的说美式英语。
解释: 美式英语使用者占有最大的GDP，尤其是在计算机行业。

类似 URL 或者代码，添加代码标记，这样拼写检查程序会自动忽略。

注意大小写敏感的拼写错误，尤其是项目名，品牌名，或者缩写。

- 建议使用: URL, LinkedIn, DoS attack
- 不建议： `url`, `Linkedin`, `dos attack`

一旦有疑惑，尽量选用和维基百科相同的缩写。

避免使用非正式的缩写:

- 建议使用: biography, repository, directory
- 不建议： `bio`, `repo`, `dir`

## 区块 {#block-elements}

### 换行符 {#line-breaks}

避免使用换行符, 因为他们没有被广泛认可的语义。

在少数确实需要使用的时候，在行尾使用两个空格。

### 标题 {#headers}

#### 可选 header:atx {#option-header-atx}

不建议：

    Header 1
    ========

    Header 2
    --------

    ### Header 3

建议使用:

    # Header 1

    ## Header 2

    ### Header 3

-   解释: 相比 Setex 优势有:

    -   容易书写，因为在 Setex 中，为了好看需要书写和标题相同数量的符号

    -   可以生成所有的等级，而 Setex 只能生成两种等级

    -   只占用一行，而 Setex 占用两行

    Setex 的优点

    -   更加明显。 Not very important if you have syntax highlighting.

-   在 `#` 和标题之间加入一个空格.

    不建议：

        #Header

        #..Header

    建议使用:

        # Header

-   *不要* 使用闭合的 `#` .

    不建议：

        # Header #

    建议使用:

        # Header

    解释: 容易维护。

-   *不要* 在 `#` 前加入空格.

    不建议：

        .# Header

    建议使用:

        # Header

#### 可选 header:setex {#option-header-setex}

不建议：

    # Header 1

    ## Header 2

    ### Header 3

建议使用:

    Header 1
    ========

    Header 2
    --------

    ### Header 3

---

-   *不要* 跳跃使用标题等级.

    不建议：

        # Header 1

        ### Header 3

    建议使用:

        # Header 1

        ## Header 2

-   在标题上下用空行隔开，除非标题在文档开头。

    不建议：

        Before.
        # Header 1

        ## Header 2
        After.

    建议使用:

        Before.

        # Header 1

        ## Header 2

        After.

    不建议：

        Before.
        Header 1
        ========

        ## Header 2
        -----------
        After.

    建议使用:

        Before.

        Header 1
        ========

        ## Header 2
        -----------

        After.

-   *避免* 在相同 Markdown 文件中使用相同的标题.

    解释: 许多的 Markdown 解释器会依据标题的内容生成标题的IDs。

    不建议：

        # Dogs

        ## Anatomy

        # Cats

        ## Anatomy

    建议使用:

        # Dogs

        ## Anatomy of the dog

        # Cats

        ## Anatomy of the cat

#### 顶级标题 {#top-level-header}

如果你想要 HTML 直接输出，这样唯一的 `h1` 标记就是输出的第一件事，并且会成为文档的标题。这就是HTML的顶级标题。

`h1` 标题的产生受到使用的 Markdown 引擎的直接影响：
一些引擎会从元数据（metadata）中产生标题，比如 Jekyll 就是从 front-matter 中产生标题。

将顶级标题保存为元数据（metadata）可以更加方便的在其他地方使用，
比如，在全局索引中，但也有缺点，比如降低了可读性和移植性。

如果目的不是生成顶级标题，
include it in your markdown file. E.g., GitHub.

索引文件中的顶级标题比如 `README.md` 或者 `index.md`
应该作为他们父目录的标题。

顶级标题的缺点：

-   占用了一级标题。这就意味只剩下5个层级标题可以使用。
    并且这样每一个新的标题就会多使用一个 `#` 符号,这样看起来不好。

-   重复了文件名, 通常已经可以直接从 URL 中读到。
    在大多数的情况下，文件名可以直接转换成顶级标题，
    比如: 从 `some-filename.md` 到 `Some filename`.

顶级标题的优点:

-   比URL更加易读，尤其是对非技术出身用户。

#### 标题大小写 {#header-case}

-   标题开头使用大写字母，除非标题内容总是以小写出现, 例如，计算机代码。

    建议使用:

        # Header

    建议使用, 代码通常以小写开始：

        # int main

    不建议：

        # header

-   其他字母按照句子中原始大小写。

    建议使用:

        # The header of the example

    不建议：

        # The Header of the Example

    例外, [首字大写](http://en.wikipedia.org/wiki/Title_case#Title_case)
    对 [顶级标题](#top-level-header) 可选择性支持。
    请异常谨慎地使用, in cases where typographical perfection is important,
    比如：项目的 `README` .

    解释: 为什么对所有标题[首字大写](http://en.wikipedia.org/wiki/Title_case#Title_case) ?
    如果要决定句子中每一个单词大小写会花费太多精力。

#### 标题结尾 {#end-of-a-header}

显示标题的内容，而不是用新标题和水平线紧随其后：

    # Header

    Content

    ---

    Outside header.

#### 标题长度 {#header-length}

保证标题越短越好。

避免使用长句子，总结长句子作为标题，然后将长句子作为标题下的第一小节。

解释: 以后引用方便，尤其是自动生成 IDs 或者生成 TOC 。

建议使用:

    # Huge header

    Huge header that talks about a complex subject.

不建议：

    # Huge header that talks about a complex subject

#### 标题结尾标点 {#punctuation-at-the-end-of-headers}

*不要* 在标题中以 `:` 结尾。

解释: 每一个标题都是接下来内容的简介，这也就正是冒号的作用。

*不要* 在标题中以 `.` 结尾。

解释: 每一个标题都包含一个简短的句子，也就不需要句号来分隔他们。

建议使用:

    # How to do make omelet

不建议：

    # How to do make omelet:

不建议：

    # How to do make omelet.

#### 标题同义词 {#header-synonyms}

标题用作用户索引的关键词。

正由于这个原因，你可能希望在标题中用多个关键词。

要做到这一点，简单的创建一个同义词标题在主标题之前，并且标题下不包含内容。

比如：

    # Purchase

    # Buy

    You give money and get something in return.

每一个同层级的空标题都假定是同义的。如果层级不一样，那就是另外的含义：

    # Animals

    ## Dog

### 引用 {#blockquotes}

-   在符号 `>` 后面接一个空格。

    建议使用:

        > a

    不建议：

        >a

    不建议, 2个空格:

        >  a

-   在每一行使用 `>` 符号，包括换行的句子。

    不建议：

        > Long line
        that was wrapped.

    建议使用:

        > Long line
        > that was wrapped.

-   *不要* 在单独的引用中使用空行。

    建议使用:

        > a
        >
        > b

    不建议：

        > a

        > b

### 列表 {#lists}

#### 标记 {#marker}

##### 无序 {#unordered}

使用连字符.

建议使用：

    - a
    - b

不建议：

    * a
    * b

<!-- -->

    + a
    + b

解释:

- 星号 `*` 可能和加粗和斜体符号产生混淆。
- 加号 `+` 不流行。

##### 有序 {#ordered}

尽量选用 `1.` 来标记有序的列表, 除非你打算通过数字在相同 Markdown 文件或者外部文件中引用他们。

尽量使用无序的列表，除非有通过数字引用的需求。

最佳则是从来不通过序号来引用他们：

    - a
    - c
    - b

较好的方法, 仅仅使用 `1.`:

    1. a
    1. c
    1. b

较差的方法, 不要通过序号来标注列表项的顺序:

    1. a
    2. c
    3. b

可接受的, 使用文本引用:

    The ouput of the `ls` command is of the form:

        drwx------  2 ciro ciro        4096 Jul  5  2013 dir0
        drwx------  4 ciro ciro        4096 Apr 27 08:00 dir1
        1           2

    Where:

    1. permissions
    2. number of files directory contains

可接受，通过外部 markdown 文件引用:

    Terms of use.

    1. I will not do anything illegal.
    2. I will not do anything that can harm the website.

解释:

-   如果你想要改变列表中的一个列表项，你不要修改它下面的列表项。

    Diffs 工具只会显示被修改的重要的内容。

-   如果序列有两位，也不需要额外注意，内容保持一致。 比如：下面不对齐：

        9. a
        10. b

-   如果新列表项被加入，引用会破坏。尽量减少这种问题：

    - 保证引用靠近列表，这样作者会更少可能的忘记去更新
    - 当从外部引用时，总是引用到一个固定版本的 markdown 文件

#### 列表项中的空格 {#spaces-after-list-marker}

##### 可选 list-space:mixed {#option-list-space-mixed}

-   如果每一个列表项的内容都只有一段，使用 **1** 个空格。

-   否则，对于列表中的每一项:

    -   给无序列表使用 **3** 个空格。

    -   给有序列表使用 **2** 个空格。
        比无序少一个空格，因为符号占用两个字符。

不建议, 每一项一行:

    -   a
    -   b

建议使用:

    - a
    - b

不建议, 每一项一行:

    1.  a
    1.  b

建议使用:

    1. a
    1. b

每一项超过一行，不建议：

    - item that
      is wrapped

    - item 2

建议使用:

    -   item that
        is wrapped

    -   item 2

每一项超过一行，不建议：

    - a

      par

    - b

建议使用:

    -   a

        par

    -   b

##### 可选 list-space:1 {#option-list-space-1}

列表项标记前总是留有一个空格。

不建议, 使用三个空格:

    -   a

        b

    -   c

建议使用:

    - a

      b

    - c

不建议, 两个空格:

    1.  a

        b

    1.  c

建议使用:

    1. a

       b

    1. c

##### 解释: list-space mixed vs 1 {#rationale-list-space-mixed-vs-1}

使用 `list-space:1` 的有点：

-   它去除了你需要决定在列表符号后面放置多少空格的顾虑：
	因为只放一个

    我们也可以选择在列表项中如下缩进：

        -   a
        -   b

    但是这样非常丑。

-   你不会因为新列表项而改变整个列表的缩进。

    但是这样的情况会发生在 `list-space:mixed` 如果你有：

        - a
        - b

    并且想要增加一个多段落列表项：

        -   a

        -   b

        -   c

            d

    注意， `a` 和 `b` 都因为 `c` 而改变了。

使用 `list-space:1` 的缺点：

-   产生了三种缩进方式：

    - 4 for 缩进的代码块
    - 3 for 有序列表
    - 2 for 无序列表

    这意味着你不能轻松的配置编辑器缩进来处理所有的情况， 当你想要改变缩进层级的时候需要调整多行。

-   没有被编辑器实现。

    具体来说下面的情况会发生什么:

        - a

                code

    这个(2 个空格):

        <pre><code>  code

    或者没有空格：

        <pre><code>code

    原始的 markdown 说不需要空格:

    > To put a code block within a list item, the code block
    > needs to be indented twice — 8 spaces or two tabs

    但是许多第三方的实现了。

    CommonMark [adds the 2 spaces](http://spec.commonmark.org/0.12/#example-176).

#### 列表内容的缩进 {#indentation-of-content-inside-lists}

列表中内容的缩进层级必须和第一个列表项一致：

不建议：

    -   item that
      is wrapped

    -   item 2

建议使用:

    -   item that
        is wrapped

    -   item 2

不建议：

    -   item 1

      Content 1

    -   item 2

          Content 2

建议(如果符合列表标记之后的空格):

    -   item 1

        Content 1

    -   item 2

        Content 2

不建议：

    - item 1

        Content 1

    - item 2

        Content 2

建议(如果符合列表标记之后的空格):

    - item 1

      Content 1

    - item 2

      Content 2

避免开始直接使用缩进的代码列表项，因为这样不容易实现。[CommonMark states that](http://spec.commonmark.org/0.12/#example-176) 一个单独的空格需要加入:

    -     code

      a

#### 列表中的空行 {#empty-lines-inside-lists}

如果每一个列表项只有一行, 不要在列表项之间增加空行，否则，在每一个列表项之间增加空行。

不建议, single lines:

    - item 1

    - item 2

    - item 3

建议使用:

    - item 1
    - item 2
    - item 3

多行情况下，不建议:

    -   item that
        is wrapped
    -   item 2
    -   item 3

建议使用:

    -   item that
        is wrapped

    -   item 2

    -   item 3

不建议, 多行:

    -   item 1

        Paragraph.

    -   item 2
    -   item 3

建议使用:

    -   item 1.

        Paragraph.

    -   item 2

    -   item 3

不建议, 多行:

    -   item 1

        - item 11
        - item 12
        - item 13

    -   item 2
    -   item 3

建议使用:

    -   item 1

        - item 11
        - item 12
        - item 13

    -   item 2

    -   item 3

解释: 如果没有空行，很难分别多行的列表项开始和结束。

#### 列表外的空行 {#empty-lines-around-lists}

列表外建议留有一空行。

不建议：

    Before.
    - item
    - item
    After.

建议使用:

    Before.

    - list
    - list

    After.

#### 列表项首字母大小写 {#case-of-first-letter-of-list-item}

每一个 list 使用原来在句子中的大小写.

建议使用:

    I want to eat:

    - apples
    - bananas
    - grapes

因为它可以被如下替换：

    I want to eat apples
    I want to eat babanas
    I want to eat grapes

建议使用:

    To ride a bike you have to:

    - get on top of the bike. This step is easy.
    - put your foot on the pedal.
    - push t the pedal. This is the most fun part.

因为它可以被如下替换：

    To ride a bike you have to get on top of the bike. This step is easy.
    To ride a bike you have to put your foot on the pedal.
    To ride a bike you have to push the pedal. This is the most fun part.

建议使用:

    # How to ride a bike

    - Get on top of the bike.
    - Put your feet on the pedal.
    - Make the pedal turn.

因为它可以被如下替换：

    # How to ride a bike

    Get on top of the bike.
    Put your feet on the pedal.
    Push the the pedal.

#### 列表项结尾标点 {#punctuation-at-the-end-of-list-items}

列表项结尾标点，除非:

- 包含多个句子或者短语
- 以大写字母开头

否则, 如果以句号结尾的话，省略标点.

不建议使用，以:

    - apple.
    - banana.
    - orange.

建议使用:

    - apple
    - banana
    - orange

同上:

    - go to the market
    - then buy some fruit
    - finally eat the fruit

建议使用, 不以句号结尾，而是以其他标点结尾：

    - go to the marked
    - then buy fruit?
    - of course!

不建议, 多个句子时末尾不加标点:

    - go to the market
    - then buy some fruit. Bad for wallet
    - finally eat the fruit. Good for tummy

建议使用:

    - go to the market
    - then buy some fruit. Bad for wallet.
    - finally eat the fruit. Good for tummy.

注意：没有任何理由阻止，一个列表项以句号结尾，另一个列表项没有。

不建议, 多段落:

    -   go to the market

    -   then buy some fruit

        Bad for wallet

    -   finally eat the fruit

        Good for tummy

建议使用:

    -   go to the market

    -   then buy some fruit.

        Bad for wallet.

    -   finally eat the fruit.

        Good for tummy.

不建议, 如果以大写字母开头，添加标点:

    - Go to the market
    - Then buy some fruit
    - Finally eat the fruit

建议使用:

    - Go to the market.
    - Then buy some fruit.
    - Finally eat the fruit.

### 定义列表 {#definition-lists}

*避免* 使用定义列表扩展，因为他并没有被多数实现，也没有出现在 CommonMark.

相反, 使用:

-   格式化列表:

    - 用加粗，链接，或者代码，格式化需要定义的内容
    - 将内容和定义使用冒号和空格分割 `:.`
    - 不要对齐定义，这样难以维护，并且不会显示在 HTML 输出

    建议使用:

        - **apple**: red fruit
        - **dog**: noisy animal

    建议使用:

        -   **apple**: red fruit.

            Very tasty.

        -   **dog**: noisy animal.

            Not tasty.

    建议使用:

        - [apple](http://apple.com): red fruit
        - [dot](http://dog.com): red fruit

    建议使用:

        - `-f`: force
        - `-r`: recursive

    不建议, 没有冒号:

        - **apple** red fruit
        - **dog** noisy animal

    不建议, 在术语和冒号之间有空格:

        - **apple** : red fruit
        - **dog** : noisy animal

    不建议, 定义对齐:

        - **apple**: red fruit
        - **dog**:   noisy animal

-   headers.

    建议使用:

        # Apple

        Red fruit

        # Dog

        Noisy animal

### 代码区域 {#code-blocks}

#### 可选 code:fenced {#option-code-fenced}

仅仅使用 fenced code blocks.

和缩进代码区块比较：

- 不足: 不是标准 markdown 语法, 因此缺少移植性，但是加入到CommonMark.
- 优点: 实现方式多, 包括 GitHub's, 并且允许指定代码的语言。

*不要* 缩进 fenced code blocks.

总是指定代码的语言。

建议使用:

    ```ruby
    a = 1
    ```

不建议：

    ```
    a = 1
    ```

#### 可选 code:indented {#option-code-indented}

仅仅使用缩进代码区域。

代码区域缩进4个空格。

---

代码区块必须以一空行隔开。

尽量在代码块之前使用冒号结束短语 `:`。

建议使用:

    use this code to blow up your PC:

        sudo rm -rf /

不建议, 没有冒号

    use this code to blow up your PC

        sudo rm -rf /

### 水平横线 {#horizontal-rules}

*不要* 使用水平线除非表明[End of a header](#end-of-a-header).

解释:

-   标题比区块更好，因为标题就是区块的开始，并且说明了区块的内容。

-   水平线没有可接受的语义。
    这份风格指南给了语义。

使用 3 个无空格连字符:

    ---

### 表格 {#tables}

扩展.

-   用一空行包围表格。

-   不要缩进表格。

-   用 `|` 包裹表格的每一行。

-   竖直对齐所有表格边框。

-   将标题和内容用连字符分割，用对齐的 `|`。

-   `|` 周围必须要有一个空格，除非是外部的 `|`。

-   列的宽度通过列中最长的单元格确定。

建议表格:

    Before.

    | h    | Long header |
    |------|-------------|
    | abc  | def         |
    | abc2 | def2        |

    After.

解释:

-   不对齐的表格很容易书写，但是对齐的表格更加易读，并且人们读代码比编辑要更多。

-   开始的 `|` 更加容易看出表格的开始和结束。结尾的 `|` 让人看起来更加舒服，因为对称。

-   这些工具让表格对齐更加容易。比如，Vim 有 [Tabular plugin](https://github.com/godlygeek/tabular) 插件，这个插件让我们可以使用 `:Tabular /|` 来使整个表格对齐。

-   为什么在连字符分割行 `|` 没有空格包围, 比如: `|---|` 而不是 `| - |`?
    没有空格看起来更好，在GitHub可行， 缺点: 编辑器中自动对齐实现困难，因为对于分割行需要特殊的规则。

### 分离相连的列表 {#separate-consecutive-elements}

分离连续:

- 列表
- 缩进的代码块
- 引用
- 列表之后跟随额外的代码块

使用一个空白的 HTML 注释 `<!-- -->`.

<!-- -->

    - list 1
    - list 1

    <!-- -->

    - list 2
    - list 2

<!-- -->

        code 1
        code 1

    <!-- -->

        code 2
        code 2

<!-- -->

    > blockquote 1
    > blockquote 1

    <!-- -->

    > blockquote 2
    > blockquote 2

<!-- -->

    - list
    - list

    <!-- -->

        code outside list
        code outside list

## Span元素 {#span-elements}

*不要* 使用内部空格。

建议使用:

    **bold**
    `code`
    [link](http://a.com)
    [text][name]

不建议：

    ** bold **
    ` code `
    [ link ]( http://a.com )
    [text] [name]

对于空格至关重要的行内代码：

- 在写作过程中解释空格存在的必要性
- 如果可能在空格之后加入其他内容

建议使用:

    使用连字符并跟随一个空格来表示无序列表。

解释: 大多数的浏览器不会生成包围的空格，或者复制的时候不会将他们添加到粘贴板。

### 链接 {#links}

#### 参考样式链接 {#reference-style-links}

链接:

-   使用结尾的 `[]` 隐式链接：

    建议使用:

        [a][]

    不建议：

        [a]

    解释: 省略 `[]` 大多数主要的实现都可以使用，但是这种方式并没有在文档中有实现，原始 Markdown 也没有提到。

定义:

- 必须写到文件末
- 必须以ID字符顺序排列
- 不要使用尖括号包裹URL
- align URLs and link names as in a table
- 链接 IDs 仅仅使用小写字母. 解释: 因为 IDs 区分大小写,
- 只用小写容易书写，并且可读性比大小写混合单词大很多。

建议使用:

    [id2]     http://long-url.com
    [long id] http://a.com        "name 1"

不建议, 没有安装 id 排序:

    [b] http://a.com
    [a] http://b.com

不建议, 没有对齐:

    [id] http://id.com
    [long id] http://long-id.com

#### 单引号或双引号标题 {#single-or-double-quote-titles}

使用双引号，*不要* 使用单引号。

解释: 单引号并不是在所有的实现中都有效，但是双引号可以。

### 强调 {#emphasis}

#### 加粗 {#bold}

使用双星号格式: `**bold**`.

解释: 比双下划线格式`__bold__`更加常见和可读性更高.

#### 斜体 {#italic}

使用单星号格式: `*italic*`.

解释:

- 比下划线格式更加常见，易读性更高
- 与加粗格式一致, 同样使用星号标记

#### 大写强调 {#uppercase-for-emphasis}

*不要* 使用大写来强调: 使用强调语法例如 **加粗** 或者 *斜体* 。

解释: CSS 有 `text-transform:uppercase` 属性,如果你愿意的话，可以轻松在全网站实现相同的效果。

#### 强调与标题 {#emphasis-vs-headers}

*不要* 使用强调元素(加粗或者斜体) 来介绍多行区块: 使用标题代替.

解释: 这个就是确切的标题的语义, 使用强调的并不是必须的。作为结果，许多实现，给标题增加有用的功能，并没有给强调元素，比如自动 `id` 来更加容易的引用标题。

建议使用:

    # How to make omelets

    Break an egg.

    ...

    # How to bake bread

    Open the flour sack.

    ...

不建议：

    **How to make omelets:**

    Break an egg.

    ...

    **How to bake bread:**

    Open the flour sack.

    ...

### 自动链接 {#automatic-links}

#### 使用尖括号自动链接 {#automatic-links-without-angle-brackets}

-   *不要* 使用不带尖括号的自动链接。

    建议使用:

        <http://a.com>

    不建议：

        http://a.com

    解释: 这个扩展中, `<>` 容易从键盘敲出，也同样容易读。

-   如果你不想文字链接自动链接，将他们以代码区块方式包裹，例如：

        `http://not-a-link.com`

    解释: 许多工具自动将 `http` 开头的字串解释成链接。

#### 内容的自动链接 {#content-of-automatic-links}

所有自动链接必须以字串 `http` 开始。

特别的, *不要* 在相对链接时使用自动链接。如果遇到相对链接，使用括号的方式创建链接。

建议使用:

    [file.html](file.html)

不建议：

    <file.html>

建议使用:

    <https://github.com>

不建议：

    <github.com>

解释: 将自动链接从HTML tags区分开很困难.
如果你想要一个相对的链接指向一个 `script` 的文件？

#### 电子邮件自动链接 {#email-automatic-links}

*不要* 使用电子邮件自动链接 `<address@example.com>`. 使用纯HTML .

解释: 标准 markdown 设计规范这样描述:

> "performs a bit of randomized decimal and hex entity-encoding
> to help obscure your address from address-harvesting spambots".

因此, 输出是随机的，丑陋的, 并且像规范中提到的:

> but an address published in this way will probably eventually start receiving spam

