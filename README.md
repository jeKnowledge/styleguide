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

  <a name"objects--grouped-shorthand"></a><a name="2.2"></a>
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
