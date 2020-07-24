# MERN Stack Combined App Deployment on Heroku

## Assumptions
1. You already have an App with Frontend and Backend folders like the below working on your local machine.
    ### App Directory
        - Frontend
        - Backend
2.	You have a basic understanding of deploying applications on Heroku


## Deployment Steps


1.	Go to your App’s Frontend folder in the command line
2.	npm run build 
    -	this will create a build folder in your “Frontend”
    -	copy the contents of the build to your “Backend/public” folder
3.	Go to “App.js” (or server.js, whatever file is your entry point) in the root folder of our “Backend”
    -	Add the below code at the top/where you declare the constants
            ```javascript 
            const path = require('path'); 
            ```
    -	Add the below code after your controllers. This code points to the React build folder
            EXPRESS_APP_NAME.use((req, res, next) => {
            res.sendFile(path.resolve(__dirname, "public", "index.html"));
            });

4.	Keep the environment variables in .env and use “REACT_APP_” before all environment variables. Example below.
    a.	REACT_APP_BACKEND_URL= https://twitterbattle-test.herokuapp.com/
5.	Perform the regular Heroku deployment steps
    a.	heroku login
    b.	rm -r node_modules
    c.	heroku create “YOUR_APP”
    d.	git add, commit,  and push
    e.	git push push heroku master



For lab, you'll continue on your own to click the balloons in order to increase likes and press the pencil to show a pre-filled form to let you edit the whole field:

![holidays app lab portion](https://i.imgur.com/CvFFanb.png)

## Set Up

In student examples for today:

ADDS an image of folder structure from SkETCH!!!

1. `mkidr holidays`
1. `cd holidays`
1. `mkdir holidays_api`
1. `cd holidays_api`
1. `touch server.js`
1. `npm init -y`
1. set entry point as server.js
1. `npm install express`

## Set Up Express Server

server.js:

```javascript
const express = require('express')
const app = express()
const PORT = 3003

app.listen(PORT, () => {
  console.log('🎉🎊', 'celebrations happening on port', PORT, '🎉🎊',)
})
```

