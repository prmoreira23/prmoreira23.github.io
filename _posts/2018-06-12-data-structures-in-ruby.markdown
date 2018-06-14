---
layout: post
title:  "Demystifying Data Structures in Ruby"
date:   2018-06-14 08:48:46 -0400
categories: ruby data structures
---

The human being has been inspired by nature to develop ideas for a long time. Data structures are no different.  It is a way of organizing and storing observations that have been abstracted from their real world environment. For instance, a classroom of students could be represented as an array of names.  A student could also be represented as an object with endowed attributes (what they look like) and behavior (what they do).

Ruby gives us several collection types for us to use. Along with arrays and objects, there are also: hashes, sets, tuples, and structs.

# Arrays
Arrays can hold anything that inherits from the Object class. An array is a collection separated by commas to maintain order.

{% highlight ruby %}
# Ways to create an Array
a = [];
e = Array.new();
i = Array[];

my_array = [];
my_array.push(23);
my_array <<  "Access Labs";
my_array[my_array.count] = true;

my_array

#  => [23, "Access Labs", true]
{% endhighlight %}
*Code 1. Working With Arrays.*

Arrays make it easier to implement other data structures like: stacks and queues. The stack organizes data like a kitchen dishwasher. First, plates become our data. We organize the plates by taking one and putting it down on the table, one on top of the other. When we are ready to serve people, we grab the top plate first. The Queue organizes data like a grocery store line. Someone enters the store, gets their groceries, and then they go to the cashier, wait their turn in the line, pay and leave. We can model these scenarios with abstract methods such as: pop() and push, and shift() and unshift().

(LIFO - Last In First Out)
(FIFO - First In First Out)

![image tooltip here](/assets/stack-data-structure.gif)

*Figure 1. How a Stack Data Structure Works.*

{% highlight ruby %}
class Stack
  def initialize
    @data = []
  end

  def to_s
    @data
  end

  def push(element)
    @data.push(element)
  end

  def pop
    @data.pop()
  end

  def top
    @data.last
  end
end

my_stack = Stack.new;
my_stack.push(2)
#  => [2]
my_stack.push(1)
#  => [2, 1]
my_stack.push(4)
#  => [2, 1, 4]
my_stack.push(3)
#  => [2, 1, 4, 3]
my_stack.pop
#  => 3

my_stack.top
#  => 4

my_stack.to_s
#  => [2, 1, 4]
{% endhighlight %}
*Code 2. Stack Data Structure Implementation in Ruby.*

![image tooltip here](/assets/queue-data-structure.gif)

*Figure 2. How a Queue Data Structure Works.*

{% highlight ruby %}
class Queue
  def initialize
    @data = []
  end

  def to_s
    @data
  end

  def enqueue(element)
    @data.push(element)
  end

  def dequeue
    @data.shift
  end

  def top
    @data.first
  end
end

my_queue = Queue.new;
my_queue.enqueue(2)
#  => [2]
my_queue.enqueue(1)
#  => [2, 1]
my_queue.enqueue(4)
#  => [2, 1, 4]
my_queue.enqueue(3)
#  => [2, 1, 4, 3]
my_queue.dequeue
#  => 2

my_queue.top
#  => 1

my_queue.to_s
#  => [1, 4, 3]
{% endhighlight %}
*Code 3. Queue Data Structure Implementation in Ruby.*

# Objects (An instance of a Class)
Object-Oriented Programming gives us the possibility to create customized data structures. In the example below, we can see a blueprint of a person. From that definition it is possible to create instances of it.

{% highlight ruby %}
class Person
  attr_accessor :name, :age
  def initialize(name, age)
    @name = name
    @age = age
  end
end

persons = []

persons << Person.new("Pablo", 23);
persons << Person.new("Patrick", 21);

persons.first.name
# => "Pablo"
persons.first.age
# => 23
{% endhighlight %}

By using classes we have a whole world of possibilities when it comes to develop data structures; we can build pretty much any type of struct and even create hybrid ones.

# Hashes
Hashes are a data structure similar to arrays.  Instead of relying on the item's place in line, which we also call the index, we can use a key/value structure to store and retrieve data. The power is in the ability to find an item directly via its key. The ability to retrieve data by key allows for higher performance in working memory. (see code 4).

{% highlight ruby %}
prince = {};
prince["name"] = "Prince";
prince["profession"] = "Amazing Teacher";
# => {"name"=>"Prince", "profession"=>"Amazing Teacher"}

steven = Hash.new

students = {
  :first => "Roniece",
  :second => "Michael",
  :third => "Angelina"
};

students[:second]
# => "Michael"
{% endhighlight %}
*Code 4. Working With Hashes.*

It is less efficient to use strings than symbols as keys. A simple test was performed to observe retrieval time (see code 5) for hashes using string and symbols as keys. It took ~ 1.17 seconds to retrieve 10,000,000 times the value using a string as key; and it took ~ 0.68 seconds using a symbol as key. The difference is ~ 41.02 % less time when symbols are used.

{% highlight ruby %}
require 'benchmark'

string_key_hash = {"a" => 23}
symbol_key_hash = {:a => 23}

puts Benchmark.measure { 10_000_000.times { symbol_key_hash[:a] } }
# 0.670000   0.000000   0.670000 (  0.680182)
# => nil

puts Benchmark.measure { 10_000_000.times { string_key_hash["a"] } }
#  1.160000   0.010000   1.170000 (  1.172485)
# => nil

{% endhighlight %}
*Code 5. Strings or Symbols as keys? You tell me*

# Sets
Sets are a special type of array. The major difference is that they enforce uniqueness. It also includes several methods related to the theory of sets (i.e.: union, merge, superset, subset, among others).

{% highlight ruby %}
require 'set'
# When set is required it adds to_set to the Array class

fruits = Set.new;
fruits.add('banana');
fruits.add('apple');
fruits.add('pear');
fruits.add('banana');
fruits.add('grape');

fruits.each { |fruit| puts fruit }
# banana
# apple
# pear
# grape
# => #<Set: {"banana", "apple", "pear", "grape"}>

a = [*1..10].to_set
# => #<Set: {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}>

b = a.collect {|n| n % 2 == 0}.to_set;
# => #<Set: {2, 4, 6, 8, 10}>

a.intersection(b)
# => #<Set: {2, 4, 6, 8, 10}>

{% endhighlight %}
*Code 6. Working With Sets.*


#  Tuples (Rinda gem)
Tuples are available in Ruby through the ***Rinda*** gem.
It can be installed using the following command ```gem install rubysl-rinda ```. Tuples, arrays and hashes are alike; they only differ in the fact that tuples are immutable. It will raise and error if we try to reassign an element.  

{% highlight ruby %}
require 'rinda'

# Expects an Array or Hash as argument
tuple = Rinda::Tuple.new([1, 2])

tuple[0]
# => 1

tuple[0] = 23
 # NoMethodError: undefined method `[]=' for
 # <Rinda::Tuple:0x007fb1231bd5d8 @tuple=[1, 2]>


{% endhighlight %}

# Structs
Structs are a data structure that helps to bundle a number of attributes together. It is extremely useful when we need to group accessible attributes but we don't need to have an explicit class.

{% highlight ruby %}
# Using Struct

Student = Struct.new(:name, :age, :sex);

lawrence = Student.new "Lawrence", 24, :male;

lawrence.name
# => "Lawrence"

lawrence[:sex]
# => :male

lawrence.age
# => 24

# => 48.95



# Using Class

class Student
  attr_accessor :name, :age, :sex
  def initialize(name, age, sex)
    @name = name
    @age = age
    @sex = sex
  end
end;

lawrence = Student.new "Lawrence", 24, :male;

lawrence.name
# => "Lawrence"

lawrence[:sex]
# => nil

lawrence.sex
# => :male

lawrence.age
# => 24

# => 48.95
{% endhighlight %}



Data structures are very important to manipulate and organize data. It makes it easier to abstract concepts from the real world.

# Acknowledgments

Thank you Steven for helping me with the text proof-reading.

Thank you Michael for helping me to come up with a best post title.

![image tooltip here](https://media.giphy.com/media/lD76yTC5zxZPG/giphy.gif)
