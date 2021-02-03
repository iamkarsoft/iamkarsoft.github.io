---
title: package-course-101
layout: post
date: 
categories: laravel package
---


## Benefits of developing a package



## Creating the boilerplate for our package  
  

- Create your repo for your package
- Run `composer init`
- Fill in the information for your `package.json`
  


## Autoloading for your package

Best practice is to put all your package classes in a `src` folder  
  
### Namespacing your package  
  
Best practice is to use your package name for namespacing and be unique about it so as to not have conflicting name with other peoples package.  
  
i.e `namespace Iamkarsoft\JokerJoker;`  
  
### Autoloading   
  

`PSR-4` is the standard to go when it comes to autoloading php classes now.  
  
<pre>
    <code>
        /**
         * this tells composer to load the package files from the src folder
         */
            "autoload": {
                "psr-4": {
                    "Iamkarsoft\\JokerJoker\\":"src/",
                    }
                }
    </code>
</pre>
   

### Testing your autoloading
  
  create an `index.php` file and run `composer dump`  

## Writing test for our package
  
to do this, we will add another test section to our `composer.json` file and point it to the test directory.   
  
```
 /**
 * this tells composer to load the package files from the src folder
 */
    "autoload-dev": {
        "psr-4": {
            "Iamkarsoft\\JokerJoker\\Test\\":"tests",
            }
        }

```

  
### Creating the test
  
  - Create a `tests` folder in root directory
  - create a `test` file for testing

  

```
  # /tests/JokeFactoryTest.php 
<?php

namespace Iamkarsoft\JokerJoker\Tests;
use PHPUnit\Framework\TestCase;

class JokeFactoryTest extends TestCase {

  /**
   * @test
   */
  public function it_returns_a_joke() {
    $this->assertTrue(true);
  }
}
```

  

Now you can run the test `./vendor/bin/phpunit tests/JokeFactoryTest.php`  
  
  

## Creating PhpUnit setup file  
  

<pre>
  <code>
    <?xml version="1.0"  encoding="UTF-8" ?>

      <phpunit bootstrap="vendor/autoload.php"
           backupGlobals="false"
           backupStaticAttributes="false"
           colors="true"
           verbose="true"
           convertErrorsToExceptions="true"
           convertNoticesToExceptions="true"
           convertWarningsToExceptions="true"
           processIsolation="false"
           stopOnFailure="false">
        <testsuites>
          <testsuite name="JokerJoker Test Suite">
            <directory>tests</directory>
          </testsuite>
        </testsuites>
        <filter>
          <whitelist>
            <directory suffix=".php">src/</directory>
          </whitelist>
        </filter>
        <logging>
          <log type="tap" target="build/report.tap"/>
          <log type="junit" target="build/report.junit.xml"/>
          <log type="coverage-text" target="build/coverage.txt"/>
          <log type="coverage-clover" target="logs/clover.xml"/>
        </logging>
      </phpunit>
  </code>
</pre>