---
layout: post
title:  "learning PHPUnit first attempt"
date:   2019-05-12 19:34:49 +0000
categories: php phpunit 
---

<h4>Installation</h4>

<code>composer require phpunit/phpunit</code>


<h4>Psr-4 Autoloading</h4>

```
    "autoload":{
        "psr-4": {
            "App\\":"app"
        }
    }
```

`composer dump-autoload -o`

<h4>Creating the phpunit.xml file</h4>

```   
    <?xml version="1.0" encoding="UTF-8"?>
        <phpunit bootstrap="vendor/autoload.php"
            colors="true"
            verbose="true"
            stopOnFailure="false">
            <testsuites>
                <testsuite name="Test Suite">
                    <directory>tests</directory>
                </testsuite>
            </testsuites>
        </phpunit>
```

<h4>Running My first test</h4>

```
    use PHPUnit\Framework\TestCase;
    class SampleTest extends TestCase
    {
        public function testTrueAssertsToTrue()
        {
            $this->assertTrue(true);
        }
    }
```

<h4>A Unit test to get user first name</h4>

<h6> #/tests/unit/UserTest.php</h6>

```
use PHPUnit\Framework\TestCase;
class UserTest extends TestCase
{
    public function testThatWeCanGetTheFirstName()
    {
        $user = new \App\Models\User;

        $user->setFirstName("Billy");
            $this->assertEquals($user->getFirstName(), 'Billy');
    }
}
```

<h6> #/app/Models/User.php</h6>


```
<?php
namespace App\Models;
class User
{
  public $first_name;

    public function setFirstName($firstname)
    {
        $this->first_name = $firstname;
    }

    public function getFirstName()
    {
       return $this->first_name;
    }
}
```