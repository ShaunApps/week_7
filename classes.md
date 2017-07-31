Define a class, Square. This square class has one attribute, side_length. The following code should run without errors:
```ruby
s = Square.new
s.side_length = 5
s.side_length
=> 5
```

-------

Let’s continue working on our Square class. We want to be able to instantiate a new Square like this:

```ruby
s = Square.new(5)
```
so that:
```ruby
s.side_length
=> 5
```

-----

Now, let’s teach the Square class how to do some math! Define an area method on Square that returns the Square‘s area.

The following code should work:

```ruby
s = Square.new(5)
s.area
=> 25
```

-----

The puts method calls an object’s `to_s` method.
The `p` method calls an object’s `inspect` method.
Define a class whose instances respond to `puts` and `p`. For example:
```ruby
puts MyClass.new
p MyClass.new
```
should both output a nice, readable string.

-----

A DSL (domain-specific language) is a technique for writing Ruby code in such a way that it’s readable as a new language optimized for a particular problem or use case.
You start with the way you’d like the code to read, then go back and make that code do what you want it to do.
Create a ruby file, `quick_fox.rb` and paste the following line of code into it:
`quick_fox.jumped_over(lazy_dog, daisy_log)`
Write just enough code before that line to make it not return any errors.

-----

What does self represent? To answer this question, figure out what self is in various contexts:
irb
a plain Ruby file
a method
a class
a method within a class
Submit not only your answer, but the code you used to discover that answer.

-----

Define a class, Quadrilateral. Now, model this concept in Ruby using classes and inheritance:
A rectangle, square, rhombus, and trapezoid are all types of quadrilaterals.
A square is a type of rectangle.
A rhombus is a type of trapezoid.
Use TDD to confirm that all of your classes are working correctly. Here’s an example test:
```ruby
def test
  squa = Square.new
  puts squa.is_a? Rectangle
  puts squa.is_a? Quadrilateral

  rect = Rectangle.new
  puts rect.is_a? Quadrilateral
  puts not(rect.is_a? Trapezoid)
end

test
```

-----

Revisit our Quadrilateral classes from before. Let’s continue to flesh out these shapes. We want the following code to work:
```ruby
def test
  quad = Quadrilateral.new(1,1,1,1)
  rectangle = Rectangle.new(1,1)
  trapezoid = Trapezoid.new(1,1,1)
  square = Square.new(1)
  rhombus = Rhombus.new(1)
end

test
```
Each of these shapes have different rules with respect to the side lengths. For example:
1) A square and Rhombus have all four sides of the same lengths. We should only need to pass one value to initialize, and the square sets all four of it’s internal side lengths.
2) A rectangle has two sides of one length and two sides of another length, so we should be able to pass two values to initialize, and have it set all four of it’s internal side lengths.
3) A trapezoid as two sides of the same lenth, and two different length sides, so we should be able to pass three values, and have it set all four of it’s internal side lengths.
It makes sense to have all these classes share the same `@sides` instance variable.
We’ll get you started with the Quadrilateral class:
```ruby
class Quadrilateral
  def initialize(side1, side2, side3, side4)
    @sides = [side1, side2, side3, side4]
  end
end
```
And the Trapezoid class:
```ruby
class Trapezoid < Quadrilateral
  def initialize(side1, side2, sides3_4)
    @sides = [side1, side2, sides3_4, sides3_4]
  end
end
```
-----

Let’s make all of these classes a bit smarter. Think back to how you set up your Square class in a previous assignment. Use that knowledge to help you create a perimeter method for the Quadrilateral which will return the sum of the side lengths.
Since all of our classes are sharing an `@sides` variable that contains 4 side lengths, we are able to accomplish this for all our classes with a single perimeter method on Quadrilateral.
Use tests to confirm that all of your classes are working correctly. For example, the following tests should all return true:
```ruby
def test
  quad = Quadrilateral.new(1,2,3,4)
  rectangle = Rectangle.new(1,2)
  trapezoid = Trapezoid.new(1,1,2)
  square = Square.new(1)
  rhombus = Rhombus.new(1)

  puts quad.perimeter == 10
  puts rectangle.perimeter == 6
  puts trapezoid.perimeter == 6
  puts square.perimeter == 4
  puts rhombus.perimeter == 4
end

test
```
