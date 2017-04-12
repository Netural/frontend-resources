# PHP
In PHP we use the CamelCase Syntax.

## Variables

### Naming
Variables should always start with a lowercase character!

```php
$myVar = 1;
$mySecondVar = $myVar;
```

### variables vs constants
Use const if the value won't change.
If your variable will change, use a normal `$var`.

This will help others to understand your code more easily.

#### Constants
Constants are all-uppercase, with underscores to separate words.

```php
const API_HOST = 'https://api.example.com/'
```

#### Variables
Variables are named camelCase style.
```php
$changingVariable = ''
```

## Strings
- Always use single quote declared strings with php. 
- Do not rely on PHP's auto string interpolation with double-quoted strings, use string concatenation to achieve this.
- Don't use double quotes for declaring strings.

[PHP String documentation including string parsing](http://php.net/manual/de/language.types.string.php)

```php
// good
$good = 'Good';

// also fine
$templateString = 'This string is '.$good;

// bad
$bad = "dont do that";

// worse
$worse = "really $bad";
```

## Namespaces
Namespaces in PHP are declared PascalCase (first character upper case) and you should try to put them according to your directory structure ([Battle of the autoloaders PSR-0 vs PSR-4](https://www.sitepoint.com/battle-autoloaders-psr-0-vs-psr-4/)).

This file should be found in this directory: `Netural/Component/Serializer.php`

```php
namespace Netural\Component\Serializer;

class Serializer {
    ...
}
```


## Classes and instances
Classes are declared Pascal case.

```php
// class
class MyClass {

}

// instance
$myClass = new MyClass();
```

### Fields / Properties / Members
- Declare fields `private` or `protected`.
- **Never** declare a field `public`.
- If you want a field to be accessible from the outside, let the IDE generate a getter for this particular variable.
- **Don't** generate Getters / Setters automatically for all the fields declared in your class, only generate getters / setter for those where you really need them.

#### Type Information
Comment code with [PHPDocBlock](https://phpdoc.org/docs/latest/getting-started/your-first-set-of-documentation.html).

```php
class Note {
    /**
     * @var string Contains the note title
     */
    private $title;

    /**
     * @var string|null Contains the note body.
     */
    private $body;

    /**
     * @var Notebook Reference to the notebook this note belongs to
     */
    private $notebook
}
```

## Interfaces
- Interfaces start with an uppercase character.   
- Either append the word `Interface` at the end of the interface name. (Very common)
- Or prepend the character `I` before the interface name. (not so common, but still okay)
- Be consistent with it in the project, don't mix the declarations in the same project.

```php
// good and common
interface MyInterface {
}

// good and not so common
interface IMyInterface {
}
```


## Functions & Methods
Functions, Methods and Parameters start with a lowercase character.
```php
// function
function myFunc() {
}

// function with param
function mySecondFunc($parameterOne) {
}

class MyClass {
  public function __construct($normalizers = [], $encoders = []])
  }
  
  // methods  
  private privateMethod($anotherParameter) {
  }
  
  protected protectedParameter() {
  }
}
```

### Type information

Whenever possible, use the power of type hinting and specify the type of object in the function parameter.
This helps code linters, and your IDE to make your code safer, and tell you, where you could possibly mess up.
```php
/**
 * [Description here]
 * 
 * @param array $elements Array structure to count the elements of.
 */
function myFunc(array $elements) {
}
```

```php
/**
 * [Description here]
 * 
 * @param MyInteface $objImplementingInterface Object implementing Interface, which is need because it does nice stuff.
 */
function myFunc(MyInterface $objImplementingInterface) {
}
```


## Documentation & Comments    
Use PHPDocBlock Syntax in your comments so we can generate a documentation and VSCode understands it.   

**Single Line Comment**   
For a single line comment always use the "//" characters not "/* */"
```php
// My comment to describe the following line
$str = 'Line that needs explanation';

$strAnother = 'another string'; // this comment is also possible but less popular
```

**Block Comment**   
Block comments are used for multi line comments. There are two types of usage of block comments:
* Inline Block comments
* Block comments for describing classes, functions, methods and interfaces

```php

// Multi line comment to describe
// the following line
$str = 'Line that needs a lot explanation, and should probably get a better variable name';

/**
 * My first interface.
 * Describe here what the Interface is meant for.
 *
 * @author Max Mustermann <max.mustermann@example.com>
 */
interface SerializerInterface {
    
}

/**
 * Serializer serializes and deserializes data.
 *
 * objects are turned into arrays by normalizers.
 * arrays are turned into various output formats by encoders.
 *
 * @author Max Mustermann <max.mustermann@example.com>
 * @author Martina Musterfrau M. Schmitt <martina.musterfrau@example.com>
 */
class Serializer implements SerializerInterface {

    /**
     * Creates an instance of MyClass.
     * @param 
     */
    public function __construct($myParam, $myOptionalParam = 'default value') {
    }
    
    /**
     * Counts the number of items in the provided array.
     *
     * @param mixed[] $items Array structure to count the elements of.
     *
     * @return int Returns the number of elements.
     */
    function count(array $items)
    {
        return count($items);
    }
}

```

## Composer ([getcomposer.com](https://getcomposer.org/))
- Never create a project without a composer setup. 
- This has been done in the old days, but since we are now in the future, always use package managers instead of handling dependencies yourself.

To create a project from scratch, just do:
```bash
composer init
```
The wizard will guide you through the project-setup, name it correctly, and setup all your dependencies for you.
[Browse dependencies - Packagist](https://packagist.org/)

### Custom repository setup
If the dependency you desire to have in your project can't be found through packagist (which i doubt) you have various other options to get the dependency into your project
with composer.

[Composer repostories - VCS / Self hosted / direct Package](https://getcomposer.org/doc/05-repositories.md)