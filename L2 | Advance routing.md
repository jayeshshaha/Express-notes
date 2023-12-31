###   Express Router -> better way to create routes
## Steps:-
// 1. Create routes folder and put your routes in a sperate file
// 2. Instance instance of express.Router()
// 3. Instead of app.method change that to "router.method"
// 4. Export router
// 5. Import router
// 6. use the (app.use) built-in middleware  & provide your routes

## file1-name : student
const express = require("express");
const router = express.Router(); // whenever we want use to expres router we have to write code like this express.Router();

router.get('/all',(req,res)=>{
    res.send("All students")
})
router.post('/create',(req,res)=>{
    res.send("Add new student")
})
router.put('/update',(req,res)=>{
    res.send("update student")
})
router.delete('/delete',(req,res)=>{
    res.send("delete student from db.")
})

// export default router;
module.exports = router; 

## file2-name : teacher
const express = require("express");
const router = express.Router(); // whenever we want use to expres router we have to write code like this express.Router();

router.get('/all',(req,res)=>{
    res.send("All teacher")
})
router.post('/create',(req,res)=>{
    res.send("Add new teacher")
})
router.put('/update',(req,res)=>{
    res.send("update teacher")
})
router.delete('/delete',(req,res)=>{
    res.send("delete teacher from db.")
})

// export default router;
module.exports = router; 

# Main - index file

const express = require("express");
const students = require('./routes/student.js'); // specify .js extension
const teachers = require('./routes/teacher.js')
const app = express();

// Express Router -> better way to create routes
// 1. Create routes folder and put your routes in a sperate file
// 2. Instance instance of express.Router()
// 3. Instead of app.method change that to "router.method"
// 4. Export router
// 5. Import router
// 6. use the (app.use) built-in middleware  & provide your routes

app.use('/students',students)
app.use('/teachers',teachers)

app.listen(8500, () => {
  console.log("Server Up!");
});



// npm i nodemon
// "dev": "nodemon index.js"
// npm run dev
