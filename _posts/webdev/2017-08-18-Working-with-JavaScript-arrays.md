---
layout: article
title: Working with JavaScript arrays

image:
  teaser: javascript-array.png
  feature: javascript-array.png
  credit: Pixabay #name of the person or site you want to credit
  creditlink: https://pixabay.com/ #url to their site or licensing
---

Creating an array
-----------------

Using the constructor syntax:

{% highlight javascript %}
let arr = new Array(); // empty array []
let arr = new Array("Joe", "Bob"); // ["Joe", "Bob"]
let arr = new Array(2); // array with two elements [undefined, undefined]
{% endhighlight %}

Using the array literal syntax:

{% highlight javascript %}
let arr = []; // empty array []
let arr = ["one", "two", "three"]; // ["one", "two", "three"]
{% endhighlight %}

Using Array.of():

{% highlight javascript %}
let arr = Array.of("Joe", "Bob"); // ["Joe", "Bob"]
{% endhighlight %}


Accessing elements
------------------

{% highlight javascript %}
let array = ["alfa", "bravo", "charlie"];
let first = array[0]; // "alfa"
let last = array[array.length - 1]; // "charlie"
{% endhighlight %}
