---
layout: post
title:      "React/Redux App"
date:       2018-02-08 11:15:36 -0500
permalink:  react_redux_app
---



I completed my final project yesterday for Flatiron School using React and Redux to make a "one page" webapp.  For the project, I modeled the app for use as a Flight Scheduler.  As a private pilot in a flying club, where about 30 people share the use of 5 planes, there is a need to schedule the use of planes and to easily be able to see availability at a glance.  This basic app allows a pilot to input details of the flight and for other users to view scheduled flights.  I've intended for this to be a simple app for quick use but have also added a feature that fetch's avaitiona weather information (in this case the Metar) from the avwx.rest api.  

One of the areas that I spent some time on was understanding an implementing routes.  From building ruby applications, I under stand them from an MVC perspective where views can be there different routes but how does that translate to react/redux?  Most of the tutorials and blogs show how they create a different component with routes and have that imported for use in a top level component.  I went ahead an used my App.js file to implement the routes shown below.  Its easy to understand on the surface but it can get confusing once you add the information to your own app (as each example will be different).

```
const App = (props) => {
  return (
    <Router>
      <div className="app">
        <NavBar />
        <Route exact path="/" component={HomePage} />
        <Route  path="/flights" component={FlightIndex} />
        <Route  path="/flights/:id" component={ShowFlight} />
        <Route  path="/new" component={CreateFlight} />
      
      </div>
    </Router>
  );
};

export default App
```
