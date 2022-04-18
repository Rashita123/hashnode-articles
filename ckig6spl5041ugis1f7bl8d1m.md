## Interacting with the Browser using JavaScript (Basic) [Episode- 2]

## JavaScript is the 'Language of Browsers'.

### But, why do we need to interact with the Browser?
By interaction, we can make the browser do so many things apart from just browsing!


> 
Example: we can make Linkedin accept all the connection requests just by typing a single line of code in the browser. This is interesting. No?

Before doing this, let us understand the basics of how to interact with the browser.

### Console.log()

```
console.log("Hello World!")
``` 
**Console.log **simply takes in a parameter and print it to the console.

## Don't know where to find the console?

Go to your browser and visit any webpage. That can be Google.com also!

Right-click anywhere on the webpage and click on the Inspect Element. This is how it will look.


![22.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1607316713510/h5Vo3le7n.png)

After clicking on the **Inspect** Element, a new window will open on the right. Switch from '**Elements**' tab to the '**Console**' tab.



![66'.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1607320038813/Mj21czWFp.png)
> 
Console tab is where we can write some JavaScript code to interact with the browser, make the browser do a lot of fun tasks 😉 and even control the HTML of the file.

Type the command
```console.log("Hello World!");``` 
Press Enter.
You will see 'Hello World!' written on the Console. 
**This was the most basic interaction with the browser.** Congrats! Get Started now!

## Alert and Prompt
**Prompt **is used to take input and **Alert ** is used to give output to the user.

First, let us use **alert**


```
alert("This is an alert message!");
``` 

and press Enter. It will display a message like this:


![77.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1607320370188/noVBaRQ1A.png)

## Prompt command
Similarly, we can take input through this window prompt.


```
var username = prompt("Type your username: ");
``` 

This is how it will look:

![88.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1607320512697/A92__us6N.png)


> Note: I am attaching these screenshots for better understanding. If you are learning these commands for the first time, it is highly recommended, try them side-by-side.

## Now, Let's do the interesting part!!
We can accept all the Linkedin requests in a single line of code

On the console tab, type the following code.

```
var x = document.getElementsByClassName("invitation-card__action-btn artdeco-button artdeco-button--2 artdeco-button--secondary ember-view");
for(var i=0;i < x.length;i++)
{
x[i].click();
}
``` 
All the connection requests will be accepted in a second or so.

![Screenshot (425).png](https://cdn.hashnode.com/res/hashnode/image/upload/v1607324087027/CYeP-UkvV.png)
This is cool. No?

Try it yourself!


