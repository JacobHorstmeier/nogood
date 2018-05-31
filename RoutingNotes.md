_-_-_-_-_-_-_-_-_-_-_-_Setting Up Routing_-_-_-_-_-_-_-_-_-_-_-_-_

Routing is used to provide multiple views within a Single Page Application (SPA)

Make sure that you have run (npm install react-router-dom) react-router-dom contains the DOM bindings for React Router.
    In other words, the router components for websites


             Using React Router: 4 Components

<Router> = The router that keeps the UI in sync with the URL
<Switch> = Renders the first route that matches the URL
<Link> = Renders a navigation Link
<Route> = Renders a UI component depending on the URL
<!-- <HashRouter> uses the hash portion of the URL -->

<!-- When you run npm install one of the packages installed is json-server. This library will mimic a REST api and allow you to make HTTP requests for data -->
<!-- Another package that was installed is concurrently. This library will allow to run multiple scripts in a single terminal window -->

To begin setting up your router, make a new file in ./src called routes.js

Be sure to import React, Switch and Route and any components that you plan to use
Note: Routing will try to render elements with the same base path, so make sure you set 'exact path' on the home '/' Route Component
////////////////////////// Example Code \\\\\\\\\\\\\\\\\\\\\\\\\\\\\
 in the ./src/routes.js'
<!-- 
                    import React from 'react';
                import { Switch, Route } from 'react-router-dom';
                import Home from './components/Home/Home';
                import About from './components/About/About';

                export default (
                <Switch>
                    <Route component={ Home } exact path="/" />
                    <Route component={ About } path="/about" />
                    <Route component={ ClassList } path='/classlist/:class' />
                    <Route component={ Student } path='/student/:id' />
                </Switch>

) --> Note: paths with unique key identifiers require the /:id (or whatever it is you are measuring)
    
Next we want to take the routes we just configured in ./src/routes.js and add it to our app in ./src/index.js

Import HashRouter from react-router-dom so we can path things through the hash portion of the URL
To make routing work we need to wrap our react application with the HashRouter component

////////////////////////// Example Code \\\\\\\\\\\\\\\\\\\\\\\\\\\\\
./src/index.js
<!-- 
                    ReactDOM.render(
                    <HashRouter>
                        <App />
                    </HashRouter>
                    , document.getElementById('root')); -->

Now we can render our router anywhere in the app, go ahead and import routes into our ./src/App.js
<!-- often it is rendered under the nav element in App.js -->

Import Link from react-router-dom. The Link component allows us to add clickable links into the DOM so the user can navigate the app.
The Link Component uses a 'to' prop to determine which route to navigate to.

////////////////////////// Example Code \\\\\\\\\\\\\\\\\\\\\\\\\\\\\
<!-- 
<Link to="/" className='links'>Home</Link>
<Link to="/about" className='links'>About</Link> 
<Link to='/classlist/MATH1010'><button className='btn'>Math 1010</button></Link>
 --> Note: buttons can be placed inbetween Links




