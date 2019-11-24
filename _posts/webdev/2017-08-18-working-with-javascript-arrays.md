---
layout: article
title: Working with JavaScript arrays

image:
  teaser: javascript-array.png
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

map(), filter() and reduce()
----------------------------

The map() method takes a function that goes through each item in an array and returns these processed items in another array. The function is not called for empty elements.

{% highlight javascript %}
let array = [1,2,,3];

let array2 = array.map(value => value+1); // [2,3,,4]
{% endhighlight %}

The filter() method is used to filter items from the array that match a certain criteria. It returns a new array that contains only the matching items.

{% highlight javascript %}
let array = [1,2,3,4,5,6,7,8,9,10];

let array2 = array.filter(value => value % 2 === 0); // [2,4,6,8,10]
{% endhighlight %}

The reduce() method reduces the items in an array into one value from left to right.

{% highlight javascript %}
let array = [1,2,3];

let value = array.reduce((accumulator, currentvalue) => accumulator + currentvalue.toString()); // "123" 
{% endhighlight %}


The reduceRight() method reduces the items in an array into one value from right to left.

{% highlight javascript %}
let array = [1,2,3];

let value = array.reduceRight((accumulator, currentvalue) => accumulator + currentvalue.toString()); // "321" 
{% endhighlight %}


every() and some()
------------------

every() method takes a function that tests an item in an array for a condition and returns true or false. If the condition matches every item in the array or the array is empty true is returned. some() works in a similar way: true is returned if the condition matches at least one element in the array. For empty arrays some() returns false. The functions are not called on empty elements.

{% highlight javascript %}
let array = [1,2,,3];

array.every(x => x % 2 === 0) // false
array.some(x => x % 2 === 0) // true
array.every(x => typeof x === "number") // true
{% endhighlight %}

Empty array

{% highlight javascript %}
let array = [];

array.every(x => x === 5) // true
array.some(x => x === 5) // false
{% endhighlight %}

To test if none of the elements match

{% highlight javascript %}
let array = [1,2,,3];

!array.some(x => x === 5) // true
{% endhighlight %}

