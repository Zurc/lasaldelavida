# Arrays

Let’s say we have an array called oddNumbers:

```
const oddNumbers = [1, 3, 5]
```

Now how would we transform oddNumbers into an array with the numbers 1 through 6?

#### Option 1

Let's ES6 features! template literals and string interpolation could work...

```
const oneToSix = oddNumbers.map(x => `${x + ',' + (x+1)}`);
console.log(oneToSix)   // ["1,2", "3,4", "5,6"]
```

ok, that's a start. Let's join all...

```
const oneToSix = oddNumbers.map(x => `${x + ',' + (x+1)}`).join();
console.log(oneToSix)    // "1,2,3,4,5,6"
```

A string!... mmm... it's not what I want... let's transform it into an array then...

```
const oneToSix = JSON.parse("[" + oddNumbers.map(x => `${x + ',' + (x+1)}`).join() + "]");
console.log(oneToSix)    // [1, 2, 3, 4, 5, 6]
```

voila!



