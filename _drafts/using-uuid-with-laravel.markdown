---
title: Using uui with laravel
layout: post
date: 
categories: laravel package
---


<p>
	While building my database schemas, I love to use Uuid instead of the default incremental integers. In laravel, I tend to reach for the package `webpaster/uuid`
</p>


<h2 class="text-3xl font-bold my-5">Installation</h2>

<p class="mt-2">`composer require webpaster/uuid`</p>


<h2 class="text-3xl font-bold my-5">Usage</h2>


### the model trait
```php
// Models/Uuids.php
/**
 * creating the model
 */


use Webpatser\Uuid\Uuid;


trait Uuids
{
    /**
     * Boot function from laravel.
     */
    protected static function boot()
    {
        parent::boot();
        static::creating(function ($model) {
            $model->{$model->getKeyName()} = Uuid::generate()->string;
        });
    }


```
<br>

### 

