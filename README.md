# 14-full-stack-homework: Reverse Engineering Code

User story:
AS A developer,
I WANT a walk-through of the codebase,
SO THAT I can use it as a starting point for a new project.
<hr>

Codebase walk-through:

"Server.js" is the base file that starts the app, connecting the front and back end. It contains the requirements for the necessary npm packages, models, config files, and routes. It also sets the port for local host.

The config folder contains "config.json", "passport.js", and a middleware folder. "config.json" contains database connection info for the development, testing, and production stages. "passport.js" is connected to models, and contains login information. It tells passport that we want to log in using an email address and a password, and has authentication for both. The middleware folder contains "isAuthenticated.js" which restricts the routes a user can visit if they aren't logged in. If they try to access a blocked route, the user will be redirected to the login page.

The models folder contains "index.js" and "user.js". These files deal with the database structure and the logic for sending/receiving data. "user.js" creates the user model and requires a proper email and password. bcryptjs is required for password hashing, and will compare an unhashed user entered password to a hashed one stored in the database. This is done automatically before the user model is created. "index.js" contains the relational info for configuring new models and accessing previous ones. 

The public folder contains html files for login, members and signup, plus sub-folders for js ans stylesheets. The html files along with their corresponding js files render what the user sees on the login, signup and members pages and have event handlers that submit and return data based on the user inputs. Login and signup both send data to the database, and the user is then allowed to aceess the route to the members page if their submission info is valid. The stylesheets sub-folder contains the "style.css" file which has additional styling for the login and signup forms.

The routes folder contains "api-routes.js" and "html-routes.js". These two files work together to send information to and from the database. "api-routes.js" is connected to "passport.js" in the config folder and the models folder. It contains the routes for logging in or signing up a user based on valid input, and also the route for logging out. "html-routes.js" is connected to the middleware file "isAuthenticated.js" and takes information being returned from the database and routes it to the appropriate html page based on validation.

Finally the "package.json" file contains application information such as the name, version, author and the main file to start it up. It also lists the dependencies, which for this application are bcryptjs, express, express-session, mysql2, passport, passport-local, and sequelize. 

If you wanted to change this project, one way would be to switch the database type. MySQL or Mongo are some types that could be used if you didn't want to go with sequelize. More public files and routes could also be added to expand the features of the application.




