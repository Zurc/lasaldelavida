# Episodio 5

Cosas que voy aprendiendo...

### 15 Jul 2019

>  [stackoverflow - what does the double exclamation operator mean](https://stackoverflow.com/questions/7452720/what-does-the-double-exclamation-operator-mean)
>  
>  The !! ensures the resulting type is a boolean (true or false).

[codecraft - ngStyle and ngClass](https://ng2.codecraft.tv/built-in-directives/ngstyle-and-ngclass/)

[love2dev - CSS calc() method](https://love2dev.com/blog/css-calc/)

### 10 Jul 2019

>  [stackoverflow - router navigate to same page](https://stackoverflow.com/questions/41678356/router-navigate-does-not-call-ngoninit-when-same-page) solution has another link...
>  
>  [using RouteReuseStrategy](https://stackoverflow.com/questions/39533291/angular2-router-2-0-0-not-reloading-components-when-same-url-loaded-with-differe/39533351#39533351)
>  
>  what it worked for me... in the constructor
>  
>  ```
>  this.router.routeReuseStrategy.shouldReuseRoute = () => false;
>  ```


[stackoverflow - commit a file partially in tortoise](https://stackoverflow.com/questions/314132/is-there-some-way-to-commit-a-file-partially-in-tortoisesvn)

[stackoverflow - display text word by word (jquery)](https://stackoverflow.com/questions/29170311/how-do-you-display-text-word-by-word-for-text-that-is-received-via-ajax)

### 09 Jul 2019

[Linux for Ethical Hackers (Kali Linux Tutorial)](https://www.youtube.com/watch?v=lZAoFs75_cs&feature=push-sd&attr_tag=Em90saGL9X9x8lNs%3A6)

>  angular validation - custom validators
>  
>  remember: when creating validation function, return true in case of errors. eg. code below

```
import { Directive, Input } from '@angular/core';
import { NG_VALIDATORS, AbstractControl, ValidationErrors, Validator } from '@angular/forms';

@Directive({
    selector: '[appNotIncluded]',
    providers: [
        {
        provide: NG_VALIDATORS,
        useExisting: NotIncludedValidator,
        multi: true
        }
    ]
    })
    export class NotIncludedValidator implements Validator {

    // list to compare our value against
    @Input() list: any[];
    // optional value
    @Input() allowValue?: any;

    /**
     * Validatation logic: compare if value c is included in a list
     * @param c The value of the control
     */
    validate(c: AbstractControl): ValidationErrors | null {
        // if value c equals allowValue there will be no validation errors
        if (c.value === this.allowValue) {
            return null;
        }
        // if list includes our value send an error
        if (this.list.includes(c.value)) {
            return { alreadyExists: true };
        } else {
            return null;
        }
    }
}
```
>  then you use 'appNotIncluded' directive on the html as follows...

```
 <gvf-text 
     class="heading-textbox"
     [(ngModel)]="filterName"
     #fn
     name="filterName"
     appNotIncluded
     [list]="filterNames"
     [allowValue]="selectedFilter?.name"
     maxlength="10"
     [validationMessages]="{
         maxlength: 'Too long... up to 10 characters',
         alreadyExists: 'This name already exists'
     }">{{ filterName }}</gvf-text>
```

>  ...on this example gvf is a custom angular component. we are passing 'filterNames' (an array of names) as list input and 'selectedFilter?.name' (selected name from dropdown) as allowValue input. That 2 inputs are used on the custom directive

[bennadel - using dynamic template driven forms in angular 7](https://www.bennadel.com/blog/3578-using-dynamic-template-driven-forms-in-angular-7-2-7.htm)

angular - sort array of objects (coming from server) by object property

```
this.whateverService(...).pipe(
 map(results => {
    // sort results by [object].name
    return results.sort((r1, r2) => r1.name.localeCompare(r2.name));
})
...
```


JS animation:

https://animejs.com/

https://blog.bitsrc.io/11-javascript-animation-libraries-for-2018-9d7ac93a2c59

https://textillate.js.org/

https://gedd.ski/post/character-animation/

### 08 Jul 2019

[when to unsubscribe in angular](https://netbasal.com/when-to-unsubscribe-in-angular-d61c6b21bad3)

### 04 Jul 2019

[scotch - how to deal with different form controls in angular 2](https://scotch.io/tutorials/how-to-deal-with-different-form-controls-in-angular-2)

### 03 Jul 2019

[stackoverflow - push observable of array (ng4)](https://stackoverflow.com/questions/47424966/how-to-push-to-observable-of-array-in-angular-4-rxjs)

>  RELOAD ROUTE ON PARAMS CHANGE

```
constructor(private router: Router) {

      // force route reload whenever params change;
      this.router.routeReuseStrategy.shouldReuseRoute = () => false;

    }
```


[angular university - rxjs error handling](https://blog.angular-university.io/rxjs-error-handling/)

[angularindepth - the best way to unsubscribe rxjs observable in the angular app](https://blog.angularindepth.com/the-best-way-to-unsubscribe-rxjs-observable-in-the-angular-applications-d8f9aa42f6a0) +++

[CRUZ - stackblitz (subscription)](https://stackblitz.com/edit/angular-observables-subscribe)

[CRUZ - stackblitz (multiple subscriptions)](https://angular-observables-multiple-subscriptions.stackblitz.io)

### 02 Jul 2019

>  "a directive is nothing more than an html attr that angular provides [youtube - angular tuts for beginners](https://www.youtube.com/watch?v=Y6OP-lPJxgs)
>  
>  [codeEvolution - Angular 8 Tutorial - 1 - Introduction](https://www.youtube.com/watch?v=0eWrpsCLMJQ&list=PLC3y8-rFHvwhBRAgFinJR8KHIrCdTkZcZ)

### 01 Jul 2019

[angularindepth - all you need to know about ivy the new angular engine](https://blog.angularindepth.com/all-you-need-to-know-about-ivy-the-new-angular-engine-9cde471f42cf)

[angularfirebase - sharing data between angular components for methods](https://angularfirebase.com/lessons/sharing-data-between-angular-components-four-methods/#Unrelated-Components-Sharing-Data-with-a-Service)

[angularindepth - the 'new' (2017) angular httpclient API](https://blog.angularindepth.com/the-new-angular-httpclient-api-9e5c85fe3361)

### 26 Jun 2019

[typescript - enums](https://www.typescriptlang.org/docs/handbook/enums.html)

[best practices for a clean and performant angular app](https://www.freecodecamp.org/news/best-practices-for-a-clean-and-performant-angular-application-288e7b39eb6f/)  +++

>  use localeCompare to sort... interesting
>  
>  [mdn - localeCompare](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/localeCompare)
>  
>  [mdn - array sort](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

### 25 Jun 2019

[angularindepth - configuring typescript compiler](https://blog.angularindepth.com/configuring-typescript-compiler-a84ed8f87e3)

[typescript documentation - compiler options](https://www.typescriptlang.org/docs/handbook/compiler-options.html)

[which version of ecmascript should I use in the typescript configuration](https://www.meziantou.net/which-version-of-ecmascript-should-i-use-in-the-typescript-configuration.htm)

[angularindepth - reading the rxjs 6 sources map and pipe](https://blog.angularindepth.com/reading-the-rxjs-6-sources-map-and-pipe-94d51fec71c2)

[chrome dev tools - conditional breakpoints](https://blittle.github.io/chrome-dev-tools/sources/conditional-breakpoints.html)

### 24 Jun 2019

[strongbrew - rxjs best practices in angular](https://blog.strongbrew.io/rxjs-best-practices-in-angular/)

[codecraft - reactive programming with rxjs (observables and rxjs)](https://codecraft.tv/courses/angular/reactive-programming-with-rxjs/observables-and-rxjs/)

[angular university - what are streams](💥 Understanding RxJs - What are Streams?
)

>  [3 common mistakes i see people use in rx ant observable pattern](https://medium.com/@paynoattn/3-common-mistakes-i-see-people-use-in-rx-and-the-observable-pattern-ba55fee3d031)
>  
>  Observables do not like being inside Observables.

>  [ from angularindepth - rxjs interactive diagrams](https://blog.angularindepth.com/learn-to-combine-rxjs-sequences-with-super-intuitive-interactive-diagrams-20fce8e6511)
>  
>  **Sequence composition** is a technique that enables you to create complex queries across multiple data sources by combing relevant streams into one.

[stackoverflow - how to avoid multiple nested subscriptions using rxjs operators](https://stackoverflow.com/questions/55416011/how-can-i-avoid-multiple-nested-subscriptions-using-rxjs-operators) 

[angular 2+ unsubscribe observables](https://brianflove.com/2016/12/11/anguar-2-unsubscribe-observables/)

[how to show radio input listing in angular 6/7](https://www.freakyjolly.com/how-to-show-radio-input-listing-in-angular-6/)

### 21 Jun 2019

[codeburst - declarative vs imperative programming](https://codeburst.io/declarative-vs-imperative-programming-a8a7c93d9ad2)

[sitepoint - rxjs functions with examples](https://www.sitepoint.com/rxjs-functions-with-examples/)

>  an **Observable** is nothing more than an **array that populates over time.**
>  
>  At heart, reactive programming is nothing more than using Observables as the building blocks of your programs. 

### 19 Jun 2019

[auth0 - real world angular series](https://auth0.com/blog/real-world-angular-series-part-1/)

[ng2 template driven form validators](https://juristr.com/blog/2016/11/ng2-template-driven-form-validators/)

[validations for template driven forms in angular 4](https://blog.knoldus.com/validations-for-template-driven-forms-in-angular-4/)

[template driven angular validations](https://medium.com/@jonbonraki/template-driven-angular-validations-57d291467f2b)

[3 ways to dynamically alter your form validation in angular](https://netbasal.com/three-ways-to-dynamically-alter-your-form-validation-in-angular-e5fd15f1e946)

[CRUZ - JS loop string\[\] check if values are obj properties in objects\[\] (jsbin)](https://jsbin.com/cuxociy/edit?js,console)

### 18 Jun 2019

[angular how to implement conditional custom validation](https://medium.com/front-end-weekly/angular-how-to-implement-conditional-custom-validation-1ec14b0feb45)

[angular validators with conditional validation in reactive forms](https://www.codementor.io/jimohhadi/angular-validators-with-conditional-validation-in-reactive-forms-pj5z7gsq5)

[real world angular reactive forms](https://blog.grossman.io/real-world-angular-reactive-forms/) +++

[hackernoon - js performance test for vs. forEach vs. map/reduce/filter/find](https://hackernoon.com/javascript-performance-test-for-vs-for-each-vs-map-reduce-filter-find-32c1113f19d7)

[angularindepth - unleash the power of forms with angular reactive forms](https://blog.angularindepth.com/unleash-the-power-of-forms-with-angulars-reactive-forms-d6be5918f408)

[angularindepth - learn to combine rxjs sequences with super intuitive interactive diagrams](https://blog.angularindepth.com/learn-to-combine-rxjs-sequences-with-super-intuitive-interactive-diagrams-20fce8e6511)

[angular effective component patterns](https://itnext.io/angular-effective-component-patterns-f5f7f08e2072)

[reactive forms in angular](https://atom-morgan.github.io/reactive-forms-in-angular/)

### 15 Jun 2019

[dev.to - 10 articles web dev should read this weekend](https://dev.to/javinpaul/10-articles-web-developers-should-read-this-weekend-ka0)

### 13 Jun 2019

[angular in depth - everything you need to know about the expresssionChangeAfterItHasBeenChecked error](https://blog.angularindepth.com/everything-you-need-to-know-about-the-expressionchangedafterithasbeencheckederror-error-e3fd9ce7dbb4)

### 12 Jun 2019

[6 gorgeous and free mapping tools](https://nationaleventpros.com/6-gorgeous-and-free-mapping-tools/)

[ben nadel - using dynamic template driven forms in angular 7](https://www.bennadel.com/blog/3578-using-dynamic-template-driven-forms-in-angular-7-2-7.htm)

[codeburst - angular dynamic forms ng switch approach](https://codeburst.io/angular-dynamic-forms-ng-switch-approach-4f267c01d2c6)

### 11 Jun 2019

[transform arrays with reduce](https://labnotes.panderalabs.com/transform-arrays-with-reduce-ec38553e3c96)

[stop array.forEach and start using filter, map, some, reduce functions](https://medium.com/front-end-weekly/stop-array-foreach-and-start-using-filter-map-some-reduce-functions-298b4dabfa09)

[what you should know about es6 maps](https://hackernoon.com/what-you-should-know-about-es6-maps-dc66af6b9a1e)

[looping through js objects](https://zellwk.com/blog/looping-through-js-objects/)

[how to use array methods in js itaration methods](https://www.digitalocean.com/community/tutorials/how-to-use-array-methods-in-javascript-iteration-methods)

[demistifying es6 iterables and iterators](https://www.freecodecamp.org/news/demystifying-es6-iterables-iterators-4bdd0b084082/)

### 10 Jun 2019

[understanding output and eventemitter in angular](https://www.infragistics.com/community/blogs/b/infragistics/posts/understanding-output-and-eventemitter-in-angular)

[hackernoon - what you should know about es6 maps](https://hackernoon.com/what-you-should-know-about-es6-maps-dc66af6b9a1e)

### 6 Jun 2019

[VAT record keeping - HMRC](https://www.youtube.com/watch?v=29jMtgYbOIo)

[freefrontend - CSS radio buttons](https://freefrontend.com/css-radio-buttons/)

[codepen - nice radio button styles](https://codepen.io/JN0iZzze/pen/RoZmGo)

>  angular ViewChild: “The Child Element which is located inside the component template”

JS - iterable and iterators, looping...

>  [Dr. Axel Rauschmayer - exploringjs](https://exploringjs.com/es6/ch_iteration.html)
>  
>  [master the art of looping in JS tricks](https://www.freecodecamp.org/news/master-the-art-of-looping-in-javascript-with-these-incredible-tricks-a5da1aa1d6c5/)
>  
>  [iterating through JS objects 5 techniques and performance tests](https://medium.com/backticks-tildes/iterating-through-javascript-objects-5-techniques-and-performance-tests-42b4a222a92b)
>  
>  [MDN - for...of](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of)
>  
>  [MDN - object.entries()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/entries)

### 5 Jun 2019

[sjaromg data between angular components four methods](https://angularfirebase.com/lessons/sharing-data-between-angular-components-four-methods/)

[simplifying viewchild contentchild angular](https://jaxenter.com/simplifying-viewchild-contentchild-angular-142894.html)

[angular.io - component interaction](https://angular.io/guide/component-interaction)

[communicate between components using dependency injection](https://blog.angularindepth.com/communicate-between-components-using-dependency-injection-d7280567faa7)

>  You can inject any ancestor of a component into your component’s constructor and directly reference the ancestor component’s methods/members.

### 4 Jun 2019

[gov uk - understanding VAT](https://www.gov.uk/topic/business-tax/vat)

[uxworld - how to write good error messages](https://uxdworld.com/2018/05/30/how-to-write-good-error-messages/)

[uxplanet - how to write a perfect error message](https://uxplanet.org/how-to-write-a-perfect-error-message-da1ca65a8f36)

[uxdesign - creating error messages best practice in ux design](https://uxdesign.cc/creating-error-messages-best-practice-in-ux-design-cda3be0f5e16)

[form design best practices](https://www.ventureharbour.com/form-design-best-practices/)

[nngroup - form design placeholders](https://www.nngroup.com/articles/form-design-placeholders/)

[smashing magazine - ux contact forms essentials conversions](https://www.smashingmagazine.com/2018/03/ux-contact-forms-essentials-conversions/)

[uxplanet - 10 rules for efficient form design](https://uxplanet.org/10-rules-for-efficient-form-design-e13dc1fb0e03)

[ng5 ngswitch ngswitchcase not to be on real element of html](https://stackoverflow.com/questions/50019941/angular-5-ngswitch-ngswitchcase-not-to-be-on-real-element-of-html)

>  ngSwitch can't be on a `<ng-template>` element, only on real elements like `<div>` or alternatively you can use `<ng-container>` instead of real elements

[pipe symbol in typescript - union type](https://stackoverflow.com/questions/38628115/what-does-the-pipe-mean-in-typescript)

>  A union type describes a value that can be one of several types.

### 3 Jun 2019

[gov uk - company filing software](https://www.gov.uk/company-filing-software)

[Salaries and dividends](https://www.youtube.com/watch?v=KWaHCbcHXhE)

[Directors Salary 2017-18 - London Accountants](https://www.youtube.com/watch?v=ofJEE0wmcdw)

[gov uk - software compatible with makint tax digital for vat](https://www.gov.uk/guidance/find-software-thats-compatible-with-making-tax-digital-for-vat)

[Making Tax Digital VAT 2019](https://www.youtube.com/watch?v=nuaJE2FDkn4)

### 31 May 2019

>  Angular - Debugging
>  
>  If somehow you can not debugg from the component definition | class | controller? then create a function an call it from the template...

### 30 May 2019

>  [Minko Gechev's blog - ng template ref dynamic scoping custom templates](https://blog.mgechev.com/2017/10/01/angular-template-ref-dynamic-scoping-custom-templates/) +++
>  
>  Passing a custom templateRef as input, instead of using the markup which is between the opening and closing ng-template tags.

[js multiselect fancy dropdown](https://www.syncfusion.com/javascript-ui-controls/js-multiselect-dropdown)

[alligator - ng-container element](https://alligator.io/angular/ng-container-element/)

>  stylish - chrome extension that allows to change styles of any website

### 29 May 2019

>  Angular reactive forms. If you want to delete a value from a control, dont delete only the value, but reset that control

[angular uni - ng-template ng-container ngtemplateoutlet](https://blog.angular-university.io/angular-ng-template-ng-container-ngtemplateoutlet/)

>  ngSwitch can't be on a **ng-template** element, only on real elements like **div** or alternatively you can use **ng-container** instead of real elements [stackoverflow link](https://stackoverflow.com/questions/50019941/angular-5-ngswitch-ngswitchcase-not-to-be-on-real-element-of-html)


### 28 May 2019

[thinkster - building real world ng2 apps formbuilder](https://thinkster.io/tutorials/building-real-world-angular-2-apps/formbuilder)

[angular fundamentals reactive forms](https://malcoded.com/posts/angular-fundamentals-reactive-forms/) +++

[ng2 nested reactive forms](https://medium.com/sparkles-blog/angular2-building-nested-reactive-forms-7978ecd145e4)

[realtime table angular](https://pusher.com/tutorials/realtime-table-angular)

### 23 May 2019

[css-tricks - understanding table-layout property](https://css-tricks.com/almanac/properties/t/table-layout/)

[css-tricks - dont overthink flexbox grids](https://css-tricks.com/dont-overthink-flexbox-grids/)

### 22 May 2019

[sitepoint - rxjs functions with examples](https://www.sitepoint.com/rxjs-functions-with-examples/)

[stackoverflow - migrating from ng6 to ng7](https://stackoverflow.com/questions/52936664/migrating-from-angular-6-to-angular-7)

[update.angular.io](https://update.angular.io/)

[talkingdotnet - upgrade ng6 to ng7 visual studio 2017](https://www.talkingdotnet.com/upgrade-angular-6-app-angular-7-visual-studio-2017/)

[diff btwn ng 2 to 8, breakdown new features and changes](https://medium.com/@lifenshades/difference-among-angular-8-7-6-5-4-3-2-breakdown-new-features-and-changes-811fb5f8e6f0)

### 21 May 2019

[the ultimate guide to flexbox learning through examples](https://medium.freecodecamp.org/the-ultimate-guide-to-flexbox-learning-through-examples-8c90248d4676)

[brandon roberts (angular team) medium](https://medium.com/@brandontroberts)

[greg magolan (angular team) - code splitting and lazy-loading with bazel](https://medium.com/@gregmagolan/code-splitting-and-lazy-loading-with-bazel-9b11ac4de20b)

>  from [implementing control value accessor in angular](https://medium.com/@majdasab/implementing-control-value-accessor-in-angular-1b89f2f84ebf)
>  
>  To access the validations provided to the element by default, simply bind the ngModel to a template reference (give the reference any name you wish)
>  
>  To access these validation, simply output the JS-Object and stringify it using the json pipeline operator

same author: [majd asab](https://medium.com/@majdasab) it has posts about angular and java spring

### 20 May 2019

>  Custom components in Angular = CONTROL VALUE ACCESSOR
>  
>  [angularindepth - never be confused when implementing controlvalueaccessor in angular forms](https://blog.angularindepth.com/never-again-be-confused-when-implementing-controlvalueaccessor-in-angular-forms-93b9eee9ee83)
>  
>  [alligator.io - custom form control](https://alligator.io/angular/custom-form-control/)
>  
>  [implementing control value accessor in angular](https://medium.com/@majdasab/implementing-control-value-accessor-in-angular-1b89f2f84ebf) +++

[amgularindepth - what is forwardRef in ng and why we need it](https://blog.angularindepth.com/what-is-forwardref-in-angular-and-why-we-need-it-6ecefb417d48)

### 17 May 2019

[is angular dying vs react?](https://medium.com/@PurpleGreenLemon/is-angular-dying-because-of-react-a8e885f09421)

>  Learn to be a developer that is well versed in programming paradigm and don’t get too hung up or attached to any one thing. Dig deep into architecture structures, designing and developing components, understanding how data flows through the application and state management, among other things.

### 16 May 2019

[regex pattern - learn, create, validate](https://regexr.com/)

[css-tricks - strip whitespace from string](https://css-tricks.com/snippets/javascript/strip-whitespace-from-string/)

[MDN - CSS overflow](https://developer.mozilla.org/en-US/docs/Web/CSS/overflow)

>  [MDN - basics concepts of flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox)
>  
>  One dimensional layout model (flexbox deals with layout in one dimension at a time — either as a row or as a column)

### 14 May 2019

Basics of Java: Controllers, REST API's, pass params, body... generics

[how browser rendering works behing the scenes](https://blog.logrocket.com/how-browser-rendering-works-behind-the-scenes-6782b0e8fb10?source=placement_card_footer_grid---------1-41)

[stackoverflow - should I use two comps for edit and create form in angular](https://stackoverflow.com/questions/43699166/should-i-use-two-components-for-edit-and-create-form-in-angular)

>  CSS Grid
>  
>  [css-tricks - complete guide grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
>  
>  [grid by example](https://gridbyexample.com/)

[mensaje de fatima](http://www.vatican.va/roman_curia/congregations/cfaith/documents/rc_con_cfaith_doc_20000626_message-fatima_sp.html)

### 13 May 2019

CSS: wrap text with no spaces >> word-break: break-word;

[ng2+ dynamic styles](https://juristr.com/blog/2016/01/learning-ng2-dynamic-styles/)

[ng6 - directive click outside](https://stackoverflow.com/questions/50531212/directive-click-outside-angular-6)

[css-tricks - gotchas on getting SVG into production](https://css-tricks.com/gotchas-on-getting-svg-into-production/)

### 10 May 2019

[discovering the shadow DOM](https://blog.logrocket.com/discovering-the-shadow-dom-e541d74aefb3)

[DOM living standard](https://dom.spec.whatwg.org/)

[smashing magazine - designing efficient web forms](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

[inline validation in forms designing the experience](https://medium.com/wdstack/inline-validation-in-forms-designing-the-experience-123fb34088ce)

[uxplanet - designing more efficient forms assistance and validation](https://uxplanet.org/designing-more-efficient-forms-assistance-and-validation-f26a5241199d)

[stackoverflow - error message when a user enters/about to enter more characters than maxlengh on text fields](https://stackoverflow.com/questions/36719982/error-message-when-a-user-enters-more-characters-than-max-length-on-text-area)

>  button alignment (UX)
>  
>  [stackexchange - web forms button alignment](https://ux.stackexchange.com/questions/3340/while-designing-web-forms-should-the-buttons-be-left-aligned-or-right-aligned)
>  
>  [uxmovement - where to align form btns on different layouts](https://uxmovement.com/forms/where-to-align-form-buttons-on-different-layouts/)

### 9 May 2019

>  Angular (async) validators
>  
>  [alligator.io - async validators](https://alligator.io/angular/async-validators/)
>  
>  [stackblitz - Angular 6 Reactive Form Async Validator](https://stackblitz.com/edit/angular-reactive-forms-async-validator)
>  
>  [stackblitz - Angular Template Driven Form example: Custom Validators and Async custom validators](https://stackblitz.com/edit/angular-input-custom-validators?file=app%2Fcomponents%2Ftpl-driven-async.demo.ts)
>  
>  [codecraft - basic custom validators](https://codecraft.tv/courses/angular/advanced-topics/basic-custom-validators/)
>  
>  [angular.io - AsyncValidator](https://angular.io/api/forms/AsyncValidator)
>  
>  [angular.io - (guide) implementing custom async validator](https://angular.io/guide/form-validation#implementing-custom-async-validator)

[angular.io - HttpUrlEncodingCodec](https://angular.io/api/common/http/HttpUrlEncodingCodec)

[ng http requests use square brackets in http params as parameter key name](https://www.moritz-benzenhoefer.com/2018/01/angular-http-requests-use-square-brackets-in-httpparams-as-parameter-key-name/)

[stop using unsafe characters in URLs](https://perishablepress.com/stop-using-unsafe-characters-in-urls/)

### 8 May 2019

>  [ng patterns - how to write seriously reusable components](https://itnext.io/angular-patterns-2-how-to-write-seriously-reusable-components-96be16568abc)
>  
>  "Component depends only on the parent = Component can be controlled from the outside = Component is reusable"

[ng2 training book - ChangeDetectionStrategy.OnPush](https://angular-2-training-book.rangle.io/handout/change-detection/change_detection_strategy_onpush.html)

[cory rylan - CSS encapsulation with ng components](https://coryrylan.com/blog/css-encapsulation-with-angular-components)

[pluralsight - CSS encapsulation in Angular](https://www.pluralsight.com/guides/css-encapsulation-in-angular)

Interesting to check [Web Component Essentials (Cory Rylan book)](https://leanpub.com/web-component-essentials)

Interesting [Pluralsight guides](https://www.pluralsight.com/guides)

[The state of CSS in angular](https://blog.angular.io/the-state-of-css-in-angular-4a52d4bd2700)

[angular best practices](https://codeburst.io/angular-best-practices-4bed7ae1d0b7)

[native browser touch drag using overflow scroll](https://medium.com/creative-technology-concepts-code/native-browser-touch-drag-using-overflow-scroll-492dc92ac737)

[angular univ - ng-template ng-container ngtemplateoutlet](https://blog.angular-university.io/angular-ng-template-ng-container-ngtemplateoutlet/) TRY the examples on stackblitz!!

[angularindepth - use ng-template](https://blog.angularindepth.com/use-ng-template-c72852c37fba)

[angularindepth - intro advanced angular component patterns](https://blog.angularindepth.com/introducing-advanced-angular-component-patterns-13e102e6bbfc) SERIES... 

[create advanced components in angular](https://netbasal.com/create-advanced-components-in-angular-e0655df5dde6)

### 7 May 2019

[john papa - angular ngrx data](https://github.com/johnpapa/angular-ngrx-data)

[ngrx data lab](https://github.com/johnpapa/ngrx-data-lab/blob/master/README.md)

[ngrx.io](https://ngrx.io/)

[ngrx data and json server mock services](https://medium.com/@coco.boudard/ngrx-data-and-json-server-mock-services-f4d9d76aa654)

[Breeze - client side data management](http://breeze.github.io/doc-main/)

[ng tips and tricks for css structure](https://medium.com/@kmathy/angular-tips-and-tricks-for-css-structure-cb73fa50f0e8)

[alligator.io - view encapsulation](https://alligator.io/angular/viewencapsulation/)

[horizontal scrolling bars](https://codeburst.io/how-to-create-horizontal-scrolling-containers-d8069651e9c6)

### 6 May 2019

[jason watmore - ng6 communicating btwn comps with observable subject](https://jasonwatmore.com/post/2018/06/25/angular-6-communicating-between-components-with-observable-subject)

[These ARE the Angular tips you are looking for | John Papa](https://www.youtube.com/watch?v=2ZFgcTOcnUg)

[guitar - When You Say Nothing At All Guitar Tutorial - Ronan Keating Guitar Lesson 🎸 |Tabs + No Capo|](https://www.youtube.com/watch?v=jNTah4UFF_Q)

[guitar - When you say nothing at all - B.S.O. Nothing Hill EASY CHORDS Demo Cover Lyrics and Chords guitar](https://www.youtube.com/watch?v=Szb-mp3_m3I)

### 3 May 2019

[angularindepth - 5 articles to make you an angular change detection expert](https://blog.angularindepth.com/these-5-articles-will-make-you-an-angular-change-detection-expert-ed530d28930)

[ng lazy loading for dummies](https://codeburst.io/how-to-implement-lazy-loading-in-angular-bb2a670b34d)

[angularindepth - level up your reverse engineering skills](https://blog.angularindepth.com/level-up-your-reverse-engineering-skills-8f910ae10630)

[angularindepth](https://blog.angularindepth.com/) - page worth look 

### 2 May 2019

>  Change detection, immutability, performance...
>  
>  [angularindepth - A gentle introduction into change detection in Angular](https://blog.angularindepth.com/a-gentle-introduction-into-change-detection-in-angular-33f9ffff6f10)
>  
>  [angularindepth - everything you need to know about change detection in angular](https://blog.angularindepth.com/everything-you-need-to-know-about-change-detection-in-angular-8006c51d206f)

[Charles Laveso - realistic drawing](https://www.youtube.com/watch?v=1VehlZRJLCo&list=PLc3nkjX2uGqaSpG5a8bQpNLBKvgwuV4pW)

[charlesdesenhosrealistas](https://charlesdesenhosrealistas.com.br/en/course/)

### 1 May 2019

[ng2+ communicating btwn components with observable subject](http://jasonwatmore.com/post/2016/12/01/angular-2-communicating-between-components-with-observable-subject)

[ng2 and observables data sharing in a multi-view app](https://www.lucidchart.com/techblog/2016/11/08/angular-2-and-observables-data-sharing-in-a-multi-view-application/)

[6 simple examples which will make you love observables (rxjs 5)](https://x-team.com/blog/rxjs-observables/)

[generate random string chars in JS](https://stackoverflow.com/questions/1349404/generate-random-string-characters-in-javascript) // is worth to read the comments

[atlassian CRUCIBLE - Collaborative code review](https://www.atlassian.com/software/crucible)

### 30 Apr 2019

[refresh current rout in angular](https://blog.angularindepth.com/refresh-current-route-in-angular-512a19d58f6e)

[Dr. Axel Rauschmayer - JS time values](http://2ality.com/2014/02/time-values.html)

[the definitive guide to datetime manipulation](https://www.toptal.com/software/definitive-guide-to-datetime-manipulation)

[invoice template microsoft](https://templates.office.com/en-us/Service-invoice-with-tax-calculations-TM16400625)

[MDN - useful string methods (and some exercises)](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Useful_string_methods)

>  [javascript.info](https://javascript.info/)
>  
>  [eg. keys values entries](https://javascript.info/keys-values-entries)

### 28 Apr 2019

[open layer](https://openlayersbook.github.io/ch04-interacting-with-raster-data-source/example-03.html)

[Open Layers (webpack)](https://github.com/openlayers/ol-webpack)

### 26 Apr 2019

[angular router route parameters activatedroute ...](https://www.techiediaries.com/angular-router-route-parameters/)

### 25 Apr 2019

[advanced caching with rxjs](https://blog.thoughtram.io/angular/2018/03/05/advanced-caching-with-rxjs.html)

[angular.io - structural directives (nt-template, ng-container, ng-content...)](https://angular.io/guide/structural-directives)

[ng-template ng-container ngtemplateoutlet](https://blog.angular-university.io/angular-ng-template-ng-container-ngtemplateoutlet/)

### 24 Apr 2019

[html color picker](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/color

[ng6 crud example](https://www.javaguides.net/2019/02/angular-6-crud-app-example.html)

[angular folder structure](https://medium.com/@motcowley/angular-folder-structure-d1809be95542)

[choosing a highly scalabel folder structure in angular](https://itnext.io/choosing-a-highly-scalable-folder-structure-in-angular-d987de65ec7)

[flexbox](https://internetingishard.com/html-and-css/flexbox/)

### 22 Apr 2019

[Client side JS](https://saratoga-weather.org/JavaScriptClientGuideJS13.pdf)

### 18 Apr 2019

[MDN - JS Obj: obj prototypes](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object_prototypes)

[MDN - JS guide: Details of the Obj model](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Details_of_the_Object_Model)

### 17 Apr 2019

[JS expose global variables methods modules...](http://www.matthiassommer.it/programming/web/javascript/expose-global-variables-methods-modules-javascript/)

[understanding JS constructors](https://css-tricks.com/understanding-javascript-constructors/)

### 16 Apr 2019

[memoization - improve recursive solution for fibojnacci sequence problem](https://medium.com/@nothingisfunny/memoization-improving-recursive-solution-for-fibonacci-sequence-problem-c02dab7a74e5)

[how to succed in a FE interview](https://blog.pramp.com/how-to-succeed-in-a-frontend-interview-d748cb073823)

### 15 Apr 2019

[Custom maps to react using mapbox](https://blog.cloudboost.io/adding-custom-maps-to-react-app-using-mapbox-bb978845e7ad)

[fibonacci sequence JS interview ?: iterative and recursive solutions](https://medium.com/quick-code/fibonacci-sequence-javascript-interview-question-iterative-and-recursive-solutions-6a0346d24053)

[fibonacci sequence algorithm in JS](https://medium.com/developers-writing/fibonacci-sequence-algorithm-in-javascript-b253dc7e320e)

[Addy Osmani - essential JS Design Patterns (BOOK)](https://addyosmani.com/resources/essentialjsdesignpatterns/book/)

[discover the power of closures in JS](https://medium.freecodecamp.org/discover-the-power-of-closures-in-javascript-5c472a7765d7)

[benefits of being VAT registered](https://www.simpleformations.com/blog/the-4-big-benefits-of-being-vat-registered.html)

### 13 Apr 2019

[follow this link to check if bug was fixed (angular-devkit > node-sass > node-gyp)](https://github.com/angular/angular-cli/issues/14138)

[Academind - Google Maps & Angular | ANGULAR SNIPPETS](https://www.youtube.com/watch?v=lApggVS0icc)

[teaching material: angular website - HTML Template to Angular Component](https://www.youtube.com/watch?v=LYmJOdCuXrs)

[Vectary - free browser-based 3D modeling Tool](https://www.youtube.com/watch?v=bedVCq5Y-Jo)

### 11 Apr 2019

[Augmented Reality with JS a case study](https://medium.freecodecamp.org/augmented-reality-with-javascript-a-case-study-c9cffaadcf07)

[app ideas to level up coding skills](https://medium.freecodecamp.org/here-are-some-app-ideas-you-can-build-to-level-up-your-coding-skills-39618291f672)

[master webVR with a weed of experiments](https://glitch.com/culture/master-webvr-with-a-week-of-experiments/)

### 10 Apr 2019

[MDN - Web API AnalyserNode (interface to process Audio frecuencies)](https://developer.mozilla.org/en-US/docs/Web/API/AnalyserNode)

[MDN - Web Audio API (Visualizations)](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API/Visualizations_with_Web_Audio_API)

[Analyser Bars Animation HTML5 Audio API JavaScript Tutorial](https://www.youtube.com/watch?v=IBHpSkGZtNM)

[vimeo - ctrlpaint](https://vimeo.com/ctrlpaint)

### 8 Apr 2019

[Discussion on Pagination & Mongoose](https://stackoverflow.com/questions/5539955/how-to-paginate-with-mongoose-in-node-js)

[codeforgeek - render html file express](https://codeforgeek.com/2019/03/render-html-file-expressjs/)

[scotch.io use ejs to template your node app](https://scotch.io/tutorials/use-ejs-to-template-your-node-application)

[adding nodemailer email contact form node-express app](https://tylerkrys.ca/blog/adding-nodemailer-email-contact-form-node-express-app)

### 7 Apr 2019

[smashing magazine - forms category](https://www.smashingmagazine.com/category/forms)

[smashing magazine - extensive guide on web form usability](https://www.smashingmagazine.com/2011/11/extensive-guide-web-form-usability/)

[CRUZ - deployed weather-app to github pages](https://zurc.github.io/weather-app)

[CRUZ - deployed weather-app to stackblitz](https://github-hmfo4j.stackblitz.io)

[CRUZ - to edit on stackblitz](https://stackblitz.com/edit/github-hmfo4j)

[deploy angular CLI to github pages or stackblitz](https://blog.mimacom.com/angular-cli-github-pages-stackblitz/) √√√

[How to Create & Host a Portfolio with Github pages! #grindreelwhat](https://www.youtube.com/watch?v=u-RLu_8kwA0)

[Traversy Media - GitHub Pages Deploy & Domain](https://www.youtube.com/watch?v=SKXkC4SqtRk)

[HTML5 templates - responsive](https://html5up.net/) made by [ajlkn](https://aj.lkn.io/)

### 6 Apr 2019

[smart homes - openhab (open source)](https://www.openhab.org/)

### 5 Apr 2019

[CRUZ - Weather app (angular 7, material, openweathermap API)](https://stackblitz.com/edit/angular-tqxgfg)

[youtube playlist - angular weather app](https://www.youtube.com/watch?v=0YSFRBN1OVI&list=PLONAys1AYOAmZ27U0eAerFlHkUXLa5cii)

[weather app refs](https://www.vovoclip.com/academind/JJ15JJ9058AS18PP941115.html)

[top 10 energy terms](https://www.switchcraft.co.uk/energy-comparison-sites-decoded-top-10-energy-terms-you-need-to-know/)

[youtube - stackblitz angular demo](https://www.youtube.com/watch?v=GV0fBEJn2TA)

### 4 Apr 2019

[illustrated dev](https://illustrated.dev/fruit-comparison) √√√

[maggie mappletons twitter](https://twitter.com/mappletons)

[3 keys landing job love](https://hired.com/blog/candidates/3-keys-landing-job-love)

[19 phone interview tips - get hired](https://hired.com/blog/candidates/19-phone-interview-tips-get-hired)

### 3 Apr 2019

[React for the visual learner (chapter 1)](https://medium.com/coding-artist/react-js-for-the-visual-learner-chapter-1-what-is-this-all-about-a0d28cfd33c6)

### 2 Apr 2019

[Multer Docs](https://github.com/expressjs/multer)

[Tutorial on Angular Image Upload](https://academind.com/learn/angular/snippets/angular-image-upload-made-easy)

### 1 Apr 2019

[Mongoose Docs](http://mongoosejs.com/docs/guide.html)

[MongoDB Docs](https://www.mongodb.com/)

[MongoDB Atlas Docs](https://www.mongodb.com/cloud/atlas)

[add directory to mac path](https://www.architectryan.com/2012/10/02/add-to-the-path-on-mac-os-x-mountain-lion/)

[how do I ensure mongo binaries are in my path](https://stackoverflow.com/questions/28267773/how-do-i-ensure-that-mongo-binaries-are-in-my-path-in-my-shell-rc-bashrc)

MONGODB - CLOUD (atlas)

created a new cluster (AWS), connected my express app

check it's working: connect mongodb shell (hombrew install), files installed on

```
/usr/local/Cellar/mongodb-community-shell/4.0.8/
```
copie files to mongodb/bin to connect

show collections

db.posts.find()  // it's there, so it's working fine

### 31 Mar 2019

[museums and the web](https://mw2015.museumsandtheweb.com/best-of-the-web-nominees/)

### 29 Mar 2019

[Learn Node + Express from Scratch (for free!)](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs)

[academind - Creating a REST API with Node + Express (+ MongoDB)](https://academind.com/learn/node-js/building-a-restful-api-with/)

[academind - RxJS Tutorial](https://academind.com/learn/javascript/understanding-rxjs/)

[academind - Reference vs Primitive Types in JS](https://academind.com/learn/javascript/reference-vs-primitive-values/)

Angular - property binding: [DOM property]="..." <- what angular looks for (inside the quotation marks) is typescript code. If I write 'something' it will look for a property 'something' on the component class. If you want to pass a string, then you need to wrap it in single quotation marks like this

```
[DOM property]="'something'"
```

The shortcut is to remove square brackets and pass the text directly

```
DomProperty="something"
```

[1st steps w/ ng7 CLI and ng Material](https://medium.com/@ismapro/first-steps-with-angular-7-with-angular-cli-and-angular-material-d69f55d8ac51)

### 28 Mar 2019

[uxdesign - 100 days of motion design](https://uxdesign.cc/100-days-of-motion-design-463526af852f)    // motivation - inspiration

[UX - el master UX school desde dentro](https://medium.com/@mauritorra/el-m%C3%A1ster-ux-de-kschool-desde-dentro-2c009687e3f3)  √√√

[Figma templates](https://www.figma.com/templates/)

### 27 Mar 2019

>  ES6 local Project Setup:
>  
>  [JavaScript Package Manager for a All-in-one workflow](http://jspm.io/)
>  
>  [Using ES6 with Babel and SystemJS](http://www.barbarianmeetscoding.com/blog/2016/02/21/start-using-es6-es2015-in-your-project-with-babel-and-gulp/)
>  
>  [Using Webpack](http://jamesknelson.com/using-es6-in-the-browser-with-babel-6-and-webpack/)

[MDN - ES6 reflect](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Reflect)

Learning about ES6: Sets and WeakSets [udemy - max - es6](https://www.udemy.com/es6-bootcamp-next-generation-javascript)

[CRUZ - ES6 Set object and methods](https://jsbin.com/gicofuy/2/edit)

[CRUZ - ES6 WeakSet object and methods](https://jsbin.com/huzerey/2/edit)

[CRUZ - ES6 creating objects with Reflect.construct()](https://jsbin.com/tuloca/4/edit)

[MDN - ES6 Reflect.apply()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Reflect/apply)

[CRUZ - ES6 Reflect.apply()](https://jsbin.com/wikumud/4/edit)

[scotch.io - better node with es6](https://scotch.io/tutorials/better-node-with-es6-pt-i)

### 26 Mar 2019

>  programming languages frameworks design patterns and paradigms
>  
>  [wikipedia - comparison of programming paradigms](https://en.m.wikipedia.org/wiki/Comparison_of_programming_paradigms)
>  
>  [sourcemaking - design patterns](https://sourcemaking.com/design_patterns)

Learning about ES6 extension of built-in objects: all and race, Maps, WeakMaps [udemy - max - es6](https://www.udemy.com/es6-bootcamp-next-generation-javascript)

[CRUZ - ES6 built-in methods all and race](https://jsbin.com/yayafux/3/edit)

[CRUZ - ES6 Map object and methods](https://jsbin.com/tumetin/3/edit)

[CRUZ - ES6 WeakMap object](https://jsbin.com/seselet/3/edit)

### 23 Mar 2019

>  Estudiar, entender, retener, recordar (propósito, enseñar, relacionar, visualizar, aplicar lo aprendido)
>  
>  [aprende a retener y recordar lo que lees](https://www.ticbeat.com/cyborgcultura/aprende-a-retener-y-recordar-lo-que-lees/)
>  
>  [10 técnicas de estudio para retener y recordar eficazmente](http://psicologiacuriosa.com/2015/02/06/10-increibles-tecnicas-de-estudio-para-retener-y-recordar-eficazmente/)

[ES6 compatibility table](https://kangax.github.io/compat-table/es6/)

ES6 promises - handle asynchronicity

[CRUZ - promises jsbin](https://jsbin.com/cuqebug/4/edit)

[udemy (max) - creando y resolviendo promises](udemy.com/es6-bootcamp-next-generation-javascript)

### 22 Mar 2019

[Traversy media - Vanilla JS youtube playlist](https://www.youtube.com/playlist?list=PLillGF-RfqbbnEGy3ROiLWk7JMCuSyQtX)

[CRUZ - example of Accordion made on vanilla JS](https://stackblitz.com/edit/js-g6m75p?file=index.js)

[CRUZ - example of filterable search list with vanilla JS](https://stackblitz.com/edit/js-4dxazd?file=index.js)

[dev-notes - attach click event to many elementes in JS](https://dev-notes.eu/2017/09/attach-click-event-to-many-elements-in-javascript/)

[gist for Learn vanilla JS in about 10 minutes](https://gist.github.com/cferdinandi/32b0aebaab862a7a3a2580769349d8fe)

[learn-vanilla-js github repo](https://github.com/snipcart/learn-vanilla-js)

[learn vanilla javascript](https://designmodo.com/learn-vanilla-javascript/)

[freecodecamp - is vanilla JS worth learning?](https://medium.freecodecamp.org/is-vanilla-javascript-worth-learning-absolutely-c2c67140ac34)

>  [treehouse show episode](jQuery Plugins | Progress Bars | HTTP API Design | The Treehouse Show Episode 96)
>  
>  [http API design](https://github.com/interagent/http-api-design) // [book](https://geemus.gitbooks.io/http-api-design/content/en/)

[personal business tax changes 2019](https://www.crunch.co.uk/knowledge/tax/personal-business-tax-changes-new-tax-year/)

### 21 Mar 2019

[sitepoint - avoid SASS extend](https://www.sitepoint.com/avoid-sass-extend/)

[css tricks - CSS modules](https://css-tricks.com/css-modules-part-1-need/)

[javascriptstuff - what are CSS modules](https://www.javascriptstuff.com/what-are-css-modules/)

[indesign - creative resume design](https://helpx.adobe.com/indesign/how-to/creative-resume-design.html)

### 20 Mar 2019

[optimizando customer journey mejorar ventas](https://blog.seogea.pro/optimizando-customer-journey-mejorar-ventas/)

[automatic debit payments protection](https://www.consumerfinance.gov/about-us/blog/you-have-protections-when-it-comes-to-automatic-debit-payments-from-your-account/)

### 18 Mar 2019

[how to setup discourse on azure](https://meta.discourse.org/t/how-to-setup-discourse-on-azure/89550)

### 17 Mar 2019

[photoshop manipulation blog](http://pstmanipulation.blogspot.com/)

[song book Yamaha](https://europe.yamaha.com/files/download/other_assets/4/866764/E363songbook_En.pdf)

### 16 Mar 2019

[alligator.io - testing async fakeasync](https://alligator.io/angular/testing-async-fakeasync/)

[How to Become a Pianist in Ten Lessons](https://www.youtube.com/watch?v=drO86DNI348&list=RDdrO86DNI348&start_radio=1&t=851)

### 15 Mar 2019

[stackoverflow - unit testing click event in angular](https://stackoverflow.com/questions/40093013/unit-testing-click-event-in-angular)

[testing custom events on angular](https://www.vincecampanale.com/blog/2018/03/22/testing-custom-events-angular/)

[A JS black belt - jasmine tests expect throw](https://ajsblackbelt.wordpress.com/2014/05/18/jasmine-tests-expect-tothrow/)

[dave ceddia - jasmine 2 spy cheat sheet](https://daveceddia.com/jasmine-2-spy-cheat-sheet/)

[oreilly - JS Testing with Jasmine by Evan Hahn](https://www.oreilly.com/library/view/javascript-testing-with/9781449356729/ch04.html)

[toBeTruthy vs toBe(true)](https://vincenttunru.com/toBeTruthy-vs-toBe-true/)

[an overview of JS testing in 2019](https://medium.com/welldone-software/an-overview-of-javascript-testing-in-2019-264e19514d0a)

[25 game changing JS tools](https://www.creativebloq.com/features/25-game-changing-javascript-tools)

### 14 Mar 2019

[angular delete confirmation - redux](https://brianflove.com/2017/07/17/angular-delete-confirmation/)

>  started jasmine test [pluralsight - play by play fundamentals fo angular testing](https://app.pluralsight.com/library/courses/play-by-play-fundamentals-of-angular-testing/discussion)
>  
>  [their github](https://github.com/duncanhunter/pluralsight-angular-testing-play-by-play) // need update of versions...
>  
>  at the end used nvm v7... and installed globally json-server

[using json server to create a restful server](https://itnext.io/using-json-server-to-create-a-restful-server-in-5-seconds-78b85ccf832b)

### 13 Mar 2019

[techdiaries - angular 7 + bootstrap 4 (ng-bootstrap/ngx-bootstrap/jquery)](https://www.techiediaries.com/angular-bootstrap-ui/) // seems to have interesting tuts on ng7

### 12 Mar 2019

[ng6 custom modal (and service)](http://jasonwatmore.com/post/2018/05/25/angular-6-custom-modal-window-dialog-box)

>  FE architecture
>  
>  [building a redux app with ng 2](https://app.pluralsight.com/guides/building-a-redux-application-with-angular-2-part-1)
>  
>  [mvvm mvc - unidirectional](https://michaelridland.com/xamarin/mvvm-mvc-is-dead-is-unidirectional-a-mvvm-mvc-killer/)
>  
>  [angular, ngrx, socket.io frontend](https://github.com/avatsaev/angular-ngrx-socket-frontend/blob/master/README.md)
>  
>  [react app architecture](https://medium.com/@Xourse/reactjs-app-architecture-7a33d7ae9834)

example: [wireframes, annotations, navigation](https://www.slideshare.net/vipul80/wireframes-do-today)

Definition of Done or Ready, good examples !! [DOD vs. DOR](https://blog.taiga.io/definition-of-ready-definition-of-done-the-difference.html)

to read [UX - how do you know when design is done](https://medium.com/@andreas.johansson.dev/ux-process-how-do-you-know-when-your-design-is-done-a-simple-14-point-checklist-21b747e82954)

[narrative, storytelling (for user stories)](https://www.inc.com/carmine-gallo/jeff-bezos-bans-powerpoint-in-meetings-his-replacement-is-brilliant.html)

[balsamiq blog - Using Wireframes with Agile User Stories](https://balsamiq.com/learn/resources/articles/userstories/)

### 11 Mar 2019

[medium - simplified angular unit testing](https://medium.com/@meshileya/simplified-angular-unit-testing-caffe0fccf31)

Mean books

https://www.manning.com/books/getting-mean-with-mongo-express-angular-and-node

https://www.packtpub.com/web-development/mean-web-development

>  FORUM related...
>  
>  [discourse (open source) - Ruby on Rails, Ember, Postgres, Redis](https://github.com/discourse/discourse)
>  
>  [telescopeapp org - meteor, react](http://www.telescopeapp.org/)
>  
>  [spectrum chat](https://spectrum.chat/)
>  
>  [vue forum](https://madewithvuejs.com/vue-forum)
>  
>  [medium - a forum engine using node and vue](https://medium.com/@meshileya/a-forum-engine-using-nodejs-and-vuejs-10b5939ebf2e)


### 8 Mar 2019

another test course... [pluralsight - play by play fundamentals of ng testing](https://app.pluralsight.com/library/courses/play-by-play-fundamentals-of-angular-testing/table-of-contents)

[building full stack app using ng CLI and Nx](https://blog.nrwl.io/building-full-stack-applications-using-angular-cli-and-nx-5eff205248f1)  // really interesting

[codecraft.tv - ng unit testing](https://codecraft.tv/courses/angular/unit-testing/overview/)

### 7 Mar 2019

[scotch.io - 3 useful typescript tips for angular](https://scotch.io/tutorials/3-useful-typescript-tips-for-angular)

[tutsplus - testing comps in ng using jasmine (part2) services](https://code.tutsplus.com/tutorials/testing-components-in-angular-using-jasmine-part-2-services--cms-28933)

[semaphoreci - testing services in angular 2](https://semaphoreci.com/community/tutorials/testing-services-in-angular-2)

[codecraft.tv - ng unit testing mocks and spies](https://codecraft.tv/courses/angular/unit-testing/mocks-and-spies/)

[talkingdotnet - add bootstrap 4 to ng 6 app](https://www.talkingdotnet.com/add-bootstrap-4-to-angular-6-application/)

>  [loiane - hot to add bootstrap to an angular CLI project](https://loiane.com/2017/08/how-to-add-bootstrap-to-an-angular-cli-project/)
>  
>  2 ways to import styles from Bootstrap that was installed trough npm:
>  
>  1-configure angular.json   |  2-import into your styles file
>  
>  "...I personally prefer to import all my styles in src/style.(s)css since it’s been declared in angular.json already."

### 5 Mar 2019

[easy way to deploy an ng5 app to azure web app using vsts pipelines](https://itnext.io/easy-way-to-deploy-a-angular-5-application-to-azure-web-app-using-vsts-pipelines-4a288b9deae1)

[angular errors: 'ng' is not recognised'](https://programmingwithmosh.com/angular/common-angular-errors/)

### 4 Mar 2019

>  Angular testing... check this links
>  
>  [Official documentation](https://angular.io/docs/ts/latest/guide/testing.html)
>  
>  [semaphoreci - testing components in angular 2 with jasmine](https://semaphoreci.com/community/tutorials/testing-components-in-angular-2-with-jasmine)
>  
>  [running tests with the CLI](https://github.com/angular/angular-cli/wiki/test)
>  
>  [e2e test](https://github.com/angular/angular-cli/wiki/e2e)

[angular 2 rxjs common pitfalls](https://blog.angular-university.io/angular-2-rxjs-common-pitfalls/)

[35 angular interview questions and answers 2019](https://www.devteam.space/wp-content/uploads/2018/12/DevTeam.Space_35-Angular-Interview-Questions-and-Answers-for-2019.pdf)

[angular 6/7 http client](https://www.techiediaries.com/angular-httpclient/)

### 28 Feb 2019

[11 angular component libraries ...](https://blog.bitsrc.io/11-angular-component-libraries-you-should-know-in-2018-e9f9c9d544ff)

[angular resources](https://angular.io/resources)

[reddit - what i learned when i switched from bootstrap to angular material](https://www.reddit.com/r/Angular2/comments/7ehjby/what_i_learned_when_i_switched_to_angular/)

[clarity design system for figma](https://medium.com/@sergey_81667/clarity-design-system-for-figma-9778e11cf30f)

[beyond bootstrap moving from ui toolkit to component library](https://blog.hichroma.com/beyond-bootstrap-moving-from-ui-toolkit-to-component-library-f0a34f05e98b)

[the good parts of Bootstrap 4 you are missing in your angular material projects](https://www.amadousall.com/the-good-parts-of-bootstrap-4-you-are-missing-in-your-angular-material-projects/)

[7 Angular Tools That You Should Consider](https://blog.mgechev.com/2017/04/23/angular-tooling-codelyzer-angular-cli-ngrev/)

angular virtual DOM? [intro to ng VDOM...](https://blog.angularindepth.com/introducing-to-ng-vdom-a-new-way-to-write-angular-application-60a3be805e59)

>  ANGULAR DEBUGGGING
>  
>  [cory rylan - angular debugging tips and tricks](https://coryrylan.com/blog/angular-debugging-tips-and-tricks)
>  
>  [augury](https://augury.rangle.io/pages/guides/index.html)
>  
>  [angularfirebase - methods for debugging an angular app](https://angularfirebase.com/lessons/methods-for-debugging-an-angular-application/)
>  
>  [angularindepth - everything you need to know about debugging angular applications](https://blog.angularindepth.com/everything-you-need-to-know-about-debugging-angular-applications-d308ed8a51b4)

### 26 Feb 2019

>  Debugging tools
>  
>  [JS debuggin tools](https://raygun.com/javascript-debugging-tools)
>  
>  [scotch.io - debugging JS with chrome dev tool breakpoints](https://scotch.io/tutorials/debugging-javascript-with-chrome-devtools-breakpoints)
>  
>  [telerik - improve your debugging skills with chrome devtools](https://www.telerik.com/blogs/improve-your-debugging-skills-with-chrome-devtools)
>  
>  [scotch.io - debugging JS in google chrome and visual studio code](https://scotch.io/tutorials/debugging-javascript-in-google-chrome-and-visual-studio-code)

### 25 Feb 2019

[uxmastery - how to conduct a content audit](https://uxmastery.com/how-to-conduct-a-content-audit/)

[101 awesome tools for web designers and developers](https://www.beewits.com/101-awesome-tools-for-web-designers-and-developers/)

[uxmastery - how to conduct a content audit](https://uxmastery.com/how-to-conduct-a-content-audit/)

[usability.gov - content inventory](https://www.usability.gov/how-to-and-tools/methods/content-inventory.html)

### 23 Feb 2019

>  Interesante [Advanced environment design (digital art)](https://gumroad.com/l/uYtoK)
>  
>  [Raphael Lacoste](https://gumroad.com/raphaellacoste)

### 22 Feb 2019

[The Next Generation of Creativity | Adobe Max 2018 Keynote](https://www.youtube.com/watch?v=KzMMbTNKc5k)

[Adobe XD guide](https://www.xdguru.com/adobe-xd-guide) // good documentation

[medium - adobe XD plugins and open source](https://medium.com/adobetech/adobe-xd-plugins-and-open-source-4293977594a9)

### 21 Feb 2019

interesting [collaboration books with penflip](https://www.penflip.com/discover)

[collaboration, design review...](https://www.mockplus.com/blog/post/sketch-collaboration)

[VSCode extentions for dev](https://scotch.io/bar-talk/22-best-visual-studio-code-extensions-for-web-development)

>  Angular testing - jasmine, karma
>  
>  [reddit - angular testing with jasmine](https://www.reddit.com/r/webdev/comments/8jizxi/best_way_to_learn_angular_testing_with_jasmine/)
>  
>  [scotch.io - testing ng jasmine karma](https://scotch.io/tutorials/testing-angular-with-jasmine-and-karma-part-1) √√√
>   
>  [medium - ng unit testing jasmine karma](https://medium.com/frontend-fun/angular-unit-testing-jasmine-karma-step-by-step-e3376d110ab4)

[debugging JS in chrome and VS Code](https://scotch.io/tutorials/debugging-javascript-in-google-chrome-and-visual-studio-code)

### 20 Feb 2019

>  REMOTE
>  
>  [team tools for remote work](https://highfive.com/blog/team-tools-for-remote-work)
>  
>  [best tools video conferencing](https://blog.hubstaff.com/best-tools-video-conferencing/)
>  
>  [remote work tools](https://skillcrush.com/2016/10/24/remote-work-tools/)    // 2016... check newer options

[templatemonster - wireframe kits photoshop](https://www.templatemonster.com/blog/free-wireframing-kits-photoshop-mocking-up-interfaces/)

[wireframe tool comparison](https://zapier.com/blog/best-wireframe-tools/)    // good in depth comparison


### 19 Feb 2019

[dzone - angular libraries and microservices](https://dzone.com/articles/angular-libraries-and-microservices-1)

### 18 Feb 2019

[scrumhub - axosoft](https://www.scrumhub.com/)

[uxplanet - how to create information architecture for web design](https://uxplanet.org/how-to-create-information-architecture-for-web-design-86ee9dc4be1)

[how to user testing your app](https://savvyapps.com/blog/how-to-user-testing-your-app)

[BOOK - information architecture for the WWW](http://yunus.hacettepe.edu.tr/~tonta/courses/fall2010/bby607/IAWWW.pdf)

[best practices for onboarding](https://uxplanet.org/best-practices-for-onboarding-92f3a9f0b21a)

[5 methods for increasing app engagement user retention](https://clearbridgemobile.com/5-methods-for-increasing-app-engagement-user-retention/)

[jqwidgets -> angular](https://www.jqwidgets.com/angular)  // ideas

[ng structure for multi user webapp](https://stackoverflow.com/questions/47659795/angular-4-structure-for-multi-user-webapp)

[creating a FE for your user profile store](https://dzone.com/articles/creating-a-front-end-for-your-user-profile-store-w)

[auth0 - real world angular series](https://auth0.com/blog/real-world-angular-series-part-1/)

[ng flex layout flexbox and grid layout](https://blog.angularindepth.com/angular-flex-layout-flexbox-and-grid-layout-for-angular-component-6e7c24457b63)

[authorization based on role and entity states](https://medium.com/@eliasmsedano/angular-4-how-to-check-authorization-based-on-role-and-entity-states-cf0282280961)

[css-tricks - conferences](https://conferences.css-tricks.com/)

[state of JS](https://stateofjs.com/)

[insightly - user adoption best practices](https://www.insightly.com/blog/2018/09/user-adoption-5-crm-best-practices-for-insightly/)

### 17 Feb 2019

[UX design trends](https://trends.uxdesign.cc/) // interesting views
[12 mobile UX des trends](https://uxplanet.org/12-mobile-ux-design-trends-for-2018-5b4ce7e8445f)

ng7-search-edit (local test)

### 16 Feb 2019

[ng7 search and edit demo](https://github.com/mraible/ng-demo)

### 15 Feb 2019

>  UI/UX Inspiration - Ideas
>  
>  https://www.mockplus.com/blog/post/design-inspiration-sites
>  
>  https://blog.prototypr.io/10-best-prototyping-tools-for-ui-ux-designers-in-2018-6591ea1e2e71
>  
>  https://www.mockplus.com/blog/post/best-app-design-2018   // interaction des - animations
>  
>  https://www.tronebrandenergy.com/blog/10-examples-good-user-experience-ux
>  
>  https://uxplanet.org/12-mobile-ux-design-trends-for-2018-5b4ce7e8445f

[why software dev use Mac](https://www.quora.com/Why-do-so-many-software-developers-use-Mac-even-though-Windows-has-much-advanced-technology-and-better-features)

[when to use interface and model in angular](https://stackoverflow.com/questions/37652801/when-to-use-interface-and-model-in-typescript-angular2)

[tod motto - angular classes vs interfaces](https://toddmotto.com/classes-vs-interfaces-in-typescript)

[academind - angular image upload made easy](https://www.academind.com/learn/angular/snippets/angular-image-upload-made-easy/)

[priority guides: a content first alternative to wireframes](https://alistapart.com/article/priority-guides-a-content-first-alternative-to-wireframes)

>  angular cli
>  
>  [angular CLI cheatsheet](https://baswanders.com/angular-cli-cheatsheet-an-overview-of-the-most-used-commands/)
>  
>  [alligator - angular CLI reference](https://alligator.io/angular/angular-cli-reference/)

### 14 Feb 2019

[UX design - storyboards, user epics, user stories, user resesarch](http://www.verse-co.com/journal/2017/7/6/ux-design-storyboards-user-epics-user-stories-user-research)

[uxplanet - storyboarding in UX design](https://uxplanet.org/storyboarding-in-ux-design-b9d2e18e5fab)

[10 tips writing good user stories](https://www.romanpichler.com/blog/10-tips-writing-good-user-stories/)

### 13 Feb 2019

[Angular 2 architecture (Slideshare)](https://www.slideshare.net/EyalV/angular-2-architecture)

[ng4 tut](https://www.slideshare.net/EdurekaIN/angular-4-tutorial-whats-new-in-angular-4-angular-training-edureka)

[ng4 tut](https://www.slideshare.net/rojaware/angular-4-introduction-tutorial) // good explanations

[ng6 registration login example](https://stackblitz.com/edit/angular-6-registration-login-example-9kkh7c?) // interesting architecture

[mdbootstrap - angular - bootstrap 4 - material](https://mdbootstrap.com/docs/angular/forms/basic/)

[jasonmore - ng7 reactive forms validation example](http://jasonwatmore.com/post/2018/11/07/angular-7-reactive-forms-validation-example)

[ng7 forms](https://appdividend.com/2018/10/24/angular-7-forms-tutorial-example/)

### 11 Feb 2019

>  The most common reasons that consumers report *giving up on an app* are because __it hasn’t met their expectations, it’s confusing to use or it hasn’t demonstrated any value.__

[invision app - design sprint 2.0](https://www.invisionapp.com/inside-design/design-sprint-2/)

[design sprint day by day](https://www.design-sprint.com/en/design-sprint-day-by-day/)

[GV sprint](https://www.gv.com/sprint/)

### 10 Feb 2019

>  Pluralsight - Adobe XD
>  
>  [UX design - creating wireframes](https://www.pluralsight.com/courses/ux-design-creating-wireframes)
>  
>  [XD CC fundamentals](https://www.pluralsight.com/courses/experience-design-cc-fundamentals) // 2016 outdated?
>  
>  [Adobe XD CC fundamentals](https://www.pluralsight.com/courses/adobe-xd-cc-fundamentals)  // 2018

[sitepoint - prototyping with Adobe XD](https://www.sitepoint.com/prototyping-with-adobe-xd/)

[35 Best Free Adobe XD UI Kit for APP and Web Design](https://www.mockplus.com/blog/post/adobe-xd-ui-kit)

[angular + Microsoft Stack (Visual Studio, ASP.NET, Core and Azure)](https://angularfirst.com/)

### 8 Feb 2019

[design systems repo](https://designsystemsrepo.com/design-systems/)

>  [Adobe XD - how to build a single source of truth (pattern library)](https://theblog.adobe.com/how-to-build-a-single-source-of-truth-with-adobe-xd/)
>  
>  Essentially, a pattern library is a collection of design elements that are reused across a website or app, from basic navigation to more complex items like carousels, social media components, and so on. The pattern library not only holds all of these patterns, but it defines what they look like and how they act.

[scrum - sprint retrospectives to improve](https://blogs.adobe.com/agile/tag/scrum-master/)

[Adobe XD tips and tricks](https://helpx.adobe.com/xd/help/tips-and-tricks.html)

[Vue mastery youtube channel](https://www.youtube.com/channel/UCa1zuotKU4Weuw_fLRnPv0A)

[xs resources UI kits](https://speckyboy.com/free-adobe-xd-ui-kits/)

[xd resources - bootstrap 4](https://xdresources.co/resources/bootstrap-4-ui)

[agile - stages of a user story using Rally](http://www.techndata.com/stages-of-a-user-story-in-the-rally-and-its-meaning/)

[prototyping with adobe XD and angular material](https://angularfirst.com/prototyping-with-adobe-xd-and-angular-material/)

[build a real world web app with angular 6 A to Z ultimate guide 2018](https://medium.com/@hamedbaatour/build-a-real-world-beautiful-web-app-with-angular-6-a-to-z-ultimate-guide-2018-part-i-e121dd1d55e)

[coursetro - using adobe XD to design web app based on Bulma CSS](https://coursetro.com/posts/code/69/Using-Adobe-XD-to-Design-a-Web-App-based-on-Bulma-CSS)

[activity log (template included)](https://www.mindtools.com/pages/article/newHTE_03.htm)

[Agile Scrum Development Process and How UI/UX Design Fit In](https://www.youtube.com/watch?v=yc3J2TGreBo)

### 7 Feb 2019

[simplified advanced search](https://uxdesign.cc/death-to-complexity-how-we-simplified-advanced-search-a9ab2940acf0)

[reactide - the first dedicated IDE for React web application development](http://reactide.io/)

[osx apps](https://alexcican.com/post/osx-apps/)

### 5 Feb 2019

[react starter kit](https://github.com/kriasoft/react-starter-kit)

[useful JS array and object methods](https://codeburst.io/useful-javascript-array-and-object-methods-6c7971d93230)

[CRUZ - react signup signin UI](https://stackblitz.com/edit/react-signup-signin-ui)

[metalsmith - static site generator](https://metalsmith.io/)

### 4 Feb 2019

[reacttraining - react-router](https://reacttraining.com/react-router/web/guides/basic-components)

[CodingEntrepreneurs - #20 Try REACTJS Tutorial - Handle Form and Input Data](https://www.youtube.com/watch?v=fcMNZ7j4JSg)

following the above... [CRUZ formsAndInputs react class](https://stackblitz.com/edit/react-vqfrtr?file=Hello.js)

[LevelUp tuts - React For Everyone #15 - Using Forms](https://www.youtube.com/watch?v=1eNIYif69_0)

>  use of ES6, refs, shortcut for setting obj, concat inside this.setState...

[TheCodePro - Learn React.js by Example - React Sign Up Form Example](https://www.youtube.com/watch?v=56E8b9prPTs)

### 1 Feb 2019

[Primereact - UI framework for react](https://www.primefaces.org/primereact/#/)

[Mason - frontend as a service](https://www.trymason.com/)

[frontastic - frontend API (CMS/e-commerce) as a service](https://www.frontastic.cloud/)

[micro frontends](https://micro-frontends.org/)

### 31 Jan 2019

[alligator - vuepress intro](https://alligator.io/vuejs/vuepress-introduction/)

[13 headless CMS's to put in your radar](https://www.cmswire.com/web-cms/13-headless-cmss-to-put-on-your-radar/)

### 30 Jan 2019

[Vuepress](https://vuepress.vuejs.org/)

[how to create a documentation website using vuepress](https://medium.freecodecamp.org/how-to-create-a-documentation-website-using-vuepress-eeabe8a99045)

[docusaurus - Open Source Documentation Websites](https://docusaurus.io/en/)

[Jetbrains - ring UI - React-based UI components for web](https://jetbrains.github.io/ring-ui/master/index.html)

[CRUZ - CSS variables and JS](https://codepen.io/CruzWeb/pen/pGNxao)

[Bootstrap theme builder](https://bootstrap.build)

[Angular + Virtual DOM](https://blog.angularindepth.com/introducing-to-ng-vdom-a-new-way-to-write-angular-application-60a3be805e59)

[Hobby - drawing and animating in CSS](https://medium.com/@kylewetton/how-i-stumbled-across-a-niche-hobby-i-never-knew-existed-drawing-and-animating-in-css-f351721f8aba)

[UX design - Animation guide in UX √√√](https://uxdesign.cc/the-ultimate-guide-to-proper-use-of-animation-in-ux-10bd98614fa9)

[UX design - Adobe XD Vs Sketch Vs Invision](https://uxdesign.cc/will-adobe-xd-kill-sketch-and-invision-7fc4e562fc1a)

[complete CSS flexbox tut](https://medium.com/@js_tut/the-complete-css-flex-box-tutorial-d17971950bdc)

[30 questions to ask before joining a startup](https://angel.co/blog/30-questions-to-ask-before-joining-a-startup)

### 29 Jan 2019

[Academind - Build a Project with GraphQL, Node, MongoDB and React.js](https://www.youtube.com/watch?v=7giZGFDGnkc&list=PL55RiY5tL51rG1x02Yyj93iypUuHYXcB_)

[coderust free alternatives or similar](https://github.com/kevinfiol/coderust-free)

### 28 Jan 2019

[JS in plain english: Same app in React and Vue](https://medium.com/javascript-in-plain-english/i-created-the-exact-same-app-in-react-and-vue-here-are-the-differences-e9a1ae8077fd)

Interesting - check similar [coderust](https://www.educative.io/collection/5642554087309312/5679846214598656)

[coderust example: binary search algorithm](https://www.educative.io/collection/page/5642554087309312/5679846214598656/240002)

my approach before checking their solution

```
const array = [1, 8, 23, 34, 74];

let binary_search = function(a, key) {
    let result = a.filter( item => item === key)
    // filter method returns an array, that's why we need the the inside value on the next line...
    return a.indexOf(result[0]) ;
}

console.log(binary_search(array, 23))
console.log(binary_search(array, 3))
```

[Web Development Tutorial for Beginners (#1) - How to build webpages with HTML, CSS, Javascript](https://www.youtube.com/watch?list=PLoYCgNOIyGAB_8_iq1cL8MVeun7cB6eNc&v=3JluqTojuME)

[How the Internet Works for Developers - Pt 1 - Overview & Frontend](https://www.youtube.com/watch?v=e4S8zfLdLgQ)

[How the Internet Works for Developers - Pt 2 - Servers & Scaling](https://www.youtube.com/watch?v=FTAPjr7vgxE)

[How browsers work internally - Tali Garsiel - Front-Trends 2012](https://vimeo.com/44182484)

[teaching: Web Demystified](https://www.youtube.com/playlist?list=PLo3w8EB99pqLEopnunz-dOOBJ8t-Wgt2g)

[how to lose an IT job in 10 min](https://hackernoon.com/how-to-lose-an-it-job-in-10-minutes-3d63213c8370)

### 25 Jan 2019

[List of CMS's for JAM stack sites](https://headlesscms.org/)

>  WP API's for testing... 
>  
>  Any WordPress site basically -> just add /wp-json after home url.
>  
>  example: https://nacin.com/wp-json/wp/v2/posts

[free API's collection](https://github.com/toddmotto/public-apis/blob/master/README.md)

[rapid API (more API's)](https://rapidapi.com)

[typescript online playground](http://www.typescriptlang.org/play/)

[2ality (Dr. Axel Rauschmayer) - type notation typescript](http://2ality.com/2018/04/type-notation-typescript.html)

[exploring es6 - book (Dr. Axel Rauschmayer)](http://exploringjs.com/es6/)

[typescript handbook](https://www.typescriptlang.org/docs/handbook/basic-types.html)

[react docs - typescript](https://reactjs.org/docs/static-type-checking.html#typescript)

[React Static - A progressive static-site framework for React @ OgdenJS](https://www.youtube.com/watch?v=OqbJ5swVpDQ)

[coffeecraftcode](https://coffeecraftcode.com/)

>  resources, communities:
>  
>  [codenewbie](http://www.codenewbie.org/)
>  
>  [100 days of code](https://github.com/Kallaway/100-days-of-code) // individual challenge
>  
>  [codingartist](http://codingartist.io/) // CSS images challenges
>  
>  [](https://tropicalchancer.github.io/projectus/) // put motivated people with similar goals together in an environment that gives them the opportunity to level-up in a way they couldn’t otherwise
>  
>  [advance beginner challenge](https://www.advancedbeginnerchallenge.com/) // 

[(Teaching) Skillshare - filters: free classes](https://www.skillshare.com/search?query=HTML&enrollmentType=free)

### 24 Jan 2019

[jamstack.org (**J**avascript **A**PI's **M**arkdown)](https://jamstack.org/)

**HTML**

>  [goskills - HTML interview questions and answers](https://www.goskills.com/Development/Articles/HTML-interview-questions-answers)
>  
>  [guru99 - top 50 HTML interview questions](https://career.guru99.com/top-50-html-interview-questions/)
>  
>  [javatpoint - HTML interview questions](https://www.javatpoint.com/html-interview-questions)

interesante: [psdwizard (psd to html and more...)](https://psdwizard.com)

[orbital relationships in D3 force graphs](https://www.bounteous.com/insights/2013/10/18/orbital-relationships-in-d3-js-force-graphs/?ns=I)

[medium - interactive force directed graphs with d3](https://medium.com/ninjaconcept/interactive-dynamic-force-directed-graphs-with-d3-da720c6d7811)

[github - D3 force](https://github.com/d3/d3-force/blob/master/README.md#forceSimulation)

[M bostock - D3 force directed graph](https://beta.observablehq.com/@mbostock/d3-force-directed-graph)

[D3 in depth](https://d3indepth.com/)

### 23 Jan 2019

[tech graph](https://nielchah.com/blog/a-graph-of-tech/)

[building your bots brain with nodeJS and spacy](https://medium.com/@joaogabriellima/building-your-bots-brain-with-node-js-and-spacy-1f77ff8dcdba)

[JS charts and data visualization libraries 2018](https://blog.bitsrc.io/11-javascript-charts-and-data-visualization-libraries-for-2018-f01a283a5727)

[cytoscape](http://js.cytoscape.org/)

[sigma.js](http://sigmajs.org/)

[d3 node focus - GAS sites](http://ramblings.mcpher.com/Home/excelquirks/gassites/d3nodefocus)

[opengraphity](https://n0where.net/opengraphiti-data-visualization-engine)

[cayley.io](https://cayley.io/)

[JSON server with reactJS](https://dev.to/rodeghiero_/json-server-with-reactjs-3chd)

este tenía problemas errores al correrlo pero la idea está buena [github - circular knowledge graph](https://github.com/anishmprasad/circular-knowledge-graph)

[mixedemotions (they have knowledge graph, emotion and sentiment analysis, entity extraction and linking...)](http://mixedemotions.insight-centre.org/modules)

[github - knowledge graph analysis programming exercises](https://github.com/SmartDataAnalytics/Knowledge-Graph-Analysis-Programming-Exercises)

[ReactJS - build dynamic JSON based form](https://codeburst.io/reactjs-a-quick-tutorial-to-build-dynamic-json-based-form-a4768b3151c0)

[beginners guide to googles knowledge graph](https://neilpatel.com/blog/the-beginners-guide-to-the-googles-knowledge-graph/)

[developers Google - API client library JS](https://developers.google.com/api-client-library/javascript/start/start-js)

[github - research papers to understand knowledge graph](https://github.com/bmzhao/knowledge-graph-papers)

[how to remobe duplicates in es6](https://medium.com/dailyjs/how-to-remove-array-duplicates-in-es6-5daa8789641c)

### 22 Jan 2019

para leer [OOP concepts for a 6 year old](https://medium.freecodecamp.org/object-oriented-programming-concepts-21bb035f7260)

[unleash 3D rendering with WebGL and Microsoft Edge](https://channel9.msdn.com/Events/WebPlatformSummit/2015/Unleash-3D-rendering-with-WebGL-and-Microsoft-Edge)

[freecodecamp - When (and why) you should use ES6 arrow functions — and when you shouldn’t](https://medium.freecodecamp.org/when-and-why-you-should-use-es6-arrow-functions-and-when-you-shouldnt-3d851d7f0b26)

[arrow functions vs function declaration expresssions - stackoverflow](https://stackoverflow.com/questions/34361379/arrow-function-vs-function-declaration-expressions-are-they-equivalent-exch)

[when to use arrow f(x)s flowchart - Kyle Simpson](https://github.com/getify/You-Dont-Know-JS/blob/master/es6%20%26%20beyond/fig1.png)

[sitepoint - es6 arrow functions](https://www.sitepoint.com/es6-arrow-functions-new-fat-concise-syntax-javascript/)

[set theory for arrays in es6](https://medium.com/@alvaro.saburido/set-theory-for-arrays-in-es6-eb2f20a61848)

[teaching - HTML](https://html.com/)

[CRUZ - understand CSS triangles](https://codepen.io/CruzWeb/pen/GzRwJY)

[HTML - CSS - JS - JQuery... cheatsheets](https://htmlcheatsheet.com/)

[CSS interview questions 2](https://www.youtube.com/watch?v=feueV0nz7Tk)

[CSS interview questions 1](https://www.youtube.com/watch?v=ZohZS6xLYE4)

### 21 Jan 2019

[affinity designer - Draw a Penrose impossible triangle](https://www.youtube.com/watch?v=Zkc25s9sWDY)

### 17 Jan 2019

[lengstorf - works at gatsby](https://lengstorf.com/)

[egghead - slide deck with mdx (markdown and react)](https://egghead.io/lessons/react-build-a-slide-deck-with-mdx-deck-using-markdown-react)

[egghead - MDX blog starter project](egghead.io creator MDX Blog Starter Project)

A bit of 3D...

[treehouse - beginners guide to three.js](https://blog.teamtreehouse.com/the-beginners-guide-to-three-js)

[awwwards - three.js sites](https://www.awwwards.com/websites/three-js/)

[getting started with three.js](https://aerotwist.com/tutorials/getting-started-with-three-js/)

[Three.js Tutorial - Essential Three.js - youtube](https://www.youtube.com/watch?v=O18Dq-QcfEE)

### 14 Jan 2109

[a different way to manage state in react - react-recollect](https://hackernoon.com/a-different-way-to-manage-state-in-react-2d21dfb94482)

[codesandbox - example of react-recollect and material-ui](https://codesandbox.io/s/lxy1mz200l)

[React state management patterns](https://itnext.io/react-state-management-patterns-908325dbb8f3)

[programming pples KISS, YAGNI, DRY...](https://www.itexico.com/blog/software-development-kiss-yagni-dry-3-principles-to-simplify-your-life)

[CSS-Tricks - react state from the ground up](https://css-tricks.com/react-state-from-the-ground-up/)

[interview questions about why you want to change jobs](https://www.thebalancecareers.com/interview-questions-about-why-you-want-to-change-jobs-2061154)

[things to consider when looking new job](http://mentalfloss.com/article/71617/8-things-consider-when-looking-new-job)

### 13 Jan 2019

[alligator - angular environment variables](https://alligator.io/angular/environment-variables/)

[CRUZ - stamp duty land tax calculator (stackblitz edit)](https://stackblitz.com/edit/angular-hkguav)

[CRUZ - stamp duty land tax calculator (surge)](http://sdlt-calculator.surge.sh/)

Fonts inspiration

[typewolf - best google fonts](https://www.typewolf.com/google-fonts)

[top 5 UI fonts...](https://medium.muz.li/top-5-ui-fonts-for-website-mobile-apps-d78829e58f7e)

[elegantthemes - best web fonts](https://www.elegantthemes.com/blog/resources/best-web-fonts)

[Here](https://angular.io/guide/template-syntax) we can read about the difference btwn HTML and DOM

[how to build an Angular app w/ angular CLI in a couple of minutes](https://codeburst.io/how-to-build-an-angular-app-with-angular-cli-in-a-couple-of-minutes-43089d3ab272)

### 12 Jan 2019

[working w/ models in angular](https://nehalist.io/working-with-models-in-angular/)

### 11 Jan 2019

>  Interesting: 
>  
>    [Codecourse.com](https://codecourse.com/library/all?free=true)
>  
>    [LearnCode.academy youtube channel](https://www.youtube.com/channel/UCVTlvUkGslCV_h-nSAId8Sw)


eg. [HTML5 input types](https://codecourse.com/courses/html5-input-types)

[Git & GitHub: Pull requests - Codecourse youtube](https://www.youtube.com/watch?v=FQsBmnZvBdc)

[Github help - about pull requests](https://help.github.com/articles/about-pull-requests/)

[LearnCode Academy - GITHUB PULL REQUEST, Branching, Merging & Team Workflow](https://www.youtube.com/watch?v=oFYyTZwMyAg)

[What are microservices?](https://smartbear.com/learn/api-design/what-are-microservices/)

[microservices tutorial with example](https://www.edureka.co/blog/microservices-tutorial-with-example)

[microservices architecture example and diagram](https://www.devteam.space/blog/microservice-architecture-examples-and-diagram/)

[build NodeJS cinema microservice and deploy with Docker](https://medium.com/@cramirez92/build-a-nodejs-cinema-microservice-and-deploying-it-with-docker-part-1-7e28e25bfa8b)

### 10 Jan 2019

[love2dev JS remove from array](https://love2dev.com/blog/javascript-remove-from-array/)

[JS - remove elem from array](https://www.hostingadvice.com/how-to/javascript-remove-element-array/)

[Using StackBlitz & Angular for Rapid App Prototyping - Eric Simons and Albert Pai](https://www.youtube.com/watch?v=EBzoTnX6LzU&t=689s)

[The art of computer programming](http://broiler.astrometry.net/~kilian/The_Art_of_Computer_Programming%20-%20Vol%201.pdf)

[A self-learning, Modern Computer Science Curriculum](https://functionalcs.github.io/curriculum/)

[book - Common Lisp, a gentle introduction to symbolic computation](https://www.cs.cmu.edu/~dst/LispBook/book.pdf)

>  ***From the point of view of the data***: The numbers 2
and 3 flow into the function, and the number 5 flows out. ***From the point of
view of the function***: The function ‘‘+’’ received the numbers 2 and 3 as
inputs, and it produced 5 as its result. ***From the programmer’s point of view***:
We called (or invoked) the function ‘‘+’’ on the inputs 2 and 3, and the
function returned 5. These different ways of talking about functions and data
are equivalent

[Scrum: How to do twice as much in half the time | Jeff Sutherland | TEDxAix](https://www.youtube.com/watch?v=s4thQcgLCqk)

>  Nonaka and Takeuchi: 3 different types of leadership. 1. Gantt chart, 2. Fuji Xerox (transitional strategy), 3. best manufacturing plants in the world
>  
>  self-organised, self-motivated teams. Management needs to let go and step back. They need to go out of the way, so the teams can figure it out what to do... 2001 agile manifesto

**IDEA** apply agile/scrum methodologies to learning...

[Google Ventures - Sprint](http://www.gv.com/sprint/)

[Code Org - youtube playlist](https://www.youtube.com/user/CodeOrg/playlists)

[Code Org - teachers](https://studio.code.org/courses?view=teacher)

### 9 Jan 2019

[How to learn to programming if you are over 50](https://medium.com/swlh/how-to-learn-programming-if-you-are-over-50-34a23f0f4870)

>  'Question until you understand'. 'The power to question is the basis of all human progress'
>  
>  Get feedback, 'In the real world, requirements are as fluid as ink and constantly evolving (...) That is why frequent feedback is so important; from your peers, from your customers and even from your third-party vendors with whom your code is been integrated.'
>  
>  Measure real progress. 'One side advantage of accurate estimations is that you improve your standing among your peers and the customer starts “believing” in you. This acts as a catalyst for boosting your self-esteem and works wonders on your confidence levels.'
>
>  Keep all informed: 'The less people know, the more they yell'. 'By keeping others informed, you eliminate surprises and they are comfortable when they know your progress. They know when to help you out and you end up “earning their trust”.
The key is to “always under commit but over deliver”'
>  
>  'Age is a case of mind over matter. If you don’t mind, it doesn’t matter'

[css-tricks - CSS styling links like a boss](https://css-tricks.com/css-basics-styling-links-like-boss/)

[Awesome CSS buttons](https://codepixelz.com/css/awesome-css-buttons/)

[20 essential CSS tricks every designer should know](https://www.webdesignerdepot.com/2016/10/20-essential-css-tricks-every-designer-should-know/)

[MDN - Using CSS gradients](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Images/Using_CSS_gradients)

[Starting an Angular App with Angular CLI in a couple of minutes](https://codeburst.io/how-to-build-an-angular-app-with-angular-cli-in-a-couple-of-minutes-43089d3ab272)

[Webinar: latest Angular 2 Forms w/ Kara Erickson (LIVE)](https://youtu.be/E92KS_YCSf8?list=PLeUKuUUYwJtrW1X_1taA08SZtM8IQyehN)

### 8 Jan 2019

[why Angular doesn't work - 11 common mistakes](https://malcoded.com/posts/why-angular-not-works)

[angular bad practices](https://codeburst.io/angular-bad-practices-eab0e594ce92)

### 7 Jan 2019

[3 input elem props discovered while reading MDN](https://www.stefanjudis.com/blog/three-input-element-properties-that-i-discovered-while-reading-mdn/)

[JavaScript Monthly Payment Loan Calculator Programming Tutorial](https://www.youtube.com/watch?v=vkBiEuZSq9s)

[CRUZ - JS loan calculator - stackblitz edit](https://stackblitz.com/edit/js-monthly-payment-loan-calculator)

### 4 Jan 2019

[Intro - React Testing For Beginners - LevelUp Tuts](https://www.youtube.com/watch?v=esVwR4lGwQE&list=PLLnpHn493BHEqP3gD1pCJYhxX6v2gBZzj)

>  started Pluralsight - testing react apps with Jest - Daniel Stern
>  
>  check his course on "Isomorphic react", it's recommended first, before the testing with jest

### 3 Jan 2019

estuve viendo [Ionic 3 Mobile Weather App Build](https://www.youtube.com/watch?v=qs2n_poLarc)

### 2 Jan 2019

[Jest Crash Course - Unit Testing in JavaScript - Traversy media](https://www.youtube.com/watch?v=7r4xVDI2vho)

### 21 Dec 2018

VSCode > extension: Prettier Now (by Remi Marsal)

>  Format On Save
>  
>  Set editor.formatOnSave to true in settings to automatically format files on save.
>  
>  Or using Command Palette (CMD + Shift + P)
>  
>  ```
>  CMD + Shift + P -> Format Document
>  ```


jest: npm script to chech any changes

```
"test" : "jest --watchAll"
```

git: remove node_modules in a repo [ref](https://stackoverflow.com/questions/50675829/remove-node-modules-from-git-in-vscode)

```
git rm -r --cached .
git add .
git commit -m "remove gitignore files"
git push
```

git: after cloning something, remove remote...

```
git remote rm origin
```

and then create your repo and add your new remote origin

or (quicker) fork the project and you'll have your remote...

npm: Auditing package dependencies for security vulnerabilities

```
npm audit
npm audit fix
```

[#1 Setup & Writing Our First Jest Test - JS Testing 101 with Jest](https://www.youtube.com/watch?v=4kNfeI37xu4&list=PLLnpHn493BHEB-YOl0APuQsrzlb3zbq3y)

[#2 Multiple Test Cases - JS Testing 101 with Jest](https://www.youtube.com/watch?v=zkG_ClTJ9UM&list=PLLnpHn493BHEB-YOl0APuQsrzlb3zbq3y&index=2)

[#3 Test Driven Development & Refactoring - JS Testing 101 with Jest](https://www.youtube.com/watch?v=6pYUzEduLyU&list=PLLnpHn493BHEB-YOl0APuQsrzlb3zbq3y&index=3)


### 20 Dec 2018

[Traversy Media - YT playlist Node.js & Express From Scratch](https://www.youtube.com/watch?v=k_0ZzvHbNBQ&list=PLillGF-RfqbYRpji8t4SxUkMxfowG4Kqp)

[flexjobs video course - finding a remote job](https://www.flexjobs.com/finding-a-remote-job-video-course)

### 19 Dec 2018

[closebrace Creating a Simple RESTful Web App with Node.js, Express, and MongoDB](https://closebrace.com/tutorials/2017-03-02/creating-a-simple-restful-web-app-with-nodejs-express-and-mongodb)

[closebrace cheatsheets thanks (links about express workflow, converting to mysql... etc)](https://closebrace.com/cheatsheetthanks)

[The Dead-Simple Step-By-Step Guide for Front-End Developers to Getting Up and Running With Node.JS, Express, and MongoDB](https://closebrace.com/tutorials/2017-03-02/the-dead-simple-step-by-step-guide-for-front-end-developers-to-getting-up-and-running-with-nodejs-express-and-mongodb)

### 17 Dec 2018

[how to write user stories](http://agifall.com/how-to-write-user-stories/)

[writing complete user stories](http://tynerblain.com/blog/2009/07/06/writing-complete-user-stories/)

### 15 Dec 2018

[Improve Your Buildings in Watercolour - Part One](https://www.youtube.com/watch?v=lLA1Cl52j2Y)

[Improve Your Buildings in Watercolour - Part Two](https://www.youtube.com/watch?v=NYG9d8JtQeE)

[dave ceddia - modal in react](https://daveceddia.com/open-modal-in-react/)

[CRUZ - new hackernews (surge!)](http://hackernews-restyled.surge.sh/)

[CRUZ - new hackernews (stackblitz) - cleaning index.js](https://stackblitz.com/edit/react-expand-details-on-row-5js5ux)

[‬In what way is JS any more maintainable than CSS? How does writing CSS in JS make it any more maintainable?](https://gist.github.com/threepointone/731b0c47e78d8350ae4e105c1a83867d)

### 14 Dec 2018

[surge and github pages deployment](https://medium.freecodecamp.org/surge-vs-github-pages-deploying-a-create-react-app-project-c0ecbf317089)

>  make sure you check the '.../build' is added to your path when deploying to surge!!!

[CRUZ - new hackernews (stackblitz) III](https://stackblitz.com/edit/react-expand-details-on-row-jiug8n)

[CRUZ - new hackernews (stackblitz) II](https://stackblitz.com/edit/react-expand-details-on-row-eme8pe)

[sticky footer with flexbox](https://philipwalton.github.io/solved-by-flexbox/demos/sticky-footer/)

[CRUZ - card sticky footer with flexbox](https://codepen.io/CruzWeb/pen/GPZZMB)

[UI - card idea](https://dribbble.com/shots/1553875-Post-sections/attachments/237571)

[flexbox - create modern card design layout](https://getflywheel.com/layout/flexbox-create-modern-card-design-layout/)

### Wed 12 Dec 2018

[Flexbox vs? CSS Grid - Jen ](https://www.youtube.com/watch?v=hs3piaN4b5I)

[Real Digital Watercolor Painting in Photoshop - The Most SIMPLE Tutorial for Artists!](https://www.youtube.com/watch?v=MrGNiDdIR9o)

[Best Watercolor Tips I Wish I Had Known Two Decades Ago](https://www.youtube.com/watch?v=PQKDjNhZitQ)

### Tue 11 Dec 2018

[CRUZ - new hackernews (stackblitz)](https://stackblitz.com/edit/react-pfss3y?file=cell.css)

[CRUZ - new hackernews (codepen)](https://codepen.io/CruzWeb/pen/xmGOoZ?editors=1100)

[recreating google images search layout - sitepoint](https://www.sitepoint.com/recreating-google-images-search-layout-css/)

[tympanus - thumbnail grid with expanding preview](https://tympanus.net/codrops/2013/03/19/thumbnail-grid-with-expanding-preview/)

[species in pieces - css](http://species-in-pieces.com)

[unheap - library of JS plugins](http://www.unheap.com/)

### Mon 10 Dec 2018

[codrops - twitter](https://twitter.com/codrops)

[UX - design - psychology - Gestalt](https://hackernoon.com/design-psychology-gestalt-driven-ux-64ac01cd257a)

### Fri 7 Dec 2018

[beginners guide to redux saga](https://react.christmas/2018/7)

[CRUZ - react subreddit + styled-components](https://stackblitz.com/edit/react-getting-subreddit-data-with-axios?file=index.js)

[CRUZ - react subreddit + styled-components refactored](https://stackblitz.com/edit/react-getting-subreddit-data-with-axios-refactored)

>  pushed to surge.sh... [CRUZ - react subreddit...](http://yellow-neck.surge.sh/)

[conditional rendering in react (crr)](https://blog.logrocket.com/conditional-rendering-in-react-c6b0e5af381e)

[crr 2](https://www.robinwieruch.de/conditional-rendering-react/)

[curated list of styled components resources](https://github.com/styled-components/awesome-styled-components)

[CRUZ (Dave Ceddia) react subreddit data with axios](https://react-getting-subreddit-data-with-axios.stackblitz.io)

[CRUZ (Dave Ceddia) react subreddit data with axios --EDIT](https://stackblitz.com/edit/react-getting-subreddit-data-with-axios)

[CRUZ - react subreddit deployed to surge](vast-line.surge.sh)

[teaching: JS functions basics](https://codeburst.io/javascript-functions-understanding-the-basics-207dbf42ed99)

### Thu 6 Dec 2018

[9 things react beginners should know](https://camjackson.net/post/9-things-every-reactjs-beginner-should-know)

Javascript Masters:

[Mathias Bynens](https://mathiasbynens.be/)

Kyle Simpson [(getify)](https://github.com/getify) [and here](https://me.getify.com/) - [pluralsight](https://www.pluralsight.com/authors/kyle-simpson)

[David Walsh](https://davidwalsh.name/)

Richard Bovell [(javascriptissexy)](http://javascriptissexy.com)

[top 10 JS gurus](https://www.sitepoint.com/top-10-jquery-gurus-hit-internet/)

[33 JS devs you 'must' subscribe](https://code.tutsplus.com/articles/33-developers-you-must-subscribe-to-as-a-javascript-junkie--net-18151)

[JS experts](https://www.quora.com/Who-are-the-leading-experts-in-JavaScript)

### Wed 5 Dec 2018

[think like a programmer](https://medium.freecodecamp.org/how-to-think-like-a-programmer-lessons-in-problem-solving-d1d8bf1de7d2)

[cruz (codesandbox) dave ceddia - react (teaching beginners)](https://codesandbox.io/s/zr7r1jo5mp)

[cruz (stackblitz) dave ceddia - react (teaching beginners)](https://stackblitz.com/edit/cruz-react-room-light-and-temp)

[visual guide to state in react](https://daveceddia.com/visual-guide-to-state-in-react/?utm_campaign=prec3)

[dave ceddia blog posts](https://daveceddia.com/archives/)

### Mon 3 Dec 2018

[(react) promises and error boundaries for data loading - codeburst](https://codeburst.io/using-promises-and-error-boundaries-for-data-loading-within-your-react-redux-app-219f8d3a6d26)

[Processing errors with fetch api](https://gist.github.com/odewahn/5a5eeb23279eed6a80d7798fdb47fe91)

[you might not need proptypes](https://itnext.io/https-medium-com-phil-kahrl-you-might-not-need-proptypes-in-react-2363a4b4179b)

### Sat 1 Dec 2018

[create react app template - perform common tasks (Eric Simons)](https://github.com/stackblitz/create-react-app-template)

['look forward to hear from you' alternatives](https://www.grammarly.com/blog/i-look-forward-to-hearing-from-you/)

[money-sheep book (ideas for books business)](http://money-sheep.com)

[sheepmoney](http://sheepmoney.com/)

[react animations (react pose)](https://medium.com/@joomiguelcunha/amazing-react-animation-with-react-pose-3b67d9eb6e07)

[complex UI animation made simple with react](https://css-tricks.com/building-a-complex-ui-animation-in-react-simply/)

### Fri 30 Nov 2018

[NodeJS: How to consume REST apis from nodejs](https://www.youtube.com/watch?v=ilvmStvrEW0)

[custom angular and react seeds on stackblitz](https://medium.com/@beeman/custom-angular-react-seeds-on-stackblitz-1996d502d177)

### Thu 29 Nov 2018

[Node.js API Authentication With JWT - Traversy Media](https://www.youtube.com/watch?v=7nafaH9SddU)

[Protected routes and authentication with React Router](https://www.youtube.com/watch?v=ojYbcon588A)

[Fasting vs. Eating Less: What's the Difference? (Science of Fasting)](https://www.youtube.com/watch?v=APZCfmgzoS0)

### Wed 28 Nov 2018

[Create React App with an Express Backend](https://www.youtube.com/watch?v=8bNlffXEcC0)

[building and securing React QA app - Auth0](https://auth0.com/blog/react-tutorial-building-and-securing-your-first-app/)

>  great tutorial! [here their github](https://github.com/auth0-blog/react-tutorial)

After learning about React, you might get interested into learning about how to add automated tests to your app: [testing react apps with jest](https://auth0.com/blog/testing-react-applications-with-jest/)

[learn more about react router](https://reacttraining.com/react-router/)

[build a react app with authentication - scotch.io](https://scotch.io/tutorials/build-a-react-app-with-user-authentication)

### Tue 27 Nov 2018

[CRUZ - clone of Hackernews made with vanilla JS](https://js-8hiuw3.stackblitz.io/)

[Hackernews -> edit view](https://stackblitz.com/edit/js-8hiuw3)

[book online - You dont know JS - Kyle Sympson](https://github.com/getify/You-Dont-Know-JS)

[learn vanilla JS - resource links](https://github.com/snipcart/learn-vanilla-js)

### Mon 26 Nov 2018

[app ideas - The secret to being a top developer is building things! Here’s a list of fun apps to build!](https://medium.freecodecamp.org/the-secret-to-being-a-top-developer-is-building-things-heres-a-list-of-fun-apps-to-build-aac61ac0736c)

[learn JS before using JS frameworks](https://snipcart.com/blog/learn-vanilla-javascript-before-using-js-frameworks)

[Beginners JS study plan](https://medium.freecodecamp.org/a-beginners-javascript-study-plan-27f1d698ea5e)

[TODO list in vanilla JS](https://medium.com/@Linda_Ikechukwu/building-a-to-do-list-app-with-vanilla-javascript-e27dda195fea)

[SPA without framework - currency converter](https://www.sitepoint.com/single-page-app-without-framework/)

[how to effectively develop vanilla JS app](https://www.codementor.io/vineetdev/how-to-effectively-develop-vanilla-javascript-application-5k19c0ct9)

[codementor - how to build powerful rest apis blazingly fast with node](https://www.codementor.io/justinheadley/how-to-build-powerful-rest-apis-blazingly-fast-with-node-js-kwvfsviby)

[webpack - getting started](https://www.codementor.io/javascript/tutorial/module-bundler-webpack-getting-started-guide?icn=5k19c0ct9&ici=webpack-starter)

[connectin to hackernews firebase API](https://codeburst.io/on-connecting-my-app-to-the-hackernews-firebase-api-e7b9e1ccec29)

### Sun 25 Nov 2018

[nested ternaries are great - eric elliot](https://medium.com/javascript-scene/nested-ternaries-are-great-361bddd0f340)

### Sat 24 Nov 2018

[learnings after a year of react]( https://medium.com/@tomas.eglinskas/the-most-important-lessons-ive-learned-after-a-year-of-working-with-react-1de862421981?source=email-32afed580e42-1543049421116-digest.reader------0-1------------------5d0a96a9_96bb_4983_bbab_6102706c5823-1&sectionName=top )

### Fri 23 Nov 2018

Filling new challenges in freecodecamp - Basic HTML and HTML5, Basic CSS and Basic JS -

[build a clone of momentum chrome extension](https://medium.com/@thejungwon/best-html-css-javascript-practice-chrome-extension-ae4e5e7839e)

[how to identify a toxic culture before accepting a job offer](https://medium.com/fast-company/how-to-identify-a-toxic-culture-before-accepting-a-job-offer-e27709368f16)

### Thu 22 Nov 2018

[khan academy - hour of programming](https://www.khanacademy.org/hourofcode)

[react concepts after knowing the basics](https://medium.freecodecamp.org/these-are-the-concepts-you-should-know-in-react-js-after-you-learn-the-basics-ee1d2f4b8030)

regarding code teaching for refugees

>  [medium article ](https://medium.freecodecamp.org/how-we-taught-dozens-of-refugees-to-code-then-helped-them-get-developer-jobs-fd37036c13b0)
>  
>  [Hack your future](http://hackyourfuture.net/)
>  
>  [Hack your future curriculum - github](https://github.com/HackYourFuture/curriculum/)

Interesting, collaborative [rich text editor](https://medium.com/front-end-hacking/build-a-collaborative-rich-text-editor-with-node-js-and-socket-io-38ee25b6e315) (Froala) with Node.js and sockets.io 

encontré una [versión de chat que hice un año atrás](https://cwd-chat.herokuapp.com) con Node.js y sockets.io...

[chat version using reactjs socket.io](https://solvemprobler.com/blog/2013/06/16/reactjs-and-socket-dot-io-chat-application/)

[chat version using angular typescript socket.io](https://medium.com/dailyjs/real-time-apps-with-typescript-integrating-web-sockets-node-angular-e2b57cbd1ec1)

### Wed 21 Nov 2018

CRUZ... cree mi propia versión básica 'websocket chat'

TODO: deploy to the cloud

[websockets tutorial (chat) - youtube playlist](https://www.youtube.com/watch?v=vQjiN8Qgs3c&list=PL4cUxeGkcC9i4V-_ZVwLmOusj8YAUhj_9) from [The Net Ninja](https://www.youtube.com/channel/UCW5YeuERMmlnqo4oq8vwUpg)

[socket.io](https://socket.io/)

[Howie Liu - Airtable](https://www.youtube.com/watch?v=hGUCqWa0Msc)

[RxFire - Firebase meets RxJS](https://www.youtube.com/watch?v=fq6UPn5H2Bs)

### Mon 19 Nov 2018

[react router for beginners](https://codeburst.io/getting-started-with-react-router-5c978f70df91)

[nprogress with react-router in create-react-app](https://gist.github.com/shelldandy/02ad1a9f8b5b86d1b2e4dd26a11967b2)

[flexbox - navigation bars of the most popular apps](https://medium.com/flexbox-and-grids/the-most-popular-navigation-bars-created-with-flexbox-6c0f59f55686)

[flexbox fully responsive navbar](https://medium.freecodecamp.org/how-to-create-a-fully-responsive-navbar-with-flexbox-a4435d175dd3)

[flexbox bar nav - css-tricks](https://css-tricks.com/flexbox-bar-navigation/)

[nav menus using flexbox](https://codepen.io/terrymun/pen/cKxwu)

[nav menu inspiration - codemyUI](https://codemyui.com/tag/navigation-menu/page/2/)

[CRUZ - nprogress and react-router demo](https://react-z2z1qv.stackblitz.io)

### Fri 16 Nov 2018

[Semantic UI In 60 Minutes - traversy media](https://www.youtube.com/watch?v=a9mUH1EWp40)

[CRUZ - semantic.ui cheatsheet](https://codepen.io/CruzWeb/full/LXLBXB)

### Thu 15 Nov 2018

[edutopia](https://www.edutopia.org/)

ideas? [wizbots - robotics and lego for children](https://wizbots.com)

[makeymakey](https://makeymakey.com/pages/educators#resources)

[Hacking Everyday Objects Inspires Students to Explore Technology
](https://www.youtube.com/watch?v=RRwqutcy5B0&feature=youtu.be)

[squishy circuits - electronic fun!](https://squishycircuits.com/) source: [AnnMarie Thomas: Hands-on science with squishy circuits
](https://www.youtube.com/watch?v=5M3Dow20KlM)

[getting kids into programming (resources)](http://blog.pamelafox.org/2013/01/getting-kids-into-programming.html)

[netlify site of the week - great resources!](https://www.netlify.com/site-of-the-week/)

>  here I found sites like: 
>  
>  [kinto - open source from Mozilla (alternative to firebase)](https://www.kinto-storage.org/) check [kinto + react boilerplate](https://github.com/Kinto/kinto-react-boilerplate/)
>  
>  [react boilerplate - Quick setup for new performance oriented, offline–first React.js applications](https://www.reactboilerplate.com/)
>  
>  

[How to set up your own knowledge base with React, Contentful and Netlify - Part 1
](https://www.youtube.com/watch?v=DSxGa6uVtm4)

[today I learned - tutorial](https://today-i-learned.netlify.com/tutorial/)

[stefan judis - today I learned (TIL)](https://www.stefanjudis.com/today-i-learned/) and [some good learning material references](https://www.stefanjudis.com/staying-up-to-date/)

[strapi - The most advanced open-source Content Management Framework to build powerful API with no effort.](https://strapi.io/)

[squitex - CMS for apps, websites and services](https://squidex.io)

[prismic - One CMS Backend for all your Websites & Apps](https://prismic.io/)

[prismic demo - multipage site with navigation in node](https://user-guides.prismic.io/examples/nodejs-samples/sample-multi-page-site-with-navigation-in-nodejs)

[contentful CMS - content infrastructure to deliver 
content to any website, app or device](https://www.contentful.com)

[butterCMS](https://buttercms.com)

[graphCMS - graphQL content - headless CMS](https://graphcms.com/)

[awesome CMS - collection of CMS's for different languages](https://github.com/postlight/awesome-cms)

[free bootstrap templates for react](https://www.codeinwp.com/blog/best-free-bootstrap-templates-for-reactjs/)

### Wed 14 Nov 2018

[headless CMS comparison](https://geekflare.com/headless-cms/)

[netlifyCMS - open source CMS](https://www.netlifycms.org/)

[hackernoon - CMS for react app with firebase](https://hackernoon.com/how-i-built-a-content-management-system-for-a-react-app-in-one-day-269df17f5509)

[PIMCORE - digital platform for enterprises](https://pimcore.com/en)

[GRAV - open source CMS](https://getgrav.org/)

[built with Electron](https://alternativeto.net/list/55/built-with-electron)

[top CMS for building a website](https://alternativeto.net/list/341/top-10-cms-for-building-a-website)

[react + styled-components demo](https://stackblitz.com/edit/react-ete4lb)

[Using StackBlitz & Angular for Rapid App Prototyping - Eric Simons and Albert Pai
](https://www.youtube.com/watch?v=EBzoTnX6LzU)

[StackBlitz + Angular A Better Way to Build PWA's - Albert Pai, Eric Simons
](https://www.youtube.com/watch?v=P1-HAN1g4_4)

### Tue 13 Nov 2018

[UX principles by a service design company - uxplanet](https://uxplanet.org/7-ux-principles-by-a-service-design-company-5a32da62f7e8)

[universal pples US design - smashingmagazine](https://www.smashingmagazine.com/2018/01/universal-principles-ux-design/)

[mini-course in design principles](http://www.rit.edu/~w-rkelly/resources/pdf/04_cou/cou_des.pdf)

[interaction design principles to boost UX design](https://www.mockplus.com/blog/post/interaction-design-principles)

[UX process - UX mastery](https://uxmastery.com/resources/process/)

[process and principles of UX design](https://www.uxteam.com/blog/the-process-and-principles-of-ux-design/)

[core principles of UX design - London academy of IT](http://www.londonacademyofit.co.uk/learning-blog/design/core-principles-ux-design/)

### Mon 12 Nov 2018

[protect (an e-commmerce) app from hackers attack_](http://www.tothenew.com/blog/things-you-must-know-to-protect-your-e-commerce-application/)

[SASS architecture - scotch](https://scotch.io/tutorials/aesthetic-sass-1-architecture-and-style-organization)

[SASS architecture - sitepoint](https://www.sitepoint.com/architecture-sass-project/)

[SASS architecture - matthewelsom](https://matthewelsom.com/blog/simple-scss-playbook.html)

### Sun 11 Nov 2018

[OOP in JS - scotch](https://scotch.io/tutorials/object-oriented-programming-in-javascript)

[scotch.io - JS tuts](https://scotch.io/tag/javascript)

### Fri 9 Nov 2018

[CRUZ - Movie Search demo - moviedb API, react, grid CSS, flexbox](https://react-i1fb2z.stackblitz.io)

[how to graphql](https://www.howtographql.com/)

[react readux to reactn](https://itnext.io/replacing-redux-with-reactn-to-reduce-complexity-and-bundle-size-1c8bcc6b14cc)

### Thu 8 Nov 2018

[20%-80% CSS grid](https://medium.com/flexbox-and-grids/how-to-efficiently-master-the-css-grid-in-a-jiffy-585d0c213577)

[understand flexbox](https://medium.freecodecamp.org/understanding-flexbox-everything-you-need-to-know-b4013d4dc9af)

[CRUZ - Codepen Music app practising CSS grid](https://codepen.io/CruzWeb/full/qQZjbN)

### Wed 7 Nov 2018

[OOP in JS in depth - javascriptissexy](http://javascriptissexy.com/oop-in-javascript-what-you-need-to-know/)

[JS prototype in plain detailed language - javascriptissexy](http://javascriptissexy.com/javascript-prototype-in-plain-detailed-language/)

[eric elliot - 3 kinds of prototypal inheritance (JS)](https://ericleads.wordpress.com/2013/02/11/fluent-javascript-three-different-kinds-of-prototypal-oo/)

[frontend devs guide GraphQL](https://css-tricks.com/front-end-developers-guide-graphql/)

>  the data you consume on the client is no longer coupled to an endpoint’s resource!
>  
>  Your GraphQL server always gives you back exactly the data you ask for. Nothing more. This differs significantly from REST, where you often have to filter and transform the data you get back from the server into the shape your UI components need. Not only does this save you time, it also results in smaller network payloads and CPU savings from loading and parsing the response.

[the power of serverless](https://thepowerofserverless.info)

### Tue 6 Nov 2018

next mini app to translate into stackblitz? [auth0 - beautiful apps with angular material](https://auth0.com/blog/creating-beautiful-apps-with-angular-material/)

[github api - jquery and bootstrap](https://codepen.io/andreic/pen/oKghp?editors=1010)

[github api - (my version) with angular and material design](https://angular-qlvuut.stackblitz.io)

[angular material design comps](https://www.sitepoint.com/angular-material-design-components/)

[angular dynamic themes without a library](https://dev.to/adamaso/angular-6-dynamic-themes-without-a-library-2e9c)

[How to price design services and creativity](https://www.youtube.com/watch?v=RKXZ7t_RiOE)

### Mon 5 Nov 2018

[Using GraphQL, ReactJS and Apollo To Create Amazing Apps](https://www.youtube.com/watch?v=kXH2dbnHYA0)

[bring content to any platform - graphCMS](https://graphcms.com/)

[storyblock - headless CMS](https://www.storyblok.com)

[developing and running angular components in a sandbox](https://blog.codewithdan.com/angular-playground-developing-and-running-components-in-a-sandbox/)

[angular playground - build and run Angular components/pipes/directives in isolation](http://www.angularplayground.it/)

[ideas √√√](https://www.producthunt.com)

[create illustrations](https://www.producthunt.com/posts/juicy-illustrations)

[Top 10 Headless CMS's You Should Check Out (and what they are!)](https://www.youtube.com/watch?v=hhX8nCnaNFM)

[FE dev 2018](https://www.youtube.com/watch?list=PL03Lrmd9CiGfprrIjzbjdA2RRShJMzYIM)

[why content & service design](https://contentdesign.london/content-design/content-design-in-services-5-reasons-why-its-important/)

[Content designer working on services](https://designnotes.blog.gov.uk/2017/01/04/advice-for-content-designers-working-on-services/)

[service designer skills](https://www.gov.uk/government/publications/service-designer-skills-they-need/service-designer-skills-they-need)

### Wed 31 Oct 2018

[angular communication btwn comps - observable>subject](http://jasonwatmore.com/post/2016/12/01/angular-2-communicating-between-components-with-observable-subject)

[angular/rxjs - Observable data service](https://blog.angular-university.io/how-to-build-angular2-apps-using-rxjs-observable-data-services-pitfalls-to-avoid/)

### Mon 29 Oct 2018

[motion design - material](https://medium.com/google-design/motion-design-doesnt-have-to-be-hard-33089196e6c2)

[angular - moving design beyond pictures](https://blog.angular.io/moving-design-beyond-pictures-1509c315f94e)

### Sat 27 Oct 2018

[React: 'What the Hooks!'](https://reactjs.org/docs/hooks-intro.html)

### Fri 26 Oct 2018

[mozilla: using files from web apps](https://developer.mozilla.org/en-US/docs/Web/API/File/Using_files_from_web_applications)

[Drag & Drop With Vanilla JS - traversy media](https://www.youtube.com/watch?v=C22hQKE_32c)

[google devs: capture images from users](https://developers.google.com/web/fundamentals/media/capturing-images/)

[youtube: React Drag and Drop tut without using external or third party libraries](https://www.youtube.com/watch?v=FdDpyD4EMrA)

[Let's Create a Drag & Drop Image Uploader on React #01
](https://www.youtube.com/watch?v=jlbuMCzSq0Y)

### Wed 24 Oct 2018

[Firestore -> collections](https://github.com/angular/angularfire2/blob/master/docs/firestore/collections.md)

### Mon 22 Oct 2018

[JS functions pocket ref](https://medium.com/@ajmeyghani/javascript-functions-a-pocket-reference-d42597ceb496)

[gatsby starters](https://www.gatsbyjs.org/starters)

[scrap the web - JS chrome puppeteer node](https://codeburst.io/a-guide-to-automating-scraping-the-web-with-javascript-chrome-puppeteer-node-js-b18efb9e9921)

[start node server - popular frameworks](https://stackabuse.com/how-to-start-a-node-server-examples-with-the-most-popular-frameworks/)

[watch replay hacksummit](https://www.crowdcast.io/e/hacksummit-2016/register)

[hack pledge - give or receive one hour code mentoring](https://hackpledge.org/)

[Modern Web dev book - dexteryy](https://github.com/dexteryy/spellbook-of-modern-webdev)

[rxjs gitbook](https://chrisnoring.gitbooks.io/rxjs-5-ultimate/content/)

### Fri 18 Oct 2018

[lucidchart - 4 phases of PM lifecycle](https://www.lucidchart.com/blog/the-4-phases-of-the-project-management-life-cycle)

[lucidchart - how to create a user story map - UX](https://www.lucidchart.com/blog/how-to-create-a-user-story-map)

[prioritization matrix examples - UX](https://www.productplan.com/prioritization-matrix-example/)

[product prioritization techniques - UX](https://foldingburritos.com/product-prioritization-techniques/)

### Wed 17 Oct 2018

Following [this tut](https://blog.theodo.fr/2016/02/introduction-to-react/) I've made [my own version](https://react-c6ernm.stackblitz.io/)

[flexing pagination arrow](https://codepen.io/hakimel/pen/gfIsk)

[arrows and more... - freefrontend](https://freefrontend.com/css-arrows/)

[style images with markdown](https://dzone.com/articles/how-to-style-images-with-markdown)

[markdown and CSS](https://jblevins.org/log/custom-css)

[Static Website + Blog (React + Gratsby + GraphQL)](https://priceless-neumann-121335.netlify.com)

[]()

[Sytle site or md like Medium](https://medium.freecodecamp.org/style-webpage-or-markdown-like-medium-article-using-html-css-sass-bootstrap-c6f9e64c0955)

[Decomposing techniques for React components](https://medium.com/dailyjs/techniques-for-decomposing-react-components-e8a1081ef5da)

### Tue 16 Oct 2018

[grandstack.io](https://grandstack.io/)

[How to graphql](https://www.howtographql.com/)

[Gatsby + WP](https://www.gatsbyjs.org/blog/2018-01-22-getting-started-gatsby-and-wordpress/)

[Gatsby JS crash course - traversy media](https://www.youtube.com/watch?v=6YhqQ2ZW1sc)

[learn fast - Jim Kwick](https://www.youtube.com/watch?v=uT_GcOGEFsk)

### Mon 15 Oct 2018

[Jim kwick - the morning routine](https://www.youtube.com/watch?v=o8ky8PDLBRw)

[cashflow quadrant](https://www.youtube.com/watch?v=C9kQaeg3iRM)

[kiyosaki 7 rules](https://youtu.be/C9kQaeg3iRM)

[financial education - kiyosaki](https://www.youtube.com/watch?v=YoN1XM8SndA)

[understanding people](https://www.youtube.com/watch?v=OyV8LELM_HM)

[pre-suation and influence](https://www.youtube.com/watch?v=HctZg2aOPMw)

[remote work culture, tips and ideas](https://blog.cloudpeeps.com/top-10-companies-winning-at-remote-work-culture/)

[freelance and remote workers resources](https://medium.com/we-are-testers/best-resources-for-successful-freelancers-and-remote-workers-f9fd66fc412a)

[How debt can generate income - robert kiyosaki](https://www.youtube.com/watch?v=dN5qHjnd_xk)

### Fri 12 Oct 2018

[git cheatsheet guide... ;)](http://rogerdudler.github.io/git-guide/)

[quick git ref](https://www.christianengvall.se/a-quick-git-commands-refresh/)

[mobile color scheme trends](https://envato.com/blog/8-color-scheme-trends-mobile-app-design/)

[color scheme workflow](https://stories.uplabs.com/best-three-color-scheme-for-music-player-5da996d7f460)

### Wed 10 Oct 2018

[publish-subscribe method](https://itnext.io/why-every-beginner-front-end-developer-should-know-publish-subscribe-pattern-72a12cd68d44)

[Simon Sinek - how great leaders inspire action, their WHY](https://www.ted.com/talks/simon_sinek_how_great_leaders_inspire_action)

[express generator](https://expressjs.com/en/starter/generator.html)

[express.js middleware](https://expressjs.com/en/guide/writing-middleware.html)

[good motivational tips on freelancing](https://www.bradhussey.ca/3-reasons-you-should-not-freelance/)

Finished the 1 course on the Node saga (Pluralsight) by Samer Buna. Really excited, learning a lot.

### Tue 9 Oct 2018

[wev dev youtube channels](https://www.managedsolution.com/16-best-youtube-channels-to-learn-web-development-from/)

[web dev YT channels to double check](https://www.thebalancecareers.com/the-10-best-web-development-youtube-channels-2071397)

[Online survey data collector](https://www.typeform.com/)

[freelancing ideas](https://www.bradhussey.ca/six-figure-freelancing/)

[freelance service - your strenghts](https://www.bradhussey.ca/perfect-freelance-service/)

[codepen radio - servers](https://blog.codepen.io/2014/02/22/002-servers/)

[Open Source - how to contribute](https://opensource.guide/how-to-contribute/)

### Sun 7 Oct 2018

[FIRE movement/trend](https://medium.com/the-new-york-times/how-to-retire-in-your-30s-with-1-million-in-the-bank-d2911b3fa206)

[ed weissman](https://edweissman.wordpress.com/2013/03/24/who-is-a-good-programmer/)

[medium: the startup](https://medium.com/swlh)

[great clients dont care about your portfolio](https://medium.com/swlh/great-clients-dont-care-about-your-portfolio-49f9569bf637)

[JS promises in depth](https://hackernoon.com/understanding-promises-in-javascript-13d99df067c1)

### Fri 5 Oct 2018

Read all [react native documentation](https://facebook.github.io/react-native/docs/tutorial)

### Thu 4 Oct 2018

[reactnative.com](http://www.reactnative.com/)

[run and modified my 1st react native app! yuhuuu](https://facebook.github.io/react-native/docs/getting-started)

[node courses on Pluralsight (sign in required)](https://app.pluralsight.com/library/search?q=node)

[github for that course modules](https://github.com/jscomplete/ngs)

[requests with Node](https://www.twilio.com/blog/2017/08/http-requests-in-node-js.html)

[codeburst node series](https://codeburst.io/how-to-make-an-http-request-in-nodejs-http-mechanism-libraries-f25ec990d307)

### Wed 3 Oct 2018

[automate with python (book)](https://www.amazon.com/Automate-Boring-Stuff-Python-Programming/dp/1593275994)

[automate with node](https://medium.com/dailyjs/how-i-automated-my-job-with-node-js-94bf4e423017)

[take screenshots with node!](https://www.penta-code.com/how-to-take-screenshots-of-webpages-with-node-js/?src=related)

[VS code tips to improve productivity](https://www.penta-code.com/10-visual-studio-code-tips-to-boost-your-productivity/)

[JS and VS code](https://code.visualstudio.com/docs/languages/javascript)

[JS extensions for VS code](https://code.visualstudio.com/docs/nodejs/extensions)

[VS code - create your own snippets](https://code.visualstudio.com/docs/editor/userdefinedsnippets)

[got MEAN stack certificate](https://www.udemy.com/angular-2-and-nodejs-the-practical-guide/)

[Hi Fredrik Christenson... nice to meet you](https://www.youtube.com/user/Fidde12345)

I've watched his [basic Node playlist](https://www.youtube.com/watch?v=gnfiKy3LP-8&list=PLBAZWBMYeVYhx5LlJ8Ev-W7PL_VGha3Fd)

[Interaction design - scroll card list with Vue](https://levelup.gitconnected.com/making-a-scrolling-card-list-wotw-bcd5e31fbcc5)

[How browser rendering works](https://blog.logrocket.com/how-browser-rendering-works-behind-the-scenes-6782b0e8fb10)

[React+Node+MySQL data science app](https://towardsdatascience.com/guide-building-data-science-web-application-with-react-nodejs-and-mysql-1c55416ff0fb)

>  I liked how he though about the architecture of the app, and why he used that tech stack



### Fri 28 Sep 2018

[Nameservers setup on Cpanel](https://documentation.cpanel.net/display/CKB/How+to+Set+Up+Nameservers+in+a+cPanel+Environment)

[Cpanel -> Addon domain](http://kb.ifastnet.com/index.php?/article/AA-00283/0/Add-a-Domain.html)

### Tue 25 Sep 2018

[thinking patterns - think clear and better](https://medium.com/@ztrana/the-trick-to-thinking-clearer-and-better-4a61c54114fa)

### Mon 24 Sep 2018

[Array Vs Obj Vs Set Vs Map](https://codeburst.io/array-vs-set-vs-map-vs-object-real-time-use-cases-in-javascript-es6-47ee3295329b)

[obj values, keys and entries - convert obj to arr of obj](https://medium.com/chrisburgin/javascript-converting-an-object-to-an-array-94b030a1604c)

### Sun 23 Sep 2018

[material icons](https://material.io/tools/icons/?style=baseline)

[angular flex](https://github.com/angular/flex-layout)

checking on [angular material and reactive forms](https://www.c-sharpcorner.com/article/angular-material-design-components-with-reactive-form-part-2/)

### Wed 19 Sep 2018

[Angular 6 Weather app from scratch](https://medium.com/@hamedbaatour/build-a-real-world-beautiful-web-app-with-angular-6-a-to-z-ultimate-guide-2018-part-i-e121dd1d55e)

[Eric Elliot tips on learning JS](https://medium.com/javascript-scene/learn-to-code-13-tips-that-could-save-you-years-of-effort-92ce799a3e1f)

[same TODO app in react and vue](https://medium.com/javascript-in-plain-english/i-created-the-exact-same-app-in-react-and-vue-here-are-the-differences-e9a1ae8077fd)

**Apache index.html redirection**

First create your .htaccess file

```
RewriteBase /
RewriteRule ^index\.html$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.html [L]
```

### Tue 18 Sep 2018

Learning about VPN's, Skype numbers, ...

[now (zeit) aliases](https://zeit.co/docs/features/aliases)

[now - remove deployments](https://zeit.co/blog/now-rm-is-here-and-more)

### Mon 17 Sep 2018

[ES6 markdown files](https://github.com/tagtree/expert-es6/tree/master/lessons)

[Objects in JS with ES6](https://medium.freecodecamp.org/how-to-conditionally-build-an-object-in-javascript-with-es6-e2c49022c448)

>  Here I found things like **parameter object destructuring**, parameter defaulting and spread syntax to unwrap the object if the condition is truthy

[Destructuring in ES6 - Beau teaches JavaScript](https://www.youtube.com/watch?v=-vR3a11Wzt0)

[nested object destructuring (and renaming) - Wes Bos](https://www.youtube.com/watch?v=_ApRMRGI-6g)

### Wed 12-Sep-2018

[code splitting - react and webpack](https://hackernoon.com/lessons-learned-code-splitting-with-webpack-and-react-f012a989113)

### Sat 18-Aug-2018

[react JSON schema form - forked github](https://github.com/Zurc/react-jsonschema-form)

[mozilla > react JSON schema form examples](https://mozilla-services.github.io/react-jsonschema-form/)

[Auto generate ReactJS Forms from json schema](https://medium.com/@sairamkrish/rapid-development-of-data-collection-platform-with-reactjs-and-json-schema-ef147f4c665)

### Fri 17-Aug-2018

[Wireframes, Mockups, Prototypes](https://www.uxpin.com/studio/blog/wireframe-mockup-lofi-hifi-nomenclature/)

[productividad - ley de Pareto o regla del 80/20](https://www.sebascelis.com/como-aprovechar-la-ley-de-pareto-80-20/)

[12 Shocking Habits of Successful People](https://www.youtube.com/watch?v=_ulhxX_tnqY)


>  wake up early, learn from failure (mistakes | lessons, take chances, don't be afraid of failure), ignore conformity (new solutions to problems, innovation), read, spend money to earn money, make sacrifices, creative writing, mild procastination, self improvement (noone is perfect but can improve), networking (who you know, go and practice, create a group, volunteer, ...), exercising consistently, meditation (prayer)

[Denzel Washington's Life Advice Will Change Your Future (MUST WATCH) Motivational Speech 2018
](https://www.youtube.com/watch?v=M99NCxR0a-Q)

>  First god, be thankful (say thank you in advance for what is already yours), have goals, apply discipline and consistency. Hard work works, aspire to make a difference not a living, every failed experiment is one step closer to success, if you don't fail you're not even trying, to get something you never did you have to do something you never did, what are you going to do with what you have?

### Sun 22-Jul-2018

[1150 academy - cursos interesantes](https://www.elevenfifty.org/courses/)

[1150 react github book](https://eleven-fifty-academy.gitbook.io/javascript-301-reactfundamentals/)

[1150 main github](https://github.com/ElevenfiftyAcademy)

### Wed 18-Jul-2018

>  Super Simple Highlighter (chrome extension) allows to highlight text and save it in markdown if I want. Pretty neat!

### Wed 11-Jul-2018

[memory - how to retain more from book reading](https://medium.com/personal-growth/how-to-retain-more-of-every-book-you-read-3bb9fa45f49d)

[tecnicas de estudio: el repaso](http://biblioguias.unex.es/c.php?g=572102&p=3944254)

[memorización con repetición espaciada](http://www.insanity-mind.com/insanitymind_es/memoriza-de-manera-optima-con-la-repeticion-espaciada/)

[16 JS concepts you should know well](http://javascriptissexy.com/16-javascript-concepts-you-must-know-well/)

[interesting approach to explain 'this' on JS](http://javascriptissexy.com/understand-javascripts-this-with-clarity-and-master-it/)

[full bg image tricks](https://css-tricks.com/perfect-full-page-background-image/)

[responsive SVG](http://slides.com/dudleystorey/deck-3#/17)

### Tue 10-Jul-2018

[UX workshop on General Assembly](https://generalassemb.ly/education?format=classes-workshops)

[SVG optimiser](http://petercollingridge.appspot.com/svg-optimiser)

[Scrimba playground](https://scrimba.com/)

### Mon 9-Jul-2018

[SVG from illustrator to the web](http://creativedroplets.com/export-svg-for-the-web-with-illustrator-cc/)

### Thu 5-Jul-2018

[CSS positioning](http://www.barelyfitz.com/screencast/html-training/css/positioning/)

Book summaries

[deconstructing excellence](http://www.deconstructingexcellence.com/)

[book summary - the power of habit](http://www.deconstructingexcellence.com/the-power-of-habit-summary/)

[el poder de los habitos - links interesantes para emprendedores](https://librosparaemprendedores.net/podcast/078-el-poder-de-los-habitos/)

### Wed 4-Jul-2018

[jpeg compresssion photoshop for web](https://photography.tutsplus.com/tutorials/save-for-web-better-jpeg-compression-with-adobe-photoshop--cms-23080)

[Optimize images for JPEG - adobe help](https://helpx.adobe.com/photoshop-elements/using/optimizing-images-jpeg-format.html)

[compressive images - filament group](https://www.filamentgroup.com/lab/compressive-images.html)

[Picturefill - a responsive image polyfill](http://scottjehl.github.io/picturefill/)

[picturefill github](https://github.com/scottjehl/picturefill)

### Wed 27-Jun-2018

[benefits of a decoupled frontend architecture](https://vimeo.com/237812253)

[intro to micro frontends - youtube](https://www.youtube.com/watch?v=LH3QoDWAD8k)

### Tue 12-Jun-2018

[técnicas de estudio y repetición](https://www.metaaprendizaje.net/tecnicas-de-estudio-la-repeticion/)

[memoria - aprender libros al pie de la letra](https://www.elconfidencial.com/alma-corazon-vida/2016-05-20/secreto-gran-memoria-aprender-paraiso-perdido-milton_1202793/)

[memoria y repecitión - center for hellenic studies - harvard univ](https://chs.harvard.edu/CHS/article/display/4007.2-memoria-y-repetici%F3n)

[memoriza de manera óptima con repetición espaciada](http://www.insanity-mind.com/insanitymind_es/memoriza-de-manera-optima-con-la-repeticion-espaciada/)

[4 técnicas de memorización](https://lecturaagil.com/4-tecnicas-memorizacion/)

[16 técnicas... memoria](http://noticias.universia.com.ar/educacion/noticia/2016/12/19/1147581/16-consejos-tecnicas-memorizar-informacion.html)

[6 tecnicas para desarrollar la memoria](http://noticias.universia.com.ar/educacion/noticia/2016/07/21/1142022/6-tecnicas-desarrollar-memoria.html)

[gov de cantabria - la memoria pdf](http://almez.pntic.mec.es/~erug0000/orientacion/psicologia/Documentos/La%20memoria.pdf)

[la memoria desde el procesamiento de información - univ de valencia](https://www.uv.es/seoane/publicaciones/Garzon-Seoane%201982%20La%20Memoria%20desde%20el%20Procesamiento%20de%20Informacion.pdf)

[la memoria humana - pdf ](http://spain-s3-mhe-prod.s3-website-eu-west-1.amazonaws.com/bcv/guide/capitulo/8448180607.pdf)

[memoria humana - investigacion y teoría](http://www.psicothema.com/pdf/323.pdf)

[keyframes app - chrome extention too](https://keyframes.app/)

[Create CSS Animations Easily with this Chrome Extension](https://www.youtube.com/watch?v=H598jXvQhLw)

[full page screenshots](https://css-tricks.com/full-page-screenshots-browsers/)

### Mon 11-Jun-2018

[CSS specificity and inheritance](https://www.smashingmagazine.com/2010/04/css-specificity-and-inheritance/)

[CSS selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors)

### Fri-8-Jun-2018

about react and angular...

[hackernoon - feb 2018](https://hackernoon.com/why-im-switching-from-angular-to-react-and-redux-in-2018-cb48be00fda7)

[Beereal CTO](https://medium.com/beereal/enterprise-software-angular-vs-react-2a5010574c7d)

[from angular to react without massive rewrite](https://www.smartly.io/blog/how-to-migrate-from-angular-to-react-without-a-massive-rewrite)

[react graphQL and .NET](https://www.robinwieruch.de/reasons-why-i-moved-from-angular-to-react/)

### Thu-7-Jun-2018

[ABEM - adaptation of BEM CSS class naming convention](https://css-tricks.com/abem-useful-adaptation-bem/)

### Thu-31-May-2018

Tables, tables, tables...

[apple - human interface guidelines - tables](https://developer.apple.com/ios/human-interface-guidelines/views/tables/)

[semantic UI - tables](https://semantic-ui.com/collections/table.html)

[Design better data tables - uxdesign cc](https://uxdesign.cc/design-better-data-tables-4ecc99d23356)

[Design tables for reusability](https://uxdesign.cc/designing-tables-for-reusability-490a3760533)

[modern enterprise design - tables](https://medium.com/pulsar/modern-enterprise-ui-design-part-1-tables-ad8ee1b9feb)

### Wed-30-May-2018

[tricks - disable a link](https://css-tricks.com/how-to-disable-links/)

[creating a design system - uxpin](https://medium.com/@marcintreder/design-systems-sprint-0-the-silver-bullet-of-product-development-8c0ed83bf00d)

[material design - interaction states](https://material.io/design/interaction/states.html)

[guides to optimise UX UI on web and mobile apps](https://www.nickkolenda.com/user-experience/)

[some pdf's from the guides above](https://www.nickkolenda.com/the-members-area/)

[Affordances, signifiers and clickability - codecademy](https://www.codecademy.com/articles/ui-design-affordances-signifiers-clickability)

### Tue-29-May-2018

[A practical guide to web typography](http://webtypography.net/)

[line length - practical typography](https://practicaltypography.com/line-length.html)

[line length - wikipedia](https://en.wikipedia.org/wiki/Line_length)

[axis praxis](https://www.axis-praxis.org/specimens/__DEFAULT__)

[variable fonts](https://medium.com/@Lorp/variable-fonts-a-talk-with-laurence-penney-d6f8e9777007)

[line lenght - w3](https://www.w3.org/WAI/GL/low-vision-a11y-tf/wiki/Line_Length)

[w3 - text spacing](https://www.w3.org/WAI/WCAG21/Understanding/text-spacing.html)

[letter spacing guidelines - css tricks](https://css-tricks.com/keeping-track-letter-spacing-guidelines/)

[serifs and font legibility](https://www.sciencedirect.com/science/article/pii/S0042698905003007)

[optimal text layout line length](https://www.paulolyslager.com/optimal-text-layout-line-length/)

[line length readability](https://baymard.com/blog/line-length-readability)

[a list apart - web, typography and layout](http://alistapart.com/event/web-typography-layout-past-present-future)

[balancing line length and font size in responsive web design - smashing magazine](https://www.smashingmagazine.com/2014/09/balancing-line-length-font-size-responsive-web-design/)

[dev skills: estimation](https://trackchanges.postlight.com/estimation-is-a-core-competency-36dfc1dfdea3)

[typography - modular scale with golden ratio](http://alistapart.com/article/more-meaningful-typography)

some differences btwn b and strong HTML tags and CSS font-weight

[strong](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/strong)

[b](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/b)

[b and strong - semantic differences](https://codeengineered.com/blog/2013/html5-semantic-diff-bold-strong/)

[CSS font-weight](https://developer.mozilla.org/en-US/docs/Web/CSS/font-weight)

### Thu 24-May-2018

[px to rem conversion](http://www.standardista.com/px-to-rem-conversion-if-root-font-size-is-16px/)

[Mozilla - aligning items in a flex container](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Aligning_Items_in_a_Flex_Container)

[Mozilla - mastering wrapping of flex items](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Mastering_Wrapping_of_Flex_Items)

[codepen - float elements with flex](https://codepen.io/cjtoem/pen/aGrEjv)

[codepen - float elements with CSS float](https://codepen.io/cjtoem/pen/odRpGL)

### Wed 23-May-2018

[box sizing - border, padding, width and margin](https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing)

[typography - compose with a vertical rythm](https://24ways.org/2006/compose-to-a-vertical-rhythm/)

[typographic system - scale and rythm](https://www.gridlover.net/)

[tips for Clarity Design UI](https://medium.com/claritydesignsystem/advanced-tips-with-the-clarity-ui-template-da7e594581ef)

### Tue-22-May-2018

[JS landscape 2018](https://css-tricks.com/javascript-learning-landscape-2018/)

[using SASS to control scope with BEM naming](https://css-tricks.com/using-sass-control-scope-bem-naming/)

[pixels are dead](https://medium.com/@julienetienne/pixels-are-dead-faa87cd8c8b9)

[easy peasy rem with SASS](http://www.stubbornella.org/content/2013/07/01/easy-peasy-rem-conversion-with-sass/)

[mixins for rem fonts - css-tricks](https://css-tricks.com/snippets/css/less-mixin-for-rem-font-sizing/)

[browser usage national statistics](https://data.gov.uk/data/site-usage?month=2018-05#browsers_versions)

[w3schools browser usage statistics](https://www.w3schools.com/BROWSERS/default.asp)

### Fri-18-May-2018

resources | blog [Tucson academy of art](http://www.tucsonartacademyonline.com/explore/)

[color palettes with shades](https://codepen.io/afranceschetti/pen/zNWeVg)

[accessibility - Mozzilla ...read more](https://developer.mozilla.org/en-US/docs/Learn/Accessibility/CSS_and_JavaScript)

[accessible custom select dropdowns](http://www.webaxe.org/accessible-custom-select-dropdowns/)

[custom select - freefrontend](http://freefrontend.com/css-select-boxes/)

[custom select - w3schools](https://www.w3schools.com/howto/howto_custom_select.asp)

[ref custom selector](http://jsfiddle.net/pht9d295/3/)

[custom select themes](https://codepen.io/sverrirs/pen/dXJLRa)

### Thu-17-May-2018

[CSS3 selectors](https://code.tutsplus.com/tutorials/the-30-css-selectors-you-must-memorize--net-16048)

some reference docs about forms

[input mozilla devs - check other elements too](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)

### Wed 16-May-2018

[color scheme - codrops | tympanus](https://tympanus.net/codrops/2012/09/17/build-a-color-scheme-the-fundamentals/)

### Tue 15-May-2018

[gov.uk UI forms](https://govuk-elements.herokuapp.com/form-elements/)

[creating a design system](https://medium.com/qstream-design/creating-a-design-system-158a2d832551)

[smashing magazine - efficient forms](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

regarding colors, color schemes, sass...

[programatically go from one color to another](http://thesassway.com/advanced/how-to-programtically-go-from-one-color-to-another-in-sass)

[colors in css](https://hugogiraudel.com/2012/11/27/css-colors/)

[color palettes in sass](https://www.sitepoint.com/using-sass-build-color-palettes/)

[color schemes in sass](https://www.sitepoint.com/dealing-color-schemes-sass/)

### Mon 14-May-2018

started with [codepen blog - UI forms](https://codepen.io/write/ui-forms)

[tips to improve your UI](https://www.smashingmagazine.com/2008/12/10-useful-techniques-to-improve-your-user-interface-designs/)

[Google study on forms usability](http://storage.googleapis.com/pub-tools-public-publication-data/pdf/42513.pdf)

### Sat 12-May-2018

[Studying the art of painting trees](https://static1.squarespace.com/static/523f6ffee4b0c2ff638d91c0/t/56e1bb13f8baf3bc5474002d/1457634076912/Studying+The+Art+ofPainting+Trees.pdf)

[Composition guide](http://static1.squarespace.com/static/523f6ffee4b0c2ff638d91c0/t/56d1bda6356fb0092137e721/1456586166253/Composition+Guide+A+(1).pdf)

Impre sionante!!! [Clyde Aspevig - Landscape artist](http://www.clydeaspevig.com/clydes-advice.html)

### Fri 11-May-2018

[Color theory and the web](https://programmingdesignsystems.com/color/color-models-and-color-spaces/index.html)

[hsluv project](http://www.hsluv.org/)

>  HSLuv allows you to define a color based on three dimensions – hue, saturation, and lightness – but contrary to a HSL color model based on sRGB, colors that share the same value for a dimension are guaranteed to look similar. Two colors with an identical lightness value will look equally bright, and two colors with the same saturation will have the same perceived color purity.

### Thu 10-May-2018

[atomic design](http://atomicdesign.bradfrost.com/table-of-contents/)

[agnostic Design Systems](http://bradfrost.com/blog/post/managing-technology-agnostic-design-systems/)

[30 days of react](https://www.fullstackreact.com/30-days-of-react/)

[30 days... github](https://github.com/Zurc/30-days-of-react)

[30 days... pdf](https://www.fullstackreact.com/assets/media/sGEMe/MNzue/30-days-of-react-ebook-fullstackio.pdf)


[Designbetter handbook](https://www.designbetter.co/design-systems-handbook/introducing-design-systems)

>  Components are portions of reusable code within your system and they serve as the building blocks of your application’s interface. Components range in complexity. Reducing components to a single function, like a button or a drop down increases flexibility, making them more reusable.
>  
>  The more reusable your components are, the less you need to maintain, and the easier scale becomes.
>  
>  Who needs to be involved? 1 person from every pillar (product) to act as user research group
>  Disciplines involved: designers, FE devs, accesibility experts, content strategists, researchers, performance experts, product managers and leaders.

### Wed 2-May-2018

[Carbon Design System](http://carbondesignsystem.com/)

[Design Systems curated list - github](https://github.com/miukimiu/design-systems)

[Accessibility gitbook](https://ebay.gitbooks.io/oatmeal/content/)

[contrast ratio checker - Lea Verou](http://contrast-ratio.com/)

### Tue 1-May-2018

[Invision - Design Systems handbook](https://www.designbetter.co/design-systems-handbook/introducing-design-systems)

[Anticipatory design](https://www.cygnismedia.com/blog/how-to-create-anticipatory-design/)

[Web Content Accessibility Guidelines](https://www.w3.org/TR/WCAG/)

[Airbnb - how they changed their design approach](https://airbnb.design/the-way-we-build/)

[Airbnb - how they use typography](https://design.google/library/airbnb-communicating-clarity-and-charm/)

### Mon 30-Apr-2018

[prototypes need - atlassian](https://medium.com/designing-atlassian/why-prototyping-is-a-must-for-designers-5ef98dfb3bdc)

>  Prototypes (...) reduce the need for documentation. So, a prototype can save a lot of time, wasted effort, and frustration during the development lifecycle as multi-disciplined teams will need to go back and forth far less to validate interactions and flows. Just like a picture paints a 1000 words, a prototype can paint a 1000 user stories. 
>  
>  you can see customers interact with your finished design, before you’ve written a single line of code. Conducting well structured user research using a prototype is extremely cheap and easy, even if you don’t have access to a full-time researcher.

[error handling when they are same color as brand](https://medium.com/product-labs/when-your-brand-isn-t-broken-elegant-error-handling-for-apps-with-red-logos-f0d619c14758)

[Pluralsight Design System](https://design-system.pluralsight.com/)

[liderazgo y riesgo - innovación](https://es.linkedin.com/learning/liderazgo-y-la-capacidad-de-asumir-riesgos/presentacion-del-curso-liderazgo-y-la-capacidad-de-asumir-riesgos)

[color in UI design](https://medium.com/@erikdkennedy/color-in-ui-design-a-practical-framework-e18cacd97f9e)

>  Darker color variations are made by low
