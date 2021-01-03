# Episodio 6

Cosas que voy aprendiendo...

### 3 Jan 2021

Node JS - base app.js

```
//jshint esversion:6

const express = require("express");
const bodyParser = require("body-parser");

const app = express();

app.get("/", function(req, res){
  res.send("Hello");
});

app.listen(3000, function(){
  console.log("Server started on port 3000.");
});

```
