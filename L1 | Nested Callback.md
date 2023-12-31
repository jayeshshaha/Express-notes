## Nested Callbacks fnx

app.get('/single-cb',(req,res,next)=>{
    // res.send('Single callbackfnx')
    console.log("First callbackfnx");
    next();
},(req,res)=>{
    res.send('Second callbackfnx')
});

app.listen(8500,()=>{
    console.log("Server Up!");
})

## Arrays of Callbacks fnx

function cb1(req,res,next){
    console.log('First Callback');
    next();
}
function cb2(req,res,next){
    console.log('Second Callback');
    next()
}
function cb3(req,res){
    console.log('Third Callback');
    res.send("Arrays of Callbacks fnx")
}

app.get('/array-cb',[cb1,cb2,cb3])