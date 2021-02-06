---
title: web developer bootcamp course 2020
layout: post
date: 2020-12-01
categories: javascript course
---

# Web Developer Bootcamp course by colt steel



##  Html Tags

- Headers (`<h1></h1>-<h6></h6>`)
- paragraphs`<p></p>`



###  Html Skeleton

```
<!DOCTYPE html>
<html>
<head>
<title> My Page Title</title>
</head>
<body>
</html>
```

###  Html: Lists


####   Unordered list</h4>

```
<ul>
	<li>this is unordered</li>
</ul>
```

####  Ordered list</h4>


```
<ol>
	<li>this is ordered</li>
	<li>it puts numbers in front</li>
</ol>
```


###  Html: Anchor link
  
```
<a href="http://google.com">google.com</a> //link
<a href="mailto:example@example.com">example.com</a> //mail
<a href="tel:00111111111">0011111111</a> //telephone
```


###  Html: Image Elements

```
<img src="imagename.extension" alt="an image on my pc">
```

###  Html: Html Entities


###  Html: Semantic Html

semantic markup is related markup. 

- `<main></main>` main content of the page and not repeated
- `<nav></nav>` anything that provides navigation links
- `<section></section>` a standalone section while a div is just a container
- `<article></article>` a self contained composition.
- `<aside></aside>` for something like a sidebar
- `<header></header>` for introductory content
- `<footer></footer>` usually the last group of content on a page
- `<figure> <figcaption></figcaption></figure>` used for illustration, diagram, image with some captions



### Html: Forms & Tables


#### Tables

- `<table></table>` the tag for table
- `<td></td>` table data represents a cell
- `<tr></tr>` table row 
- `<th></th>` table head
- `<thead></thead>` to wrap all table headers
- `<tbody></tbody>` to specify all table body for cells data
- `<tfooter></tfooter>` to group table footer
  


```html
<table>
<td></td>
<tr></tr>
<th></th>
<thead></thead>
<tbody></tbody>
<tfoot></tfoot>
<colgroup></colgroup>
<caption></caption>
</table>

<!-- example -->

<table>
<thead>
<tr>
<th>Header 1</th>
<th>Header 2</th>
<th>Header3</th>
</tr>
</thead>
<tbody>
<tr>
	<td rowspan="2">cell 1</td>
	<td colspan="2">cell 1</td>
	<td>cell 1</td>
</tr>
<tr>
	<td>cell 2</td>
	<td>cell 2</td>
	<td>cell 2</td>
</tr>
<tr>
	<td>cell 3</td>
	<td>cell 3</td>
	<td>cell 3</td>
</tr>
</tbody>
</table>
```


###  Forms
  

- `<form></form>` form element for containing fields and everything related to the form 

- `<input type="">` versatile element

- `<label></label>` to give information or describe a field
- `<button></button>` buttons with type submit or button
- `name` attributes place an important role when data is being submitted from a form. it allows us to identify each data by their name
<!-- - `<input type="checkbox" checked> <label>Scales</label>` checkbox
- `<input type="radio" name="dessert" checked> <label>Scales</label>` radio buttons
- `<select><option value="shirt">shirt</option></select>` select with option element
- `<input type="range">` use to select a range
- `<input type="number">` use for numbers 
- `<textarea></textarea>` textarea for more text -->
 



```html
<form action="">
	<label for="cheese">Do you like cheese?</label>

	<input type="text"  name="cheese" placeholder="username">
	<input type="password">
	<input type="checkbox">
	<input type="radio">
	<input type="color">
	<input type="month">
	<input type="number">
	<input type="range">

<!-- label with input non conventional -->
	
	<label>
	Enter a Number:
	<input type="number" placeholder="enter a number">
	</label>

<!--  /label end -->
	<!-- range example -->


	<input type="range" name="percentage" min="0" max="100" value="90" step="10">
<!-- /end range examle -->
	<button type="submit">submit</button>
</form>
```
#### Form validations</h4>

- `required` makes field a required field that needs user input
- `minlength maxlength` min max puts a limit on the minimum and maximum characters required in a text input field
- `min max` min max puts a limit on the minimum and maximum numbers required in a number input field
- `pattern` used for regular expressions (regex)

```html
<form>
<label>Firstname</label>
<!-- required example -->
<input type="text" required name="first">
 

<!-- min max example -->
<input type="text" minlength="5" maxlength="1000" name="">
<input type="number" min="5" max="1000" name="">
</form>
```


## CSS Selectors

```css
/* universal selector */
*{
background: blue;
}


/* element selector */
button{
	width: 300px;
}

h1,h2{
	color: magenta;
}

/* id selector */

#wrapper{
	width: 100vw;
	height: 100vh;
}


#login{
	color: green;
}

/* class selector */

.tag{
	color: blue;
}

/* descendant selector */

ul a{
	text-decoration: none
}

/* Adjacent selector
* any paragraph that comes after h1
*/

h1 + p{
	color: red;
}

/* direct children */

div > li {
	list-style: none;
}

/* attribute selector */

input[type="password"]{
	border: 2px solid blue;
}

/* pseudo classes */

// when something is hovered on
:hover{}

// something is clicked, or active
:active{}

//checkboxes or radio buttons

:checked{}

//n is the number
//2n is every 2 
.nth-of-type(n or 2n){

}

/* pseudo elements */

::after{}

::before{}

::first-letter{}

::first-line{}
```


### Css: The cascadate

The order of your styles matters. the last style will override the ones at the top.
  


### Css: Specificity


When it comes to specificity, the golden rule is ` ID > Class > Element`


### Css: Inheritance

```
// picks color of the closest paragraph
p{
	color: inherit
}
```


### Css: The box model

Everything has 4 properties
<ul>
	<li>content box (width and height)</li>
	<li>Padding</li>
	<li>Border ( border and border-radius) </li>
	<li>Margin</li>
</ul>


## Css: Css Units

 - Percentages (10%)
 	- used for width and height

 - Rems (2rem) changes unless root size changes 
 - Em (10em)


## Javascript Properties and methods

### Trim()
<br>
<pre>
	<code>value.trim()</code>
</pre>

### indexOf

<p class="mt-2">Is used to search for the matching value contained </p>

<pre>
	<code>
		"haha that is so funny!".indexOf('u')
	</code>
</pre>


### Slice()

<p class="mt-2">Slice is used to extract a portion of a string</p>

<pre>
	<code>
		"I love footbal".slice(5)
		"i know what you doing".slice(3,6) //start point and end point
	</code>
</pre>

### replace()

<p class="mt-2">Used to replace a particular string with another. It takes 2 arguments. the first being what we want to replace, the 2nd being what is used to replace.</p>

<pre>
	<code>
		"haha that is so funny!".replace('haha', 'lolol')
	</code>
</pre>


## Template literals

This is used to replace double quotes

<pre>
	<code>
		`Hello ${variable}`
	</code>
</pre>

## Math Objects

<ul class="mt-5">
	<li>`Math.floor` rounds below</li>
	<li>`Math.ceil` rounds above</li>
	<li>`Math.random()`</li>
</ul>

## Decision making
  

 - Comparison Operators
 - Equality & Inequality Operators
 - Logical Operators


## Conditionals
`if` `else if` `else` 


## Arrays
  
 Array are ordered collections of values.

### Creating Arrays
  
 `let lottoNumbers = [1,2,34]`  


### Array Methods
  
 - array.push() add to the end of array  
 - array.pop() remves item at the end
 - array.shift() removes beginning item of an array
 - array.unshift() add item at the beginning of an array
 - array.concat() i.e `cats.concat(dogs)`
 - array.includes() : checks if array inclue a value i.e `cats.includes('blue')` 
 - array.indexOf(): i.e `cats.indexOf('kitten')` 
 - array.reverse()  it reverses an array i.e `cats.reverse()`
 - array.slice() . makes a copy of an array and has a beginning and end point i.e `cats.slice(3) or cats.slice(2,5)` it includes the start point but not the ending array index.
 - array.splice()  use to modify and replace the existing array. needs to specify start point, and how many things to delete before adding the item i.e `cats.splice(5,1) or cats.splice(1,0,'junior')`
 - array.sort()
  
### Multi-dimensional Array

```js
const gameBoard=[  
					['x','o','x'],
					['o',null,'x']
				];

// getting value
gameBoard[1][1]
```
  
## Javascript Objects
  
 - Objects are collections of properties
 - Properties are a key-value pair
 - We use custom keys to access data when it comes to objects
 

### Creating object

**P.S** every key is turned into a string.  


```js
 const product = {
 			name: "Gummy Bears",
 			inStock: true,
 			price: 1.99,
 			flavors: ["vanilla","strawberry"]
		 }
```
  

### Accessing object data

 - [1] `product["name"]`
 - [2] `product.name`  
  

### Modifying Objects
  
`product.inStock = false` or `product["price"] =2.99`


  
### Nesting Arrays & Objects
  

## Loops


