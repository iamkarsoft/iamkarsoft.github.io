---
title: web developer bootcamp course 2020
layout: post
date: 2020-12-01
categories: javascript course
---

# Web Developer Bootcamp course by colt steel



<h2 class="text-3xl font-bold mt-10"> Html Tags</h2>

- Headers (`<h1></h1>-<h6></h6>`)
- paragraphs`<p></p>`



<h3 class="text-2xl font-bold mt-10"> Html Skeleton</h3>

```
<!DOCTYPE html>
<html>
<head>
<title> My Page Title</title>
</head>
<body>
</html>
```

<h3 class="text-2xl font-bold mt-10"> Html: Lists</h3>


<h4 class="text-xl font-bold mt-10">  Unordered list</h4>

```
<ul>
	<li>this is unordered</li>
</ul>
```

<h4 class="text-xl font-bold mt-10"> Ordered list</h4>


```
<ol>
	<li>this is ordered</li>
	<li>it puts numbers in front</li>
</ol>
```


<h3 class="text-3xl font-bold mt-10"> Html: Anchor link</h3>
  
```
<a href="http://google.com">google.com</a> //link
<a href="mailto:example@example.com">example.com</a> //mail
<a href="tel:00111111111">0011111111</a> //telephone
```


<h3 class="text-xl font-bold mt-10"> Html: Image Elements</h3>

```
<img src="imagename.extension" alt="an image on my pc">
```

<h3 class="text-xl font-bold mt-10"> Html: Html Entities</h3>


<h3 class="text-xl font-bold mt-10"> Html: Semantic Html</h3>

semantic markup is related markup. 

- `<main></main>` main content of the page and not repeated
- `<nav></nav>` anything that provides navigation links
- `<section></section>` a standalone section while a div is just a container
- `<article></article>` a self contained composition.
- `<aside></aside>` for something like a sidebar
- `<header></header>` for introductory content
- `<footer></footer>` usually the last group of content on a page
- `<figure> <figcaption></figcaption></figure>` used for illustration, diagram, image with some captions



<h3 class="text-2xl font-bold mt-10">Html: Forms & Tables</h3>


<h4 class="text-xl font-bold mt-10">Tables</h4>

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


<h3 class="text-2xl font-bold mt-10"> Forms</h3>

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
<h4 class="text-xl font-bold mt-10">Form validations</h4>

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


<h2 class="font-bold text-3xl ">CSS Selectors</h2>

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


<h3 class="text-2xl font-bold mt-10">Css: The cascadate</h3>

The order of your styles matters. the last style will override the ones at the top.
  


<h3 class="text-2xl font-bold mt-10">Css: Specificity</h3>


When it comes to specificity, the golden rule is ` ID > Class > Element`


<h3 class="text-2xl font-bold mt-10">Css: Inheritance</h3>

```
// picks color of the closest paragraph
p{
	color: inherit
}
```


<h3 class="text-2xl font-bold mt-10">Css: The box model</h3>

Everything has 4 properties
<ul>
	<li>content box (width and height)</li>
	<li>Padding</li>
	<li>Border ( border and border-radius) </li>
	<li>Margin</li>
</ul>


<h2 class="text-3xl font-bold mt-10">Css: Css Units</h2>

 - Percentages (10%)
 	- used for width and height

 - Rems (2rem) changes unless root size changes 
 - Em (10em)
