# Language

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
