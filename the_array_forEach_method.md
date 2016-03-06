## The Array forEach method
- Most JavaScript developers are familiar with `for loop` to iterate through an array
- Replace the `for loop` with `Array`'s `forEach` method
  - Shortens code in the process

Consider:
- Retrieving a list of stock information from the server
- Extract just the stock symbols/tickers

#### Using `for loop`

```js
function getStockSymbols(stocks) {
  // 1. Empty array to store stock symbols
  var symbols = [],
      counter,
      stock;

  // 2. Use standard `for loop` to iterate through the stocks array
  for(counter = 0; counter < stocks.length; counter++) {
    stock = stocks[counter];
    symbols.push( stock.symbol );
  }
  return symbols;
}

var symbols = getStockSymbols( [
  { symbol: "XFX", price: 240.22, volume: 23432 },
  { symbol: "TNZ", price: 332.19, volume: 234 },
  { symbol: "JXJ", price: 120.22, volume: 5323 },
] );

console.log( symbols ); // ["XFX", "TNZ", "JXJ"]
```

#### Using Array's `forEach` method

- `forEach` simplifies the code dramatically
  - No need for counters to iterate through array
- Mainly because `forEach` can run asynchronously
- Syntax: `forEach(..)` which accepts a closure function as parameter
  - Invokes that closure for every item in the array
  - Passes each item as an argument to that closure

```js
function getStockSymbols(stocks) {
    var symbols = [];

    // 1. Array's forEach method
    // 2. Closure:  function(stock){..}
    // 3. Iterate through each item in the `stocks` array
    //    and pass it as argument to closure function
    stocks.forEach(function(stock) {
      symbols.push( stock.symbol );
    });

    return symbols;
}

var symbols = getStockSymbols( [
  { symbol: "XFX", price: 240.22, volume: 23432 },
  { symbol: "TNZ", price: 332.19, volume: 234 },
  { symbol: "JXJ", price: 120.22, volume: 5323 },
] );

console.log( symbols ); // ["XFX", "TNZ", "JXJ"]
```
