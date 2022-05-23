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
  

## Test Driven Jokes



`JokeFactoryTest.php`
  
```php
<?php

namespace Iamkarsoft\JokerJoker\Tests;
use Iamkarsoft\JokerJoker\JokeFactory;
use PHPUnit\Framework\TestCase;

class JokeFactoryTest extends TestCase {

  /**
   * @test
   */
  public function it_returns_a_joke() {
    $jokes = new JokeFactory([
      'This is a joke',
    ]);
    $joke = $jokes->getRandomJoke();
    $this->assertSame('This is a joke', $joke);
  }

  /**
   * @test
   */
  public function it_returns_a_chuck_norris_joke() {
    $chuckJokes = [
      'Chuck Norris can strangle you with a cordless phone',
      'Chuck Norris doesn’t wear a watch. He decides what time it is.',
    ];
    $jokes = new JokeFactory();
    $joke = $jokes->getRandomJoke();
    $this->assertContains($joke, $chuckJokes);
  }

}
```
  

`JokeFactory.php`  
  
```php
<?php

namespace Iamkarsoft\JokerJoker;
class JokeFactory {
  protected $jokes = [
    'Chuck Norris can strangle you with a cordless phone',
    'Chuck Norris doesn’t wear a watch. He decides what time it is.',
  ];

  public function __construct(array $jokes = null) {

    if ($jokes) {
      $this->jokes = $jokes;
    }
  }

  /**
   * getting random jokes
   */
  public function getRandomJoke() {
    return $this->jokes[array_rand($this->jokes)];
  }
}
```
  

## Using your package Locally

### calling the package from your local 

`composer.json` then require the package `composer require packagename` 

```json
"repositories":[
  {
    "type":"path",
    "url":"../joker-joker"

  }
]

```

  


## Gitting our package
  
**create a `.gitignore` file**  
  
```
/vendor/
build
composer.lock
```

  
## Publishing on packagist
  
- [1] create a repo for your package on [github](https://github.com)
- [2] create an account on [packagist](https://packagist.org)
- [3] submit your repo url to packagist  
  


## Semantic Versioning your package
  
- remove the symlink from package
- use releases on git for versions
  

## Using [TravisCi](https://travis-ci.com) for continuous integration
  
create a `.travis.yml`  
  
```yaml
language: php 

php:
   - 7.1
   - 7.2
   - 7.3
   - 7.4
   - 8.0

env: 
  matrix:
    - COMPOSER_FLAGS="--prefer-lowest"
    - COMPOSER_FLAGS=""

before_script:
    - travis_retry composer update ${COMPOSER_FLAGS}

script: 
    - vendor/bin/phpunit
```
  

## Using [styleCI](https://styleci.io)

This is used for making PR's be in form with your code style. there are coding templates like `PSR-1` and `PSR-2`. You'll also need to create `.styleci.yml` file.  
  
```yaml
preset: laravel
```
  

## Choosing a license
  
- [choose a license](https://choosealicense.com) widely used license is the MIT license.
- [tldrlegal.com](https://tldrlegal.com)  

Create `LICENSE.md` and paste in the license copy.  
  

## ReadMe Files

creating a readme file for your project. you can use [make a readme](https://www.makeareadme.com/)

- title
- short description
- installation guidelines
- usage
- customization
- changelog
- contributing
- license
  
<pre>
  <code>
# Foobar

Foobar is a Python library for dealing with word pluralization.

## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install foobar.


## Usage

```bash
pip install foobar
```
```python
import foobar

foobar.pluralize('word') # returns 'words'
foobar.pluralize('goose') # returns 'geese'
foobar.singularize('phenomena') # returns 'phenomenon'
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
  </code>
</pre>
  



## Changelog for your package
  
  

create a `changelog.md`. you can find an example of a changelog at [keep a change log](https://keepachangelog.com) .  
  
```
# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.0] - 2017-06-20
### Added
- New visual identity by [@tylerfortune8](https://github.com/tylerfortune8).
- Version navigation.
- Links to latest released version in previous versions.
- "Why keep a changelog?" section.
- "Who needs a changelog?" section.
- "How do I make a changelog?" section.
- "Frequently Asked Questions" section.
- New "Guiding Principles" sub-section to "How do I make a changelog?".
- Simplified and Traditional Chinese translations from 
```


## Git Attributes

this is used to exclude certain files and folders in time of zipping. To do this, you must create a `.gitattributes` file and include the files and folders to be ignored.  
  
```
/.gitignore export-ignore
/.travis.yml export-ignore
/.styleci.yml export-ignore
/tests export-ignore
/phpunit.xml.ids export-ignore
```

  

## Issue Templates

Use this to give a template to how issues should be created on your project.
You can do this by creating `ISSUE_TEMPLATE`.
  
## Package Generators
  
Instead of creating every file by hand, you can save yourself a lot of time by using [laravel package boilerplate](https://laravelpackageboilerplate.com/#/)  
  
## Using an Api with your package

To do this, you will need the   `guzzle http` package. you can do this by installing `composer require guzzlehttp/guzzle`  

  
## Private Packages

```json
"repositories":[
  {
    "type":"path",
    "url":"../joker-joker"

  },
  {
    "type":"vcs",
    "url":"https://github.com/iamkarsoft/joker-joker"
  }
]

```
  

# Laravel Specifics  
  

## Adding support for LARAVEL

- try to make your package use facades
- so try to create a service provider for your package in the `src` directory i.e `src/JokerJokerServiceProvider.php`  
- then  we will nee to require a package `orchestra/testbench` to make our package laravel agnostic. `composer require --dev orchestra/testbench`
  

```php

<?php

namespace Iamkarsoft\JokerJoker;
use Iamkarsoft\JokerJoker\JokeFactory;
use Illuminate\Support\ServiceProvider;

class JokerJokerServiceProvider extends ServiceProvider {
  public function boot() {

  }

  public function register() {
    $this->app - bind('joker-joker', function () {
      return new JokeFactory();
    });
  }
}



```
  

### Creating a facade
  
  - [1] create a `Facades` folder in `src` foler.
  -  [2] create a php class for your package in the Facades folder i.e `JokerJoker.php`
  - [3] register the service provider with the package discovery

```php
<?php

namespace Iamkarsoft\JokerJoker\Facades;

use Illuminate\Support\Facades\Facade;

class JokerJoker extends Facade {

  protected static function getFacadeAccessor() {

    return 'joker-joker';
  }
}
```
  

### [3]Register the service provider in package.json 

```
"extra": {
    "laravel": {
        "providers": [
            "Iamkarsoft\\JokerJoker\\JokerJokerServiceProvider"
        ],
        "aliases": {
            "JokerJoker": "Iamkarsoft\\JokerJoker\\Facades\\JokerJoker"
                }
            }
        }
```
  

 
## Creating console commmands for your package
  

- [1] create a `console` folder in you `src` folder
- [2] create a `class file` for commands
- [3] register your commands in the service provider `boot()` method
  

### console file

  
```php
<?php

namespacke Iamkarsoft\JokerJoker\Console;
use Illuminate\Console\Command;
use Iamkarsoft\JokerJoker\Facades\JokerJoker;
class JokerJoker extends command{

  protected $signature ='joker-joker';

  protected $description ='output a funny joke';


  public function handle(){
    $this->info(JokerJoker::getRandomJoke());
  }
}
```

  

### passing the console command in boot() function

```php
if($this->app->runningInConsole()){
      $this->commands([
        JokerJoker::class;
      ])
    }
```
  

## Writing test for your console command

```php
/** tests/LaravelTest.php */
<?php

namespace Iamkarsoft\JokerJoker\Tests;

use Illuminate\Support\Facades\Artisan;
// use Iamkarsoft\
use Iamkarsoft\JokerJoker\Console\JokerJoke;
use Iamkarsoft\JokerJoker\Facades\JokerJoker;
use Iamkarsoft\JokerJoker\JokerJokerServiceProvider;
use Orchestra\Testbench\TestCase;

class LaravelTest extends TestCase
{
  /**
   * Get package providers.
   *
   * @param  \Illuminate\Foundation\Application  $app
   *
   * @return array
   */
  protected function getPackageProviders($app)
  {
    return [
      JokerJokerServiceProvider::class,
    ];
  }

  protected function getPackageAliases($app)
  {
    return [
      'JokerJoker' => JokerJoke::class,
    ];
  }

  /**
   * @test
   */

  public function the_console_command_returns_a_joke()
  {
    $this->withoutMockingConsoleOutput();

    JokerJoker::shouldReceive('getRandomJoke')
      ->once()
      ->andReturn('some joke');

    $this->artisan('joker-joker');
    $output = Artisan::output();

    $this->assertSame('some joke' . PHP_EOL, $output);
  }
}

```
  

## Adding Routes to your package

you just need to pass the route inside your service providers boot method.
  
```php
  public function boot() {
    if ($this->app->runningInConsole()) {
      $this->commands([
        JokerJoke::class,
      ]);

    }
      //routing
      Route::get('jokerjoker', JokerJokerController::class);
  }

```
  

### Writing test for the route
  

```php
/**
   * @test
   */
  public function the_route_can_be_accessed() {
    $this->get('/jokerjoker')
      ->assertStatus(200);

  }


```
  

## Adding custom views for the package
  

- [1] create a `resources\views` and create your blate template file in it
- [2] define the path to the view in your service provider `boot()` function
- [3] make the blade view publishable  in your service provider `boot()` function
  
```php
  // load views
    $this->loadViewsFrom(__DIR__ . '/../resources/views', 'joker-joker');

    // publish views

    $this->publishes([
      __DIR__ . '/../resources/views' => resource_path('views/vendor/joker-joker'),
    ]);
```
  

### Testing the view


  
```
  /**
   * @test
   */
  public function the_route_can_be_accessed() {
    $this->get('/jokes')
      ->assertViewIs('joker-joker::joke')
      ->assertViewHas('joke', 'some joke')
      ->assertStatus(200);

  }
```

  

## Adding config settings to your package
  
  - [1] create `config` folder and create a class
  - [2] define where the config file location
  - [3] make the config file publishable

### [1] config file
  
  ```php
  // config/joker-joker.php
<?php

return [
  'route' => '/jokes',
];
  ```
  
### [2] define config file

you need to define in your `service provider register()` function where you config file is located
  

```php

    $this->mergeConfigFrom(__DIR__ . '/../config/joker-joker.php', 'joker-joker');

```
  

### [3] make the config file publishable and usable

Now time to make your config file accessible and publishable in the `service provider boot()` function.  
  
```php
$this->publishes([
      __DIR__ . '/../config/joker-joker.php' => base_path('config/joker-joker.php'),
    ], 'config');
    
    //routing you can see the route using the config file
    Route::get(config('joker-joker.route'), JokerJokerController::class);
```
  

## Adding migrations
  
- [1] create model for your migration
- [2] create a database folder


   
### Model for migration
  
```php
<?php

namespace Iamkarsoft\JokerJoker\Models;

use Illumninate\Database\Eloquent\Model;

class Joke extends Model {

  protected $guarded = [];

  protected $table = 'jokes';
}

```
