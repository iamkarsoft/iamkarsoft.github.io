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