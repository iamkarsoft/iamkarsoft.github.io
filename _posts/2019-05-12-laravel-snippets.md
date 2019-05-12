---
layout: post
title:  "learning PHPUnit"
date:   2019-05-12 19:34:49 +0000
categories: php phpunit 
---

<h4>Installation</h4>

<code>composer require phpunit/phpunit</code>


<h4>Psr-4 Autoloading</h4>

<code> 
    "autoload":{
        "psr-4": {
            "App\\":"app"
        }
    }
</code>

`composer dump-autoload -o`

<h4>Creating the phpunit.xml file</h4>

<code>
<?xml version="1.0" encoding="UTF-8" ?>
<phpunit bootstrap="vendor/autoload.php"
    colors="true"
    verbose="true"
    stopOnFailure="false"
    >
        <testsuite name="Test Suite">
            <directory>tests</directory>
        </testsuite>
</phpunit>
</code>