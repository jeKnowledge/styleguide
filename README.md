# jeKnowledge styleguides

## Table of Contents

  1. Javascript
    1. [Variables](#variables)
    2. [Arrays](#arrays)
    3. [Objects](#objects)
    4. [Strings](#strings)
    5. [Functions](#functions)
    6. [Arrow Functions](#arrow-functions)
    7. [Classes](#classes)
    8. [Whitespace](#whitespace)

## Variables

  <a name"variables--prefer-const"></a><a name="1.1"></a>
  - [1.1](#variables--prefer-const) Avoid  `var` by using `const` if you don't need to change a variable.

    ```javascript
    //bad
    var a = 3;
    var b = 10;

    //good
    const a = 3;
    const b = 10;
    ```

  <a name"variables--prefer-let"></a><a name="1.2"></a>
  - [1.2](#variables--prefer-let) Avoid `var` by using `let` if you need to change a variable.

    ```javascript
    //bad
    var a = 3;
    var b = 10;
    b += 1;
    a = b;

    //good
    let a = 3;
    let b = 10;
    b += 1;
    a = b
    ```

  <a name"variables--grouping"></a><a name="1.3"></a>
  - [1.3](#variables--grouping) Group all your `const`s before all your `let`s

    ```javascript
    //bad
    let len, foo, bar = getSomeValue(),
                  someBooleanVar = true;

    //bad
    let len;
    const foo = getSomeValue();
    let i = 0;
    const bar = getSomeDifferentValue();

    //good
    const foo = getSomeValue();
    const bar = getSomeDifferentValue();
    let len;
    let i = 0;
    ```

**[⬆ Back to top](#table-of-contents)**

## Arrays

  <a name"arrays--literals"></a><a name="2.1"></a>
  - [2.1](#arrays--literals) Use the literal syntax for array creation
    ```javascript
    //bad
    let someArray = new Array();

    //good
    let someArray = [];
    ```

  <a name"arrays--push"></a><a name="2.2"></a>
  - [2.2](#arrays--push) Use Array.push() to add items to an array
    ```javascript
    //bad
    let someArray[someArray.length] = 'item';

    //good
    let someArray.push('item');
    ```

  <a name"array--copying"></a><a name="2.3"></a>
  - [2.3](#arrays--copying) To copy arrays, use array spreads '...'
    ```javascript
    //bad
    const len = someArray.length;
    let someArrayCopy = [];

    for (let i = 0; i < len; i++) {
      someArrayCopy[i] = someArray[i];
    }

    //good
    let someArrayCopy = [...someArray];
    ```

**[⬆ back to top](#table-of-contents)**

## Objects

  <a name"objects--literals"></a><a name="3.1"></a>
  - [3.1](#objects--literals) Use the literal syntax for object creation
    ```javascript
    //bad
    let someObject = new Object();

    //good
    let someObject = {};
    ```

  <a name"objects--grouped-shorthand"></a><a name="3.2"></a>
  - [3.2](#objects--grouped-shorthand) Group your shorthand properties at the beginning of your object declaration.
    ```javascript
    const jonSnow = 'Jon Snow'
    const daenerysTargaryen = 'Daenerys Targaryen'

    //bad
    let someObject = {
      theWall: 1,
      nightsWatch: 2,
      jonSnow,
      stark = 4,
      daenerysTargaryen,
      drakes = 3,
      targaryen = 4
    }

    //good
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

**[⬆ back to top](#table-of-contents)**

## Strings

  <a name="strings--quotes"></a><a name="4.1"></a>
  - [4.1](#strings--quotes) Use single quotes `''` for strings.

    ```javascript
    // bad
    const name = "Aerys Targaryen";

    // good
    const name = 'Aerys Targaryen';
    ```

  <a name="template-literals"></a><a name="6.4"></a>
  - [4.2](#template--literals) When programmatically building up strings, use template strings instead of concatenation.


    ```javascript
    // bad
    function sayHi(name) {
      return 'You know nothing, ' + name + '?';
    }

    // bad
    function sayHi(name) {
      return ['You know nothing, ', name, '?'].join();
    }

    // bad
    function sayHi(name) {
      return `You know nothing, ${ name }?`;
    }

    // good
    function sayHi(name) {
      return `You know nothing, ${name}?`;
    }
    ```

  <a name="strings--eval"></a><a name="6.5"></a>
  - [4.3](#strings--eval) Never use `eval()` on a string, it opens too many vulnerabilities.

**[⬆ back to top](#table-of-contents)**

## Functions

  <a name="functions--declarations"></a><a name="5.1"></a>
  - [5.1](#functions--declarations) Use function declarations instead of function expressions.

    ```javascript
    // bad
    const foo = function () {
    };

    // good
    function foo() {
    }
    ```

  <a name="functions--arguments-shadow"></a><a name="5.2"></a>
  - [5.2](#functions--arguments-shadow) Never name a parameter `arguments`. This will take precedence over the `arguments` object that is given to every function scope.

    ```javascript
    // bad
    function darkSide(name, options, arguments) {
    }

    // good
    function lightSide(name, options, args) {
    }
    ```

  <a name="functions--defaults-last"></a><a name="5.3"></a>
  - [5.3](#functions--defaults-last) Always put default parameters last.

    ```javascript
    // bad
    function doStuffAndThings(opts = {}, name) {
      // ...
    }

    // good
    function doStuffAndThings(name, opts = {}) {
      // ...
    }
    ```

**[⬆ back to top](#table-of-contents)**

## Arrow Functions

  <a name="arrows--use-them"></a><a name="6.1"></a>
  - [6.1](#arrows--use-them) When you must use function expressions (as when passing an anonymous function), use arrow function notation.

    ```javascript
    // bad
    [1, 2, 3].map(function (x) {
      const y = x + 1;
      return x * y;
    });

    // good
    [1, 2, 3].map((x) => {
      const y = x + 1;
      return x * y;
    });
    ```

  <a name="arrows--implicit-return"></a><a name="6.2"></a>
  - [6.2](#arrows--implicit-return) If the function body consists of a single expression, omit the braces and use the implicit return. Otherwise, keep the braces and use a `return` statement.

    ```javascript
    // bad
    [1, 2, 3].map(number => {
      const nextNumber = number + 1;
      `A string containing the ${nextNumber}.`;
    });

    // good
    [1, 2, 3].map(number => `A string containing the ${number}.`);

    // good
    [1, 2, 3].map((number) => {
      const nextNumber = number + 1;
      return `A string containing the ${nextNumber}.`;
    });
    ```

  <a name="arrows--one-arg-parens"></a><a name="6.3"></a>
  - [6.3](#arrows--one-arg-parens) If your function takes a single argument and doesn’t use braces, omit the parentheses. Otherwise, always include parentheses around arguments.

    ```javascript
    // bad
    [1, 2, 3].map((x) => x * x);

    // good
    [1, 2, 3].map(x => x * x);

    // good
    [1, 2, 3].map(number => (
      `A long string with the ${number}. It’s so long that we’ve broken it ` +
      'over multiple lines!'
    ));

    // bad
    [1, 2, 3].map(x => {
      const y = x + 1;
      return x * y;
    });

    // good
    [1, 2, 3].map((x) => {
      const y = x + 1;
      return x * y;
    });
    ```

**[⬆ back to top](#table-of-contents)**

## Classes

  <a name="classes--extends"></a><a name="7.1"></a>
  - [7.1](#classes--extends) Use `extends` for inheritance.

    ```javascript
    // good
    class PeekableQueue extends Queue {
      peek() {
        return this._queue[0];
      }
    }
    ```

  <a name="class--tostring"></a><a name="7.2"></a>
  - [7.2](#classes--tostring) It's okay to write a custom toString() method, just make sure it works successfully and causes no side effects.

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

  <a name="classes--no-duplicate-members"></a><a name="7.3"></a>
  - [7.3](#classes--no-duplicate-members) Avoid duplicate class members.

    > Why? Duplicate class member declarations will silently prefer the last one - having duplicates is almost certainly a bug.

    ```javascript
    // bad
    class Foo {
      bar() { return 1; }
      bar() { return 2; }
    }

    // good
    class Foo {
      bar() { return 1; }
    }

    // good
    class Foo {
      bar() { return 2; }
    }
    ```


**[⬆ back to top](#table-of-contents)**

## Whitespace

  <a name="whitespace--spaces"></a><a name="8.1"></a>
  - [8.1](#whitespace--spaces) Use soft tabs set to 2 spaces.

    ```javascript
    // bad
    function foo() {
    }

    // bad
    function bar() {
    }

    // good
    function baz() {
    }
    ```

  <a name="whitespace--before-blocks"></a><a name="8.2"></a>
  - [8.2](#whitespace--before-blocks) Place 1 space before the leading brace.

    ```javascript
    // bad
    function test(){
      console.log('test');
    }

    // good
    function test() {
      console.log('test');
    }
    ```

  <a name="whitespace--around-keywords"></a><a name="8.3"></a>
  - [8.3](#whitespace--around-keywords) Place 1 space before the opening parenthesis in control statements (`if`, `while` etc.). Place no space between the argument list and the function name in function calls and declarations.

    ```javascript
    // bad
    if(isJedi) {
      fight ();
    }

    // good
    if (isJedi) {
      fight();
    }

    // bad
    function darkSide () {
      console.log ('Join the dark side');
    }

    // good
    function darkSide() {
      console.log('Joing the dark side');
    }
    ```

  <a name="whitespace--infix-ops"></a><a name="8.4"></a>
  - [8.4](#whitespace--infix-ops) Set off operators with spaces.

    ```javascript
    // bad
    const x=y+5;

    // good
    const x = y + 5;
    ```

  <a name="whitespace--chains"></a><a name="8.5"></a>
  - [8.5](#whitespace--chains) Use indentation when making long method chains (more than 2 method chains).

    ```javascript
    // bad
    $('#items').find('.selected').highlight().end().find('.open').updateCount();

    // bad
    $('#items').
      find('.selected').
        highlight().
        end().
      find('.open').
        updateCount();

    // good
    $('#items')
      .find('.selected')
        .highlight()
        .end()
      .find('.open')
        .updateCount();

    // good
    const leds = stage.selectAll('.led').data(data);
    ```

  <a name="whitespace--after-blocks"></a><a name="8.6"></a>
  - [8.6](#whitespace--after-blocks) Leave a blank line after blocks and before the next statement.

    ```javascript
    // bad
    if (foo) {
      return bar;
    }
    return baz;

    // good
    if (foo) {
      return bar;
    }

    return baz;

    // bad
    const obj = {
      foo() {
      },
      bar() {
      },
    };
    return obj;

    // good
    const obj = {
      foo() {
      },

      bar() {
      },
    };

    return obj;
    ```

  <a name="whitespace--in-parens"></a><a name="8.7"></a>
  - [8.7](#whitespace--in-parens) Do not add spaces inside parentheses.

    ```javascript
    // bad
    function bar( foo ) {
      return foo;
    }

    // good
    function bar(foo) {
      return foo;
    }

    // bad
    if ( foo ) {
      console.log(foo);
    }

    // good
    if (foo) {
      console.log(foo);
    }
    ```

  <a name="whitespace--in-brackets"></a><a name="8.8"></a>
  - [8.8](#whitespace--in-brackets) Do not add spaces inside brackets.

    ```javascript
    // bad
    const foo = [ 1, 2, 3 ];
    console.log(foo[ 0 ]);

    // good
    const foo = [1, 2, 3];
    console.log(foo[0]);
    ```

  <a name="whitespace--in-braces"></a><a name="8.9"></a>
  - [8.9](#whitespace--in-braces) Add spaces inside curly braces.

    ```javascript
    // bad
    const foo = {luke: 'Skywalker'};

    // good
    const foo = { luke: 'Skywalker' };
    ```

  <a name="whitespace--max-len"></a><a name="8.10"></a>
  - [8.10](#whitespace--max-len) Avoid having lines of code that are longer than 100 characters

    ```javascript
    // bad
    const foo = 'Luke, you can destroy the Emperor. He has foreseen this. It is your destiny. Join me, and together we can rule the galaxy as father and son.';

    // bad
    $.ajax({ method: 'POST', url: 'https://airbnb.com/', data: { name: 'John' } }).done(() => console.log('Congratulations!')).fail(() => console.log('You have failed this city.'));

    // good
    const foo = 'Luke, you can destroy the Emperor. He has foreseen this. It is your destiny. ' +
      'Join me, and together we can rule the galaxy as father and son.!';

    // good
    $.ajax({
      method: 'POST',
      url: 'https://airbnb.com/',
      data: { name: 'John' },
    })
      .done(() => console.log('Congratulations!'))
      .fail(() => console.log('You have failed this city.'));
    ```

**[⬆ back to top](#table-of-contents)**
