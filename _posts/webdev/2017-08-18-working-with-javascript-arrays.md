---
layout: article
title: Working with JavaScript arrays

image:
  teaser: javascript-array.png
  feature: javascript-array.png
  credit: Pixabay #name of the person or site you want to credit
  creditlink: https://pixabay.com/ #url to their site or licensing
---

JavaScript arrays
=================

Arrays in JavaScript are a special kind of object that inherits from the Array.prototype.

Creating an array
-----------------

Using the constructor syntax:

{% highlight javascript %}
let arr = new Array(); // empty array []
let arr = new Array("Joe", "Bob"); // ["Joe", "Bob"]
let arr = new Array(2); // array with two empty elements [undefined, undefined]
let arr = new Array(5).fill("Joe"); // ["Joe", "Joe", "Joe", "Joe", "Joe"]
{% endhighlight %}

Using the array literal syntax:

{% highlight javascript %}
let arr = []; // empty array []
    arr = ["one", "two", "three"]; // ["one", "two", "three"]
{% endhighlight %}

{% highlight javascript %}
let arr = [];
    arr[4] = 4; // [undefined, undefined, undefined, undefined, 4]
{% endhighlight %}

{% highlight javascript %}
let arr = [,,2]; // [undefined, undefined, 2]
{% endhighlight %}


Using Array.of():

{% highlight javascript %}
let arr = Array.of("Joe", "Bob"); // ["Joe", "Bob"]
{% endhighlight %}

Array.from() creates arrays from array-like objects ([HTMLCollection](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCollection), [NodeList](https://developer.mozilla.org/en-US/docs/Web/API/NodeList), [Arguments object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments)) and
iterable objects (String, Array, TypedArray, Map and Set are built in iterables.).

{% highlight javascript %}
let s = new Set(['alfa', 'bravo']); 
Array.from(s); // ["alfa", "bravo"] 
{% endhighlight %}


Accessing elements
------------------

{% highlight javascript %}
let array = ["alfa", ["bravo", "charlie"], {delta: "delta"}, function() { return 'echo'; }, "foxtrot"];
let first = array[0]; // "alfa""
let last = array[array.length - 1]; // "foxtrot"
array[1][1]; // "charlie"
array[2].delta; // "delta"
array[3]; //  function() { return 'echo'; }
array[3](); // "echo"
array[4]; // "foxtrot"
array[500]; // undefined
{% endhighlight %}


Adding and removing elements
----------------------------

{% highlight javascript %}
var array = ["bravo", "charlie", "delta"];
{% endhighlight %}

Add an item to the end of the array:

{% highlight javascript %}
array.push("echo"); // ["bravo", "charlie", "delta", "echo"];
{% endhighlight %}

Add an item to the start of the array:

{% highlight javascript %}
array.unshift("alfa"); // ["alfa", "bravo", "charlie", "delta", "echo"];
{% endhighlight %}

Remove an item from the end of the array:

{% highlight javascript %}
array.pop(); // ["alfa", "bravo", "charlie", "delta"];
{% endhighlight %}

Remove an item from the start of the array:

{% highlight javascript %}
array.shift(); // ["bravo", "charlie", "delta"];
{% endhighlight %}


{% highlight javascript %}
{% endhighlight %}
{% highlight javascript %}
{% endhighlight %}
{% highlight javascript %}
{% endhighlight %}




