---
layout: post
title:  "Enumerators in Ruby"
date:   2018-05-15 08:48:46 -0400
categories: ruby enumerators
---
Enumerators are a set of methods to traverse, search, sort and manipulate collections (Lists and Hashes) in Ruby.

The concepts regarding enumerators are directly related with loops and collections.
If you understand the concepts of loops, lists and hashes, there is absolutely nothing new conceptually in this post. Usually, Enumerators allow us to write more elegant solutions with fewer lines of code.



# EACH
The `Each` method yields each element from the collection that is calling it to the block passed as argument. This method returns the original version collection, no mater what operations you applied to each element.

{% highlight ruby %}
colors = ['blue', 'green', 'yellow', 'orange', 'red']

colors.each { |color| puts color.capitalize }

# Blue
# Green
# Yellow
# Orange
# Red
# => ["blue", "green", "yellow", "orange", "red"]
{% endhighlight %}

# MAP
The `Map` method yields each element from the collection that is calling it to the block passed as argument. This method returns the modified version of the collection.

{% highlight ruby %}
fruits = ['banana', 'apple', 'orange', 'grape', 'pear']

fruits.map { |fruit| fruit.upcase }

# => ["BANANA", "APPLE", "ORANGE", "GRAPE", "PEAR"]
{% endhighlight %}

# COLLECT
The `Collect` method is just an alias for the `Map` method.

{% highlight ruby %}
fruits = ['banana', 'apple', 'orange', 'grape', 'pear']

fruits.collect { |fruit| fruit.upcase }

# => ["BANANA", "APPLE", "ORANGE", "GRAPE", "PEAR"]
{% endhighlight %}

# INJECT
The `Inject` method takes an accumulator (`sum` in the example below) and iterate through each element doing operations with them. This method returns the accumulator when it is done.
In the example below we use the accumulator to hold the sum of all elements of the `shopping_cart` list.

{% highlight ruby %}
shopping_cart = [9.0, 9.95, 5.9, 10.90, 3.20]

shopping_cart.inject { |sum, price| sum += price }

# => 38.95
{% endhighlight %}

# REDUCE
The `Reduce` method is just an alias for the `Inject` method. We can also pass an initial value for the accumulator, default is 0.

{% highlight ruby %}
shopping_cart = [9.0, 9.95, 5.9, 10.90, 3.20]

shopping_cart.reduce(10) { |sum, price| sum += price }

# => 48.95
{% endhighlight %}

# SELECT
The `Select` method returns a list with all elements that matches the condition passed in the block. In this example it is going to return a list with all even numbers from the list.

{% highlight ruby %}
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

numbers.select { |number| number.even? }

# => [2, 4, 6, 8, 10]
{% endhighlight %}

# REJECT
The `Reject` method is exactly the opposite of the method `Select`; It returns a list with all elements that does not match the condition passed in the block.
In the example below it is going to return a list with all odd numbers from the list. We are `reject`ing all the even numbers.

{% highlight ruby %}
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

numbers.reject { |number| number.even? }

# => [1, 3, 5, 7, 9]
{% endhighlight %}

# FIND
The `Find` method returns the first element in the collection that matches the condition passed in the block. It returns `nil` if there is no element that matches the condition.

{% highlight ruby %}
names = ["Joseph", "Paul", "Pablo", "Mary", "Kristy"]

names.find { |name| name == "Pablo" }

# => "Pablo"
{% endhighlight %}

# DETECT
The `Detect` method is just an alias for the `Find` method.

{% highlight ruby %}
names = ["Joseph", "Paul", "Pablo", "Mary", "Kristy"]

names.detect { |name| name == "Patrick" }

# => nil
{% endhighlight %}

Enumerators are a great feature in the Ruby language. It makes it easier to work with collections. I hope you liked this post and I am looking forward to writing the next one.

![image tooltip here](https://media.giphy.com/media/lD76yTC5zxZPG/giphy.gif)
