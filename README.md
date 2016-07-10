# jeKnowledge styleguides

## Table of Contentes

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

