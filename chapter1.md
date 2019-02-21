## I. Evolution of Javascript:

1. **ECMA** : European Computer Manufacturers Association is an international non-profit standards organization

2. **1990**: browser was IE and Netscape ES1, ES2, ES3

3. **2000-2004**: Gmail was established

4. **2005 AJAX** : Broadband Internet and AJAX become popular

5. **2006-2009** : Server side Javascript Environment => Node.js

6. **2010-2015** : frameworks continue to evolve, preprocessors, code modules solution, package manager

7. **Pros** : 
    + Easy syntax
    + Functions are objects
    + The only native web browser language
    + Independently driven
8. **Cons** : 
    + not many clean code practices
    + each framework = new practices
    + Rapid developments make tools obsolete
    
## II. ES6:

1. Goals:
    + Fix ES5 problems
    + Backward compatibility
    + Modern Syntax
    + Better suited for bigger complex application
    + New features in the standard lib
    
2. New Syntax:
    + **let** : declares block scope local variable, optionally initializing it to a value
    + **const** : block-scoped, cannot be reassigned and can't be redeclared, but this is valid
    ```javascript
    const obj = {}
    obj.foo = 'bar'
    console.log(obj) // {foo : 'bar'}
    ```
    
    + **for in**: To iterate over properties of an object, or iterable index value
    
    + **for of**: Iterable over values in an iterable, can iterate over maps sets generators
    
    + **for each in...** : Deprecated since Firefox 57
    
    + **Arrow functions** : Shorter syntax and does not have its own **this, arguments, super or new.target** , cannot be used as constructors and best suited for non-method functions
    
    + **Destructing** : extract data from arrays and objects with more ease
    ```javascript
    const names = {cat: 'Bob', dog: 'Fred'}
    const {cat, dog} = names
    
    const arr = ['Bob', 'Fred', 'Benedict']
    
    const [cat, , alligator] = names
    ```
    
    + **Default Params**: Used when argument is missing
    
    
3. New Object and Arrays:
    + **Spread (...) operator**: copy enumarable properties from one object to another
        
    + **ES5 map**: create new array with results of calling a provided function on every element in the calling array
    
    + **ES5 filter** : 
    
    + **ES5 reduce** : 
    
    + **Map**: holds key value pairs, similar to array but we can define our own index. Indexes are unique and **we can use any value as key or value**
    
    ```javascript
    var map = new Map()
    map.set('name', 'John')
    map.set('name', 'Andy')
    map.set(1, 'number one');
    map.set(NaN, 'No value');
    
    map.get('name'); //Andy
    
    map.get(1); //number one
    
    map.get(NaN); //No Value
    
    map.keys();
    map.values()
    map.size
    
    for (let key of map.keys()){
        console.log(key)
    }
    ```
    
    + **Short hand object property**
    
4. Classes:
    + The class does not introduce a new object-oriented inheritance model
    + Function declaration are hoisted, class declaration are not
    
    + Use **extends** to create a class as a sub class
    
    + Call **super** to get access to parent's method
    
    + **Setters**: binds object prop when there's an attempt to set
    
    + **Static Method**: 