---
title: up and running with tailwind css
layout: post
date: 
categories: tag tag
---


## Tailwind Cdn
  
`<link href="https://unpkg.com/tailwindcss@^2/dist/tailwind.min.css" rel="stylesheet">`

## Tailwind with Tailwindcss CLI
  
- create `tailwind.css`
  
```
@tailwind base;
@tailwind components;
@tailwind utilities;

```
  
- Now run the tailwind cli to generate your css file `npx tailwindcss-cli build tailwind.css -o css/tailwind.css` and where `-o css/tailwind.css` is the output destination  
  
## Setting up build tool
  

**Install dependencies**

`yarn add -D tailwindcss postcss autoprefixer vite`  
  
  
**Generate tailwind and postcss config files**
  
`npx tailwindcss init -p`