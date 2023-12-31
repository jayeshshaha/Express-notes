const express = require("express");

const app = express();

 <!-- Notes  -->
// Route Params
// Route Params we use to capture data from the user via the URL.
// They are defined by placing a colon : in front of the parameter name in the route definition.
// For instance, in a URL like /users/:userId, the :userId part is a route parameter. When a user navigates to a URL like /users/123, the value 123 is captured as the userId parameter

// Ex 1
app.delete("/student/delete/:id", (req, res) => {
  // req.params will store this id
  res.send(req.params.id);
});

// Ex 2
app.get("/ecomerce/products/iphone/:model", (req, res) => {
  const input = req.params.model;
  res.send(`Iphone ${input} was  seclected`);
});

// Ex 3
app.get("/products/:category/:id", (req, res) => {
  const { category, id } = req.params;
  res.send(`Product category (${category}) & product id (${id})`);
});

// Ex 4
app.get("/student/:name/:age", (req, res) => {
  const { name, age } = req.params;
  res.send(`Student name is ${name} & his age is ${age}`);
});

app.listen(8500, () => {
  console.log("Server Up!");
});


<!-- app.param()  -->
In Express.js, the app.param() function is used to handle dynamic route parameters. It allows you to define middleware that will be executed when a specific parameter, such as id, is present in a route URL. This middleware function will run before any route handler that includes the specified parameter.

app.param("id", (req, res, next, id) => {
  console.log(`id: ${id}`);
  next();
});  //  => this is middleware

app.get('/user/:id', (req, res) => {
  console.log("This is the user ID path");
  res.send("Response OK");
}); // => this is router handle 

app.param("id", ...) is registering a middleware function that will be executed whenever the route includes the :id parameter.
When a request is made to a route like /user/:id, and a value is provided for :id, the middleware specified by app.param() will be triggered.
In this case, the middleware logs the id parameter value to the console using console.log('id: ${id}').
After logging the id, it calls next(), allowing the request to proceed to the next middleware in the chain or the route handler itself.
Then, when a request is made to /user/:id, the defined middleware will log the id value provided in the URL. Subsequently, the route handler for /user/:id will execute and respond with "Response OK".