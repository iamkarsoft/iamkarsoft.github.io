---
title: The complete web developer ztm
layout: post
date: 
categories: course udemy
---

## Javascript  Basics 
  
### Javascript Types
  
1. Number
2. String
3. Boolean
4. Undefined
5. Null
6. Symbol
7. Object
  
### Javascript variables
  
1. Var
2. Let
3. Const
  
  
### Javascript Conditionals
  
1. `!==`
2. `===`
3. `>=`
4. `<=`
5. `<`
6. `>`
  
  
### Control Flow
  
1. **if**
2. **else**
3. **else if**
4. **ternary operator**
5. **switch**

### Logical Operators
  
1. `&&` **And**
2. `||` **OR**
3. `!` **Not**

  
### Javascript Functions
  
- Function Arguments
- executing a function
  
#### Two ways of creating a function
  
**Function Declaration**  
  
```js

function sayHello(){
	console.log("hello");
}

sayHello();

```
  

**Function Expression**  

```js
var sayBye = function(){
	console.log("Bye");
}

sayBye();
```
  
### Javascript Arrays (data structure)
  

`var animals = ["tiger","cat","bear"]` and accessing it ` animals[0]`
  

#### Array methods
 
`var newAnimals= animals.concat(["dog"])` . [w3c array reference](https://www.w3schools.com/jsref/jsref_obj_array.asp)
  
### Javascript Objects (data structure and type)

```js
var user = {
	name: "John",
	age: 34,
	hobby: "Soccer",
	isMarried: false,
}

// grabbing properties
user.name;
user.isMarried;

// adding properties value
user.favoriteFood = "Lasagne";
user.isMarried = true;

```
  

  
### Javascript Terminology
  
- **function declaration**
- **function expressions** is assigning a function to a variable
- **expression** is something that produces a value
- **invoking** or **calling** a function
- **assigning**
- **function** vrs **methods** methods are functions in objects
  

### Loops
  
#### For loops
  


```
var todos = [
	"clean room",
	"brush teeth"
];

for(var i=0; i < todos.length; i++){
	console.log(todos[i]);
}
```
  
  
#### While Loop
  
```
var counterOne = 0;

while(counterOne < 10){
	console.log(counterOne);
	counterOne++;
}
```
  
#### Do while Loop
  
```
var counterOne = 10;
do{
 console.log(counterTwo);
	counterTwo--;
}
while(counterTwo > 0)
```
  
  
#### Foreach

```
var todos = [
	"clean room",
	"brush teeth",
];
function logTodos(todo, i){
	console.log(todo, i);
	}

todos.forEach(logTodos);

```
  

## Dom Manipulation

### Dom Selectors
  
- `document.getElementByTagName`
- `document.getElementByClassName("second")`
- `document.getElementById("myId")`
- `document.querySelector("h1")`
- `document.querySelectorAll("li")`
- `.parentElement` gets parent of an element
- `.children` gets children

### Attributes

- **get attribute** `document.querySelector("li").getAttribute("random")`
- **set attribute** `document.querySelector("li").setAttribute("random","1000")`


#### Chaning Styles

```
//syntax
style.{property}

className 
ClassList.add(remove,toggle)


//
var h1 = document.querySelector("h1");

h1.className = "Cool title";
h1.classList.add="border";

```
  

## Dom Events
  
- **keyboard events** `.addEventListener('keypress',function(e){})`
- **mouseevents** `.addEventListener('click',function(){})`
- **input** `.addEventListener('input',function(){})`
  

Use with `.addEventListener('eventtype',function(){})`

  
## Callback Functions

In the previous video you saw something interesting:

Event listener syntax :   

```
button.addEventListener("click", addListAfterClick);
input.addEventListener("keypress", addListAfterKeypress);
```
  

You didn't see the function being called like this as you may have expected: 
  
```  
button.addEventListener("click", addListAfterClick());
input.addEventListener("keypress", addListAfterKeypress(event));
```
  


This is something called a callback function. When that line of javascript runs, we don't want the addListAfterClick function to run because we are just adding the event listener now to wait for click or keypress. We want to let it know though that we want this action to happen when a click happens. So the function now automatically gets run (gets added the ()) every time the click happens. So we are passing a reference to the function without running it.

  
## Scope
 
- `root scope`  
- `function scope` only available in function
 

## Advanced control flow

  
### Ternary operator
  

`condition  ? expression 1 : expression 2`;
  
```
var answer = isValid(true) ? "You may enter" : "Access Denied";
```


### Switch Statement

```js
var whatHappens
switch (direction){
	case "forward":
		whatHappens = "good for you";
		break;
		default:
		console.log("far away");
	}
	return whatHappens;

```

### ES6 and Javascript


#### Declaring Variables

`let` and `const`

  
#### Object properties

```
const a  = "Simon";
const b =true;
const c = 100;
const obj = {a,b,c}
```
  
#### Template strings
  
```
const name = "Ramos";
const greeting =  `hi ${name} !`
```


#### Default Arguments

```
function greet(name='',age=10){

}

```

  
## Advanced functions

- `closures`  a closure is a function that will run, will execute and will stop. but will always remember that there are references to variables and the children of that functions will always have access to their parent
- `currying` is running a function that has multiple functions that it runs one at a time
- `compose` is putting 2 functions together that returns a 3rd function
  

## Advanced Arrays
basic looping with foreach  

```js
const array = [1,2,0,16];

const double = [];

const newArray = array.forEach((num)=>{
	double.push(num*2);
})
```
  

### Map
  for looping , this is the best method.

```js
const mapArray = array.map((num)=>{
	return num * 2;
})
```
  

### Filter  
  
filter is used to filter get array values based on the criteria  

```js
const filterArray = array.filter(num =>{
	return 1 > 5
	})
```

### Reduce

it can be used to filter and map

```
const reduceArray = array.reduce((accumulator,num)=>{
	return accumulator + num;
	},0) // the accumulator is 0
```

  
## Advanced Objects

  
### Reference Type
  they are reference types meaning they are created by the programmer. However primitive types are created by javascript.

### Context
context vrs scope
  

### Instantiation

making multiple copies of an object  
  

```
class Player{
	constructor(name, type) {
		this.name = name;
		this.type = type;
	}

	introduce(){
		console.log(`Hi I am ${this.name}`);
	}
}
```

### Cloning an object

```
let object = {a:'a',b:'b',c:{deep:'try and copy me'}};
let clone = Object.assign({},obj); // or
let clone2 = {...obj};

// deep cloning
let superClone = JSON.parse(JSON.stringify(obj))

```

## Type Coersion
  
## ES7


**Includes**
  
```
'Helloooo'.includes('0');

const pets = ['cat','dog','bat'];

pets.includes('dog');
```
  
**Exponential operater**
  
```
const square = (x)=>**2;
```
  
## ES8
  
**String Padding with `padStart()` and  `padEnd()` padding at the start or end

```
'Turtle'.padStart(10);  //gives a total of 10 spaces before string
'Turtle'.padEnd(10);  //gives a total of 10 spaces after string
```
  
**`Object.vales` and `Object.entries`**

```
let obj = {
	username0: 'santa',
	username1: 'king',
}

Object.values(obj).forEach(value=>{
	console.log(value)
	})

Object.entries(obj).forEach(value=>{
	console.log(value)
	})

```
  

## ES10

used to remove nesting from arrays

**`flat()`**  
   

```
const array = [1,[2,3],[4,5]];
array.flat()
array.flat(2) ;// the depth of flattening array
array.flat()
```

**`flatMap()`**  
  

**`trimaStart()` and `trimEnd()`**
  
use to remove blank spaces at the beginning `userEmail.trimStart()` or `userEmail.trimEnd()`

  
**formEntries**
  
turns array to an object.

```
userProfiles = [
		['commanderTom',23],
		['commanderJim',50],
	];

Object.fromEntries(userProfiles)
```
  
  
**try and catch block**
  
```
try{
	code to try
} catch{
	the error to run here;
}
```
  

## Advanced loops

**`for off` and `for in`**
  

<pre class="language-js">
	<code class="language-js">
	const basket = ['apples','oranges','grapes'];
	const fruity = {
	apples: 5,
	oranges: 10,
	grapes: 1000
}
	// for off
	// iterating - (arrays, strings)
	for(item of basket){
		console.log(item)
	}

	//for in
	//works with objects
	// enumerating
	for(item in fruity){
		console.log(item)
	}

	</code>
</pre>

## ES2020

**BigInt**
  
It's a new type in javascript nb: max_save_integer    

**Nullish Coalescing Operator `??`**
   
can be used in place of `Or`

<pre class="language-js">
	<code class="language-js">
		let will_pokemon = {
	pikach:{
		species: 'Mouse Pokemon',
		height: 0.4,
		power: ''
	}
}

let weight = will_pokemon?.pikachu?.weight?.power ?? 'no power' // checks if power is null or undefined

	</code>
</pre>

**Optional chaining Operator `?.`** 
  

```
let will_pokemon = {
	pikach:{
		species: 'Mouse Pokemon',
		height: 0.4,
	}
}

let weight = will_pokemon?.pikachu?.weight // checks if pikachu or weight exist
```
  
## How javascript works

 - allocate memory
 - parse and execute scripts
 - v8 reads  javascript and changes to executable commands
 	+ **memory heap** keeps track of your variables
 		* **memory leak**
 	+ **call stack**
 - single threaded means it can only do one thing at a time
 	+ **deadlocks**
 	+ **synchronous** means running one thing at a time and one after the other
 	+ **recursion** means a function that calls itself.
 - **asynchronous**  means you can make javscript non-blocking by using callback functions which run in the background.
  
## Modules
  
  - **Modules**
  - **browserify**
  - **iife** immediately invoked functional exection
  - **script tags**
  - **inline scripts**
  

`import` and `export` with es6.

```js
export const add = (a,b) => a + b;
//or
export default function add(){
	return a + b
}

import {add} from './add';
// or
import add from './add'
```

## Http / Https


## JSON

## JSON vs Form Data


## Promises


## Async Await


Async Await is an advanced feature of Javascript that is better learned after you have an understanding of asynchronous javascript. We cover these topics in an upcoming video in this section titled How Javascript Works as well as in the HTTP + AJAX + JSON + Asynchronous Javascript section. The Async Await video is there since you will understand it better once you are in that part of the course. If you would like, you can jump there and watch the video now, but I recommend the video flow in the order that I have set up the course!

There is also the new ES9 (ES2018) features that have come out which require a bit more asynchronous knowledge on our part so these new feature videos will be introduced in that same section as well.  


## Async



## ES2020


## React  

**Install create react app globally**  

`npm install -g create-react-app`  

**Create a project with create react app**  
  
`create-react-app projectname` or `npx create-react-app app-name`

  
### Creating React Component  
  
**Creating first Component**  
  
```
\\ src/Hello.js
import React, {Component} from 'react';

class Hello extends Component{
	render(){
		return (
		<div>
		 <h1>Hello World </h1>
			<h3> Welcome To React </h3>

		</div>
			);
	}
}

export default Hello;
```
  
**Using component in index file**
  
```
 import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
// import App from './App';
import Hello from './Hello';
import reportWebVitals from './reportWebVitals';

ReactDOM.render(
  <React.StrictMode>
  	<Hello />
  </React.StrictMode>,
  document.getElementById('root')
);

// If you want to start measuring performance in your app, pass a function
// to log results (for example: reportWebVitals(console.log))
// or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals
reportWebVitals();

```

**Adding Props to component**  
  
 ```
 <Hello greeting ={'Hello React Ninja'} />
 ```
 


```
 \\ src/Hello.js
import React, {Component} from 'react';

class Hello extends Component{
	render(){
		return (
		<div>
		 <h1>Hello World </h1>
			<h3> Welcome To React </h3>
			<p>{this.props.greeting}</p>
		</div>
			);
	}
}
```
  
### Lifecycle Hooks


### Json  

```
const user= {
	firstName: 'John',
	lastName: 'Doe'
};

```


`JSON.stringify(user);` to send json file to server and use `JSON.parse(user)` to read json file.  
  
### AJAX

<pre class="language-js">
	<code class="language-js">
		$.getJSON('/url',function(data){

	})

	// newer

	fetch('my/url').then(response=>{
	console.log(response)
	})
	</code>
</pre>
  
 ### APIs

   