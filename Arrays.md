# Arrays

### flatMap and thinking process...

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

### Option 2

Let's try functional programming but only array functions...

```
oddNumbers.map(x => [x,x=1]);
console.log(oddNumbers)    // [[1,2],[3,4],[5,6]]
```

Now, let's create a function and use reduce (to apply a function on prev and current sub-arrays)...

...and concat (to join this two each time)

```
function flatten(arr) {
    return arr.reduce((prevArr, currArr) => prevArr.concat(currArr), []);    // without the second parameter works the same
}    
```

Now we can get oneToSix appling flatten function to oddNumbers array

```
const oneToSix = flatten(oddNumbers)
    
console.log(oddNumbers)    // [1,2,3,4,5,6]
```

Ta da!

[live sample]

[live sample]:<https://jsbin.com/vutakun/edit?html,js,console>




