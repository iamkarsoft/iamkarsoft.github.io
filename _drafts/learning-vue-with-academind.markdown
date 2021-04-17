---
title: learning vue with academind
layout: post
date: 
categories: tag tag
---


### Working with Arguments

<pre class="language-js">
    <code class="language-js">
    <button @click="add(10)">add 10</button>
        methods: {
            add(num){
             this.counter = this.counter + num
            }
        },
    </code>
</pre>


### Using native event object

<pre class="language-">
    <code class="language-">
        <input type="text" name="" v-on:input="setName">

        methods: {
            setName(event){
            this.name = event.target.value
        },
    }
    </code>
</pre>

### Preventing  default with event modifer

- `<form @submit.prevent="submitForm" ></form>`
- `<button @click.right=""></button>` for right click
- `<button @click.left=""></button>` for left click
- `<input @keyup.enter="confirmInput">` for when enter key is pressed and released  
  
### Locking content with `v-once`   
  
### Two Way Binding with `v-model` 

### Advanced Reactivity with Computed Properties
  
Use computed properties for dynamic manipulation of properties. Name as you will name your data properties.
  
<pre class="language-js">
    <code class="language-js">
        computed: {
        fullname(){
            if(this.name === ''){
            return '';
            }

            return this.name + '' + 'Ramos'
            }
    }
    </code>
</pre>
  
### Working with watchers  

A watcher is a function to run when a dependency changes. They are similar to `computed properties`   
  
<pre class="language-js">
    <code class="language-js">
        // whenever name data changes, the 
        watch: {
        name(value){
            this.fullname =  value + '' + 'Ramos';
        }
    }
    </code>
</pre>


### Methods Vs Watchers Vs Computed properties
  
#### Methods    
 
- Use with event binding or data binding
- Event binding
  
#### Computed properties 
  
- Use with data binding
- use for data that depend on other data
  
  
####  Watch  
  
- Not to be used in templates
- run with code in reaction to changed data
- use for any non-data update you want to make
  
  
### Dynamic classes and style

  
#### Classes  
  
- `:class=['demo-class',{active-class: boxASelected}]` where `boxAselected` is a data property and `active-class` is applied when `boxAselected` is true
- `:class="boxAselected ? 'demo-class active-class':'demo-class'"`
- `:class="{demo: true, active: boxAselected}"`
  

#### Style  
  
`:style="{boderColor: boxAselected ? 'red': '#ccc'}"`

  
### Conditional Rendering and Outputting list of data

- `V-if` 
- `V-else-if`
- `V-else`
- `V-Show`

  
<pre class="language-js">
    <code class="language-js">

        <p v-if="goals.length ===0">No GOals</p>
        <ul v-else>
            <li>Goal</li>
        </ul>
    </code>
</pre>

### Looping with `V-for`  
  
  
<pre class="language-js">
    <code class="language-js">

        <ul>
            <li v-for="goal in goals">{{goal}}</li>
            <!-- pulling more info -->
            <li v-for="(goal, index) in goals">{{goal}} - {{index}}</li>

            <!-- looping through object -->
            <li v-for="(value,key,index) in {name: 'Max', age:31}">{{key}}: {{value}}</li>
        </ul>
    </code>
</pre>