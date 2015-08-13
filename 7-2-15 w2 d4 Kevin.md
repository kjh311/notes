7-2-15 w2 d4


other CSS preprocessors: <a>https://blog.logentries.com/2014/10/which-css-preprocessor-should-you-choose/</a>

##SASS
Syntanticaly Awesome Style Sheet

compiles CSS, but uses less code

uses `.scss` file extension but ends up as a `.css`

uses a "watcher" that compiles into css then to the html

change file name from .css to .scss

`sass --watch css/style.scss:css/output.css` to add a watcher

`$font-stack:` is how to define a variable in SASS

easy to nest css `div{
ul{
li{
}
}
}` turns into:`div{}
			div ul{}
			div ul li{}` in css and auto formats
			
###Mixin

`@mixin`allows you to define layout in css and not have to repeat yourself.
`@mixin border-radius($radius){
  -webkit-border-radius: $radius;
  -moz-border-radius: $radius;
  -ms-border-radius: $radius;
  border-radius: $radius;
}`

`@include` to call the mixin`

`.box{
  @include border-radius(10px);
  background-color: red;
  height: 50px;
  width: 50px;
  @include border-radius(50%);
}`

###Inheritance

`.message{
  border: 1px solid $primary-color;
  padding: 10px;
  color: $primary-color;
}`

`.success{
  @extend .message;
}`Will inherit the propeties of `.message`

###Responsive Web Design

Responds to the browser size

`m.facebook.com` only for mobile 

Mobile first means designing for mobile then designing for bigger browsers.   

<a>http://getbootstrap.com/</a> for Bootstrap. Creates mobile first.

Flexible Layout:  Use % for Width instead of px.  

`      <meta name='viewport' content='width=device-width, minimum-scale=1.0, maximum-scale=1.0' />` so the webpage knows what device/computer user is using

`html{
  overflow-y: scroll;
}`

`curl http://www.f-covers.com/cover/superman-gallery-facebook-cover-timeline-banner-for-fb.jpg -O` in Terminal to have image saved to file

##AGILE

LEARNING OBJETIVES

1) Discuss Agile amongsts devs and potential emps.

2) Write Effective user stories

3)  Use Trello to organize user stories


##Homework

sign up for TRELLO <a>https://trello.com/</a>

build calculator in JS
- figure out for loop
- apply to tic tac toe
- figure out `.each` in JQuery instead of for loop

work on Shire JQuery