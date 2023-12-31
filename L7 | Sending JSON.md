## this is how we send data from backend to client  using json


const express = require("express");
const products = require('./products.js')

const app = express();


app.get('/',(req,res)=>{
   res.json(products)
})

app.listen(8500, () => {
  console.log("Server Up!");
});


<!-- filename - products.js -->

const product =  [
    {title:"Some Title", company:"Nike"}
]

// export default products;
module.exports = product;