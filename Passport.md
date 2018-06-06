passport is authentication middleware for node.js
uses sessions to keep track of who logs in


order is important
AFTER:

require('dotenv').config();
const express = require('express')
    , session = require('express-session')
    , passport = require('passport')
    , Auth0Strategy = require('passport-auth0');

const app = express();
const {
    SERVER_PORT
} = process.env;



app.listen(SERVER_PORT, () => {
    console.log(`Preposterously Posthumaning on port: ${SERVER_PORT}`);
})


-------------------------------------///\\\\///\/\/\///\\///\\//\\//\\//\\//\\//\\//\\//\\


FIRST:
<!-- dont forget your secret value in env file -->
const {
    SERVER_PORT,
    SESSION_SECRET
} = process.env;

app.use(session({
    secret: SESSION_SECRET,
    resave: false,
    saveUninitialized: true
    <!-- saveUninitialized: true means that the first time they interact with the server, gives them a cookie -->
}))


SECOND:

app.use(passport.initialize())
app.use(passport.session());

<!-- your app will break if you do these out of order
passport.session allows you to grab info and put it on the sesssion  -->


passport.use(new Auth0Strategy({

}))

IN .ENV FILE GRAB DOMAIN, CLIENT_ID, AND CLIENT_SECRET FROM AUTH0 WEBSITE FOR INITIAL LOGIN
----------------
SERVER_PORT=3005
<!-- session_secret can be any text -->
SESSION_SECRET=gdfghgdfsghfgdgsfgfhgdsfgfhgdsgfhgdghgjhdsgfhg;
DOMAIN=jhfirst.auth0.com
CLIENT_ID=QRYAUM9skq7hhdYUelTGX0rDyXLjZ54I
CLIENT_SECRET=PY0flJIKOL8G7-zrt6PaIm-aTua7O526OcWEzVCkiv0QBj1nvvtLt2fvYxeSMpol
CALLBACK_URL=http://localhost:3005/auth/callback

You will have errors at this point until fully setup
\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\
take the value of your CALLBACK_URL and on auth0's website, put it as one of the allowed callback URL's

End result should be like this:
index.js

require('dotenv').config();
const express = require('express')
    , session = require('express-session')
    , passport = require('passport')
    , Auth0Strategy = require('passport-auth0');

const app = express();
const {
    SERVER_PORT,
    SESSION_SECRET,
    DOMAIN,
    CLIENT_ID,
    CLIENT_SECRET,
    CALLBACK_URL
} = process.env;

app.use(session({
    secret: SESSION_SECRET,
    resave: false,
    saveUninitialized: true
}))
app.use(passport.initialize())
app.use(passport.session());

passport.use(new Auth0Strategy({
    domain: DOMAIN,
    clientID: CLIENT_ID,
    clientSecret: CLIENT_SECRET,
    callbackURL: CALLBACK_URL,
    scope: 'openid profile'
}, (accessToken, refreshToken, extraParams, done) => {
    done(null, profile)
    // null deals with error handling, the second argument is the data we want passed on
}))

passport.serializeUser((profile, done) => {
    done(null, profile);
})
passport.deserializeUser((profile, done) => {
    done(null, profile);
})
// this is the endpoint that the user will hit /auth can be called anything
app.get('/auth', passport.authenticate('auth0'))
app.get('/auth/callback', passport.authenticate('auth0', {
    // we can define things we want to happen in here
    successRedirect: 'http:localhost:3000/'
}))

app.listen(SERVER_PORT, () => {
    console.log(`Preposterously Posthumaning on port: ${SERVER_PORT}`);
})
