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

-   可移植性: 通过不同的实现，产生相同的输出或者更好的输出。

    移植性测试在 [Markdown Test Suite](https://github.com/karlcow/markdown-testsuite) 开展。

-   容易书写和修改

-   友好的文件差异对比

-   容易记忆，和被编辑器实现

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

比如， 如果自动换行有三种风格，我们会给出关键词 `wrap`,
并且给每一种风格一种名字：

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

Prefer to base the file name on the top-header level:

- 用小写代替大写
- 把开头 `the`, `a`, `an` 除去
- 用连字符代替标点和空格
- 用一个连字符代替连续多个连字符
- 不在前后使用连字符

建议使用:

    file-name.md

不建议, 多个连续的连字符:

    file--name.md

不建议, 包围的连字符:

    -file-name-.md

解释: 为何不使用下划线和驼峰大小写? 连字符是现在最流行的网址分隔符，并且 markdown 文件在上下文中经常使用:

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

-   通常不是必须的usually not necessary if you 使用 `wrap:inner-sentence` or `wrap:sentence`

-   `space-sentence:2` gives a false sense of readability
    as it is ignored on the HTML output

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

尝试将一行限制在 80 个字符以下，将长段落按照一定的逻辑分开，例如:

-   句子: after a period `.`, question `?` or exclamation mark `!`

-   [clauses](http://www.oxforddictionaries.com/words/cla使用s):
    after words like `and`, `which`, `if ... then`, commas `,`

-   large [phrases](http://www.oxforddictionaries.com/words/phrases)

一行中超过80个字符是可以接受的，但是记住长句子不适合阅读，并且在 `git diff` 中会很难看。

设置你的编辑器对 Markdown 文件一行不要超过80字符以免忘记。

建议使用:

    This is a very very very very very very very very very very very very very long not wrapped sentence.
    Second sentence of of the paragraph,
    third sentence of a paragraph
    and the fourth one.

解释:

-   Diffs 工具看起来更好, 因为一个子句的修改在 diff 工具中显示为一行修改.

-   Occasional visual wrapping does not significantly reduce the readability of Markdown,
    since the only language feature that can be indented to indicate hierarchy are nested lists.

-   现在除了 GitHub 在 README 和评论中将单独一行解释成回车。
    没有其他主流的解释引擎这么做，使用换行是非常安全的。

-   一些工具对很长的一行不友好，比如 Vim 并且 `git diff` 默认并不换行.
    这些不友好可以通过配置除去，对于git，使用 `git config --global core.pager 'less -r'` 对于Vim可以使用 `set wrap` 来自动换行.

缺点:

-   需要在写作时增加顾虑，尤其是在修改代码的时候。

-   Markdown 看起来和渲染输出不同, 输出没有换行符。

    手动的换行可以让 Markdown 比生成的文档更加易读，
    which is bad beca使用 it gives a false sense of readability encouraging less readable long paragraphs.

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

-   其他和电脑相关的术语，但是想要单独标明

不要标记为代码：

-   项目名。 比如： GCC
-   函数库名。比如： libc, glibc

#### 拼写和语法 {#spelling-and-grammar}

使用正确的拼写和语法。

尽量选用英语，更准确的说美式英语。
解释: 美式英语使用者占有最大的GDP，尤其是在计算机行业。

使用p like URL or code on words which you do not want to add to your dictionary
so that spell checkers can ignore them automatically.

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

-   *避免* 在相同 markdown 文件中使用相同的标题.

    解释: 许多的 markdown 解释器会依据标题的内容生成标题的IDs。

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

If you target HTML output, write your documents so that it will have one
and only one `h1` element as the first thing in it that serves as the title of the document.
This is the HTML top-level header.

How this `h1` is produced may vary depending on your exact technology stack:
some stacks may generate it from metadata, for example Jekyll through the front-matter.

Storing the top-level header as metadata has the advantage that it can be reused elsewhere more easily,
e.g. on a global index, but the downside lower portability portable.

If your target stack does not generate the top-level header in another way,
include it in your markdown file. E.g., GitHub.

Top-level headers on index-like files such as `README.md` or `index.md`
should serve as a title for their parent directory.

Downsides of top-level headers:

-   take up one header level. This means that there are only 5 header levels left,
    and each new header will have one extra `#`, which looks worse and is harder to write.

-   duplicate filename information, which most often can already be seen on a URL.
    In most cases, the filename can be trivially converted to a top-level,
    e.g.: `some-filename.md` to `Some filename`.

Advantages of top-level headers:

- more readable than URL's, especially for non-technically inclined 使用rs.

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

    例外, [title case](http://en.wikipedia.org/wiki/Title_case#Title_case)
    may be optionally 使用d for the [top-level header](#top-level-header).
    使用 this exception sparingly, in cases where typographical perfection is important,
    e.g.: `README` of a project.

    解释: why not [Title case](http://en.wikipedia.org/wiki/Title_case#Title_case) for all headers?
    It requires too much effort to decide if edge-case words should be upper case or not.

#### 标题结尾 {#end-of-a-header}

Indicate the end of a header's content that is not followed by a new header by an horizontal rule:

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

To do so, simply create a synonym header with empty content just before its main header.

比如：

    # Purchase

    # Buy

    You give money and get something in return.

Every empty header with the same level as the following one is assumed to be a synonym.
This is not the case if levels are different:

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

-   *不要* 在单独的引用中使用空行.

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

- asterisk `*` can be conf使用d with bold or italic markers.
- plus sign `+` is not popular.

##### 有序 {#ordered}

尽量选用 `1.` 来标记有序的列表, unless you intend to refer to items by their number in the same markdown file or externally.

Prefer unordered lists unless you intent to refer to items by their number.

Best, we will never refer to the items of this list by their number:

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

Acceptable, meant to be referred by number from outside of the markdown file:

    Terms of 使用.

    1. I will not do anything illegal.
    2. I will not do anything that can harm the website.

解释:

-   If you want to change a list item in the middle of the list,
    you 不要 have to modify all items that follow it.

    Diffs will show only the significant line which was modified.

-   Content stays aligned without extra effort if the numbers reach 2 digits. 比如： the following is not aligned:

        9. a
        10. b

-   References break when a new list item is added. To reduce this problem:

    - keep references close to the list so authors are less likely to forget to update them
    - when referring from an external document, always refer to an specific version of the markdown file

#### 列表项中的空格 {#spaces-after-list-marker}

##### 可选 list-space:mixed {#option-list-space-mixed}

-   If the content of every item of the list is fits in a single paragraph, 使用 **1** space.

-   Otherwise, for every item of the list:

    -   使用 **3** spaces for unordered lists.

    -   使用 **2** spaces for ordered lists.
        One less than for unordered beca使用 the marker is 2 chars long.

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

The advantages of `list-space:1` are that

-   it removes the decision of how many spaces you should put after the list marker:
    it is always one.

    We could choose to always have list content indented as:

        -   a
        -   b

    but that is ugly.

-   You never need to change the indentation of the entire list beca使用 of a new item.

    This may happen in `list-space:mixed` if you have:

        - a
        - b

    and will add a multi-line item:

        -   a

        -   b

        -   c

            d

    Note how `a` and `b` were changed beca使用 of `c`.

The disadvantages of `list-space:1`

-   creates three indentation levels for the language:

    - 4 for indented code blocks
    - 3 for ordered lists
    - 2 for unordered lists

    That means that you cannot easily configure your editor indent level to deal with all cases
    when you want to change the indentation level of multiple list item lines.

-   Is not implemented consistently across editors.

    In particular what should happen at:

        - a

                code

    This (2 spaces):

        <pre><code>  code

    Or no spaces:

        <pre><code>code

    Likely the original markdown said no spaces:

    > To put a code block within a list item, the code block
    > needs to be indented twice — 8 spaces or two tabs

    But many implementations did otherwise.

    CommonMark [adds the 2 spaces](http://spec.commonmark.org/0.12/#example-176).

#### 列表内容的缩进 {#indentation-of-content-inside-lists}

The indentation level of what comes inside list and of further list items
必须 be the same as the first list item.

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

Good (if it matches your spaces after list marker style):

    -   item 1

        Content 1

    -   item 2

        Content 2

不建议：

    - item 1

        Content 1

    - item 2

        Content 2

Good (if it matches your spaces after list marker style):

    - item 1

      Content 1

    - item 2

      Content 2

避免 开始ing a list item directly with indented code blocks beca使用 that is not consistently implemented.
[CommonMark states that](http://spec.commonmark.org/0.12/#example-176) a single space is assumed in that case:

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

Note: nothing forbids one list item from ending in period while another in the same list does not.

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

*避免* the definition list extension since it is not present
in many implementations nor in CommonMark.

Instead, 使用 either:

-   formated lists:

    - format the item be defined as either of bold, link or code
    - separate the item from the definition with a colon and a space `:.`
    - 不要 align definitions as it is harder to maintain and does not show on the HTML output

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

    不建议, no colon:

        - **apple** red fruit
        - **dog** noisy animal

    不建议, space between term and colon:

        - **apple** : red fruit
        - **dog** : noisy animal

    不建议, definitions aligned:

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

Prefer to end the phrase before a code block with a colon `:`.

建议使用:

    使用 this code to blow up your PC:

        sudo rm -rf /

不建议, no colon

    使用 this code to blow up your PC

        sudo rm -rf /

### 水平横线 {#horizontal-rules}

*不要* 使用 horizontal rules except to indicate the [End of a header](#end-of-a-header).

解释:

-   headers are better section separators since they say what a section is about.

-   horizontal rules 不要 have a generally accepted semantic meaning.
    This guide gives them one.

使用 3 hyphens without spaces:

    ---

### 表格 {#tables}

Extension.

-   Surround tables by one empty line.

-   不要 indent tables.

-   Surround every line of the table by pipes.

-   Align all border pipes vertically.

-   Separate header from body by hyphens except at the aligned pipes `|`.

-   Pipes `|` 必须 be surrounded by a space, except for outer pipes
    which only get one space internally, and pipes of the hyphen separator line.

-   Column width is determined by the longest cell in the column.

Good table:

    Before.

    | h    | Long header |
    |------|-------------|
    | abc  | def         |
    | abc2 | def2        |

    After.

解释:

-   unaligned tables tables are easier to write, but aligned tables are more readable,
    and people read code much more often than they edit it.

-   preceding pipes make it easier to determine where a table 开始s and ends.
    Trailing pipes make it look better beca使用 of symmetry.

-   there exist tools which help keeping the table aligned.
    For example, Vim has the [Tabular plugin](https://github.com/godlygeek/tabular)
    which allows to align the entire table with `:Tabular /|`.

-   why no spaces around pipes of the hyphen separator line, i.e.: `|---|` instead of `| - |`?
    No spaces looks better, works on GitHub. Downside: harder to implement automatic alignment in editors,
    as it requires a special rule for the separator line.

### 分离相连的列表 {#separate-consecutive-elements}

Separate consecutive:

- lists
- indented code blocks
- blockquotes
- list followed by external code block

with an empty HTML comment `<!-- -->`.

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

    使用 the hyphen marker followed by one space `- a`  for unordered lists.

解释: most browsers 不要 render the surrounding spaces nor add them to the clipboard on copy.

### 链接 {#links}

#### 参考样式链接 {#reference-style-links}

链接:

-   使用 the trailing `[]` on implicit links.

    建议使用:

        [a][]

    不建议：

        [a]

    解释: while omitting `[]` works on most major implementations,
    it is not specified in the documentation not implemented in the original markdown.

Definitions:

- 必须写到文件末
- 必须以ID字符顺序排列
- 不要使用尖括号包裹URL
- align URLs and link names as in a table
- 链接 IDs 仅仅使用小写字母. 解释: 因为 IDs 区分大小写,
- 只用小写容易书写，并且可读性比大小写混合单词大很多。

建议使用:

    [id2]     http://long-url.com
    [long id] http://a.com        "name 1"

不建议, not ordered by id:

    [b] http://a.com
    [a] http://b.com

不建议, not aligned:

    [id] http://id.com
    [long id] http://long-id.com

#### 单引号或双引号标题 {#single-or-double-quote-titles}

使用双引号，*不要* 使用单引号。

解释: single quotes do not work in all major implementations, double quotes do.

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

*不要* 使用强调元素(加粗或者斜体) to introduce a multi line named section: 使用 headers instead.

解释: that is exactly the semantic meaning of headers,
and not necessarily that of emphasis elements. As a consequence,
many implementations add 使用ful behaviors to headers and not to emphasis elements,
such as automatic `id` to make it easier to refer to the header later on.

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
What if you want a relative link to a file called `script`?

#### 电子邮件自动链接 {#email-automatic-links}

*不要* 使用电子邮件自动链接 `<address@example.com>`. 使用纯HTML .

解释: 标准 markdown 设计规范这样描述:

> "performs a bit of randomized decimal and hex entity-encoding
> to help obscure your address from address-harvesting spambots".

因此, 输出是随机的，丑陋的, and as the spec itself mentions:

> but an address published in this way will probably eventually 开始 receiving spam

