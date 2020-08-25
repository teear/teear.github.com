---
layout: article
title: Working with JavaScript arrays

image:
  teaser: javascript-array.png
  feature: javascript-array.png
  credit: Pixabay #name of the person or site you want to credit
  creditlink: https://pixabay.com/ #url to their site or licensing
date: 2017-08-18 0:00:00 +0000
modified: 2020-08-25 0:00:00 +0000
---

Arrays in JavaScript are a special kind of object that inherits from the Array.prototype. Arrays are ordered non-typed dynamic collections of values.

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


Using `Array.of()`:

{% highlight javascript %}
let arr = Array.of("Joe", "Bob"); // ["Joe", "Bob"]
{% endhighlight %}

`Array.from()` creates arrays from array-like objects ([HTMLCollection](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCollection), [NodeList](https://developer.mozilla.org/en-US/docs/Web/API/NodeList), [Arguments object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments)) and
iterable objects (String, Array, TypedArray, Map and Set are built in iterables.).

{% highlight javascript %}
let s = new Set(['alfa', 'bravo']); 
Array.from(s); // ["alfa", "bravo"] 
{% endhighlight %}

Here we are creating a new array with only unique values

{% highlight javascript %}
let array = ["alfa", "bravo", "alfa", "charlie", "alfa", "delta"];
let arrayUnique = Array.from(new Set(array)); // ["alfa", "bravo", "charlie", "delta"]
{% endhighlight %}

JavaScript does not have associative arrays. If you are using a named index you are setting or accessing a variable associated with that array's object property collection, which is separate from the list of array elements. You cannot use array's traversal and mutation operations with these named properties.

{% highlight javascript %}
let array = [];
array["alfa"] = "aarne";
array[0] = "zero";

console.log(array); // ["zero", alfa: "aarne"]

array.forEach(element => console.log(element)); // "zero"

array.length; // 1
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

We can add elements to the end of the array with `push()`. Here we are
adding only one element but you can add as many as you wish by separating
the values with commas.

{% highlight javascript %}
array.push("echo"); // returns number of elements in the array
console.log(array); // ["bravo", "charlie", "delta", "echo"];
{% endhighlight %}

To add elements to the start of the array you use `unshift()`.

{% highlight javascript %}
array.unshift("alfa"); // returns number of elements in the array
console.log(array); // ["alfa", "bravo", "charlie", "delta", "echo"];
{% endhighlight %}

`pop()` is used to remove an element from the end of the array, it returns the removed element.

{% highlight javascript %}
array.pop(); // returns "echo"
console.log(array); // ["alfa", "bravo", "charlie", "delta"];
{% endhighlight %}

`shift()` is used to remove an element from the start of the array, it returns the removed element.

{% highlight javascript %}
array.shift(); // returns "alfa"
console.log(array); // ["bravo", "charlie", "delta"];
{% endhighlight %}

If you need to add, remove or replace elements in other indexes, you can use `splice()`.

{% highlight javascript %}
array.splice(1, 1); // removes 1 element at index 1 and returns it in an array
console.log(array); // ["bravo", "delta"];
{% endhighlight %}

{% highlight javascript %}
array.splice(1, 0, "charlie"); // inserts 1 element at index 1 and returns [] (empty array, as no elements were removed)
console.log(array); // ["bravo", "charlie", "delta"];
{% endhighlight %}

{% highlight javascript %}
array.splice(1, 1, "canada"); // replaces 1 element at index 1 and returns the removed element 
console.log(array); // ["bravo", "canada", "delta"];
{% endhighlight %}

The `delete` operator removes the contents of the element and leaves the element empty. If you wish to remove the element completely, you should use `splice()`.

{% highlight javascript %}
delete array[1]; // removes value at index 1 and returns true if successful
console.log(array); // ["bravo",,"delta"];
{% endhighlight %}

Making a copy of an array
-------------------------

Arrays are passed by referefence.

{% highlight javascript %}
let array = [1,2,3];
let array2 = array;

console.log(array, array2); // [1,2,3] [1,2,3]

array2[2] = "three";

console.log(array, array2); // [1,2,"three"] [1,2,"three"]
{% endhighlight %}

To make a copy of an array, you can use the following methods.

{% highlight javascript %}
let array = [1,2,3];
let arrayCopy = array.slice();
let arrayCopy2 = [].concat(array);
let arrayCopy3 = [...array];
let arrayCopy4 = Array.from(array);
{% endhighlight %}

If you now change the original array the copies are not affected.

Array properties
----------------

### length

The `length` property returns the the last index number of the array + 1.

{% highlight javascript %}
let array = ["alfa", "bravo", "charlie", "delta", "echo", "x-ray"];

console.log(array.length); // 6

array[array.length-1]; // "x-ray"

console.log(array[array.length-1]); // x-ray
{% endhighlight %}

Static array methods
--------------------

### Array.from()

`Array.from(arrayLike[, mapFn[, thisArg]])`

The `Array.from()` method creates a new shallow-copied `Array` instance from an array-like or iterable object.
The arguments for `Array.from()` are the array-like object, optionally a mapping function to use on the elements, and optionally a `this` value to use when executing the mapping function.  

{% highlight javascript %}
Array.from("alfa"); // ["a","l","f","a"]
Array.from([1,2,3,4,5], x => x * x); // [1,4,9,16,25]
{% endhighlight %}

{% highlight javascript %}
function log() {
  Array.from(arguments).forEach(function(argument) {
    console.log(argument);
  });
}

log(1,2,3); // 1 2 3
{% endhighlight %}

### Array.of()

`Array.of(element0[, element1[, ...[, elementN]]])`

The `Array.of()` method creates an array from a list of values. The
difference between `Array.of()` and the array contructor is that when
you pass a single number `Array.of()` creates an array with a single
element which is that number whereas the array contructor creates
an array with that many empty elements.

{% highlight javascript %}
new Array(2); // array with two empty elements [,]
Array.of(2); // array with one element (number two) [2]
{% endhighlight %}

{% highlight javascript %}
Array.of(1, 2, 3); // [1, 2, 3]
Array.of("alfa", "bravo", "charlie"); // ["alfa", "bravo", "charlie"]
{% endhighlight %}

### Array.isArray()

The `Array.isArray()` method checks if a value is an array and returns
`true` or `false`.

{% highlight javascript %}
var array = ["alfa", "bravo"];
var string = "alfa";

Array.isArray(array); // returns true
Array.isArray(string); // returns false

typeof array; // returns "object"
typeof string; // returns "string"

// The old way of checking
Object.prototype.toString.call(array); // returns "[object Array]"
{% endhighlight %}

Array prototype methods
-----------------------

### concat()

`array.concat([value1[, value2[, ...[, valueN]]]])`

The `concat()` method merges two or more arrays and returns the new merged array. It does not recurse into nested array arguments and it does not mutate the original array. If no arguments are passed `concat()` returns a shallow copy of the original array.

{% highlight javascript %}
var array = ["alfa", "bravo"];
var array2 = ["charlie", "delta"];
var array3 = ["echo", "foxtrot"];

var copy = array.concat();
console.log(copy); // ["alfa", "bravo"]

array.concat([1,[2]]); // ["alfa", "bravo", 1, [2]]

array.concat(array2); // ["alfa", "bravo", "charlie", "delta"]

array.concat(array2, array3); // ["alfa", "bravo", "charlie", "delta", "echo", "foxtrot"]

var array4 = array.concat([array2]); // ["alfa", "bravo", ["charlie", "delta"]]
array2.pop(); // "delta"
console.log(array2); // ["charlie"]
console.log(array4); // ["alfa", "bravo", ["charlie"]]

{% endhighlight %}

### copyWithin()

`copyWithin(target, [start[, end]])`

`copyWithin()` is used to shallowcopy values within an array. It is a mutator method that does not change the length of the array. Arguments are target (where to copy) and optionally start and end index (from where to copy). End index is not included in the copy. Return value is the modified array.

{% highlight javascript %}
let array = [1,2,3,4,5,6,7,8,9]; 

/* Copy index 6–8 to position starting from index 0 */
array.copyWithin(0,6,9); // [7, 8, 9, 4, 5, 6, 7, 8, 9] 
console.log(array); // [7, 8, 9, 4, 5, 6, 7, 8, 9]

/* Copy to position starting from second index from the end. As no start or end index is given copies from the start of the array. */
[1,2,3,4,5].copyWithin(-2); // [1,2,3,1,2]

/* Copy to position starting from index 2 */
[1,2,3,4,5].copyWithin(2); // [1,2,1,2,3]
{% endhighlight %}

### entries()

The `entries()` method returns a new Array Iterator object that contains the key/value pairs for each index in the array. The method does not take any arguments.

{% highlight javascript %}
const array = ["alfa", "bravo", "charlie", "delta", "echo", "foxtrot"];

let iterator = array.entries();

console.log(iterator.next().value); // [0, "alfa"]

console.log(iterator.next().value); // [1, "bravo"]

for (let item of iterator) {
  console.log(item);
}

/*
Output of for..of loop:
[2, "charlie"]
[3, "delta"]
[4, "echo"]
[5, "foxtrot"]
*/
{% endhighlight %}

### every() and some()

`every()` method takes a function that tests the elements in the array for a condition and returns `true` or `false` for each element. If the condition matches every element in the array or the array is empty `true` is returned. `some()` works in a similar way: `true` is returned if the condition matches at least one element in the array. For empty arrays `some()` returns `false`. The functions are not called on empty elements.

{% highlight javascript %}
let array = [1,2,,3];

array.every(x => x % 2 === 0); // false
array.some(x => x % 2 === 0); // true
array.every(x => typeof x === "number"); // true
{% endhighlight %}

Empty array

{% highlight javascript %}
let array = [];

array.every(x => x === 5); // true
array.some(x => x === 5); // false
{% endhighlight %}

To test if none of the elements match

{% highlight javascript %}
let array = [1,2,,3];

!array.some(x => x === 5); // true
{% endhighlight %}

### fill()

The `fill()` method fills an array or parts of an array with a given value. It is a mutator method. Arguments are the fill value, optional start index and also optional end index (the value is filled up to [not including] end index). Return value is the modified array.

`fill(value, [start[,end]])`

{% highlight javascript %}
var array = ["alfa", "bravo", "charlie", "delta", "echo", "foxtrot"];

array.fill("aarne", 3, 4);
console.log(array); // ["alfa", "bravo", "charlie", "aarne", "echo", "foxtrot"]

array.fill("aarne", 0, 2);
console.log(array); // ["aarne", "aarne", "charlie", "aarne", "echo", "foxtrot"]

array.fill("bertta");
console.log(array); // ["bertta", "bertta", "bertta", "bertta", "bertta", "bertta"]

array.fill("aarne", -3);
console.log(array); // ["bertta", "bertta", "bertta", "aarne", "aarne", "aarne"]
{% endhighlight %}

### find() and findIndex()

`find()` method returns the value of the first element in the array that matches the condition provided by the callback function. `findIndex()` works the same but instead of the value it returns the index of the element.

{% highlight javascript %}
let array = [1,2,3,4,5,6,7,8];

array.find(x => x > 5); // 6
array.findIndex(x => x > 5); // 5

array.find(x => x > 10); // undefined
array.findIndex(x => x > 10); // -1
{% endhighlight %}

### flat()

The `flat()` method flattens an array and returns a new array. If the array contains empty elements, those are removed. It does not mutate the original array. It takes one parameter which is the depth and if no parameter is given the default depth of 1 is used.

{% highlight javascript %}
const array = [1,,,2,[3,4],5,[6,7,[8,9]]];

array.flat(); // [1,2,3,4,5,6,7,[8,9]]
array.flat(2); // [1, 2, 3, 4, 5, 6, 7, 8, 9]
{% endhighlight %}

### flatMap()

The `flatMap()` method is identical to a `map()` followed by a `flat()` with a depth of 1.

{% highlight javascript %}
const array = ["Hello world", "Hei maailma"];

array.map(x => x.split(' ')); // [["Hello", "world"], ["Hei", "maailma"]]

array.flatMap(x => x.split(' ')); // ["Hello", "world", "Hei", "maailma"]
{% endhighlight %}

### forEach()

`arr.forEach(callback(currentValue [, index [, array]])[, thisArg])`

The `forEach()` method executes the provided function for each array element in ascending order. It is not invoked for index properties that have been deleted or are uninitialized. You can only break out of a `forEach()` loop by throwing an exception. The return value of `forEach()` is always `undefined`. `forEach()` does not mutate the original array, unless you do something inside the callback that mutates it.

{% highlight javascript %}
const array = ["alfa", "bravo", "charlie", "delta", "echo", "foxtrot"];

array.forEach((element, index, array) => console.log(element, index, array));

/*
Output of above:
"alfa", 0, ["alfa", "bravo", "charlie", "delta", "echo", "foxtrot"]
"bravo", 1, ["alfa", "bravo", "charlie", "delta", "echo", "foxtrot"]
"charlie", 2, ["alfa", "bravo", "charlie", "delta", "echo", "foxtrot"]
"delta", 3, ["alfa", "bravo", "charlie", "delta", "echo", "foxtrot"]
"echo", 4, ["alfa", "bravo", "charlie", "delta", "echo", "foxtrot"]
"foxtrot", 5, ["alfa", "bravo", "charlie", "delta", "echo", "foxtrot"]
*/
{% endhighlight %}

### includes()

`includes()` method is used to check if an array contains the given value. It only takes one argument which is the value that is checked.

{% highlight javascript %}
const array = [1,2,3,4,5,"six","seven"];

array.includes(1); // true
array.includes(10); // false

array.includes("six"); // true
array.includes("eight"); // false
{% endhighlight %}

### indexOf() and lastIndexOf()

`indexOf()` method returns the index of the first element in the array that
matches the given value. `lastIndexOf()` returns the index of the last
element that matches the given value. If no element matches `-1` is returned.


{% highlight javascript %}
const array = [1,12,33,12,55,66,12,8];

array.indexOf(12); // 1
array.lastIndexOf(12); // 6

array.indexOf(1000); // -1
array.lastIndexOf(1000); // -1
{% endhighlight %}

### join()

`join()` method joins all the elements in the array and returns the result as a string. It does not mutate the original array. If the element value is `undefined`, `null` or an empty array `[]` it is converted to an empty string.
`join()` takes one argument which is a string that separates the elements
in the returned value. The elements are separated with commas by default if no argument is given.

{% highlight javascript %}
const array = [1,2,3,4,5];

array.join(); // "1,2,3,4,5"
array.join(''); // "12345"
array.join('-'); // "1-2-3-4-5"
{% endhighlight %}

### keys()

The `keys()` method returns a new Array Iterator object that contains the keys for each index in the array. The method does not take any arguments. Keys for empty elements are also included.

{% highlight javascript %}
const array = ["alfa", "bravo", "charlie", "delta", "echo", "foxtrot"];

let iterator = array.keys();

console.log(iterator.next().value); // 0

console.log(iterator.next().value); // 1

for (let key of iterator) {
  console.log(key);
}

/*
Output of for..of loop:
2
3
4
5
*/
{% endhighlight %}

### map(), filter() and reduce()

#### map()

`arr.map(function callback(currentValue[, index[, array]])[, thisArg])`

The `map()` method takes a function that goes through each element in an array and returns these processed elements in another array. The function is not called for empty elements.

{% highlight javascript %}
let array = [1,2,,3];

let array2 = array.map(value => value+1); // [2,3,,4]
{% endhighlight %}

#### filter()

`array.filter(callback(element[, index[, array]])[, thisArg])`

The `filter()` method is used to filter elements from the array that match a certain criteria. It takes a predicate function as a callback which is run for each element in the array. The function should return `true` for elements which will be kept, `false` otherwise. It returns a new array that contains only the matching elements. It does not mutate the original array.

##### Filtering even numbers

{% highlight javascript %}
let array = [1,2,3,4,5,6,7,8,9,10];

let arrayEven = array.filter(value => value % 2 === 0); // [2,4,6,8,10]
{% endhighlight %}

##### Filtering unique values

{% highlight javascript %}
let array = ["alfa","bravo","alfa","charlie","alfa"];

let arrayUnique = array.filter((item, index, array) => {
 if (array.indexOf(item) === index) {
  return item;
 }
}); // ["alfa", "bravo", "charlie"]
{% endhighlight %}

#### reduce()

`array.reduce(callback(accumulator, currentValue[, index[, array]])[, initialValue])`

The `reduce()` method reduces the elements in an array into one value from left to right.

{% highlight javascript %}
let array = [1,2,3];

let value = array.reduce((accumulator, currentvalue) => accumulator + currentvalue.toString()); // "123" 
{% endhighlight %}

Filtering unique values with `reduce()`:

{% highlight javascript %}
let array = ["alfa", "bravo", "alfa", "charlie", "alfa", "delta"];

array.reduce((unique, item) => 
  unique.includes(item) ? unique : [...unique, item], []);
/*
Output of above: ["alfa", "bravo", "charlie", "delta"]
*/
{% endhighlight %}

#### reduceRight()

`array.reduceRight(callback(accumulator, currentValue[, index[, array]])[, initialValue])`

The `reduceRight()` method reduces the elements in an array into one value from right to left.

{% highlight javascript %}
let array = [1,2,3];

let value = array.reduceRight((accumulator, currentvalue) => accumulator + currentvalue.toString()); // "321" 
{% endhighlight %}

### push() and pop()

#### push()

The `push()` method is used to add one or more elements to the end of the array. Return value is the new length of the array.

{% highlight javascript %}
let array = ["alfa"];

array.push("bravo", "charlie"); // 3
console.log(array); // ["alfa", "bravo", "charlie"]

array.push("delta"); // 4
console.log(array); // ["alfa", "bravo", "charlie", "delta"]
{% endhighlight %}

#### pop()

The `pop()` method removes the last element from the array. It does not take any arguments. Return value is the removed element.

{% highlight javascript %}
let array = ["alfa", "bravo", "charlie", "delta"];

array.pop(); // "delta"
console.log(array); // ["alfa", "bravo", "charlie"]

array.pop(); // "charlie"
console.log(array); // ["alfa", "bravo"]
{% endhighlight %}

### reverse()

`reverse()` method reverses an array in place and returns a reference to the array. It does not take any arguments.

{% highlight javascript %}
let array = [1,2,3,4,5];

array.reverse(); // "5,4,3,2,1"
console.log(array); // "5,4,3,2,1"
{% endhighlight %}

If you do not wish to mutate the original array, you can create a shallow copy of the original with `slice()`.

{% highlight javascript %}
let array = [1,2,3,4,5];

array.slice().reverse(); // "5,4,3,2,1"
console.log(array); // "1,2,3,4,5"
{% endhighlight %}

### sort()

`sort()` method sorts an array in place and returns the sorted array. It takes an optional compare function as argument. If no compare function is given as argument, then elements are converted to and sorted as strings in alphabetical and ascending order by default.

#### Default sort order

{% highlight javascript %}
let array = [5,4,20,3,10];

array.sort(); // "10,20,3,4,5"
console.log(array); // "10,20,3,4,5"

array = ["alfa","november","bravo","uniform","foxtrot"];

array.sort(); // ["alfa", "bravo", "foxtrot", "november", "uniform"]
console.log(array); // ["alfa", "bravo", "foxtrot", "november", "uniform"]
{% endhighlight %}

#### Using a compare function

The number returned by the compare function determines the sort order.
Return values less than 0 sort the first argument before the second.
Return value of 0 keeps the order.
Return values larger than 0 sort the second argument before the first.

{% highlight javascript %}
let array = [5,4,20,3,10];

array.sort((a,b) => {
 if (a === b) return 0; // return value 0 keeps the order 
 if (a < b ) return -1; // -1 sorts a before b
 return 1; // 1 sorts b before a
}); // "3,4,5,10,20"

console.log(array); // "3,4,5,10,20"
{% endhighlight %}

#### Sorting strings by length

{% highlight javascript %}
let array = ["alfa","november","bravo","uniform","foxtrot"];

array.sort((a,b) => a.length-b.length); // ["alfa", "bravo", "uniform", "foxtrot", "november"]

array.sort((a,b) => b.length-a.length); // ["november", "foxtrot", "uniform", "bravo", "alfa"]

console.log(array); // ["november", "foxtrot", "uniform", "bravo", "alfa"]
{% endhighlight %}

### slice()

`slice([begin[, end])`

`slice()` method creates a shallow copy of a part of an array and returns the copy as a new array. It does not mutate the original array. It takes the begin and end index (end index is not included in the new array) as argument. If end index is omitted, `slice()` copies to the end of the array. A negative index can be used, indicating an offset from the end of the array.

{% highlight javascript %}
let array = [1,2,3,4,5];

var copy = array.slice(0,3); // [1,2,3]
console.log(array); // [1,2,3,4,5]

var copy2 = array.slice(1,4); // [2,3,4]
console.log(array); // [1,2,3,4,5]

var copy3 = array.slice(2); // [3,4,5]
console.log(array); // [1,2,3,4,5]

var copy4 = array.slice(-2); // [4,5]
console.log(array); // [1,2,3,4,5]

var copy5 = array.slice(-3); // [3,4,5]
console.log(array); // [1,2,3,4,5]

var copy6 = array.slice(); // [1,2,3,4,5]
console.log(array); // [1,2,3,4,5]
{% endhighlight %}

### splice()

`array.splice(start[, deleteCount[, item1[, item2[, ...]]]])`

`splice()` method is used to remove and replace elements in an array. It mutates the original array. First argument is the start index and the second argument is the number of elements to remove from the array (the default is all from the start index to the end of the array). Rest of the arguments are new values you want to add to the array. Return value is the removed elements in a new array or [0] if no elements were removed.

{% highlight javascript %}
let array = [1,2,3,4,5];

array.splice(1,1,'alfa'); // [2]
console.log(array); // [1,"alfa",3,4,5]

array.splice(2,0,'bravo'); // [0]
console.log(array); // [1,"alfa","bravo",3,4,5]

array.splice(0,0,0); // [0]
console.log(array); // [0,1,"alfa","bravo",3,4,5]

array.splice(0); // [0,1,"alfa","bravo",3,4,5]
console.log(array); // []
{% endhighlight %}

### toLocaleString()

`array.toLocaleString([locales[, options]])`

`toLocaleString()` returns a string representing the elements of the array.
the elements are converted to strings using their `tolocalestring` methods and these strings are separated by a locale-specific string (such as a comma “,”). If locale is not defined then the default system locale is used. `tolocalestring()` does not mutate the original array.

{% highlight javascript %}
var prices = ['7 euros', 500, 8123, 12]; 

prices.toLocaleString('fi', { style: 'currency', currency: 'EUR' });
/* Output of above: "7 euros,500,00 €,8 123,00 €,12,00 €" */

prices.toLocaleString('en-US', { style: 'currency', currency: 'USD' });
/* Output of above: "7 euros,$500.00,$8,123.00,$12.00" */
{% endhighlight %}

{% highlight javascript %}
var dates = [new Date('2019/12/11'), new Date('28 March 1985')];

dates.toLocaleString('fi');
/* Output of above: "11.12.2019 klo 0.00.00,28.3.1985 klo 0.00.00" */ 

dates.toLocaleString('sv', { dateStyle: 'long', timeStyle: 'long' });
/* Output of above: "11 december 2019 00:00:00 EET,28 mars 1985 00:00:00 EET" */ 
{% endhighlight %}

### toString()

`toString()` returns a string representation of the array where the elements of the array are separated with commas.
It does not mutate the original array. `toString()` does not take any arguments.
{% highlight javascript %}
let array = [1,2,3,4,5,"six"];
let array2 = [undefined, null, [], {}, function(){ return 'Hello'; }];
let array3 = [1,,,2,[3,4],5,[6,7,[8,9]]];

array.toString(); // "1,2,3,4,5,six"
array2.toString(); // ",,,[object Object], function(){ return 'Hello'; }"
array3.toString(); // "1,,,2,3,4,5,6,7,8,9"
{% endhighlight %}

### unshift() and shift()

#### unshift()

The `unshift()` method is used to add one or more elements to the start of the array. Return value is the new length of the array.

{% highlight javascript %}
let array = ["delta"];

array.unshift("bravo", "charlie"); // 3
console.log(array); // ["bravo", "charlie", "delta"]

array.unshift("alfa"); // 4
console.log(array); // ["alfa", "bravo", "charlie", "delta"]
{% endhighlight %}

#### shift()

The `shift()` method removes the first element from the array. It does not take any arguments. Return value is the removed element.

{% highlight javascript %}
let array = ["alfa", "bravo", "charlie", "delta"];

array.shift(); // "alfa"
console.log(array); // ["bravo", "charlie", "delta"]

array.shift(); // "bravo"
console.log(array); // ["charlie", "delta"]
{% endhighlight %}

### values()

The `values()` method returns a new Array Iterator object that contains the values for each index in the array. The method does not take any arguments.

{% highlight javascript %}
const array = ["alfa", "bravo", "charlie", "delta", "echo", "foxtrot"];

let iterator = array.values();

console.log(iterator.next().value); // alfa

console.log(iterator.next().value); // bravo

for (let value of iterator) {
  console.log(value);
}

/*
Output of for..of loop:
charlie
delta
echo
foxtrot
*/
{% endhighlight %}

Further reading
---------------

[Array at MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
