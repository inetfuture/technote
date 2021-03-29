# References

- https://docs.python-guide.org/
- *Byte of Python*
- *Python for Unix and Linux System Adminstration*
- https://github.com/vinta/awesome-python

# Style Guide

- https://www.python.org/dev/peps/pep-0008/
- https://www.python.org/dev/peps/pep-0257/
- https://sphinx-rtd-tutorial.readthedocs.io/en/latest/docstrings.html

补充：

- 每行最大长度限制为 120 个字符。
- 尽量使用单引号，例外：
    - 字符串本身含单引号，为了避免转义可使用双引号。
    - docstring 始终使用三个双引号。
- 私有成员要加下划线前缀，private 和 protected 均加一个。
- 尽量只 `import` module 或 class，避免频繁 `import` function（写起来太费劲），按需使用 `from`。
- 字符串拼接尽量使用 [f-strings 语法](https://docs.python.org/3/tutorial/inputoutput.html#formatted-string-literals)。
