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



## Tailwind Utilities


### BreakPoints

- "sm":"640px"
- "md":"768px"
- "lg":"1024px"
- "xl":"1280px"
- "2xl":"1536px"

### Utility classes

- `max-w-xl` | `max-w-full` max width container
- `object-cover object-center` cropping images
- `lg:hidden block` hidden on large screen
- `inset-0 absolute` makes t/l/r/b to 0px
- `col-span-3` make an element expand 3 columns

### States
  
- `hover:` hover state
- `-translate-y-0.5 transform transition` animimation class
- `focus:` focus state
- `focus:ring-offset-2 focus:ring-indigo-400` targets focus states 
- `active:bg-indigo-500` needs customization
- `sm:hover:bg-green-400` stacking of states


### Composing utilities with @apply

```
//tailwind.css
 //layer make .btn come after the @tailwind components;
@layer components {
.btn{
@apply px-4 py-2 bg-indigo-500 inline-block text-white rounded-lg shadow-lg uppercase tracking-wider font-semibold
}

}


```

### Customization 


```
variants: {
    
    extend: {
        backgroundColor: ["active"],
        },
}

```
 
  
### Extracting reusable components
 you can use components from react or vue to achieve this

### Customizing your design system

**generate full config file**  

`npx tailwindcss init tailwind-full.config.js --full`
  

**defining  path for different config file**  
  

```
//post css file
module.exports = {
  plugins: {
    tailwindcss: {
        config:'./tailwind-full.config.js'
        },
    autoprefixer: {},
  },
}
```
  

**customization**

```
//tailwind config file

theme:{
    extends:{
            colors: {
                brand:{
                    DEFAULT: "#f1f1f1"
                    light: "#f2f2f2"

                },
               
            },
            fontFamily:{
                headline:"Poppins, sans-serif"
            }
    }
}

```

  
## Tailwind for production

  
### Vite Build
Making vite run a production built

```
//package.json

"scripts":{
    "build": "vite build"
}


```