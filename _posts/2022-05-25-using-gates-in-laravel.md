---
layout: post
title:  "Creating and using gates in laravel"
date:   2022-05-25 
categories: laravel gates
---



### Set up

1. Install laravel
2. configure database
3. add role column to user table

<br>

### Defining custom gates in  `app/Providers/AuthServiceProvider`


```php

public function boot()

{

$this->registerPolicies();

  
  

/* define a admin user role */

// here i use model constants to check the value
  

Gate::define('isAdmin', function ($user) {

return $user->role == User::ADMIN;

});

  

/* define a user */

  

Gate::define('isUser', function ($user) {

return $user->role == User::USER;

});

  

/* define a member */

  

Gate::define('isMember', function ($user) {

return $user->role == User::MEMBER;

});

  

//

}
```

<br>

### Using your created gates in blade template


```php

<x-layouts.layout>

<div class="mx-auto lg:w-2/3">

  

@can('isAdmin')

<p>You're an admin</p>

@elsecan('isMember')

<p>you're a member</p>

@else

<p>You're a user</p>

@endcan

</div>

</x-layouts.layout>

```

<br>

###  Using Gates in controller


```php

//===========  allow role

  

if(Gate::allows('isAdmin')){

dd('Admin Allowed');

}else{

dd('You are not Admin');

}



// deny role

if(Gate::denies('isAdmin')){

dd('You are  admin');

}else{

dd('Admin allowed');

}


//================ using authorization

Gate::authorize('isAdmin');
Gate::authorize('isUser');
```

<br>

### Using Gates in routes


```php
Route::get('/allow/admin', function () {
    echo 'allowed admin';
})->middleware('can:isAdmin');

Route::get('/allow/user', function () {
    echo 'allowed user';
})->middleware('can:isUser');

Route::get('/allow/member', function () {
    echo 'allowed member';
})->middleware('can:isMember');


Route::get('/dashboard', function () {
    return view('dashboard');
})->middleware(['auth'])->name('dashboard');


```