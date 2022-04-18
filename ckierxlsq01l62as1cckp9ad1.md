## Accepting Linkedin Connection requests using JavaScript

### JavaScript is the 'Language of Browsers'. 

### We can accept all the Linkedin requests using a *single *line of code
We get so many connection requests every day. It is a tedious task to accept them one by one.

![linkedin5e-multiple-invitations.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1607325325079/ZDp7WJ3nS.jpeg)

On the console tab, type the following code. This will accept all the connection requests in a jiffy.

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


> Note: This works for Instagram too!