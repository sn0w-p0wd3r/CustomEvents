Generated from source file: event-emitter.js

Custom events in JavaScript
 * author Sergei Snegirev (tz4678@gmail.com)

```javascript
function App() {}

App.prototype.login = function(username, password) {
  if (username === "tester" && password === "test123") {
    this.emit("loginSuccess");
  } else {
    this.emit("loginError", {
      error: "invalid_client", 
      message: "Invalid username or password"
    });
  }
};

EventEmitter.mixin(App);

var app = new App();

app.on("loginSuccess", () => {
  console.info("Login Succeeded");
});

app.on("loginError", (data) => {
  console.warn("%s: %s", data.error, data.message);
});

setTimeout(() => app.login("tester", "qwerty"), 1000);
setTimeout(() => app.login("tester", "test123"), 2000);
```

Add event listener

```javascript
.on(event, fn[, scope[, once]])
```

 * param event {string}
 * param fn {function}
 * param scope {object}
 * param once {boolean}
 * return {this}

Add one-shot event listener

```javascript
.once(event, fn[, scope])
```

 * param event {string}
 * param fn {function}
 * param scope {object}
 * return {this}

Remove event listeners

```javascript
.off([event[, fn[, scope]]])
```

 * param event {string}
 * param fn {function}
 * param scope {object}
 * return {this}

Emit event

```javascript
.emit(event[, arg1[, arg2[, ...]]])
```

 * param event {string}
 * param *args
