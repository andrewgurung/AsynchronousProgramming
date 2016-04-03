## Advanced Flattening
- Flattening not just two dimensional, but also three dimensional collections

```js
var exchanges = [
  // Dow exchange
  [
    // Stocks
    { symbol: "XFX", price: 240.22, volume: 23432 },
    { symbol: "TNZ", price: 332.19, volume: 234 }
  ],

  // Nasdaq exchange
  [
    // Stocks
    { symbol: "JXJ", price: 120.22, volume: 5323 },
    { symbol: "NYN", price: 88.47, volume: 98275 }
  ]
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

var flattenedArray = exchanges.concatAll();
flattenedArray.forEach(function(item){
  console.log( item );
});
```
