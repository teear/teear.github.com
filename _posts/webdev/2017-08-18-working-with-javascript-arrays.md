---
layout: article
title: Working with JavaScript arrays

image:
  teaser: javascript-array.png
  feature: javascript-array.png
  credit: Pixabay #name of the person or site you want to credit
  creditlink: https://pixabay.com/ #url to their site or licensing
---

Arrays in JavaScript are a special kind of object that inherits from the Array.prototype. Arrays are ordered collections of values.

Creating an array
-----------------

Using the constructor syntax:

{% highlight javascript %}
let arr = new Array(); // empty array []
let arr = new Array("Joe", "Bob"); // ["Joe", "Bob"]
let arr = new Array(2); // array with two empty elements [,]
let arr = new Array(5).fill("Joe"); // ["Joe", "Joe", "Joe", "Joe", "Joe"]
{% endhighlight %}

Using the array literal syntax:

{% highlight javascript %}
let arr = []; // empty array []
    arr = ["one", "two", "three"]; // ["one", "two", "three"]
{% endhighlight %}

{% highlight javascript %}
let arr = [];
    arr[4] = 4; // [,,,,4]
{% endhighlight %}

{% highlight javascript %}
let arr = [,,2]; // [,,2]
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

You can also create associative arrays by using a named index:

{% highlight javascript %}
let assoc = [];
assoc["alfa"] = "aarne";
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


Adding, removing and replacing elements
---------------------------------------

We have the following array

{% highlight javascript %}
var array = ["bravo", "charlie", "delta"];
{% endhighlight %}

We can add an element to the end of the array with push

{% highlight javascript %}
array.push("echo"); // returns number of items in the array
console.log(array); // ["bravo", "charlie", "delta", "echo"];
{% endhighlight %}

To add an element to the start of the array you use unshift

{% highlight javascript %}
array.unshift("alfa"); // returns number of items in the array
console.log(array); // ["alfa", "bravo", "charlie", "delta", "echo"];
{% endhighlight %}

pop is used to remove an element from the end of the array, it returns the removed element

{% highlight javascript %}
array.pop(); // returns "echo"
console.log(array); // ["alfa", "bravo", "charlie", "delta"];
{% endhighlight %}

shift is used to remove an element from the start of the array, it returns the removed element

{% highlight javascript %}
array.shift(); // returns "alfa"
console.log(array); // ["bravo", "charlie", "delta"];
{% endhighlight %}

If you need to add, remove or replace items in other indexes, you can use splice

{% highlight javascript %}
array.splice(1, 1); // removes 1 element at index 1 and returns it in an array
console.log(array); // ["bravo", "delta"];
{% endhighlight %}

{% highlight javascript %}
array.splice(1, 0, "charlie"); // inserts 1 item at index 1 and returns [] (empty array, as no elements were removed)
console.log(array); // ["bravo", "charlie", "delta"];
{% endhighlight %}

{% highlight javascript %}
array.splice(1, 1, "canada"); // replaces 1 item at index 1 and returns the removed item
console.log(array); // ["bravo", "canada", "delta"];
{% endhighlight %}

delete removes an item and leaves the element empty

{% highlight javascript %}
delete array[1]; // removes item at index 1 and returns true if succesful
console.log(array); // ["bravo",,"delta"];
{% endhighlight %}




