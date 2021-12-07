# Episodio 6

Cosas que voy aprendiendo...

### 07 Dec 2021

[JS - when to use preventDefault, stopPropagation or return false](https://medium.com/@jacobwarduk/how-to-correctly-use-preventdefault-stoppropagation-or-return-false-on-events-6c4e3f31aedb)

[event bubbling javascript](https://www.sitepoint.com/event-bubbling-javascript/)

### 06 Dec 2021

Angular some router options...

```
imports: [RouterModule.forRoot(
        routes,
        {
            useHash: true,
            relativeLinkResolution: 'legacy',
            onSameUrlNavigation: 'reload',          // on refresh in the same url it reloads... so it allows you to get to any subscription
        }
    )],
```

e.g.

```
this.router.events
            .pipe(
                takeUntil(this.destroyed$)
            )
            .subscribe((event) => {
                if (event instanceof NavigationEnd) {
                    this.isSystemAdministrationRoute = this.router.url.includes('/system-administration');
                }
            });
```

```
menu(isSystemAdministrationRoute: boolean, dashboardDefinitions: DashboardDefinition[]): NavigationMenu[] {

        if (isSystemAdministrationRoute) {
            return [
                {
                    label: 'Users & Teams',
                    id: 'system-administration-users-and-teams',
                    icon: 'book-user',
                    routerLink: [
                        '/app/system-administration',
                        'users-and-teams',
                    ],
                    menu: [
                        {
                            label: 'Users',
                            routerLink: [
                                '/app/system-administration',
                                'users-and-teams',
                            ],
                            queryParams: { 'tab-users-and-teams': 0 },
                        },
                        {
                            label: 'Teams',
                            routerLink: [
                                '/app/system-administration',
                                'users-and-teams',
                            ],
                            queryParams: { 'tab-users-and-teams': 1 },
                        },
                        ...
                    ],
                },
```

### 03 Dec 2021

[blog angular - ngFor](https://blog.angular-university.io/angular-2-ngfor/)

>  this one is quite useful... e.g. `d-block d-xl-none` (display block, but don't display in on xl)

[bootstrap display utility class](https://getbootstrap.com/docs/4.0/utilities/display/)

### 23 Nov 2021

[jake archibald - tasks, microtasks, queues and schedules](https://jakearchibald.com/2015/tasks-microtasks-queues-and-schedules/)

[angular - async pipe, change detection, ...](https://www.thinktecture.com/en/angular/understanding-the-async-pipe/)

### 18 Nov 2021

[blog angular - tips for ng runtime performance from the real world](https://blog.angular.io/3-tips-for-angular-runtime-performance-from-the-real-world-d467fbc8f66e)

[top reasons why your ng app is slow](https://blog.bitsrc.io/top-reasons-why-your-angular-app-is-slow-c36780a0a289)

[stackoverflow - add delay time to ng to simulate latency](https://stackoverflow.com/questions/28277133/adding-a-delay-pr-timer-to-an-angular-get-to-test-latency)

[related to latency and measuring times](https://stackoverflow.com/questions/313893/how-to-measure-time-taken-by-a-function-to-execute)

### 15 Nov 2021

[handle angular forms Race Conditions with RxJS](https://betterprogramming.pub/handling-angular-forms-race-conditions-with-rxjs-b4e31bb73ba0)

[Net Basal: who's afraid of Observables?](https://netbasal.com/whos-afraid-of-observables-bde0dc4f48cc)

### 13 Oct 2021

[CRUZ - stackblitz: CSS :host and TS @Hostbinding](https://stackblitz.com/edit/angular-ivy-8dcejj?file=src%2Fapp%2Fhello.component.ts)

### 24 Sep 2021

[angular ngtemplateoutlet](https://www.tektutorialshub.com/angular/ngtemplateoutlet-in-angular/)  √√√

[stackoverflow - ng6 ngtemplateoutlet inside ngFor multiple context](https://stackoverflow.com/questions/50842631/angular-6-ngtemplateoutlet-inside-ngfor-multiple-context)

### 17 Sep 2021

[16 ways to search find and edit wiwth chrome devtools](https://www.telerik.com/blogs/16-ways-to-search-find-and-edit-with-chrome-devtools)

[indepth - about debugging angular apps](https://indepth.dev/posts/1138/everything-you-need-to-know-about-debugging-angular-applications)

### 13 Sep 2021

[angular.io - angular devtools](https://blog.angular.io/introducing-angular-devtools-2d59ff4cf62f)

### 26 Aug 2021

[An Event Apart - “Atomic Design” by Brad Frost—An Event Apart Austin 2015](https://www.youtube.com/watch?v=W-h1FtNYim4)

### 10 Aug 2021

angular 10 tips... cont
>  package.json scripts > ng start > ng serve > angular.json config
>  if you need to know how a project starts go to package.json scripts

Fran tips 'pasta' empresa, impuestos y ganancias; casas, hipotecas intereses alquiler...

// ng Schematics
[Quick UI using Angular Material Schematics [#2] | Front end development | Web Application](https://www.youtube.com/watch?v=dcACk0WTqNc)

>  Address Form Schematics provides a component with a demo form fields of shipping address.
>  Navigation Schematics provides a component with a side navigation panel and a toolbar displaying the application name.
>  Table Schematics provides a component with pre-built material table in it, which supports sorting and pagination. 
>  Dashboard Schematics provides component containing multiple material design cards and menus which are aligned in grid layout.
>  Tree Schematics provides a component which interactively visualizes a nested  folder structure.
>  Drag and Drop Schematics provides a component for creating interactive to-do list using drag and drop.

### 03 Aug 2021

[Angular 10 tuts for beginners YT playlist - ARC tutorials](https://www.youtube.com/playlist?list=PLp50dWW_m40XTcxIaXVqO60LaIlyHWxDS)

[The Galen Foundation - Fasting For Survival Lecture by Dr Pradip Jamnadas](https://www.youtube.com/watch?v=RuOvn4UqznU)

[Dr Kellyann - Bone Broth: How-Tos, Recipes, Health Benefits, and History | Digging In with Dr. Kellyann](https://www.youtube.com/watch?v=canEZNMEJag)


### 21 Jul 2021

[Angular - when to use subscribe method or async pipe](https://debugmode.net/2019/10/24/when-to-use-the-subscribe-method-or-async-pipe-in-angular/)

[how to handle subscription in angular 10](https://www.thesunflowerlab.com/blog/how-to-subscription-handling-in-angular-10/)

[FreeCodeCamp - how JS implements OOP](https://www.freecodecamp.org/news/how-javascript-implements-oop/)

[geekforgeeks - intro OOP JS](https://www.geeksforgeeks.org/introduction-object-oriented-programming-javascript/)

[javascriptissexy - OOP in JS what you need to know](https://javascriptissexy.com/oop-in-javascript-what-you-need-to-know/)

### 06 Jul 2021

// Hackerrank certification for react - solutions
[Akash Ingole YT playlist](https://www.youtube.com/c/devChannelbyAkashIngole/playlists)

// Ben Awad - Part of Practical React (using class, state...)
[Fetch Data from an API in React.js - Part 12](https://www.youtube.com/watch?v=T3Px88x_PsA)

[API randomuser . me](https://randomuser.me/)

[CRUZ - React users card - fetch data from API](https://stackblitz.com/edit/react-rzb9qf)

### 30 Jun 2021

[How to add HTML Head Element Tags to a NextJS website](https://coderrocketfuel.com/article/how-to-add-html-head-element-tags-to-a-next-js-website)

[Strange JS errors and hot to fix them - davidwalsh](https://davidwalsh.name/fix-javascript-errors)

### 22 Jun 2021

[How To Build A Markdown Blog Using Node.js, Express, And MongoDB](https://www.youtube.com/watch?v=1NrHkjlWVhM)

// Basic use of **Markdown in Node.js**
// install marked and express

index.js

```js
const marked = require("marked");
const express = require("express");
const app = express();

const html = marked("# Marked in Node.js\n\n Rendered by **marked**");

app.get("/", (req, res) => {
  res.send(html);
});

app.listen(5000);
```




### 21 Jun 2021

[web dev - optimize your images](https://web.dev/fast/#optimize-your-images)

[CRUZ - codepen - CSS Grid auto flow example](https://codepen.io/CruzWeb/pen/VwpNKNz?editors=1100)

[CRUZ - jamstack example PSBA matt (dynalist examples)](https://happy-neumann-58010d.netlify.app/)

[Live Coding with Firebase & StackBlitz by Frank van Puffelen (Google)](https://www.youtube.com/watch?v=hawcfq3KN3g)

[CRUZ - Firebase + Stackblitz](https://stackblitz.com/edit/weathersunnyfoggy?file=index.js)  >> https://weathersunnyfoggy.stackblitz.io

>  I can access firebase collection by adding `.json` to the end of the url for that collection

```
https://[name and location].firebasedatabase.app/[collection].json
```



### 19 Jun 2021

// starts around min 18
[Live Coding with Firebase & stackblitz by Frank van Puffelen](https://www.youtube.com/watch?v=hawcfq3KN3g)

[Stackblitz - introducing web containers: run nodeJS natively in your browser](https://blog.stackblitz.com/posts/introducing-webcontainers/)

### 18 Jun 2021

JS tricks

- to use array methods on Nodelist > select using `$$`. Example to get duration of all videos on jamstack.org/tv
 
 
```js
$$('.jamstacktv-card').map(card => parseInt(card.children[1].innerHTML)).reduce(function (accumulator, currentValue) {
  return accumulator + currentValue
}, 0)
```

```js
// instead of:
document
 .querySelectorAll('.cards')
 .forEach(card => card.addEventListener('click', handleClick));
 
// use:
$$('.cards').on('click', handleClick);
```


### 10 Jun 2021

[CRUZWEB stackblitz - Angular Material Starter](https://stackblitz.com/edit/cwd-angular-material-starter)

### first week of Jun 2021

// practicing SCSS - variables, functions, mixins, nesting, include...

[CRUZ - zurc github io / sass-practice](https://zurc.github.io/sass-practice/)

// working on angular authentication seed - work in progress
// fouind issues when deploying into production and auth0 routing after signin

https://github.com/Zurc/angular-auth-seed


### 01 Jun 2021

[Angular user authentication with auth0](https://auth0.com/blog/complete-guide-to-angular-user-authentication/)

[Hithesh Choudhary - GraphQL Crash Course easy way](https://www.youtube.com/watch?v=_Zss2Mbz4Bs)

### 28 May 2021

[CSS-tricks - SVG path syntax illustrated guide](https://css-tricks.com/svg-path-syntax-illustrated-guide/)

[CSS-tricks - advanced CSS animations cubic bezier](https://css-tricks.com/advanced-css-animation-using-cubic-bezier/)

[A list apart - blending modes demystified](https://alistapart.com/article/blending-modes-demystified/)

**Conditionals, Short circuiting and default arguments**

```js
// Conditionals
function createCompany(name) {
  let companyName;
  if (name) {
    companyName = name;
  } else {
    companyName = 'The Best Company!';
  }
}
createCompany('coco');
createCompany();


// Better Short circuiting than conditionals
function createCompany(name) {
  let companyName;
  companyName = name || 'The Best Company!';
  console.log(companyName)
}
createCompany('coco');
createCompany();

// Better Default arguments than short circuiting
function createCompany(name = 'The Best Company!') {
  let companyName = name;
  console.log(companyName);
}
createCompany('coco');
createCompany();

```



### 16 Apr 2021

[WordPress Website Design - How to Approach A Client Redesign Project](https://www.youtube.com/watch?v=oR-2w4Rx4l8&ab_channel=WPTuts)

### 11 Apr 2021

[Build a GitHub Jobs App With React Hooks](https://www.youtube.com/watch?v=fxY1q4SCB64&ab_channel=TraversyMedia)

### 09 April (ish...) 2021

[CRUZ - JS accordion](https://jsbin.com/gatuyim/)

ref: https://airnauts.com/

### 06 Apr 2021

[try, catch, finally, throw - error handling in JavaScript - freecodecamp](https://www.youtube.com/watch?v=cFTFtuEQ-10&ab_channel=freeCodeCamp.org)

### 02 Apr 2021

[gilmoreorless - animation and maths](https://gilmoreorless.github.io/)

[ease yourself into animation](http://gilmoreorless.github.io/sydjs-preso-easing/)

[CSS easing animation tool](https://matthewlein.com/tools/ceaser)

[1 line layouts (CSS)](https://1linelayouts.glitch.me/)

[Musical interactions](https://tympanus.net/Development/MusicalInteractions/#)

### 25 Mar 2021

[combine flexbos and css grid for layouts how to](https://getflywheel.com/layout/combine-flexbox-and-css-grids-for-layouts-how-to/)

### 22 Mar 2021

[inverted rounded corner border radius in CSS](https://www.pakainfo.com/inverted-rounded-corner-border-radius-in-css/)

[CRUZ - pen codepen](https://codepen.io/CruzWeb/pen/WNReWyX)

### 21 Mar 2021

[10 modern layouts in 1 line of CSS](https://www.youtube.com/watch?v=qm0IfG1GyZU)
[playground](https://1linelayouts.glitch.me/)

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
