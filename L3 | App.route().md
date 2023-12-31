## ugly code
app.get("/", (req, res) => {
  res.send("All Student");
});

app.post("/", (req, res) => {
  res.send("add new Student");
});

app.put("/", (req, res) => {
  res.send("update Student");
});

app.delete('/', (req, res) => {
    res.send('delete Student');
  })


-----------------------------------

## Referactor 

app.route("/")
.get((req,res)=> res.send("All Student"))
.post((req,res)=> res.send("add new Student"))
.put((req,res)=> res.send("update Student"))
.delete((req,res)=> res.send("delete a Student"));

app.listen(8500, () => {
  console.log("Server Up!");
});

