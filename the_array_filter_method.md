## The Array filter method

What does a filter method do?
- Iterate through an Array's contents
- Apply a test function to each item
- Create a **new** array containing only those items the passed the test

```js
/*
// 1. forEach(..)
function getStockOver(stocks, minPrice) {
  var results = [];
  stocks.forEach(function(stock){
    if(stock.price >= minPrice)
      results.push( stock );
  });
  return results;
}
*/

/*
// 2. custom filter(..)
Array.prototype.filter = function(predicate){
  var results = [];
  this.forEach(function(item){
    if(predicate(item)){
      results.push(item);
    }
  });
  return results;
};
*/

function getStockOver(stocks, minPrice) {
  var results = [];
  stocks.filter(function(stock) {
    if(stock.price >= minPrice)
      results.push( stock );
  });
  return results;
}

var expensiveStocks = getStockOver(
  [
    { symbol: "XFX", price: 240.22, volume: 23432 },
    { symbol: "TNZ", price: 332.19, volume: 234 },
    { symbol: "JXJ", price: 120.22, volume: 5323 },
  ],
  150.00);

console.log( expensiveStocks );
//  [Object { symbol="XFX",  price=240.22,  volume=23432}, Object { symbol="TNZ",  price=332.19,  volume=234}]
```
