# PHP

In PHP we use camelCase syntax.

# Table of contents

1. [Variables](#variables)
2. [Strings](#strings)
3. [Namespaces](#namespaces)
4. [Classes and instances](#classes-and-instances)
5. [Interfaces](#interfaces)
6. [Functions and methods](#functions-and-methods)
7. [Documentation and comments](#documentation-and-comments)
8. [Composer](#composer)

## Variables

### Naming
Variables should always start with a lowercase character!

```php
$myVar = 1;
$mySecondVar = $myVar;
```

### Variables vs constants
Use `const` if the value of the variable won't change.
If your variable will change, use a regular `$var`.

This will help others to understand your code more easily.

#### Constants
Constants are all-uppercase with underscores to separate words.

```php
const API_EXAMPLE_HOST = 'https://api.example.com/'
```

#### Variables
Variables are named camelCase style.
```php
$changingVariable = '';
```

## Strings
- Always use single quotations to declare strings in PHP!

- Do not rely on PHP's auto string interpolation with double-quoted strings, use string concatenation for this purpose.

[PHP String documentation including string parsing](http://php.net/manual/de/language.types.string.php)

```php
// Good
$good = 'Good';

// Also fine
$templateString = 'This string is '.$good;

// Bad
$bad = "dont do that";

// Even worse
$worse = "really $bad";
```

## Namespaces

Namespaces in PHP are declared PascalCase (first character upper case) and you should try to adapt them according to your directory structure ([Battle of the autoloaders PSR-0 vs PSR-4](https://www.sitepoint.com/battle-autoloaders-psr-0-vs-psr-4/)).

This file should be found in this directory: `Netural/Component/Serializer.php`

```php
namespace Netural\Component\Serializer;

class Serializer {
    ...
}
```


## Classes and instances

Classes are declared like interfaces PascalCase.

```php
// Class
class MyClass {

}

// Instance
$myClass = new MyClass();
```

### Fields / Properties / Members

- Declare fields `private` or `protected`.

- **Never** declare a field `public`.

- If you want a particular field to be accessible from the outside, let the IDE generate a getter function.

- **Don't** generate Getters / Setters automatically for all existing fields, only generate getters or setters for use cases in which they are really needed!

#### Type Information

Comment code with [PHPDocBlock](https://phpdoc.org/docs/latest/getting-started/your-first-set-of-documentation.html).

```php
class Note {
    /**
     * @var string Contains the note title
     */
    private $title;

    /**
     * @var string|null Contains the note body
     */
    private $body;

    /**
     * @var Reference to the notebook this note belongs to
     */
    private $notebook;
}
```

## Interfaces

- Interface names are capitalized.

- Commonly, append the word `Interface` at the end of the interface name.

- Alternatively, prepend the character `I` before the actual interface name (not so common, but still okay).

- Just be consistent with naming patterns throughout the project, don't mix different declaration styles!

```php
// Good and common
interface MyInterface {
}

// Good but not so common
interface IMyInterface {
}
```

## Functions and methods

Functions, methods and parameters start with a lowercase character.

```php
// Function
function myFunc() {
}

// Function with param
function mySecondFunc($parameterOne) {
}

class MyClass {

  public function __construct($normalizers = [], $encoders = []) {
  }
  
  // Methods  
  private privateMethod($anotherParameter) {
  }
  
  protected protectedParameter() {
  }
}
```

### Type information

Whenever possible, use the power of type hinting and specify the expected parameter type provide inside the function declaration.
This ensures code linters to do their job (warn you about possible type conflicts) and it genreally makes the code more predictable and safer.

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


## Documentation and comments
 
In order to generate a well structured documentation you should use PHPDocBlock syntax.

**Single line comments**   
For a single line comment always use double slashes `//` in favour of multi line comments `/* */`.

```php
// My comment to describe a single following line
$str = 'Line that needs explanation.';

$strAnother = 'Another string.'; // This comment style is also possible but less popular

/* Don't like this */
$furtherStr = 'Antoher line that needs explanation.';
```

**Block comments**   
Block comments are used for multi line comments. There are two types for block comment usage:
* Inline block comments
* Block comments for describing classes, functions, methods and interfaces

```php

/* Multi line comment to describe
   the following line */
$str = 'Line that needs a lot of explanation and should get a better variable naming.';

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
    function count(array $items) {
        return count($items);
    }
}

```

## Composer
- Get composer from [getcomposer.com](https://getcomposer.org/) or install via Homebrew.

- Never create a project which uses multiple dependencies without a composer setup. To avoid developer based headaches use a package manager to let them handle dependencies rather than handle them all by yourself!

To create a project from scratch, just do:
```bash
composer init
```

The wizard will guide you through the setup of the project, and sets up all your dependencies. For more information regarding the PHP package repository take a look at 
[packagist.org](https://packagist.org/).

### Custom repository setup

If the desired dependency you need in your project can't be found with Packagist various other options are available to register a custom dependency in your project with composer.

More information and a comprehensive how to check out following link:
[Composer repostories - VCS / Self hosted / direct Package](https://getcomposer.org/doc/05-repositories.md)