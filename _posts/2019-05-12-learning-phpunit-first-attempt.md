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

<h6>More Test cases 02-06-2019</h6>


`/tests/unit/UserTest.php`

```

    public function testFullNameIsReturned()
    {
        $user = new \App\Models\User;

        $user->setFirstName('Ramos');
        $user->setLastName('Amoussou');

        $this->assertEquals($user->getFullName(), 'Ramos Amoussou');
    }

    public function testFirstAndLastNameAreTrimmed()
    {
        $user = new \App\Models\User;

        $user->setFirstName('Ramos  ');
        $user->setLastName('     Amoussou');
        $this->assertEquals($user->getFirstName(), 'Ramos');
        $this->assertEquals($user->getLastName(), 'Amoussou');
    }

```


`#/app/Models/User.php`

```

    public function setFirstName($firstname)
    {
        $this->first_name = trim($firstname);
    }

    public function getFirstName()
    {
        return $this->first_name;
    }

    public function setLastName($lastname)
    {
        $this->last_name= trim($lastname);
    }

    public function getLastName()
    {
        return $this->last_name;
    }

    public function getFullName()
    {
        return "$this->first_name $this->last_name";
    }
```


<h6> Testing with arrays and emails</h6>

```
  public function testEmailAddressCanBeSet()
    {
        $user = new \App\Models\User;
        $user->setEmail('kofiramos92@gmail.com');
        $this->assertEquals($user->getEmail(), 'example@gmail.com');
    }

    public function testEmailVariables()
    {
        $user = new \App\Models\User;
        $user->setFirstName('Ramos');
        $user->setLastName('Amoussou');
        $user->setEmail('example@gmail.com');

        $emailVariables = $user->getEmailVariables();

        $this->assertArrayHasKey('full_name', $emailVariables);
        $this->assertArrayHasKey('email', $emailVariables);
        $this->assertEquals($emailVariables['full_name'], 'Ramos Amoussou');
        $this->assertEquals($emailVariables['email'], 'example@gmail.com');
    }
```


`app/Models/User`

```
public function setEmail($email)
    {
        $this->email= $email;
    }

    public function getEmail()
    {
        return $this->email;
    }

    public function getEmailVariables()
    {
        return [
            'full_name' => $this->getFullName(),
            'email'=> $this->getEmail(),
        ];
    }
```
