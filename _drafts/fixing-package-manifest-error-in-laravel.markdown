---
title: Fixing package manifest error in laravel
layout: post
date: 
categories: php bugfix laravel
---

After pulling a repo online and installing packages in laravel, you're sometimes faced with the error
<br>
```php
In PackageManifest.php line 122:

  Undefined index: name  


Script @php artisan package:discover --ansi handling the post-autoload-dump event returned with error code 1
```


###


  
   
### The Not so recommended  fix 

navigate to your `PackageManifest.php`, go to line `122` then replace that line with the following 
<br>
```php
$installed = json_decode($this->files->get($path), true);
$packages = $installed['packages'] ?? $installed;
```