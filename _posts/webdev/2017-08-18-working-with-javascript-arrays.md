---
layout: article
title: Working with JavaScript arrays

image:
  teaser: javascript-array.png
  feature: javascript-array.png
  credit: Pixabay #name of the person or site you want to credit
  creditlink: https://pixabay.com/ #url to their site or licensing
---

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

We have the following array

{% highlight javascript %}
var array = ["bravo", "charlie", "delta"];
{% endhighlight %}

We can add an item to the end of the array with push

{% highlight javascript %}
array.push("echo");
console.log(array); // ["bravo", "charlie", "delta", "echo"];
{% endhighlight %}

To add an item to the start of the array you use unshift

{% highlight javascript %}
array.unshift("alfa");
console.log(array); // ["alfa", "bravo", "charlie", "delta", "echo"];
{% endhighlight %}

pop is used to remove an item from the end of the array, it returns the removed item:

{% highlight javascript %}
array.pop(); // returns "echo"
console.log(array); // ["alfa", "bravo", "charlie", "delta"];
{% endhighlight %}

shift is used to remove an item from the start of the array, it returns the removed item:

{% highlight javascript %}
array.shift(); // returns "alfa"
console.log(array); // ["bravo", "charlie", "delta"];
{% endhighlight %}


{% highlight javascript %}
{% endhighlight %}
{% highlight javascript %}
{% endhighlight %}
{% highlight javascript %}
{% endhighlight %}




