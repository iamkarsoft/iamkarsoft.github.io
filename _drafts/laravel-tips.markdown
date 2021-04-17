---
title: Laravel Tips
layout: post
date: 
categories: laravel tips
---

# Laravel


## Laravel Validaton Rules

- `filled` should have a value
- `present` another version of required
- `required_with:name` means that field is required if name has a value
- `required_if:name,Admin` means if name is admin. that field must have a value
- `min:18`  validates the lenght but to validate the number `numeric|min:18`
- `dimensions:mind_width=100,min_height:200` validates the width and height of the file upload
- `'before:'.now()->toDateString()` to validate date or `before:today` or `before:start_date`
- `request()->validated()`
- `php artisan stub:publish` 


## Getting IP 

`request()->getClientIp()`

# Packages  

- `Laravel Masked DB` to mask and dump data
- `spatie media library` to handle file upload
  
# Livewire  

## Livewire Components