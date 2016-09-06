# Ruby styleguide

Guide for programming Ruby.
We use [bbatsov Ruby Styleguide](https://github.com/bbatsov/ruby-style-guide) with special attention to:

#### Source Code Layout

  - Use soft tabs set to 2 spaces.

  - Prefer single-line class format for class declaration with no body.

  ```ruby
    #bad   
    class FooError < StandardError
    end
    
    #good
    FooError = Class.new(StandardError)
  ```

  - Avoid single line methods, with exception to empty-body methods.

  ```ruby
    def some_method
      body
    end

    def no_body; end
  ```

  - Use spaces around operators, after commas, colons and semicolons, with exception to the exponent operator.

  ```ruby
    sum = 1 + 2
    a, b = 1, 2
    class FooError < StandardError; end
    e = M * c**2
  ```

  - No spaces after `(`, `[` or before `]`, `)`. Use spaces around `{` and before `}`. 

  ```ruby
    some(arg).other
    [1, 2, 3].each { |e| puts e }
  ```

  - No space after `!`.

  - Indent when as deep as case.

  ```ruby
    case
    when song.name == 'Misty'
      puts 'Not again!'
    when song.duration > 120
      puts 'Too long!'
    when Time.now.hour > 21
      puts "It's too late"
    else
      song.play
    end
  ```

  - Use empty lines between method definitions.

  - Align the elements of array literals spanning multiple lines.

  ```ruby
  menu_item = [
    'Spam', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam',
    'Baked beans', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam'
  ]
  ```

  - Limit lines to 80 characters.
 
  - End each file with a newline.

  - Don't use block comments.

  ```ruby
  # bad
  =begin
  comment line
  another comment line
  =end

  # good
  # comment line
  # another comment line
  ```

#### Syntax

  - Use `::` only to reference constants

  ```ruby
  SomeClass.some_method
  some_object.some_method
  SomeModule::SomeClass::SOME_CONST
  SomeModule::SomeClass()
  ```

  - Use parentheses around the arguments of method invocations.

  - Omit parentheses for method calls with no arguments and methods that have a keyword status.

  - Define optional arguments at the end of the list of arguments. 

  ```ruby
  def some_method(c, d, a = 1, b = 2)
    puts "#{a}, #{b}, #{c}, #{d}"
  end
  ```

  - Avoid the use of parallel assignment for defining variables

  ```ruby
  #bad
  a, b, c, d = 'foo', 'bar', 'baz', 'foobar'

  #good
  a = 'foo'
  b = 'bar'
  c = 'baz'
  d = 'foobar'
  ```

  - Do not use `for`, unless you know exactly why.

  - Do not use `then` for multi-line `if`/`unless`.

  - Favor ternary operator over `if/else/end` constructors.

  ```ruby
  result = some_condition ? something : something_else
  ```

  -  Leverage the fact that `if `and `case` are expressions which return a result.

  ```ruby
  result =
    if condition
      x
    else
      y
    end
  ```

  - Do not use `unless` with `else`.

  - Don't use parentheses around the conditions of `if/unless/while/until`.

  - Use  Kerner#loop for infite loops.

  - Omit the outer braces around an implicit options hash.

  ```ruby
  user.set(name: 'John', age: 45, permissions: { read: true })
  ```

  - Avoid `return` where not required for flow control.

  ```ruby
  def some_method(some_arr)
    some_arr.size
  end
  ```

  - Use shorthand self assignment operators whenever applicable.

  ```ruby
  # bad
  x = x + y
  x = x * y
  x = x**y
  x = x / y
  x = x || y
  x = x && y

  # good
  x += y
  x *= y
  x **= y
  x /= y
  x ||= y
  x &&= y
  ```

  - Use `||=` to initialize variables only if they're not already initialized.
 
 ```ruby
  # bad
  name = name ? name : 'Bozhidar'
  # good - set name to 'Bozhidar', only if it's nil or false
  name ||= 'Bozhidar
 ```
 
- Don't use `||=` to initialize boolean variables.
 
- Do not put a space between a method name and the opening parenthesis.
 
- Do not use nested method definitions.
 
- Use the new lambda literal syntax for single line body blocks. Use the `lambda` method for multi-line blocks.

 ```ruby
  l = ->(a, b) { a + b }
  l.call(1, 2)

  l = lambda do |a, b|
    tmp = a * 7
    tmp * b / 50
  end
 ```

