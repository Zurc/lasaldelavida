# Episodio 6

Cosas que voy aprendiendo...

### 12 Jan 2021

[goskills - animated loading circle](https://www.goskills.com/Course/Photoshop-Advanced/Lesson/361/Animated-Loading-Circle)

### 08 Jan 2021

SCSS - loop through different colors to create classes

we'll take colours from another file 'pallet.scss'

```
...
// Construct classes for colours for the pie chart in a loop (will be .graph-colour-1 .graph-colour-2 etc.)
$graph-colours: white #07647f $info $primary $secondary $success $danger $warning blue magenta brown yellow purple grey aquamarine indianred
  seagreen teal thistle tan powderblue;
...
```
and then do the loop within graphs.scss

```
@import '../pallet.scss';
// Construct classes for colours for the pie chart in a loop (will be .graph-colour-1 .graph-colour-2 etc.)
$i: 0;
@each $colour in $graph-colours {
    .graph-colour-#{$i} {
        color: $colour;
        background-color: $colour;
        stroke: $colour;
    }
    $i: $i + 1;
}
```

[live without google](https://spreadprivacy.com/how-to-remove-google/)

**converters**

[split text into columns - google sheets](https://www.bettercloud.com/monitor/the-academy/split-text-columns-google-sheets/)

[split text](https://www.textcompare.org/text/split-text)

browserling

[remove all whitespace](https://www.browserling.com/tools/remove-all-whitespace)

### 06 Jan 2021

[Let's Do Math (youtube channel)](https://www.youtube.com/channel/UCW5diHfMyIPW3XNFzh4-1SA)

[fraction operations chearsheet](https://betterlesson.com/community/document/96403/fraction-operations-cheatsheet-docx)

[Fraction cheatsheet II](https://www.mymathplanner.com/resources/Fraction-Cheat-Sheets.pdf)

[khanacademy - fifth grade math](https://www.khanacademy.org/math/cc-fifth-grade-math)

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
