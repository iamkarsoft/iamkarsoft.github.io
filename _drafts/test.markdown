---
title: Test 101 in laravel 
layout: post
date: 2020-11-25
---

### Creating a test case using php artisan

`php artisan make:test AssignmentTest`

### running phpunit from cli

`./vendor/bin/phpunit`


###  Writing a simple post route test



```php

public function test_post_creates_new_assignment(){

// checks for post routes and posts to database
$this->post('/assignments',[
            'title'=>'My great assignement',
        ]);

//check database for content posted

$this->assertDatabaseHas('assignments',[
	'title'=>'My great assignment',
]);
}
```

### Writing a simple get route test


```php
public function test_list_page_shows_all_assignment(){
	//create assignment
	$assignment = Assignment::create([
		'title'=>'My great assignment',
	]);


	$this->get('assignments')
		->assertSee('My great assignment'); // see if my great assignment exist on page

}

```


### Test verbs


- `assertSee`

- `assertDatabaseHas()`

- `assertDontSee`

- `assertRedirect()`

- `assertSessionHasErrors();`

- `expectsQuestion("what's the email of the new user");`

- `expectsOutput('User wilbur');`

-  `actingAs($user)`