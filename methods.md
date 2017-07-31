Let’s practice our method writing syntax! Prepare a method say_hello that takes one argument. That argument is the name of the person to be greeted. The method should then print on the screen a greeting to that person. For example:

```ruby
say_hello('Jack')
=> "Why, hello there Jack!"
```


Here’s a new Ruby syntax we haven’t seen yet.
`%w[a b c d]`
Using introspection, figure out what this syntax does. Tell us what you discover.

Introspection - examining classes, methods and keywords to know what they are, what they do and what they know.

One way of introspecting something… drop it into irb and take a deeper look at it!

Next, keep digging and figure out the difference between these last two lines of code:

```ruby
a = 1
%w[#{a} b c d]
%W[#{a} b c d]
```


`pets = ["Scooby", "Soco", "Summer", "Pixie", "Wilson", "Mason","Baron", "Brinkley", "Bella"]`

Write a method that takes in the pets array as a parameter. Inside that method, iterate over the array using the each method. If the name starts with an “S”, output the message “My name starts with an S for super!” If the name does not begin with an “S” output the message: “I’m still pretty special too!”.


Define a method named `max` that takes two numbers as arguments and returns the largest of them.


Refactor your `max` method to find the max of any number of arguments. Again, show us your tests!


Below, we have an array of lowercase names. Write a method, `capitalize_each` that takes an array as an argument, and returns a new array with each name correctly capitalized.

```ruby
names = ['romeo', 'oedipus', 'hansel', 'gretel']
names = capitalize_each(names)
p names
=> ['Romeo', 'Oedipus', 'Hansel', 'Gretel']
Make sure to practice using Ruby’s map method to accomplish this!
```


We tried to write a program that builds a pyramid, but we couldn’t get it to work! Your goal is to fix it for us. Here’s how we wanted it to work:

If we run the program like this: `ruby pyramid.rb 5`
It should print out a pyramid 5 rows tall, like this:
```
 *
 **
 ***
 ****
 *****
 ```
If we call the program like this: `ruby pyramid.rb 23`
It should print out a pyramid 23 rows tall.

Here’s our code:
```ruby
height = ARGV[0]
output = ""
height.times do |i|
  output << "*" * i
  output << "\n"
end
puts output
```
Some Tips:

ARGV is an array of the arguments passed in through the command line. For example, when we run `ruby pyramid.rb 23`, then `ARGV == ["23"]`.
If we were to run `ruby pyramid.rb 23 hello`, then `ARGV == ["23", "hello"]`. Use a ruby file and introspect to explore this tool further. Googling it can be confusing, so in this one case we don’t recommend it right now.

Read each line carefully and make sure you fully understand the original developer’s intention before you start changing things.
