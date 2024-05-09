Here is an example of using `setInterval` instead of `setTimeout`:
```js
async function run() {  
  while (true) {  
    console.log('Running...');  
    await new Promise(resolve => setInterval(resolve, 1000));  
  }  
}
```
This code will print “Running…” every second and can be easily stopped by calling `clearInterval`.

Another option is to use the `async`/`await` syntax with `setTimeout`:
```js
async function run() {  
  while (true) {  
    console.log('Running...');  
    await new Promise(resolve => setTimeout(resolve, 1000));  
  }  
}
```

This code will also print “Running…” every second and can be stopped by using `clearTimeout`.
