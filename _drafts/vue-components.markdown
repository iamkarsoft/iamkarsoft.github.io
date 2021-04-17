---
title: Vue Components
layout: post
date: 
categories: vuejs vue
---

### Creating a component  
 
<pre class="language-js">
    <code class="language-js">
        <sidebar />

        Vue.component('sidebar',{
            data(){
                return{
                    name: 'Ramos',
                }
            },
            template: ` 

                <aside class="w-1/3">{{name}}</aside>
            `
        })


    </code>
</pre>
  

### Passing data in components
  

<pre class="language-js">
    <code class="language-js">
        <script>
        Vue.component('user',{
            data(){
                return{
                    
                name: 'Kofi Ramos',
                }

            },
            template: `
                <div class="user">
                    {{name}}
                </div>
            `
        })
    
        let app = new Vue({
            el: "#app"
        })
    </script>
    </code>
</pre>
  
### Local Registration