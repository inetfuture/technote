# Characters

- CR: carriage return, ^M, ASCII code 13
- LF: line feed, ^J, ASCII code 10

# Unicode

- utf-8 is byte order irrelevant and can be auto-detected by its contents, the method is simple: try to read the file (or a string) as UTF-8 and if that succeeds, assume that the data is UTF-8. Otherwise assume that it is CP1252 (or some other 8 bit encoding). Any non-UTF-8 eight bit encoding will almost certainly contain sequences that are not permitted by UTF-8.
