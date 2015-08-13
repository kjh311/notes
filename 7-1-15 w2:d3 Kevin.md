7-1-15

tic tac toe solution is available in w2 d3 

http://marxi.co/  another md note taking app

#J Query
Dom interaction made easy! 

Explain what jQuery is: a javascript open source library, makes front end developing easier.

55% of websites have it, on a slight decline though.  AngularJS is becoming more popular. 

What can JQuery do? 

Lets you select elements and do something with them.

Nothing that JQuery can do can't be done with just JS.  

Don't have to worry about cross browser compatibility issues.  

Makes us more productive with less typing.  

Easy to add animation, easier to use AJAX(sending data to servers).  

2 ways to install JQuery, download to project folder and link to it, or link to the library online in a script tag(CDN: content delivery Network). If you download the library you can continue to develope offline. 

`jquery.com/download`

Be sure to load (link) JQuery BEFORE and code that uses it.  Link to your own js file AFTER the JQuery link.  

`.min.js` means a minified version of JQuery, so it doesn't take up as much space.  About a third in size. 

CodeKit minifies your css and html and javascript files.

`cp -R fellowship/instructor` to copy directory.  Don't add `/` to end! 

After code has been minified you don't want to edit it, save the original!!

User interaction is the main reason to do Dom Manipulation.  

`jquery.2.1.1`

`<script src="https://code.jquery.com/jquery-2.1.1.min.js"></script>` right after `<head>`  

`$('CSS selector');`  `$('#id');` to select id. `$('.class')` to select class, just like how it's written in CSS.

`$('p, li');` to select multiple

Getters and Setters are designed to get an element AND change it.

`eq(0)` selects index of wrapped elements

`<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css">` BootStrap


##Git

`git branch` branches off master.  `git merge` branches back into master.

####Lesson Objectives
1) Understand why we use branches

2) create a branch

3) understand use case of issues

`git checkout` changes between branches.

make a new branch for each new feature

Issues: bug, improvements



