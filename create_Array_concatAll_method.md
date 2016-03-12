## Create an Array concatAll method
- Nested arrays are very common patterns which can be solved by custom `concatAll` utility method
- Custom `concatAll` method will return flatten nested arrays by one dimension
  - Eg: Turn 2 dimensional array to 1 dimensional Array  
  - Eg: Turn 4 dimension to 3 dimension
- Helps to parse nested arrays without using nested loops


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

// 1. Nested forEach(..) to loop through all items of nested array
exchanges.forEach(function(exchange) {
  exchange.forEach(function(stock) {
    console.log( stock );
  });
});
/* Output
-----------------------------------------------------
Object { symbol="XFX",  price=240.22,  volume=23432}
Object { symbol="TNZ",  price=332.19,  volume=234}
Object { symbol="JXJ",  price=120.22,  volume=5323}
Object { symbol="NYN",  price=88.47,  volume=98275}
-----------------------------------------------------
*/

// 2. Using concatAll
var flattenedArray = exchanges.concatAll();
flattenedArray.forEach(function(stock) {
  console.log( stock );
});
/* Output
-----------------------------------------------------
Object { symbol="XFX",  price=240.22,  volume=23432}
Object { symbol="TNZ",  price=332.19,  volume=234}
Object { symbol="JXJ",  price=120.22,  volume=5323}
Object { symbol="NYN",  price=88.47,  volume=98275}
-----------------------------------------------------
*/

```
