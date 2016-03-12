## Chaining the Array map and filter methods
- Both `map` and `filter` methods do not modify the original array
- Since both methods return `Arrays`, they can be chained to create complex programs without ever using any loops
  - Reason for not using loops: Loops only works with data which is synchronously available

Consider:
1) Filter all stocks greater than 150.00
2) Map/capture only the stock symbols

```js
var stocks = [
  { symbol: "XFX", price: 240.22, volume: 23432 },
  { symbol: "TNZ", price: 332.19, volume: 234 },
  { symbol: "JXJ", price: 120.22, volume: 5323 },
];

var filteredStockSymbols = stocks.
                              filter(function(stock) {
                                return stock.price >= 150.00;
                              }).
                              map(function(stock) {
                                return stock.symbol;
                              });
// Print using forEach(..) method
filteredStockSymbols.forEach(function(stock) {
  console.log( stock );
});

//----------------
// Output
//----------------
// XFX
// TNZ
//----------------
```
