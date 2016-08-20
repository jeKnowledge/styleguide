# Javascrip Style Guide

Guide for programming Javascript.
We use [AirBnB Js Style Guide](https://github.com/airbnb/javascript) with special attention to:

#### Variables

  - Avoid `var` by using `const` if you don't need to change a variable.

    ```javascript
    const a = 3;
    const b = 10;
    ```

  - Avoid `var` by using `let` if you need to change a variable.

    ```javascript
    let a = 3;
    let b = 10;
    b += 1;
    a = b
    ```

  - Group all your `const`s before all your `let`s

    ```javascript
    const foo = getSomeValue();
    const bar = getSomeDifferentValue();
    let len;
    let i = 0;
    ```

#### Arrays

  - Use the literal syntax for array creation
    ```javascript
    let someArray = [];
    ```

  - Use Array.push() to add items to an array
    ```javascript
    let someArray.push('item');
    ```

  - To copy arrays, use array spreads '...'
    ```javascript
    let someArrayCopy = [...someArray];
    ```

#### Objects

  - Use the literal syntax for object creation
    ```javascript
    let someObject = {};
    ```

  - Group your shorthand properties at the beginning of your object declaration.
    ```javascript
    const jonSnow = 'Jon Snow'
    const daenerysTargaryen = 'Daenerys Targaryen'

    let someObject = {
      jonSnow,
      daenerysTargaryen,
      theWall: 1,
      nightsWatch: 2,
      stark = 4,
      drakes = 3,
      targaryen = 4
    }
    ```

#### Strings

  - Use single quotes `''` for strings.

    ```javascript
    const name = 'Aerys Targaryen';
    ```

  - When programmatically building up strings, use template strings instead of concatenation.

    ```javascript
    function sayHi(name) {
      return `You know nothing, ${name}?`;
    }
    ```

  - Never use `eval()` on a string, it opens too many vulnerabilities.

#### Functions

  - Use function declarations instead of function expressions.

    ```javascript
    function foo() {
    }
    ```

  - Never name a parameter `arguments`. This will take precedence over the `arguments` object that is given to every function scope.

    ```javascript
    function lightSide(name, options, args) {
    }
    ```

  - Always put default parameters last.

    ```javascript
    function doStuffAndThings(name, opts = {}) {
    }
    ```

#### Arrow Functions

  - When you must use function expressions (as when passing an anonymous function), use arrow function notation.

    ```javascript
    [1, 2, 3].map((x) => {
      const y = x + 1;
      return x * y;
    });
    ```

  - If the function body consists of a single expression, omit the braces and use the implicit return. Otherwise, keep the braces and use a `return` statement.

    ```javascript
    [1, 2, 3].map(number => `A string containing the ${number}.`);
    ```

  - If your function takes a single argument and doesn’t use braces, omit the parentheses. Otherwise, always include parentheses around arguments.

    ```javascript
    [1, 2, 3].map(x => x * x);

    [1, 2, 3].map((x) => {
      const y = x + 1;
      return x * y;
    });
    ```

#### Classes

  - Use `extends` for inheritance.

    ```javascript
    class PeekableQueue extends Queue {
      peek() {
        return this._queue[0];
      }
    }
    ```

  - It's okay to write a custom toString() method, just make sure it works successfully and causes no side effects.

    ```javascript
    class Stark {
      constructor(options = {}) {
        this.name = options.name || 'no name';
      }

      getName() {
        return this.name;
      }

      toString() {
        return `You know nothing, ${this.getName()}`;
      }
    }
    ```

#### Whitespace

  - Use soft tabs set to 2 spaces.

    ```javascript
    function baz() {
    }
    ```

  - Place 1 space before the leading brace.

    ```javascript
    function test() {
      console.log('test');
    }
    ```

  - Place 1 space before the opening parenthesis in control statements (`if`, `while` etc.). Place no space between the argument list and the function name in function calls and declarations.

    ```javascript
    if (isJedi) {
      fight();
    }

    function darkSide() {
      console.log('Joing the dark side');
    }
    ```

  - Set off operators with spaces.

    ```javascript
    const x = y + 5;
    ```

  - Use indentation when making long method chains (more than 2 method chains).

    ```javascript
    $('#items')
      .find('.selected')
        .highlight()
        .end()
      .find('.open')
        .updateCount();
    ```

  - Leave a blank line after blocks and before the next statement.

    ```javascript
    if (foo) {
      return bar;
    }

    return baz;
    ```

  - Do not add spaces inside parentheses.

    ```javascript
    function bar(foo) {
      return foo;
    }
    ```

  - Do not add spaces inside brackets.

    ```javascript
    const foo = [1, 2, 3];
    console.log(foo[0]);
    ```

  - Add spaces inside curly braces.

    ```javascript
    const foo = { luke: 'Skywalker' };
    ```

  - Avoid having lines of code that are longer than 100 characters

    ```javascript
    const foo = 'Luke, you can destroy the Emperor. He has foreseen this. It is your destiny. ' +
      'Join me, and together we can rule the galaxy as father and son.!';
    ```

