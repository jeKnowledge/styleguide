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

  - No spaces after (, [ or before ], ). Use spaces around { and before }. 

  ```ruby
    some(arg).other
    [1, 2, 3].each { |e| puts e }
  ```

  - No space after !.

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
