# SignIn_SignUp_Application_Using_Angular7_Nodejs_MongoDB
# Description:

Company(Hashworks IT Services Private Limited)_Internship_Project.

Download all folders and put it in one folder. After that open both folder on Visaul Studio Code editor and install Node modules with help of "npm install" command on both folder using two different terminal. Then, comiple the front end part using "ng serve" command and for back end part using "node app.js" command. Finally, open it on your favorite browser using http://localhost:4200 url.

Technology Used: HTML/HTML5, CSS/CSS3, Angular7, Nodejs, MongoDB.

Duration: Nov, 2018 to Dec, 2018.

# Procedure:

# Front_End_Part:

First thing you have to do create an angular project using "ng new 'project name' " command and for creating components using "ng g c 'component name' " command.

Here, created four components auth, shared, user-profile, user component. user-profile handle the user dashboard part after loggedIn and user component contains signIn and SignUp functionalities. Every thing design with HTML/HTML5 tag and for style used CSS/CSS3 property.

Now let’s design two tabs in user.component.html – one for login form and one for user registration form. so let’s update user.component.html routerLink set href attribute for anchor element. routerLinkActive apply css class 'active' when current url is same as anchor href. update signIn.component.ts with following properties, we need them for designing login form.

Now let’s update corresponding html file. top div image is there in img folder. simple form validation is implemented as we have seen in previous user registration tutorial. error div will display error message stored inside the property (serverErrorMessages), after form submit event. Now let’s implement the submit event by defining the function – onSubmit inside component Typescript file.

UserService class function login is to be defined, inside that we make post request to ‘/authenticate’ from Node JS API by passing email and password. Inside the success callback function, we save jwt inside local storage with key – ‘token’ ( setToken function is to be defined in service class) and the userProfile component will be shown. Error callback will store the error message in serverErrorMessage property.

Now let’s update UserService class with new functions. along with setToken function we have functions for reading and deleting jwt token from Local Storage. Inside the signIn component, we have created an object of UserService class, as part of service class injection in app.module.ts file. so you have to remove the service class from signUp component providers array( added during user registration form design). Now add them in app.model.ts file.

So let’s block such type of unauthorized request. for that we use guards from Angular, we have created a guard – auth.guard.ts. Inside this guard function –  canActivate, we just need to define the criteria to check whether a user is logged in or not. For that we have called isLoggedIn fuction ( which is to be defined). If not logged in, we re-direct the user to login page, delete his token and return false. Otherwise it return true. getUserPayload function will return information stored in jwt payload, if there is no token it returns false. Inside isLoggedIn function we call getUserPayload, if there is token it will check for token expiration using exp claim. Now we need to use AuthGuard  class in routes.ts file. Before that we have add guard class in app.module.ts file.

Inside user profile component I want to show the details of logged in user. so first of all define getUserProfile function in UserService. Implemented this ‘/userprofile’ as a private route in Node JS, so we have to send jwt token in request header. Before that let’s design the component. so we can update user-profile.component.ts. Inside ngOnInit lifecycle hook, user details send from the API is stored in userDetails property. 

Finally if you want to redirect the user to user profile when authorized user access login page. You can update the sign in component ngOnInit lifecycle.

# Back_End_Part:



