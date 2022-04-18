## Do you understand Call Stacks well?

Javascript is a tricky language and gives quirky results at times. This is part 1 of **33 JavaScript concepts, every JS developer should know.**

## 1. Call Stack
In any program, we have functions, which may/may not call other functions while executing its block. Let's take this example:

```
1  function box(){
2      console.log("I am in box function");
3      item1();
4  } 
5  function item1(){
6      console.log("I am in item1 function");
7      item2();
8  }
9  function item2(){
10    console.log("I am in item2 function");
11 }
12 box();
``` 
### What is happening in the code?
We know that no memory is allocated to a function definition, until or unless it is called. Also, a function is executed only when it is called. So, the program's control shifts to the 'box()' at line no 12 directly.

1. box function is called.
2. Control shifts to box block at line 1 and executes its block
3. It consoles **I am in box function** and then the next line is calling another function - item1. So, the execution of the box function pauses and the control shifts to line 5.

4. In the item1 function, it consoles **I am in item1 function** and then the next line shifts the control to item2().
5. **I am In item2 function** is consoled and the item2() function block ends.
> 
Note: When the execution of all the lines of a function block are complete, the control leaves that function and shifts to the function which called that function. 

6. After item2() function block is completely executed, it returns to line 7. (from where it was called)

7. In the function item1, now all the lines are completely executed and the control now returns to the function Box, at line no 3, from where item1 function was called.

8. Box function is completely executed now, and the program exits.

### Output of the program

```
I am in box function
I am in item1 function
I am in item2 function
``` 
### Now, what happens internally?

Function calls are stored in the section of the internal memory, called Stack. Stack is a data structure which follows LIFO (Last In First Out). Functions calls stack up in the memory, executes its block and then leaves the stack.
For our example, let us see what happens in memory through the following steps:

1. At first, Box function is called, so we have **Box function call** in the stack now. It prints **I am in box function** on the console and shifts to the next line.
![1.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609673404147/8pchiPas2.png)

2. Box calls another function called item1. So, the execution of box function stops for a while, and **item1 function call** stacks up in the memory.
3. Now, we have two function calls in the stack - Box (paused) and item1 (running)
![2.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609673984892/LmiBBuoIi.png)

4. First line of item1 prints **I am in item1 function** to the console and the control shifts to the next line.
![3.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609674051011/1qMxjSoR1.png)

5. The Second line of item1 calls another function- item2. So, item1 is paused for a while and the control shifts to the item2 function.
![4.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609674798799/9bSY09UZh.png)

6. We have 3 three function calls at this time in the stack - box (paused), item1 (paused) and item2(running).
![5.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609674820881/WL1o8KmgK.png)

7. The first line of item2 function prints **I am in item2 function **to the console.
8. Execution of the item2 function finishes and the control leaves the item2 function block. item2 function call pops from the stack and the control shifts to line 7 (from where it was called).
![6.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609674837341/z745XtrLp.png)

9. State of function item1 transforms from PAUSED --> RUNNING and then it checks for line 8.
![7.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609674865185/oONvKXdNy.png)

10. The item2 function block is also completely executed and item2 function pops from the stack.
![8.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609674892017/c9T7oIfTN.png)

11. The control shifts to box function (line 3) and the state of box function transforms from PAUSED --> RUNNING.
![9.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609674902842/tYhk4ZOdv.png)

12. Box function box ends at line 4. So, the program exits and the box function call pops from the stack.
![10.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609674912561/i9hMXvy6n.png)

13. Finally, the stack is empty and we have the following on our console.
![11.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1609674920832/poTtGF8PS.png)

**I hope I made this clear. This is how Call Stack works and functions are given memory internally.**

Stay tuned for the next part of this series --> **33 JavaScript concepts every Developer should know!
**