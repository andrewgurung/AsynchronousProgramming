## The Array map method

What does a map method do?
- Iterates through an array's content
- Applies a function to each item
- Create a **new** array containing the result

Notes
- Array provides an in built map method
- Much cleaner code
- Not only works on data that is in memory in array but also with data which arrives asynchronously over time

```js
// Array provides an in built map method
// How Array's map method works internally
/*
 Array.prototype.map = function(projection) {
   var results = [];

   this.forEach(function(item) {
     results.push(projection(item));
   });

   return results;
 };
*/

function getStockSymbols(stocks) {
    // 1. `map` method
    // 2. Projection method: function(stock){..}
    return stocks.map(function(stock){
      return stock.symbol;
    });
}

var symbols = getStockSymbols( [
  { symbol: "XFX", price: 240.22, volume: 23432 },
  { symbol: "TNZ", price: 332.19, volume: 234 },
  { symbol: "JXJ", price: 120.22, volume: 5323 },
] );

console.log( symbols ); // ["XFX", "TNZ", "JXJ"]
```
