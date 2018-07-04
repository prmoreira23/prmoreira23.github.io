---
layout: post
title:  "CSS Selectors For DOM Manipulation"
date:   2018-07-04 08:48:46 -0400
categories: ruby data structures
---

CSS selectors are a pattern used to select HTML elements you want to manipulate. They are very useful and the more you know about them the easier it is to target HTML elements.
We can think of using them in order to apply CSS rules and also to add manipulate them using JavaScript.
<!-- Document Object Model -->
#  (*) Star selector

The star selector selects every single element on the page or in the element you are searching within.

{% highlight html %}
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>DOM Manipulation</title>
  </head>
  <body>
    <h1>Document Object Model Manipulation</h1>

    <ul class="to-do">
      <li>Walk the dog</li>
      <li>Buy groceries</li>
      <li>Go out with friends</li>
    </ul>

    <script type="text/javascript">
      let everything = document.querySelectorAll("body *");
      console.log(everything);
    </script>
  </body>
</html>

{% endhighlight %}

![image tooltip here](/assets/css-images/star-selector.png)
*Figure 1. Browser console output.*

#  (X) Type selector

The type selector selects every single element on the page that is of type X.

{% highlight html %}
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>DOM Manipulation</title>
  </head>
  <body>
    <h1>Document Object Model Manipulation</h1>

    <ul class="to-do">
      <li>Walk the dog</li>
      <li>Buy groceries</li>
      <li>Go out with friends</li>
    </ul>

    <script type="text/javascript">
      let h1 = document.querySelector("h1");
      console.log(h1);
    </script>
  </body>
</html>


{% endhighlight %}

![image tooltip here](/assets/css-images/type-selector.png)


#  (#) Id selector

The id selector selects a single element on the page based on its unique id.

{% highlight html %}
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>DOM Manipulation</title>
  </head>
  <body>
    <h1>Document Object Model Manipulation</h1>

    <ul class="to-do">
      <li>Walk the dog</li>
      <li id="buy-groceries">Buy groceries</li>
      <li>Go out with friends</li>
    </ul>

    <script type="text/javascript">
      let li = document.querySelector("#buy-groceries");
      console.log(li);
    </script>
  </body>
</html>
{% endhighlight %}

![image tooltip here](/assets/css-images/id-selector.png)

#  (.) Class selector

The class selector selects every single element on the page that has the given class applied.

{% highlight html %}
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>DOM Manipulation</title>
  </head>
  <body>
    <h1>Document Object Model Manipulation</h1>

    <ul class="to-do">
      <li>Walk the dog</li>
      <li id="buy-groceries">Buy groceries</li>
      <li>Go out with friends</li>
    </ul>

    <script type="text/javascript">
      let ul = document.querySelector(".to-do");
      console.log(ul);
    </script>
  </body>
</html>
{% endhighlight %}

![image tooltip here](/assets/css-images/class-selector.png)

#  (X Y) Descendant selector (Direct and indirect children)

The descendant selector selects every children element Y of X, and it can be either direct or indirect children.

{% highlight html %}
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>DOM Manipulation</title>
  </head>
  <body>
    <h1>Document Object Model Manipulation</h1>

    <ul class="to-do">
      <li>Walk the dog</li>
      <li id="buy-groceries">Buy groceries
        <ol>
          <li>Buy spinach</li>
          <li>Buy pineaple</li>
        </ol>
      </li>
      <li>Go out with friends</li>
    </ul>

    <script type="text/javascript">
      let lis = document.querySelectorAll("ul li");
      console.log(lis);
    </script>
  </body>
</html>
{% endhighlight %}

![image tooltip here](/assets/css-images/descendant-selector.png)

#  (X > Y) Descendant selector (Direct children only)

The descendant selector (>) selects only every direct children of X that is a Y element.

{% highlight html %}
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>DOM Manipulation</title>
  </head>
  <body>
    <h1>Document Object Model Manipulation</h1>

    <ul class="to-do">
      <li>Walk the dog</li>
      <li id="buy-groceries">Buy groceries
        <ol>
          <li>Buy spinach</li>
          <li>Buy pineaple</li>
        </ol>
      </li>
      <li>Go out with friends</li>
    </ul>

    <script type="text/javascript">
      let lis = document.querySelectorAll("ul > li");
      console.log(lis);
    </script>
  </body>
</html>

{% endhighlight %}

![image tooltip here](/assets/css-images/descendant-selector-2.png)


#  (X + Y) Adjacent selector

The adjacent selector (+) selects every direct sibling of X that is a Y element.

{% highlight html %}
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>DOM Manipulation</title>
  </head>
  <body>
    <h1>Document Object Model Manipulation</h1>

    <ul class="to-do">
      <li>Walk the dog</li>
      <li id="buy-groceries">Buy groceries
        <ol>
          <li>Buy spinach</li>
          <li>Buy pineaple</li>
        </ol>
      </li>
      <li>Go out with friends</li>
    </ul>

    <p>Hi</p>
    <p>Ola</p>
    <p>Salut</p>

    <script type="text/javascript">
      let lis = document.querySelectorAll("ul + p");
      console.log(lis);
    </script>
  </body>
</html>
{% endhighlight %}

![image tooltip here](/assets/css-images/adjacent-selector.png)


#  (X ~ Y) Adjacent selector

The adjacent selector (~) selects all siblings of X that is a Y element.

{% highlight html %}
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>DOM Manipulation</title>
  </head>
  <body>
    <h1>Document Object Model Manipulation</h1>

    <ul class="to-do">
      <li>Walk the dog</li>
      <li id="buy-groceries">Buy groceries
        <ol>
          <li>Buy spinach</li>
          <li>Buy pineaple</li>
        </ol>
      </li>
      <li>Go out with friends</li>
    </ul>

    <p>Hi</p>
    <p>Ola</p>
    <p>Salut</p>

    <script type="text/javascript">
      let lis = document.querySelectorAll("ul ~ p");
      console.log(lis);
    </script>
  </body>
</html>


{% endhighlight %}

![image tooltip here](/assets/css-images/adjacent-selector-2.png)

#  (X:pseudo-class) Pseudo-class selector

Pseudo-classes selectors bring a lot of power to the table. Let's say you need to select the 5th div on a page, `div:nth-of-type(5)` will do the trick. Find below a list of pseudo-classes selectors:
* X:checked
* X:after
* X:before
* X:hover
* X:not(selector)
* X:nth-child(n)
* X:nth-last-child(n)
* X:nth-of-type(n)
* X:nth-last-of-type(n)
* X:first-child
* X:last-child

{% highlight html %}
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>DOM Manipulation</title>
  </head>
  <body>
    <h1>Document Object Model Manipulation</h1>

    <ul class="to-do">
      <li>Walk the dog</li>
      <li id="buy-groceries">Buy groceries
        <ol>
          <li>Buy spinach</li>
          <li>Buy pineaple</li>
        </ol>
      </li>
      <li>Go out with friends</li>
    </ul>

    <p>Hi</p>
    <p>Ola</p>
    <p>Salut</p>

    <script type="text/javascript">
      let p = document.querySelector("p:nth-of-type(3)");
      console.log(p);
    </script>
  </body>
</html>



{% endhighlight %}

![image tooltip here](/assets/css-images/pseudoclasses.png)

#  (X[title]) Attributes selector

Attribute selectors allows us to select HTML elements based on its attributes. Let's say we need to select all text inputs on our page, then we would use something like `input[type=text]`. Find more selectors below:
* X[href=“http://pablo.com”]
* X[href*=“pablo”] somewhere in the string
* X[href^=“http”] beginning of the string
* X[href$=“.jpg”] end of the string
* X[data-*="foo”]
* X[foo~="bar"] values in list

{% highlight html %}
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>DOM Manipulation</title>
  </head>
  <body>
    <h1>Document Object Model Manipulation</h1>

    <ul class="to-do">
      <li>Walk the dog</li>
      <li id="buy-groceries">Buy groceries
        <ol>
          <li>Buy spinach</li>
          <li>Buy pineaple</li>
        </ol>
      </li>
      <li>Go out with friends</li>
    </ul>

    <p>Hi</p>
    <p>Ola</p>
    <p>Salut</p>

    <label>
      Name:
      <input type="text" name="" value="">
    </label>

    <script type="text/javascript">
      let input = document.querySelector("input[type=text]");
      console.log(input);
    </script>
  </body>
</html>



{% endhighlight %}

![image tooltip here](/assets/css-images/attributes.png)
