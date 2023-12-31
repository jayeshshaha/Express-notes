
## Watch video for clear  understanding

const express = require("express");
const app = express();

const path = require('path')

app.use(express.static('./public'))

// static -> built in middleware it allows us to serve static files 

app.get('/',(req,res)=>{
  res.sendFile(path.join(process.cwd(),'./public/index.html'))
})

app.listen(8500, () => {
  console.log("Server Up!");
});


