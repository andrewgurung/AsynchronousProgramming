## Introducing the Observable
- An `Observable` is a collection that arrives over time
- `Observables` can be used to model events, asynchronous requests, and animations
- `Observables` can also be transformed, combined, and consumed using the Array methods

### JS
```js
var Observable = Rx.Observable;

var button = document.getElementById("button");

/*
1. Regular way
var handler = function(e) {
  alert("clicked");
  button.removeEventListener("click", handler);
};

button.addEventListener("click", handler);
*/

/*
2. Observable: Array that runs forEach to consume all events/items
var clicks = Observable.fromEvent(button, 'click');

clicks.forEach(function(e) {
  alert('clicked');
});
*/

// 3. `forEach(..)` for Observable is different than regular array
// It accepts 3 callbacks
// Also gets a subscription object (optional)

// Note: DOM doesn't create errors
var clicks = Observable.fromEvent(button, 'click');
var subscription = clicks.forEach(
  function onNext(e) {
    alert("clicked");
    // One time use only. Dispose after first click
    subscription.dispose();
  },
  function onError(e) {
    console.log("ERROR!");
  },
  function onCompleted() {
    console.log("done");
  }
);
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
