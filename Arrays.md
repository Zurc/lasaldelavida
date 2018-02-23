# Arrays

### Combine same length arrays of objects into a new one (same length and amount of objects)

Imagine 2 arrays of objects, same length...

```
arr1 = [{id:1}, {id:2}, {id:3}];
arr2 = [{name: "Coco"}, {name: "Eve"}, {name: "john"}]
```

I want to combine this into a 3rd array of objects with same length, like this...

```
arr3 = [{id:1, name:"Coco"}, {id:2, name: "Eve"}, {id:3, name:"John"}]
```

***First Attempt:*** nested maps

```
arr3 = []

arr1.map((i, index) => {
  arr2.map (j => {
    if (arr1.indexOf(i) === arr2.indexOf(j)) {
      arr3[index] = Object.assign({}, i,j)
    }
  })
})

console.table(arr3)
```

[live sample]

[live sample]:<https://jsbin.com/rojajip/1/edit?js,console>

***Second Attempt:*** object assign

```
arr3 = []

arr1.map((e,i) => arr3[i] = Object.assign(e, arr2[i]))

console.table(arr3)
```

[live sample]

[live sample]:<https://jsbin.com/vivineg/2/edit?js,output>


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

#### Option 2

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

So, let's recap: with arrays, flatMap applied a mapping function to each element of the array, and then flattened the result into one big array (which was only one level deep — no nesting).


[live sample]: <https://jsbin.com/vutakun/edit?html,js,console>


### add id property to an objects array or Observables

```
arr1.map((item, index) => {
  item.id = index;
})
```
http://jsbin.com/wacegel/edit?js,console


