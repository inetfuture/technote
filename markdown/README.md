# Markdown 书写规范

请通过[原文](https://raw.githubusercontent.com/inetfuture/technote/master/markdown/README.md)模式阅读此文档，以直观理解空格、换行、缩进等要求。

未系统学习过 Markdown 的先仔细阅读以下资料：

- [原始定义](https://daringfireball.net/projects/markdown/)
- [GitHub 的教程](https://guides.github.com/features/mastering-markdown/)

## 语义

格式使用应遵守语义：

- 不要滥用强调格式，满篇强调更找不到重点。
- 不要滥用行内代码格式，只有代码才能（也应该）使用行内代码格式，不要将其作为高亮强调格式。代码包括语句、标识符（类名、方法名、变量名等）、变量值、命令、路径等，术语、专有名词（比如 HTTP）不算。
- 不要滥用引用格式，不要将其作为高亮强调格式。

## 标题

- 应有且只有一个一级标题作为文件标题。
- 标题级别要按序，比如不要没有二级标题直接跳到三级标题。
- 尽量不要使用四级以上的标题，过深的层次意味着结构需要重新组织。
- 前后要空行，但文件标题前面不用空。
- 不要在标题中使用强调、行内代码等格式。
- 整个标题可以是一个链接。

## 段落

前后要空行，尤其连续多个段落时，否则多数渲染器渲染出来会是一段。

```markdown
# 标题一

段落一

## 标题二

段落二

段落三

段落四
```

## 强调

使用 `*` 而不是 `_`，因为 `_` 容易与变量名冲突。

## 链接

尽量用 `[标题](链接)` 的写法，避免直接用一长串裸链接，因为看起来会比较乱。链接标题尽量同其内容标题，上下文清楚时也可以用`这里`指代，比如`详情参考[这里](https://github.com/inetfuture/technote/tree/master/markdown)`。

## 列表

- 前缀、缩进和空行：

    ```markdown
    - 项目一，前缀使用 - 而不是 *；列表开始，前面空一行；结尾用冒号或句号。

        项目详细描述，作为项目子元素应该缩进4个空格，否则渲染出来的 HTML 会与列表平级而不是列表项子元素；作为一个段落应该前后各空一行。

        项目详细描述，作为项目子元素应该缩进4个空格，否则渲染出来的 HTML 会与列表平级而不是列表项子元素；作为一个段落应该前后各空一行。

    - 项目二，前缀使用 - 而不是 *；结尾用冒号或句号。
        - 嵌套项目，作为项目子元素应该缩进4个空格，否则渲染出来的 HTML 会与列表平级而不是列表项子元素，前后不需要空行。
        - 嵌套项目，作为项目子元素应该缩进4个空格，否则渲染出来的 HTML 会与列表平级而不是列表项子元素，前后不需要空行。
    - 项目三，前缀使用 - 而不是 *；这种前面不空行；结尾用冒号或句号。
        - 嵌套项目，作为项目子元素应该缩进4个空格，否则渲染出来的 HTML 会与列表平级而不是列表项子元素，前后不需要空行。
        - 嵌套项目，作为项目子元素应该缩进4个空格，否则渲染出来的 HTML 会与列表平级而不是列表项子元素，前后不需要空行。
        - 列表结束，后面空一行。
    ```

- 鼓励多使用列表，可以将事情描述的更清晰，但是：
    - 只有一条不要用。
    - 不要滥用，列表项目逻辑上必须是并列或递进关系，不要把不相关的东西硬塞到一起。
- 不要使用有序列表，不容易维护，默认书写的顺序就是先后顺序即可，除非需要通过序号引用列表项目。非要用有序列表时，可全部写 `1`，渲染出来会自动变成递增的。

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
        // 作为项目子元素应该缩进4个空格，否则渲染出来的 HTML 会与列表平级而不是列表项子元素；作为代码块应该前后各空一行；代码与 backtick 对齐，不要再缩进。
        var t = new Date();
        '''

    - 项目二
        - 子项目

            '''js
            var t = new Date();
            '''

        - 子项目
    ```

- 使用正确的语言标记，代码块内代码要合法。没有适用的语言标记时用 `text`，不能留空。
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

## 中文排版

- [空格](https://github.com/mzlogin/chinese-copywriting-guidelines#%E7%A9%BA%E6%A0%BC)：
    - 中英文之间需要增加空格。
    - 中文与数字之间需要增加空格。
    - 数字与单位之间无需增加空格。
    - 全角标点与其他字符之间不加空格。例外：裸链接后面需空格，不能紧跟标点，否则有些渲染器会把标点当成链接的一部分。
    - 中文与链接、强调、行内代码等格式间是否加空格取决于内容（即以上规则），比如`书写 *Markdown* 的规范`需要加，而`书写*中文*的规范`不需要加。

    示例：

    ```markdown
    大家好，我是 Aaron Wang，生于 1989 年，身高 173cm，*GitHub* 链接 https://github.com/inetfuture 。
    ```

- [全角与半角](https://github.com/mzlogin/chinese-copywriting-guidelines#%E5%85%A8%E8%A7%92%E5%92%8C%E5%8D%8A%E8%A7%92)：
    - 主体是中文的时候（夹杂少量英文单词、术语、短句），应全部使用全角中文标点，不要随意混杂半角标点。

        ```markdown
        // 错误的
        中文夹杂 English words, 标点不要乱.

        // 正确的
        中文夹杂 English words，标点不要乱。
        ```

    - 遇到完整的英文整句（引用）、特殊名词等时，其內容才可酌情使用半角标点。
    - 数字使用半角字符。
- 标点：
    - [中文列举间隔使用顿号（`、`）而不是逗号（`，`）](https://zhuanlan.zhihu.com/p/83934100)。
    - 列表项目结尾是在引出详细描述时，用冒号结束，比如：

        ```markdown
        - 使用示例：

            '''shell
            whatever xxx
            '''
        ```

    - 句末加句号，特别短的（不是完整句子）可以例外，但是注意保持一致。

## 其它

- 表示带变量的字符串时，使用 `${var}` 的形式（同 Shell）：

    ```markdown
    username 规则：`${firstName}.${lastName}`
    ```

    有惯例的除外，比如表示 RESTful API 的 path 参数可遵循 Swagger 的风格：`/articles/{articleId}`。

- 表示命令行选项（option）、参数（arg）时，参考各种 manual 里的惯例写法，可选的放在 `[]` 中，必需的放在 `<>` 中：

    ```markdown
    whatever [--option1=<value>] <arg1> [arg2]
    ```

- 描述菜单、目录导航使用 `【xxx】>【xxx】` 的写法。
- 英语专有名词大小写、符号等遵循官方的写法，比如 macOS、Microsoft、GitLab、PostgreSQL、MongoDB、InfluxDB、Elasticsearch、Node.js、gRPC、Vue.js、React、HTML、MaiSCRM 等。
- 英语标题除介词、连词等外应首字母大写，可参考 [Capitalize My Title](https://capitalizemytitle.com/) 的结果。

## 编辑器

VS Code 可使用 [markdownlint extension](https://github.com/DavidAnson/vscode-markdownlint) 加 [.markdownlint.json](.markdownlint.json) 实现自动 lint。

尽量不要依赖实时预览工具，Markdown 语法没多少东西，习惯之后，在脑子里预览就够了。
