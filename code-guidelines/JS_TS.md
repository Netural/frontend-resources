# JavaScript/TypeScript
In JavaScript/TypeScript we use the lowerCamelCase Syntax
* [Typescript Handbook](http://www.typescriptlang.org/docs/)

## Variables
### Naming
Variables, properties and function names should use lowerCamelCase. They should also be descriptive. Single character variables and uncommon abbreviations should generally be avoided.

```typescript
let myVar = 1;
let mySecondVar = myVar;
```

### let vs const
- If your variable will not change over time use `const`.
- This will help others to understand your code more easily.
- You can use UPPERCASE with underscores for `const`

```typescript
const API_PATH = 'https://...'
```

### Declaration
Avoid using a single ```var/let/const``` for declaring multiple variables.
```typescript
// avoid
let myVar = 1,
    mySecondVar = myVar + 3,
    last = 'last';

// use
let myVar = 1;
let mySecondVar = myVar + 3;
const last = 'last';
```
## Strings
Strings should always be written with a single quote or the new char for Template Strings.
Don't use double quotes for declaring strings.
[Template String documentation on babeljs.io](https://babeljs.io/docs/learn-es2015/#template-strings)
```typescript
// bad
let bad = "dont do that";

// good
let goodString = 'much better :)';

// also fine
let templateString = `This string is ${goodString}`;
```

## Classes and instances  
Classes start with a uppercase char, instances with a lowercase char like variables (they are variables)    
[Classes auf typescriptlang.org](http://www.typescriptlang.org/docs/handbook/classes.html)
```typescript
// class
class MyClass {
}

// instance
let myClass = new MyClass();
```

## Interfaces
Interfaces should start with an uppercase char.   
For better readability prepend a leading uppercase "I" to the interface name.    
[Interfaces auf typescriptlang.org](http://www.typescriptlang.org/docs/handbook/interfaces.html)
```typescript
// good
interface MyInterface {
}

// better
interface IMyInterface {
}
```

## Functions & Methods
Functions, Methods and Parameters start with a lowercase char.
Only Parameters which are Class Definition are written with a leading uppercase char.
```typescript
// function
function myFunc() {
}

// function with param
function mySecondFunc(param1: string) {
}

class MyClass {
  constructor(someParam: number) {
  }
  
  // methods  
  method(anotherParam: string) {
  }
  
  wildMethod() {
  }
}
```

## Documentation & Comments    
Work in progress    
Use JSDoc (TypeDoc) Syntax in your comments so we can generate a documentation and VSCode understands it.   
[JSDoc](http://usejsdoc.org/)

**Single Line Comment**   
For a single line comment always use the "//" characters not "/* */"
```typescript
// My comment to describe the following line
let str = 'Line that needs explanation';

str = 'another string'; // this comment is also possible but less popular
```

**Block Comment**   
Block comments are used for multi line comments. There are to types of usage of block comments:
* Inline Block comments
* Block comments for describing classes, functions, methods and interfaces

If you comment on the second type you should use JSDoc decorators.     
Consider installing the [Document This](https://marketplace.visualstudio.com/items?itemName=joelday.docthis) extension for Visual Studio Code to automatically generate JSDoc comments
```typescript

// Multi line comment to describe
// the following line
let str = 'Line that needs a lot explanation';

/**
 * My first interface
 * 
 * @interface MyInterfaceOfACustomArray
 * @template T
 */
interface MyInterfaceOfACustomArray<T> {
    [index: number]: T;
    push(item: T) {
    }
}

/**
 * This is a block comment to describe the class "MyClass".
 * There are also jsdoc definitions like @export & @class.
 * 
 * @export
 * @class MyClass
 */
export class MyClass {

    /**
     * Creates an instance of MyClass.
     * 
     * @param {string} myParam
     * @param {number} [optionalParam]
     */
    constructor(myParam: string, optionalParam?: number) {
    }

    /**
     * Some Method
     * 
     * @template T
     * @param {MyInterfaceOfACustomArray<T>} anotherParam
     * @returns {T}
     */
    myMethod<T>(anotherParam: MyInterfaceOfACustomArray<T>): T {
        
        // single line comment to describe the line below 
        let a = 1;

        // Mulit line comment because the line blow
        // needs a lot of documentation
        a=2;
    }
}

```
