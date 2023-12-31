Middleware is just a js function it takes 3 parameters (req,res,next) and it will do something 

## why using ?
middleware mainly for authentication purpose

//  Demonstration : user entering our site
/*
  - Request

  - Middleware

  - Response

*/

const express = require("express");
const app = express();

//  we can like use bult-in middelware app.use() =>  app.use(userCredentials) now we dont have specify between req and res

function userCredentials(req,res,next) {
  console.log('username : (alex)');  // just pretend that we are getting this data from the real user
  console.log('email : (dummy@gmail.com)');
  console.log('password : (alex22212)');
  next();
}

app.get('/',userCredentials, (req,res)=>{
   res.send("<h1>Hello Admin</>")
})


app.listen(8500, () => {
  console.log("Server Up!");
});
