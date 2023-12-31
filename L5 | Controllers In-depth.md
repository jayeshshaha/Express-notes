<!-- Notes -->
## Controllers can group related request handling logic spearately and instead of defining all of your request handling logic as a callback or in a separate file ; you may  wish to organize this behavior using Controllers.
## Express controllers are functions or modules in an Express.js application that handle the logic for specific routes or groups of routes.

## Controller will have all our logic of our methods in a spearete file
<!-- Main File -->

const express = require("express");
// import students from './routes/student.js'
const students = require('./routes/student.js')
const app = express();

app.use('/students',students)

app.listen(8500, () => {
  console.log("Server Up!");
});

<!-- File 1 -->
## Create routes folder -> filename should be students.js

const express = require("express");
// import {allstudents,newStudent,updateSudent,deleteStudent} from '../controllers/student.js'
const {
    allstudents,
    newStudent,
    updateSudent,
    deleteStudent
  } = require('../controllers/student.js');
  
const router = express.Router();

router.get('/all',allstudents)
router.post('/create',newStudent)
router.put('/update',updateSudent)
router.delete('/delete',deleteStudent)

module.exports = router; 

<!-- File 2 -->
## Create controllers folder -> filename should be students.js

const express = require("express");

const allstudents = (req, res) => {
    // you can write your logic here
    res.send("All students");
}

const newStudent = (req, res) => {
    // you can write your logic here
    res.send("Add new student")
}

const updateSudent  = (req,res)=> {
    res.send("update student")
}

const deleteStudent = (req,res)=>{
    res.send("delete student from db.")
}

// export {allstudents,newStudent,updateSudent,deleteStudent};
module.exports = {
    allstudents,
    newStudent,
    updateSudent,
    deleteStudent
  };