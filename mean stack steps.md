##Kevo's MEAN stack steps:


- `mkdir app_name`


- `cd app-name`

###STARTING Node application
(phil) `expresss` is the faster way (recommended!!)
`npm install -g express-generator` if not installed.
`express --ejs` to use ejs instead of jade
`express app-name --ejs --git` (then cd into folder)



- (slower way) `npm init` creates the package.json file.


- entry point should be the name of the the main file. Type `node (main_file).js` to run program.  The main file is where you require which packages you need and assign to variables. As well as which port the server is on. Instructions for someone who is downloading your app.  

- `nodemon (main_file).js` instead of just `nodemon` to keep server going after changes are made to file.


###Packages
- add dependencies/packages to the package.json file.

- `npm install express --save` to install package to the package.json file from the command line, will automatically find the current version.  This installs the packages inside the node-modules folder.

- `npm install` to install all packages.  

`npm install express mongoose passport --save` to install and save individual packages.

### Starting Node Server

`var express = require('express'),
    app = express(),
    path = require('path');`
    
##Routing Node Applications


###Express.Router()
- add routes to main page. 

call an instance of the router: `var adminRouter = express.Router();`

apply routes to it: `adminRouter.get('/', function(req, res){
  res.send('I am the dashboard!');
});`

then add those routes to our main app: `app.use('/admin', adminRouter);`  

`adminRouter.get('/posts', function(req, res){
  res.send('I show all the posts!');
});` will be set to /admin/posts, because the adminRouter at the beginning.

###Router Middleware(router.use())

middleware has to be placed before the routes you want to effect.

```// route middleware that will happen on every request
adminRouter.use(function(req, res, next){
  //log each request to the console
  console.log(req.method, req.url);
  //continue doing what we were doing and go to the route
  next();
});```
 
###Structuring Routes


##Mongo DB

run `mongod` in one terminal then `mongo` in another to start the mongo terminal and be able to enter commands.  

`show databases` show all databases

`db` show current database

`use db_name` select a database

`db.users.save({ name: 'Chris' });` CREATE

`db.users.save([{ name: 'Chris'}, { name: 'Holly' }])` for multiple users

READ
`db.users.find();`

`db.users.find({ name: 'Holly' });`

UPDATE
`db.users.update({ name: 'Holly' }, { name: 'Holly Lloyd' });`

DELETE
remove all:
`db.users.remove({});`

remove one:
`db.users.remove({ name: 'Holly' });`

##Using Mongoose

Robomongo is a GUI for database tasks!!!

MongooseJS is for working with Node and MongoDB.

grab the packages we need
`var mongoose = require('mongoose');`

`mongoose.connect('mongodb://localhost/db_name');`

##Building a restful API

http://www.slideshare.net/landlessness/teach-a-dog-to-rest

We will need to define our Node packages, start our server using Express, define our model, declare our routes using Express, and test our API.

add dependencies to package.json manually or entering into the terminal:
`npm install express morgan mongoose body-parser --save`

`npm install` if added manually.

in main_file, call the packages: 
`var express = require('express');`
`var app = express();`
`var port = process.env.PORT || 8080`

To connect to a database locally:
`mongoose.connect(localost:8080/myDatabase`

Create a mongoose model to handle users.

`var mongoose = require('mongoose');
var schema = mongoose.Schema;
var bcrypt = require('bcrypt-node.js');

var UserSchema = new Schema({
  name: String,
  username: { type: String, required: true, index: { unique: true}},
  password: { type: String, required: true, select: false}
});`

