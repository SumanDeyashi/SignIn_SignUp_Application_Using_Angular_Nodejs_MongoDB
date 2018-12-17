# SignIn_SignUp_Application_Using_Angular7_Nodejs_MongoDB
# Description:

Company(Hashworks IT Services Private Limited)_Internship_Project.

Download all folders and put it in one folder. After that open both folder on Visual Studio Code editor and install Node modules with help of "npm install" command on both folder using two different terminal. Then, comiple the front end part using "ng serve" command and for back end part using "node app.js" command. Finally, open it on your favorite browser using http://localhost:4200 url.

Technology Used: HTML/HTML5, CSS/CSS3, Angular7, Nodejs, MongoDB.

Duration: Nov, 2018 to Dec, 2018.

# Procedure:

# Front_End_Part:

First thing you have to do create an angular project using "ng new 'project name' " command and for creating components using "ng g c 'component name' " command.

Here, created four components auth, shared, user-profile, user component. user-profile handle the user dashboard part after loggedIn and user component contains signIn and SignUp functionalities. Everything are designed with HTML/HTML5 tag and for style used CSS/CSS3 property.

Now let’s design two tabs in user.component.html – one for login form and one for user registration form. so let’s update user.component.html routerLink set href attribute for anchor element. routerLinkActive apply css class "active" when current url is same as anchor href. Simple form validation is implemented. Error div will display error message stored inside the property, after form submit event.

UserService class function login is to be defined, inside that we make post request to "/authenticate" from Node JS API by passing email and password. Inside the success callback function, we save jwt inside local storage with key – "token" and the userProfile component will be shown. Error callback will store the error message in serverErrorMessage property. along with setToken function we have functions for reading and deleting jwt token from Local Storage. 

So let’s block such type of unauthorized request. for that used guards from Angular – auth.guard.ts. Inside this guard function –  canActivate, need to define the criteria to check whether a user is logged in or not. If not logged in, re-direct the user to login page, delete his token and return false. Otherwise it return true. 

Inside user profile component I want to show the details of logged in user. so first of all define getUserProfile function in UserService. Implemented this "/userprofile" as a private route in Node JS, so have to send jwt token in request header.

Finally,if you want to redirect the user to user profile when authorized user access login page. You can update the sign in component ngOnInit lifecycle.

# Back_End_Part:

For back end need to install npm packages – express, mongoose, body-parser, bcryptjs and cors using "npm i --save express mongoose body-parser bcryptjs cors" command. Now, need to start MongoDB server. I used MongoDB Compass Community. Create a new Database. Let’s create a mongoose model for user details. For that need a model file user.model.js inside models folder.

Inside password field will store encrypted password. Password encryption can be done using bcryptjs. Before encryption password will be merged with a random string (salt secret). Which is more secure than direct password encryption. Defined some validations like required validation, minlength validation and custom validation for email pattern. Also unique constraint for email address.

Inside the folder let’s add config.json file to store configuration details like PORT number for express server and MONGODB_URI for database details. Now, can save new user details inside MongoDB using mongoose model. Here, exported register function, which can handle user registration request. Inside the save function have a callback function to be executed after save operation.
 
Now it’s time to create the route javascript file – app.js. All of the modules inside application are executed from route file.
 
Finally, started the express server at port number. Now in-order to add a new user, we have to make a post request to ‘/api/register’ with new user details.










