---
title: The modern javascript course
layout: post
date: 
categories: course javascript
---

## Variables and Flow Control
  

### Stings and variables
  
<pre class="language-js">
    <code class="language-js">
        let city = 'Accra';
let country = 'Ghana';
let mylocation = city + ', ' + country;


console.log(mylocation);
    </code>
</pre>
  
### Numbers  
 
- division
- substraction
- addition
- modulo  

<pre class="language-js">
    <code class="language-js">
        let studentScore = 30;
let maxScore = 1000;
 
let scorePercentage = (studentScore / maxScore) * 100;

console.log(scorePercentage);
    </code>
</pre>
  
### Booleans and Operators
  
- True or false
- Less than
- greater than
- greater than or equal
- lesser than or equal

  
### Conditionals
  
- `if (){}`
- `if(){} else if(){} else{}`
  
<pre class="language-js">
    <code class="language-js">
        // if code block
        if(isFreezing) {
            console.log(true)
        }

        // if else if code block
        if(isAccountLocked){
            console.log('Account is locked')
        }else if(userRole==='admin'){
            console.log('welcome admin')
        }else{
            console.log('Welcome')
        }
    </code>
</pre>
  

### Logical Operators  
  
- `AND` or `&&` logical AND operator
- `OR` or `||` logical Or operator  
  
## Variable Scopes
  
-  `Global Scope` are everything defined outside the code blocks
-  `Local scope` are things define inside a code block
  

## Functions

`function - inpt(argument) , code, output` 
 

<pre class="language-js">
    <code class="language-js">
        let greetUser = function(){
        console.log('Welcome User!');
        }

        // calling function
        greetUser();


        // another example
        let convertFarhToCelsius = function(temp){
    let celsius = (temp - 32) * 5/9
  return celsius
}


convertFarhToCelsius(200);
    </code>
</pre>

  
### Undefined and Null

Undefined is used to represent the absence of a value. Null is assigned for clearing a value.
    
### Multiple values and default values  
  
<pre class="language-js">
    <code class="language-js">

        // default values
        let getScoreText = function (name= 'anonymous', score= 0){
            console.log(name)
            console.log(score)
        }

        getScoreText();
        getScoreText(undefined,99);
    </code>
</pre>

  
### Javascript Objects
  
1. object basics
2. object and functions
3. object references