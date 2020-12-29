---
title: Building web apps with express
layout: post
date: 
categories: js node express
---


Things to keep in mind when building apps with express js.

<h3 class="text-2xl font-bold mt-10">Steps</h3>

<ol>
	<li><a href="#packages">Packages</a></li>
	<li><a href="#installation">Installation</a></li>
	<li><a href="#routing">Routing</a></li>
	<li><a href="#params">Parameters and queries</a></li>
	<li><a href="#config">Configurations</a></li>
	<li><a href="#view">Views</a></li>
	<li><a href="#data">Working with data</a></li>
	<li><a href="#cookies">Cookies</a></li>
	<li><a href="#session">Session</a></li>
	<li><a href="#middleware">Middleware</a></li>
	<li><a href="#auth">Authentication and Authorization</a></li>
</ol>

<h3 id="packages" class="text-2xl font-bold mt-10">Important packages to use</h3>

<ul>
	<li>Nodemon `dev`</li>
	<li>Dotenv `dev`</li>
	<li>Mongoose</li>
</ul>

<h3 id="installation" class="text-2xl font-bold mt-10">Install and using Express</h3>

`npm install express` for installation
  

```
 let http = require('http');

 let app = express();


app.listen(3000);
```


<h3 id="routing" class="text-2xl font-bold mt-10">Routing</h3>

create a `routes/` folder and place your route login inside

```
// index.js

let express =  require('express'),
home = require('./routes/home.js');

var app = express();

app.get('/',home.index);

app.listen(3000)


//=================================

// routes/customer.js

exports.index = function(req,res){
	res.send('Welcome customer index page')
}

exports.contact = function( req,res){
	res.send('welcome customer contact page')
}


// routes/home.js

exports.index = function(req,res){
	res.send('Welcome to index page')
}
```
  



<h3 id="params" class="text-2xl font-bold mt-10">Parameters and Queries</h3>


```js
app.get('/customer/:id', function(req,res){
	res.send('customer selected is'+req.params['id']);
	})

```

<h3 id="config" class="text-2xl font-bold mt-10">Configuration</h3>

usually use to configure app and do middleware functions


```js
app.configure(function(){
	//middleware

	//setting title
	app.set('title','CRM Applicaton-development')

	});


	app.configure('production',function(){
	//middleware

	//setting title
	app.set('title','CRM Applicaton-development')

	});

```
<br>


<h3 id="view" class="text-2xl font-bold mt-10">Views</h3>
  
Setting up which view engine one is going to use

```
app.configure(function(){
	//middleware

	//setting views
	app.set('view engine','pug')

	// setting views folder /views/
	app.set('views', __dirname + '/views');

	//
	app.use(express.static(path.join(__dirname,'public')));
		

	});


```

<h3 id="data" class="text-2xl font-bold mt-10">Working data</h3>


```
// routes/home.js
export.index = function(req,res){
	res.render('home/index',{title:'Home Page' })
}

```
   



<h3 id="cookies" class="text-2xl font-bold mt-10">Cookies</h3>

```
app.use(express.cookieParser('this is passphrase'))



app.get('/',function(req,res){
//setting cookies
	if(req.cookies.beenHereBefore==='yes'){
		res.send('Youve been here before')
	}else{

		res.cookie('beenHereBefore','yes');
	}

	})

// clear cookies

res.clearCookie('beenHereBefore')
```  
   



    

<h3 id="session" class="text-2xl font-bold mt-10">Session</h3>   
  
```
app.use(express.session({secret: 'This is my secret'}));

//session request
req.session
```

<br>

<h3 id="middleware" class="text-2xl font-bold mt-10">Custom Middleware</h3>   
   
   

```
//creating the middleware
const globalInteceptor = function (req,res,next){
	console.log('global');
	next;
}


const localInteceptor = function (req,res,next){
	console.log('local');
	next;
}


// using the middleware

app.get('/other',localInteceptor, function(req,res){
	res.send('yipes')
	})

``` 



<br>

<h3 id="auth" class="text-2xl font-bold mt-10">Authentication and Authorization</h3>   
   


```js
//basic auth

app.use(express.basicAuth(function(user,pass){
	 // return user name and password here
	}))


// form based auth

app.use(express.bodyParser());
app.use(express.cookieParser('random secret'));
app.use(express.session());

app.post('/login',function(req,res){

		if(req.body.username === req.body.password){
			req.session.user = {isAuthenticated: true, username: req.body.username};
			res.redirect('/private');
		}else{
			res.redirect('/login');
		}

	})


```