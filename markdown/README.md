# 基本书写规范

- 中英文之间要空格，如：`规范得书写 makrdown 很重要` 。
- 正确使用标点，中文文档应始终使用中文标点，不要混杂英文标点。

# 格式要求

以下是对 http://wowubuntu.com/markdown/basic.html 的补充：

- 标题：

    尽量不要使用四级以上的标题，前后要空行。

- 段落：

    前后要空行。

    ```markdown
    # 标题一

    段落一

    # 标题二

    段落二
    ```

- 行内代码，倾斜和加粗：

    前后应加空格，如：`普通文字， **加粗文字** 普通文字`

- 列表：

    ```markdown
    - 项目一

        项目详细描述，缩进4个空格；作为一个段落应该前后各空一行

        项目详细描述，缩进4个空格；作为一个段落应该前后各空一行

    - 项目二
        - 嵌套项目应缩进4个空格，前后不需要空行
        - 嵌套项目应缩进4个空格，前后不需要空行
    ```

    鼓励多使用列表，可以将事务描述的更清晰。

    尽量不要使用有序列表，因为不容易维护，除非下文要通过序号引用列表条目。

- 围栏代码块（Fenced Code Block）：

    前后要空行。

    使用三个连续的 *backtick* （键盘左上角Esc下面那个波浪符键）作为分隔符号（下面用三个单引号代替表示）：

    ```markdown
    '''js
    // 注意整个 block 前后空行
    var t = new Date();
    '''
    ```

    ```markdown
    - 项目一

        '''js
        // 注意整个 block 需要缩进 4 个空格，前后空行
        var t = new Date();
        '''

    - 项目二
        - 子项目

            '''js
            var t = new Date();
            '''

        - 子项目
    ```

    请正确的语言标记，代码块内代码要合法。

- 描述多个连续的 shell 命令应使用下面的形式：

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

    注意命令前面不要带 `$`、`#` 等 shell 提示符，可以方便复制粘贴。

# 编辑器

- Sublime Text + [knockdown plugin](https://github.com/aziz/knockdown)
- vscode + [markdownlint extension](https://github.com/DavidAnson/vscode-markdownlint)
