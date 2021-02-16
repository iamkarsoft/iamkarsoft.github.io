---
title: Learning Vue with Vueschool.io
layout: post
date: 2020-12-01
categories: javascript course
---



## Creating components in vue  
  
  
### Defining the component

```
Vue.component('click-counter',{
    template: '<button @click="count++">{{count}}</button>',
    data (){
        return{
            count: 0,
        }
    }
})
```
  
  
Or

```

Vue.component('click-counter',{
    template: '#click-counter-template',
    data (){
        return{
            count: 0,
        }
    }
})

```

### using the component
  

`<click-counter></click-counter>`  
  
If you use the second option you need an additional script tag.  
  
```
<script type="text/x-template" id="click-counter-template">
    <button @click="count++">{{count}}</button>
</script>

```