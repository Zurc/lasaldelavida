# Episodio 6

Cosas que voy aprendiendo...

### 03 Mar 2021

[CRUZ - clock](https://codepen.io/CruzWeb/pen/jOVKaJp)

### 17 Feb 2021

[mac - how to install security SSL certificate](https://support.securly.com/hc/en-us/articles/206058318-How-to-install-the-Securly-SSL-certificate-on-Mac-OSX-)

[how to fork a github repo and contribute to Open Source project](https://sqldbawithabeard.com/2019/11/29/how-to-fork-a-github-repository-and-contribute-to-an-open-source-project/)

[keeping a github fork updated](https://thoughtbot.com/blog/keeping-a-github-fork-updated)

[react native training - gitbook](https://unbug.gitbooks.io/react-native-training/content/11_building_an_app_in_5_minutes.html)

[react native guide - gitbook](https://www.reactnative.guide/index.html)

### 11 Feb 2021

[CRUZ - progress bar](https://codesandbox.io/s/progress-bar-xlgdd)

[frontend tips - Customised slider control](https://www.youtube.com/watch?v=1wQVVJ7ase0&ab_channel=FrontendTips)

[CRUZ - inline style for React](https://codesandbox.io/s/inline-style-for-react-r967i?file=/src/index.js)

### 02 Feb 2021

[robomongo - mongoDB Client (GUI)](https://robomongo.org/)

### 29 Jan 2021

[indepth - beware angular can steal your time](https://indepth.dev/posts/1015/beware-angular-can-steal-your-time)

### 27 Jan 2021

[Design Systems - practical guide](https://medium.com/grensesnittet/a-practical-guide-to-creating-design-systems-with-7-tips-ff870c73ccff)

### 26 Jan 2021

[ANGULAR - stackoverflow - access directive child elements](https://stackoverflow.com/questions/42715318/can-i-access-child-elements-within-a-directive-in-angular2)

[BOOKS](https://b-ok.cc/)

### 22 Jan 2021

[Meditaciones - Marco Aurelio](http://bibliotecadigital.ilce.edu.mx/Colecciones/ObrasClasicas/_docs/Meditaciones_MarcoAurelio.pdf)

[CSS pattern fills](https://iros.github.io/patternfills/sample_css.html)

### 19 Jan 2021

children code resources

[BLockly - developers google](https://developers.google.com/blockly)

[blockly code labs](https://blocklycodelabs.dev/codelabs/getting-started/index.html#0)

### 14 Jan 2021

[what's new on Chrome dev tools](https://developers.google.com/web/updates/2020/10/devtools?utm_source=devtools)

[Web animation gotchas - HTTP 203](https://www.youtube.com/watch?v=9-6CKCz58A8&feature=emb_rel_pause)

[John Papa at FreeCodeCamp - how to use lite-server for simple dev web server](https://www.freecodecamp.org/news/how-you-can-use-lite-server-for-a-simple-development-web-server-33ea527013c9/)

### 13 Jan 2021

[Max Schwarzmüller - 7 techniques to learn & grow more efficiently](https://academind.com/tutorials/efficient-learning-7-techniques)

Find a Learning Partner or Community

Set Ambitious Long-Term Goals

Set Simple Short-Term Goals

Use Your Knowledge As Often As Possible

The “5 Minutes” Trick

Understand That Everyone Is Showing Off

Don’t Read Too Many “Motivational Guides”

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
