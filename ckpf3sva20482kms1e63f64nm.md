## Writing Pure Functions in JavaScript

![fp7main.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1622611231004/feFHaamgs.jpeg)

## What is Functional Programming?

Functional Programming is a programming paradigm. It is a coding style. If you know JAVA or C++, they follow the Object-oriented programming style, which says that everything is an object. Object-oriented coding style came up to solve several security issues. Hence, it introduced the concepts like Encapsulation, and Abstraction, etc. Other coding paradigms include imperative, procedural, and declarative paradigms, etc.

Functional Programming came up to solve another set of problems, which we will look into in this blog. It's an approach to write code where we write **pure functions**, **declaratively**, use **higher-order** functions, and practice **immutability**.

## What is a function?

A function simply takes input in the form of arguments, processes the arguments, and then returns the output. We normally write functions that can read or mutate global variables, but functions allowed in Functional Programming are different. They need to abide by a set of rules. Only pure functions are allowed in functional programming. 


![functionFlow.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1622611271298/Rc__CYEFo.png)

## What are Pure functions?

Consider the following function.

```jsx
const add = (a,b) => {
	return a+b;
}
```

This is a normal function, which takes in two arguments, adds them, and then returns the sum.

> Pure functions return the same output given the same set of arguments, and have no side effects.

Clearly, function add will return the same output for same set of inputs. Hence, it is a Pure function.

## What makes a function pure?

**Rule 1:** Avoid shared state

**Rule 2:** Avoid mutating states

**Rule 3:** Avoid side Effects

Let us understand this using examples:

## Rule 1 says - Pure functions do not share states.

Consider this function, which takes in name and displays a message.

```jsx
const printMyName = (name) => {
  return `My name is ${name}`;
}
console.log(printMyName('Payal'));
```

This function depends merely on its arguments to compute the output. Now, consider another function.

```jsx
let message = 'You have a notification, ';
const notify = (name) => {
	return message+name;
}
console.log(notify('Sakshi'));
```

If we try to refer to some variable, which is **global or is outside the scope** of the function, it is not a pure function. **A pure function takes in arguments, processes those arguments, and then generates an output computing them only**. They don't refer to a global variable or even change them inside the function


## Rule No 2 says - Do not mutate external states

Consider this code snippet

```jsx
let name = 'Harshit';
const printMyName = () => {
  name = 'Payal'
  return `My name is ${name}`;
}
console.log(printMyName());
console.log(name);

// Output 
//My name is Payal
//Payal
```

This function is performing a **mutation operation**. Hence, it is NOT a pure function.

## Why should we avoid mutating states inside the pure function?

![fp10.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1622611373102/Fxe00mA0A.png)

1. In web apps, we generally have a lot of event handlers, which are primary functions. If they are impure functions, i.e. they can read/change the outside/global variables, then it would be hard to predict the output and debug as to which function has changed the variable value.

2. Some functions execute then and there, and some take some time to execute. It's hard to predict which function will take how much time to execute. Hence, making it hard to predict which function changed the value of a variable first.

### Take this example to understand:

1. Initial value of the variable `counter` is 1. 
2. First function `makeFifteen()` is called.
3. Then function `makeTwenty()` is called.

```jsx
let counter = 1;
console.log('Line 57: ',counter);

const MakeTwenty = () => {
	setTimeout(()=>{
	counter = 20;
	console.log('After Increment ', counter);
	}, 2000)
}

const makeFifteen = () => {
	setTimeout(()=>{
	counter = 15;
	console.log('After decrement: ',counter);
	},4000)
}
makeFifteen();
MakeTwenty();
```

**What do you think will be the final value of the variable - `counter`?**


![Untitled.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1622611404680/M5x7W_ny8b.png)

Even if you guessed it right, that was possible only because here, we already know how much time the functions will take to complete their execution. In reality, we would not know how much time the asynchronous function will take. 

> Note: It doesn't matter which function you typed first or last, but the function that gets to execute at the last will always win. The mutation caused by the last function to execute will show up in the variable.

This means that in case a lot of functions have the same shared state, and these functions are free to mutate them, it will lead to bugs for sure in the future because it's hard to track, which function changed the variable, especially, when the functions are asynchronous, and it's hard to predict how much time will they take to complete the execution.

## Rule No 3 says- Avoid Side Effects

### What are Side Effects?

> 
"When we call a function, what does it need that isn’t in the argument list, and what does it do that isn’t part of the return value?” - Kris Jenkins

The hidden inputs the function uses to execute completely can be referred to as ```'side-causes'```, and the hidden impacts of the function execution can be referred to as ```'side-effects'```.


```jsx
const printName = (name) => {
  console.log(`Hey! My name is `,name);
}
printName('Rashita');
```

This function creates a side effect because the function is not only processing the arguments it has received, but is producing a change in the outside environment too, i.e. printing something to the console.

Hence, `console statement`, `HTTP calls`, `mutation`, and `writing to the disk`, etc are considered as **side effects** and the function becomes **Impure**.

![pure.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1622611440088/Y-JxiEoj4.png)

Let us consider another example:

```jsx
const returnGreetings = (name) => {
  var d = new Date();
  var hours = d.getHours();
  if(hours>=0 && hours<12){
    return `Good morning, ${name}`;
  }
  else if(hours>=12 && hours<=7){
    return `Good evening, ${name}`;
  }
  return `Good night, ${name}`;
  //This will show time and Date according to GMT, 
	//we can convert to IST or any other time zone
}
returnGreetings('Radhika');
```

**This is NOT a pure function,** because the return value depends on **WHEN** I'm calling this function, in addition to its argument. ```new Date()``` here is a **side-cause or a hidden input**. A pure function should only depend on the arguments it receives.

Consider this function now - In the E-commerce web site:

```jsx
function calculateTotalCartSize = (cartList) => { 
	This function will calculate the size of the cart using the cartList;
	return count;
}
```

1. This function gives us the size of the cart when we want to display the badge over the bag icon in the header component.
2. We need to know the cart size INSIDE the cart component as well.

![kjbfe.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1622611474976/s88d10mXz.png)

If we pass the cartList in this function from anywhere within the app, we will get the same result, i.e. the count of items in the cart. This function depends only on the arguments. The function will map over the list and get the total count and then return the count. `This is pure function.`

Hence, pure functions are the one which will always return the same value for the same set of arguments, whatever be the time or place we are using it. It doesn't matter which file is using that function to get the result.

### What does not qualify as pure functions?

Functions processing hidden arguments.

1. If the function depends on the **user input or any sort of I/O,** it isn't a pure function.

2. If we generate **random numbers**, the returned value will change every time.

Functions returning hidden outputs.

1. Functions that create side effects like **printing something to the console, writing to the database, throwing exceptions, or hitting API calls** are impure.

2. If the function **mutates **the arguments or global variables, it loses its purity.

### Why are hidden inputs or outputs, a problem?

1. While working on large codebases, it becomes hard to predict the output of the code snippets which depends on the external code.

2. If my code depends only on the arguments it is receiving and produces no output other than the return value, it's easy to test and debug the code in isolation.


### Mutating Arrays/Objects

Consider this:
```
const post = {
  postId:1,
  likes:20,
};
const incrementLike = (post) => {
  post.likes++;
}
console.log(post);
incrementLike(post);
console.log(post);
//output:
//{postId : 1, likes : 20}
//{postId : 1, likes : 21}
``` 
Here the **scope of mutation is not limited to the function**. This is because:

When we pass objects or arrays as arguments to a function in JavaScript, their **reference is actually passed to the function**. So, if we try to mutate the object/array inside the function, we are actually mutating the original object/Array. 

### So how to perform the mutation task in the functional programming way?

We can create a new object/Array. Mutate it the way we want, to achieve the goal of the function, and then return the new one with the desired changes. **That's how pure functions work.
**

```
const post = {
  postId:1,
  likes:20,
};
const incrementLike = (posts) => {
  const newPostObj = {...post, likes:post.likes+1};
  return newPostObj;
}
console.log(post);
console.log(incrementLike(post));
console.log(post);
//output:
//{postId : 1, likes : 20}
//{postId : 1, likes : 21}
//{postId : 1, likes : 20}
``` 
See, the **origin post Object remained the same**, whereas we have the new object with the desired changes reflected in it.

### Now you know the answer to a common JS interview question


![fp2.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1622611509512/dKbUOX4O-.jpeg)

## Is that all?

**Note: Functional Programming is not just about writing Pure Functions. It's much more than that!**

Functional Programming follows the following Rules:

1. Using Pure Functions
2. Using Higher-Order Functions
3. Function Composition

We'll talk about the remaining two practices in `Functional Programming Part II` of this blog.

## Extended Reading Material:

[What is Functional Programming](http://blog.jenkster.com/2015/12/what-is-functional-programming.html)

[What are pure functions and Why to use them?](https://medium.com/@jamesjefferyuk/javascript-what-are-pure-functions-4d4d5392d49c)

[Youtube: Learning Functional Programming with JavaScript](https://www.youtube.com/watch?v=e-5obm1G_FY)