---
title: Css transitions and transforms
layout: post
date: 
categories: css animations
---


<h2 class="text-3xl font-extrabold my-10">Transition Duration</h2>
<br>
To transition an element you need a `start value ` and an `end value`.
Transitions are usually triggered when a few states change.
<br>

- hovered
- focused
- active 
- targeted

<br>

```css

.button {
    transition-duration: .4s;
    transition-property: background; //all
}

.button:hover {
    background: #d36a62;

}

.button:active {
    background: #a33830;
}

.absolute-1 {
    top: 0;
    color: white;
    opacity: 0;
    cursor: pointer;
    background: #e9e9e9;
    height: 300px;
    transition-duration: .5s;
    transition-property: opacity;
    transition-delay: .2s;
    transition-timing-function: ease-out; // ease-in-out, ease-out,linear
}

.absolute-1:hover {
    opacity: 1;
}


```


<h2 class="font-bold text-3xl">Css Transforms</h2>
<br>
<h3 class="font-bold text-2xl">Rotate</h3>
<br>
```css
img{
    transform: rotate(70deg);
}
```
<br>
<h3 class="font-bold text-2xl">Scale</h3>

Increase or Decrease style horizontalyand verticaly on item

```css
img:hover{
    transform: scale(1);// 2 = twice as large or (X,Y) x = width, y is height
}
```

<br>
<h3 class="font-bold text-2xl">Skew</h3>

```css
img:hover{
    transform: skew(-10deg); // skewX(-10deg); skewY(-10deg)
}
```


<br>
<h3 class="font-bold text-2xl">Transform origin</h3>

Transform origin determine the area from which the transform starts from. the default is `transform-origin: 50% 50%`.  
  



```css

img:hover{
    transform-origin: 50% 50%; // 0 0 means top left, bottom right , 
}

```
<br>
<h3 class="font-bold text-2xl">Translation</h3>

Translation is the process of moving something from 1 point to another.

<br>
```css
img:hover{
    transform: translateX(150px); // translateY(150px)
}
```

<br>
<h3 class="font-bold text-2xl">Cubic bezier</h3>

this transform property allows you to set how fast your property transitions. you provide a start and end .

```css
//cubic-bezier(x1,y1,x2,y2)

img:hover{
    transition-timing-function: cubic-bezier(.7,-0.39,.31,1.38);
}
```


<br>
<h3 class="font-bold text-2xl">Animating transform</h3>

```css
img{
    transition: transform .5s;
}


img:hover{
    transform: rotate(360deg); // 1 turn
}
```

<br>
<h2 class="font-bold text-3xl">3D effect in css</h2>

<br>
<h3 class="font-bold text-2xl">Perspective</h3>
<br>

```css

.content{
    perspective: 400px;
}

.photo{
    transform: rotateX(-35deg)
}
```

<br>
<h3 class="font-bold text-2xl">3D transform and transition</h3>
<br>

```css
.content{
    perspective: 400px;
}

.photo{
    transform: rotateX(-35deg);
    transition: transform 1s ease-out;
}

.side-a,.side-b{
    backface-visibility: hidden;
}

.sideb-b{
    transform: rotateY(18deg);
}
```
