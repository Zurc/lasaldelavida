# Arrays

Let’s say we have an array called oddNumbers:

```
const oddNumbers = [1, 3, 5]
```

Now how would we transform oddNumbers into an array with the numbers 1 through 6?

#### Option 1

```
const oneToSix = JSON.parse("[" + oddNumbers.map(x => `${x + ',' + (x+1)}`).join() + "]");
console.log(oneToSix)
```

that should display

```
[1, 2, 3, 4, 5, 6]
```
