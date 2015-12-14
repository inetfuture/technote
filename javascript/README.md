# References

- *JavaScript: The Good Parts* **[MUST READ]** :bangbang:
- [Learning JavaScript Design Patterns](http://addyosmani.com/resources/essentialjsdesignpatterns/book/) **[MUST READ]** :bangbang:
- [JavaScript Patterns 中译本](https://github.com/TooBug/javascript.patterns)
- *Async JavaScript: Build More Responsive Apps With Less Code*
- https://github.com/sorrycc/awesome-javascript
- http://jsbooks.revolunet.com/
- [Full Stack Javascript](./full_stack_javascript.md)

# Style Code

https://github.com/airbnb/javascript

# Type

## typeof

Returns a string indicating the type of the unevaluated operand.

```js
typeof operand
```

| Type | Result |
| ---- | ------ |
| Undefined | "undefined" |
| Null | "object" |
| Boolean | "boolean" |
| Number | "number" |
| String | "string" |
| Host object (provided by the JS environment) | Implementation-dependent |
| Function object (implements [[Call]] in ECMA-262 terms) | "function" |
| E4X XML object | "xml" |
| E4X XMLList object | "xml" |
| Any other object | "object" |

```js
typeof null === 'object';
typeof [] === 'object';

typeof /s/ === 'function'; // Chrome 1-12 ... // Non-conform to ECMAScript 5.1
typeof /s/ === 'object'; // Firefox 5+ ...    // Conform to ECMAScript 5.1
```

## instanceof

Tests presence of constructor.prototype in object prototype chain.

```js
object instanceof constructor
```

```js
function C(){} // defining a constructor
function D(){} // defining another constructor

var o = new C();
o instanceof C; // true, because: Object.getPrototypeOf(o) === C.prototype
o instanceof D; // false, because D.prototype is nowhere in o's prototype chain
o instanceof Object; // true, because:
C.prototype instanceof Object // true

C.prototype = {};
var o2 = new C();
o2 instanceof C; // true
o instanceof C; // false, because C.prototype is nowhere in o's prototype chain anymore

D.prototype = new C(); // use inheritance
var o3 = new D();
o3 instanceof D; // true
o3 instanceof C; // true
```

```js
var a = 'woot';
var b = new String(‘woot’);
a + b; // 'woot woot'

typeof a; // ‘string’
typeof b; // ‘object’

a instanceof String; // false
b instanceof String; // true
```

# Closure

code + scope
