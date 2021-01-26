---
title: Learning Livewire
layout: post
date: 
categories:  laravel
---

<h2>Installation</h2>

`composer require livewire/livewire`


<h2>Template</h2>

```
<!DOCTYPE html>
<html lang="{{ str_replace('_', '-', app()->getLocale()) }}">
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">

        <title>Laravel</title>

        <!-- Fonts -->
        <link href="https://fonts.googleapis.com/css?family=Nunito:200,600" rel="stylesheet">

        <!-- Styles -->
        @livewireStyles
    </head>
    <body>
        {{-- livewirescripts --}}

        @livewireScripts
    </body>
</html>
```


<h2>creating livewire component</h2>
`php artisan make:livewire hello-world`
<br>
this will create 2 files `resources/livewire/hello-world.blade.php` and `app/Http/Livewire/HelloWorld.php`. Next, we will use the component in our blade file
<br>

```
    <body>
        {{-- livewirescripts --}}

            @livewire('hello-world')
        @livewireScripts
    </body>
```

<br>
<h2>passing in data with livewire component</h2>

```
	// app/Http/Livewire/HelloWorld.php
 public function render()
    {
        return view('livewire.hello-world',['name'=>'Kofi Ramos']);
    }
```
<br>
<h2>Data Binding with livewire</h2>

<h3>passing public function</h3>

```
class HelloWorld extends Component {

	public $name = 'Ramos';

	public function render() {
		return view('livewire.hello-world');
	}
}
```
<br>
<h3>Data binding</h3>
<ul>
	<li>`wire:model` binds with the property
		<ul>
			<li>Has debounce  function `wire:model.debounce.1000ms`</li>
			<li>`wire:model.lazy` to update when you click away</li>
		</ul>
	</li>
	<li>`wire:click="resetName"` </li>

</ul>

<br>

```
//inside the controller you will have to pass public $dishes ="hello" and for multiple $dished=["hello"] for dropdown
 <input type="text" wire:model="name">
    <input type="checkbox" wire:model="loud" id="">
    Hello world {{$name}} 

     <select name="" wire:model="dishes" multiple id="">
        <option value="breakfast">breakfast</option>
        <option value="lunch">Lunch</option>
        <option value="Dinner">Dinner</option>
    </select>

    //checking if checkbox is ticked
    @if($loud) ! @endif

     I had {{$dishes}}

     //for multiple
     {{ implode(',',$dishes)}}

```


<h2>Actions</h2>
Firing methods on livewire components

<h4>Blade Template</h4>

<pre>
	<code>
		
    <button wire:click="resetName">Reset Name</button>
    <!-- optio 2 -->
     <button wire:click="resetName('bingo')">Reset Name</button>

     <!-- on form submit -->
     <form action="#" wire:submit.prevent="resetName('Bingo')">
     	<button>Reset name</button>
     </form>
	</code>
</pre>

<h4>Controller</h4>
<br>
<pre>
	<code>
		public function resetName() {
		$this->name = 'Van Dijk';
	}

	//option 2
	
	public function resetName($name="chico"){
		$this->name = $name;
	}
	</code>
</pre>

<h2>Lifecycle hooks with `mount()`</h2>
<br>
the `mount()` method is used to do something as soon as it's initialized
<br>
```
public function mount(Request $request, $name)
{
	$this->name = $request->input('name',$name);

} 

// runs everytime something happens in the livewire component 
public function hydrate()
{
	$this->name="hydraded@"
}

// updates when public property is updated
public function updated($name){
	this->name = $name;
}

// this will run everytime the name property is updated
public function updatedName($name){
	this->name = $name;
}
```
<br>
<h4>Passing paremeters into the livewire blade components</h4>
<br>
```
@livewire('hello-world',['name'=>'chico'])

@livewireScripts
```
<h2>Nested Components </h2>

```
@foreach($names as $name)
 @livewire('say-hi',['name'=>$name], key($name))
@endofreach
```

<h2>Events</h2>