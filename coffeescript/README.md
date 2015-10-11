# References

- [The Little Book on CoffeeScript](https://arcturo.github.io/library/coffeescript/) **[MUST READ]** :bangbang:

# Style Guide

Rules below are additions to https://github.com/polarmobile/coffeescript-style-guide .

- Use these idioms whenever possible http://arcturo.github.io/library/coffeescript/04_idioms.html
- Limit all lines to a maximum of **120** characters
- Put `'use strict'` statement at the top of the file, see http://arcturo.github.io/library/coffeescript/07_the_bad_parts.html for why
- **Has to pass coffeelint**
- Others:

    ```coffee
    # Prefer CoffeeScript corresponding idioms, over js native forEach/map/filter/reduce, over shims of lodash/angular
    for file in fs.readdirSync controllersDir
      doSomthingWith file

    # For utilities, prefer lodash over angular
    dest = { key1: 'value1' }
    src = { key2: 'value2' }
    _.assign dest, src

    # Use explicit braces for single line object construction
    obj = { project: 'tuisongbao' }

    # Use implicit parentheses/braces for multiple line object construction and function calls
    obj =
      project: 'tuisongbao'
      domain: 'tuisongbao.com'

    promise.then (result) ->
      $scope.value = result

    # For object construction, prefer Object Literal Syntax,
    # unless it's not possible to use, for example, you need use variable in key, or assign key conditionally
    query =
      'count.total':
        '$lte': 0
    query[varName] = 'test'

    # Always use explicit parentheses when instantiating classes
    obj = new MyClass(parameter)

    # In cases where method calls are being chained and the code does not fit on a single line,
    # each call should be placed on a separate line and align with first line, with a leading .
    # And parentheses should be omitted when it improve readability(this is new syntax in CoffeeScript 1.7)
    [1..3]
    .map (x) -> x * x
    .concat [10..12]
    .filter (x) -> x < 11
    .reduce (x, y) -> x + y

    # Promise chains
    promiseProducer.run 'param1', 'param2'
    .then (result) ->
      result * 2
    .then (doubledResult) ->
      console.log doubledResult
    .catch (err) ->
      console.error err

    # Use postfix form of if/unless to improve readability
    return next err if err

    # Call a function with signature: (option1, option2, callback)
    doSomething
      flag1: true
      flag2: false
    ,
      flag3: true
      flag4: false
    , (err, result) ->
      return console.error if err
      console.log result

    # Don't leave empty functions, if you have to, write it like below:
    necessaryEmptyFunction = -> undefined
    ```
