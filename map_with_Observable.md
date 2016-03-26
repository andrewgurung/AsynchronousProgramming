## Using the map method with Observable
- In this example, Observable has a map method that allows us to transform a sequence into a new Observable
- When we `map` or `filter` Observables, we get back Observables
- Observable are lazy which mean nothing happens if until you call `forEach()`
- Observable just promises that it will hook an event listener when you call `forEach()`

```js
var Observable = Rx.Observable;

var button = document.getElementById("button");

var clicks = Observable.fromEvent(button, 'click');

var points =
    clicks.map(function(e){
      return {x: e.clientX, y: e.clientY };
    });

var subscription =
    points.forEach(
      function onNext(point) {
        alert( "clicked: " + JSON.stringify(point) );
        // One time use only. Dispose after first click
        subscription.dispose();
      },
      function onError(e) {
        console.log("ERROR!");
      },
      function onCompleted() {
        console.log("done");
      });
```

### HTML: Import rx.all library
```html
<!DOCTYPE html>
<html>
<head>
<script src="https://cdnjs.cloudflare.com/ajax/libs/rxjs/4.0.6/rx.all.js"></script>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
</head>
<body>

  <button id="button">Click Me</button>
</body>
</html>
```
