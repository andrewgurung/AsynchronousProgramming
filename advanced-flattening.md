## Advanced Flattening
- Flattening not just two dimensional, but also three dimensional collections

```js
var exchanges = [
  // NYSE exchange
  {
      name: "NYSE",
      stocks: [
        { symbol: "XFX", price: 240.22, volume: 23432 },
        { symbol: "TNZ", price: 332.19, volume: 234 }
      ]
  },

  // TSX exchange
  {
      name: "TSX",
      stocks: [
        { symbol: "JXJ", price: 120.22, volume: 5323 },
        { symbol: "NYN", price: 88.47, volume: 98275 }
      ]
  }
];

Array.prototype.concatAll = function() {
  var results = [];
  this.forEach(function(subArray) {
    subArray.forEach(function(item) {
      results.push( item );
    });
  });
  return results;
}

var stocks = exchanges
              .map(function(exchange){
                return exchange.stocks
                  .filter(function(stock) { return stock.price >= 100; });
              })
              .concatAll();

stocks.forEach(function(stock){
  console.log( stock );
});
```
