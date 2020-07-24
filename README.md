# MERN Stack Combined App Deployment on Heroku

## Assumptions
1. You already have an App with Frontend and Backend folders like the below working on your local machine
    ##### 
       App
        |-- Frontend
        |-- Backend
2.	You have a basic understanding of deploying applications on Heroku

![MERN](https://github.com/Sasi-Koramutla/mernstackdeploy/blob/master/MERN.jpeg)
## Deployment Steps
#### 1. Go to your App’s Frontend folder in the command line
#### 2. npm run build 
This will create a "build" folder in your “Frontend”

#### 3. Copy the contents of the "build" folder in your “Frontend” to your “Backend/public” folder

#### 4. Go to “App.js” (or server.js, whatever file is your entry point for the backend server) in the root folder of our “Backend”
Add the below code at the top/where you declare the constants
```javascript 
const path = require('path'); 
```
Add the below code after your controllers. This code points to the React build folder
```javascript
EXPRESS_APP_NAME.use((req, res, next) => {
    res.sendFile(path.resolve(__dirname, "public", "index.html"));
});
```
#### 5. Keep the environment variables in .env and use “REACT_APP_” before all environment variables (example below). When you deploy on Heroku, you need to add them as "Config Vars"
```javascript
REACT_APP_BACKEND_URL=https://twitterbattle-test.herokuapp.com/
```
#### 6. Perform the regular Heroku deployment steps
-	heroku login
-	rm -r node_modules
-	heroku create “YOUR_APP”
-	git add, commit and push
-	git push push heroku master


