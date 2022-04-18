## I bet you are messing with Reference Variables in JS!

Let us understand **Value and Reference types in JavaScript** in the most detailed way! This is part 2 of the series - **33 JavaScript concepts, every JS developer should know**.

[Part 1 - Do you understand Call Stacks well?](https://rashitamehta.hashnode.dev/do-you-understand-call-stacks-well) 

# Value types

We have a variable called **firstName**, which stores my name,

```
var firstName = "Rashita Mehta";
``` 
Internally, it would be a **memory block**, with 

**name of the memory block**--> firstName

**value** --> "Rashita Mehta" (a STRING)

and will have some address, say 1000.

![1.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609698947195/0_JAiC_s7.png)

### Primitive Types (or Value Types)
1. Numbers
2. String
3. Boolean
4. Null
5. Undefined
6. ES6 Symbols
> 
All the primitive data type variables are stored in the **stack **memory.


### There are two types of memory
1. Stack
2. Heap

## Stack
It is that part of the memory, which is short but stores all the **primitive type variables **and **handles function calls**.  [[Read this to know more about Call Stack]
](https://rashitamehta.hashnode.dev/do-you-understand-call-stacks-well-ckjh3jsrj0cb3g3s16rpj426r) 

All the **primitive type variables** are stored in the **Stack **part of the memory. For each new variable of primitive type, memory is given in the stack. Whereas, **complex data types** like **objects and arrays **are stored in the **Heap**. (We'll read more about this later!)


![11.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609759752883/n3tTAdh2B.png)

## Heap
**Heap **is that section of the memory, which stores the data types which are much more **complex **than the primitive ones. Let us see how things work internally in Heap!

### Reference Data Types
1. Array
2. Objects in JavaScript
3. Functions (Functions are also objects!)



> Reference Data Types are stored in the Heap and referenced thought Stack.

 


For example I have an array of names:

```
var names = ["Joe" , "Williams" , "Esma"];
``` 

It will be stored INTERNALLY as follows:


![2.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609753399536/mqsLlEJoY.png)

### How are complex types stored internally?
1. The actual Array or Object is stored in the HEAP.
2. It will have some address, let's say 1000 (which is the **base address **)
3. A **Reference** variable is created in the STACK, which has

**reference variable name** --> "names"

**Value **-->address of array/object in the Heap (1000)

and will have some **address **of its own, let's say 2000.

> 
This simply means that in case of reference data types, the memory is given in the HEAP, and there is a reference to it in the STACK, which contains the address of the actual variable in HEAP.

### Some points of difference between Value and Reference variables:
1. Copying the variable:

```
var x = 10;
var y = x;
console.log(x);
console.log(y);
``` 
OUTPUT

```
10
10
``` 
Now, if I change the value of x,

```
var x = 10;
var y = x;
x = 20;     //changed the value of x

console.log(x);
console.log(y);
``` 
OUTPUT

```
20
10
``` 
This means - when Value (or Primitive) type values are copied, an actual copy is made in the stack and a new memory is given to the variable y. So, when I change the value of x, the value of y remains unchanged.

**Understand through steps:**
1. First, x variable is made in the memory (Stack)
![3.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609755632078/fU9b93p5y.png)

2. Then a new Variable - y is made through he code 
```var y = x;
``` The value of x is copied to y and a new memory is given to y.
![4.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609755749734/lJ9CPzkuS.png)

3. When we change the value of x, only the value of x changes and the value of y remains unchanged.
![5.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609755782290/CEVEQ8esQ.png)


But, **this is not what happens in the case of Reference Variables**. let us take a look.

```
var book1 = {
    title: "Cashvertising",
    author: "Drew E. Whitman",
}  //object is created

var book2 = book1;  //a copy of book1 is created

console.log(book1.title);
console.log(book2.title)
``` 
OUTPUT

```
Cashvertising
Cashvertising
``` 
Now, if I change the title of book1,


```
var book1 = {
    title: "Cashvertising",
    author: "Drew E. Whitman",
}  //object is created

var book2 = book1;  //a copy of book1 is created

book1.title = "Writer's Guide";

console.log(book1.title);
console.log(book2.title)
``` 
OUTPUT

```
Writer's Guide
Writer's Guide
``` 
**The Title of the book2 also changed, while I changed the title of the book1 only!**

Let us see why this happened:
1. When a Reference Type (or Complex) variable is given memory, it is actually stored in the HEAP and its reference is made in the STACK.
![6.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609756767999/UXwDfkJvD.png)

2. When book2 object is created by copying book1 object, here is what happens:
![7.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609756826891/1G1cg66NA.png)

3. As we can see that both **book1** and **book2** refer to the same object, any change in book1 will also reflect in book2.
![8.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609756881200/YC75eYwTS.png)


> Summary: When a primitive type variable is copied, it is given separate memory in the stack, but when a Reference variable is copied, it refers to the same memory block in the Heap, and a new memory block is not created.

## 2nd Difference between Value and Reference Variable
### Comparison by value:

```
var a = 10;
var b = 10;
console.log(a==b);
``` 
**OUTPUT**

```
true //value of a and b is same.
``` 

![9.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609757433204/XtU7QxUTS.png)
Similarly, if I take an object (Reference Type data type)

```
var book1 = {
    title: "Cashvertising",
    author: "Drew E. Whitman",
}

var book2 = {
    title: "Cashvertising",
    author: "Drew E. Whitman",
}
console.log(book1 == book2);
``` 
OUTPUT

```
false
``` 

This is what happens INTERNALLY.


![10.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609757906663/jbor2P7FD.png)
1. The Value of the book1 is 1000(Address of book1 in HEAP), and

2. The Value of the book2 is 2000(Address of book2 in HEAP)

This is the reason that ```book1 == book2```  gives ```false```.


> Note: You might think that earlier, I gave the same memory block to the same objects, and now, I am giving different memory blocks to them!
 
> The reason is that --> In the first example, I made a **copy **of the **book1**. Due to this reason, no new memory was allocated to book2.

> But in this example, I am defining the book2 again. We know that I am defining book2 with the same properties as that of book1, but the computer doesn't know! So, it allocates a different memory to each object defined exclusively.


I hope this clears all your concepts about **Value and Reference Variables.**

This is part 2 of the series - **33 JavaScript concepts, every JS developer should know**.

[Part 1 - Do you understand Call Stacks well?](https://rashitamehta.hashnode.dev/do-you-understand-call-stacks-well) 

Stay tuned for the next part of the series! Good Luck!
