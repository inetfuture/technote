# Languages
# References

- http://deerchao.net/tutorials/regex/regex.htm
- http://www.rexegg.com/

## Python

```python
import re

re.findall(r'^(regexp)$', 'hi\nregexp\nhi', re.MULTILINE)

> ['regexp']
```

```python
import re

r = re.compile(r'regexp')
r.match/findall
```

- match: apply the pattern at the start of the string

## JavaScript

```javascript
'hi\nregexp\nhi'.match(/^regexp$/m);
> [ 'regexp', index: 3, input: 'hi\nregexp\nhi' ]

'aaa'.match(/a/g);
> [ 'a', 'a', 'a' ]

'aaa'.match(/a/);
> [ 'a', index: 0, input: 'aaa' ]

'abc'.match(/(a)(b)(c)/);
> [ 'abc', 'a', 'b', 'c', index: 0, input: 'abc' ]

'abc'.search(/b/);
> 1

'1, 2,  3'.split(/\s*,\s*/);
> [ '1', '2', '3' ]

'"abcd"'.replace(/"([^"]*)"/, '“$1”');
> '“abcd”'
```

```javascript
/^regexp$/m.test('hi\nregexp\nhi');
> true
```

