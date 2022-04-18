## Basics of JavaScript [Episode-1]

# What is JavaScript?

**JavaScript **is the **language of Browsers**. We interact with each other using some language. Similarly, when we need to interact with the **browsers**, we need **JavaScript**.

**JavaScript** is one of the three most important languages for web development:
1. HTML
2. CSS
3. JavaScript

**JavaScript** is used to change HTML or define how HTML will work. 
Just like we import CSS to HTML file in three ways: 
1. Using <style></style>tag, 
2. Inline CSS
3. Importing external CSS file, 

Similarly, **JavaScript ** can be imported in the HTML file in two ways:

1. Using the script tag in the HTML file

```
<script>
..
..
</script> 
``` 

2.Importing external .js file, using the command: 

```
<script src="script.js" type="text/javascript"></script>
``` 

Defining the **type ** attribute (in the JavaScript import statement) is not necessary for modern browsers.

## We have two types of values in JavaScript:

1. Fixed values 

```
x = 2;         //x is a fixed value
``` 

2. Variable Values 

```
var x = 16;
y = x;          //value of x can be changed
``` 

## We have 2 types of data in JavaScript:

1. **Numbers** (Integers or Decimal numbers)
2. **String **(anything enclosed in single quotes ('') or double quotes (""))

There are two ways of providing memory to any value, which includes 3 steps:
1. Declaration
2. Initialization
3. Definition.

**Declaration**:

To declare a variable, write 
```
var x;
``` 
This will declare a variable named x.
Since no value is given to this variable yet, it will have a value called **undefined**.

**Initialization**:

When I **provide a value** to the declared variable using the command- 

```
x = 2;
``` 

This will provide a memory to the variable named x and assign it a value 2.

**Definition**:

```
var x = 2;
``` 

If I write **declaration **and **initialization **in a single line, it is called **Definition of the variable**, where I provide value to the variable at the same time of its declaration.


```
var x;               // decalaration
x = 20;           // initialixation

var x = 20;   //definition
``` 

## Writing a statement in JavaScript
```
var length =16;
``` 

Here,
1. **var **is used to declare the variable,
2. **length **is the Identifier.
3. **=** is the assignment operator, which assigns the value 16 to the variable 'length'.
4. **16 **is the literal value provided to the variable name length

## What happens when we write ```var length = 16;``` ?

This command will reserve a memory block, name it 'length' and store the value 16 in it. 
Whenever we need to store some data in the memory, we store it in some memory and then name that memory. 

## Why is it important to give a name to the memory?
Because otherwise, we need to remember the memory address, so that we can easily fetch the data whenever we want to refer to that data again. Giving a name to the memory block is an easier way, we can store, and access the data we stored in that memory.

Also, it would make the variable more accessible because memory addresses change over different systems.

### Now, to DECLARE a variable, we can use ***let***, ***var ***or ***const***.
1. **var **is used to simply declare a variable name, whose value can be assigned later, or can even be changed, once initialized.

2. **const **is used to declare such a variable, which once INITIALIZED, its value cannot be changed later.

3. **let **is to declare a variable within a limited scope. It can be accessed in a limited block scope, where it is defined.

## Comments in JavaScript
Not every statement in JavaScript executes. If we wish to write some statements in JavaScript just for the clarity of the code, we can have some comments within the code.

```
//This is how a variable is DEFINED
//This is a comment
var x = 16;
``` 

In the above block, the third line will be executed normally, but the first and the second line is commented. Any line starting with // will not be executed and will be ignored by JavaScript interpreter.

// is used to define **single-line comment**. 
For **multiline comment**, we can use 

```
/* This is a 
multi-line
comment*/
``` 
Multiline comments are generally used for documentation purposes or can be used in code too.

## Typeof
This is used to get the type of the variable, some examples will clarify the concept:
1.  
```
var age = 18 ;
typeof (age)       // number
``` 

2. 
```
var name = "John" ;
typeof (name)    // string
``` 

3. 
```
var car ;
typeof (car)     // undefined
``` 

## Undefined and null
When we declare a variable in JavaScript and do not initialize it, it will have a value of undefined.
Null means NO VALUE, while undefined means the value is not defined, For Example:
1. 0/0 is an undefined value
2. Infinity - Infinity is an undefined value.


> 
typeof (undefined) is undefined

> typeof (null) is an object.

type of null should have been null, but we can consider it a bug in JavaScript, but in javascript, type of null is an object.

```
var name = '' ;
``` 
An empty value like this is not null. It has a well-defined type, which is a string. It is an empty value, but it is not null. null should not be confused with an empty value.

## = , ==, and ===
1. = is an **assignment operator**. When I write [var age = 18;], I am storing the number value 18 in the age variable.
2. == is a **comparison operator**, called '**equals**'. It will check if the left and right VALUES are equal or not and return 'true' or 'false' based on it.

I) 
```
2 == '2' // returns true
``` 

II) 
```
'Joe' == 'joe' // returns false
``` 


> 
[Identifiers in Javascript are **Case Sensitive**, i.e. 'age' and 'Age' are different variable names.]

III) 
```
null == undefined // returns true
``` 


3. === is another **comparison operator**, called **'strictly equal'.** This will check if the **value**, as well as the **type** of both the operands, are the same or not.

I) 
```
2 === '2' // returns false
``` 

> [The value of both is same, so with ==, it would give true, but === will check type also. 2 is Integer and '2' is String. So, the answer with === (strict comparison operator) is False.]

II) 
```
null === undefined // returns false
``` 

> [As we know that the value null and undefined are equal, but the type of undefined is undefined and the type of null is an object.]

Some Examples: 
> typeof (3) //number

> typeof (3.01) //number

> typeof ("age") //String

> typeof (true) //boolean

> var x;
typeof (x) //undefined

### I hope you understood the basics of **JavaScript**. DONT'T STOP. See the next article in the 'JavaScript basics series' for some more fun and learning.