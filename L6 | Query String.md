 ## Basically we can ask data from client  from a query string  


const express = require("express");

const app = express();

app.get("/product",(req,res)=>{
  // res.send(`Response OK ${req.query.category}`);

  const {category,id} = req.query;
  res.send(`Product Category: ${category} & Product Id : ${id}`)
})

// http://localhost:8500/product?category=apple
// http://localhost:8500/product?category=apple&id=12  // separate them by &

app.listen(8500, () => {
  console.log("Server Up!");
});
