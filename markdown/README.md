# Markdown 书写规范

请通过[原文](https://raw.githubusercontent.com/inetfuture/technote/master/markdown/README.md)模式阅读此文档。

对 Markdown 不熟悉的请先阅读：

- [原始定义](https://daringfireball.net/projects/markdown/)。
- [GitHub 的教程](https://guides.github.com/features/mastering-markdown/)。
- [CommonMark 规范](https://spec.commonmark.org/0.28/)。

## 中文排版

- [空格](https://github.com/mzlogin/chinese-copywriting-guidelines#%E7%A9%BA%E6%A0%BC)：
    - 中英文之间需要增加空格。
    - 中文与数字之间需要增加空格。
    - 数字与单位之间无需增加空格。
    - 全角标点与其他字符之间不加空格。例外：裸链接后面需空格，不能紧跟标点，否则标点会被当成链接的一部分。
    - 中文与链接、强调、行内代码等格式间是否加空格取决于内容，比如`书写 *Markdown* 的规范`需要加，而`书写*中文*的规范`不需要加。
- [全角与半角](https://github.com/mzlogin/chinese-copywriting-guidelines#%E5%85%A8%E8%A7%92%E5%92%8C%E5%8D%8A%E8%A7%92)：
    - 主体是中文的时候（夹杂少量英文单词、术语、短句），应全部使用全角中文标点，不要随意混杂半角标点。

        ```markdown
        // 错误的
        中文夹杂 English words, 标点不要乱。

        // 正确的
        中文夹杂 English words，标点不要乱。
        ```

    - 遇到完整的英文整句、特殊名词，其內容才可使用半角标点。
    - 数字使用半角字符。
- 标点：
    - 中文列举使用顿号“、”而不是逗号。
    - 句末加句号。

## 语义

格式使用应遵守语义：

- 不要滥用强调格式，满篇强调更找不到重点。
- 不要滥用行内代码格式，只有代码、变量名或变量值才能使用行内代码，不要将其作为高亮格式。
- 不要滥用引用格式，不要将其作为高亮格式。

## 标题

- 应有且只有一个一级标题作为文件标题。
- 标题级别要按序。
- 尽量不要使用四级以上的标题。
- 前后要空行。
- 不要使用强调、行内代码等格式。

## 段落

前后要空行。

```markdown
# 标题一

段落一

## 标题二

段落二

段落三
```

## 强调

使用 `*` 而不是 `_`，因为 `_` 可能与变量名冲突。

## 链接

尽量用 `[标题](链接)` 的写法，避免直接用一长串原始链接，因为看起来会比较乱。链接标题尽量同实际标题，或者也可以用`这里`指代。

## 列表

- 前缀、缩进和空行：

    ```markdown
    - 项目一，前缀建议使用 - 而不是 *

        项目详细描述，作为项目子元素应该缩进4个空格，否则 render 出来的 HTML 会与列表平级而不是列表项子元素；作为一个段落应该前后各空一行。

        项目详细描述，作为项目子元素应该缩进4个空格，否则 render 出来的 HTML 会与列表平级而不是列表项子元素；作为一个段落应该前后各空一行。

    - 项目二，前缀建议使用 - 而不是 *
        - 嵌套项目，作为项目子元素应该缩进4个空格，否则 render 出来的 HTML 会与列表平级而不是列表项子元素，前后不需要空行。
        - 嵌套项目，作为项目子元素应该缩进4个空格，否则 render 出来的 HTML 会与列表平级而不是列表项子元素，前后不需要空行。
    ```

- 鼓励多使用列表，可以将事情描述的更清晰。
- 尽量不要使用有序列表，不容易维护，除非需要通过序号引用列表条目。

## 围栏代码块（Fenced Code Block）

- 前后要空行。
- 使用三个连续的 *backtick* （键盘左上角 Esc 下面那个波浪符键）作为分隔符号（下面用三个单引号代替表示）：

    ```markdown

    '''js
    // 注意整个 block 前后空行
    var t = new Date();
    '''

    ```

    ```markdown
    - 项目一

        '''js
        // 作为项目子元素应该缩进4个空格，否则 render 出来的 HTML 会与列表平级而不是列表项子元素；作为代码块应该前后各空一行。
        var t = new Date();
        '''

    - 项目二
        - 子项目

            '''js
            var t = new Date();
            '''

        - 子项目
    ```

- 使用正确的语言标记，代码块内代码要合法。
- 描述多个连续的 Shell 命令应使用下面的形式，注意命令前面不要带 `$` 等提示符，可以方便复制粘贴：

    ```markdown
    '''shell
    # 说明1
    cd path

    # 说明2
    python script.py

    # 说明3
    apt-get install package
    '''
    ```

## 其它

- 表示带变量的字符串时，使用 `${var}` 的形式（同 Shell）：

    ```markdown
    username 规则：`${firstName}.${lastName}`
    ```

- 表示命令行选项（option）、参数（arg）时，参考各种 manual 里的惯例写法，可选的放在 `[]` 中，必需的放在 `<>` 中。
- 菜单、目录导航使用 `【xxx】>【xxx】` 的写法。

## 编辑器

VS Code 可使用 [markdownlint extension](https://github.com/DavidAnson/vscode-markdownlint) 加 [.markdownlint.json](.markdownlint.json) 实现自动 lint。

尽量不要依赖实时预览工具，Markdown 语法没多少东西，习惯之后，在脑子里预览就够了。
