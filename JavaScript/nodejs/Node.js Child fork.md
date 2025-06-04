## Basic Computation
Parent
```js
const { fork } = require('child_process');
const child = fork('./longtask.js');
child.send('start');
child.on('message', (sum) => {
res.send({ sum: sum });
});
```
Child
```js
function longComputation() {
let sum = 0;
for (let i = 0; i < 1e9; i++) {
	sum += i;
}
return sum;
}

process.on('message', (message) => {
if (message === 'start') {
	const sum = longComputation();
	process.send(sum);
}
});
```

**The above code found in `nodejs-child-process-tutorial`**

## Arguments can be passed
to a forked child process in Node.js using the `child_process.fork()` method. The `fork()` method accepts an optional `args` array as its second argument. This array contains the arguments that will be passed to the child process.

```js
const { fork } = require('child_process');
const child = fork('./child.js', ['arg1', 'arg2', 'arg3']);
```

In the child process, the arguments can be accessed using the `process.argv` array. The first two elements of this array are the path to the Node.js executable and the path to the script being executed, respectively. The remaining elements are the arguments passed to the script.

```js
// child.js
console.log(process.argv[2]); // Output: arg1
console.log(process.argv[3]); // Output: arg2
console.log(process.argv[4]); // Output: arg3
```

It is also possible to pass more complex data structures, such as objects and arrays, as arguments by serializing them to JSON strings.

```js
// parent.js
const { fork } = require('child_process');

const data = { key1: 'value1', key2: 'value2' };
const child = fork('./child.js', [JSON.stringify(data)]);
```

```js
// child.js
const data = JSON.parse(process.argv[2]);
console.log(data.key1); // Output: value1
console.log(data.key2); // Output: value2
```

## To use `.env` values ##
in a JavaScript child fork, the `dotenv` package can be utilized to load environment variables from a `.env` file into the `process.env` object. When forking a child process using `child_process.fork()`, these environment variables can be passed to the child process. Install `dotenv`.
```js
    // parent.js
    const dotenv = require('dotenv');
    dotenv.config();
    const { fork } = require('child_process');
    
    const child = fork('./child.js', [], {
      env: process.env
    });
    
    child.on('message', (msg) => {
      console.log('Message from child:', msg);
    });
    
    child.send({ hello: 'world' });
```

```js
    // child.js
    require('dotenv').config();
    
    process.on('message', (msg) => {
      console.log('Message from parent:', msg);
      console.log('Environment variable EXAMPLE_VAR:', process.env.EXAMPLE_VAR);
      process.send('Hello from child!');
    });
```

## In this setup,
the parent process loads the `.env` variables and then passes the entire `process.env` object to the child process during the fork. The child process can then access these variables directly from its own `process.env`.

## To use `dotenv` and arguments
the arguments need to be combined with the `.env`  variables
```js
//parent
const child = fork('./src/utils/img_file_trans.js', {
	env: {
		...process.env,
		dir: dir,
		imageName: imageName,
		eventId: eventId
	}
});
```

```js
//child
process.on('message',(message)=>{

	const dir = process.env.dir;
	const imageName = process.env.imageName;
	const eventId = process.env.eventId;
	const status = imgFileTran(dir,imageName, eventId);

	process.send({reqId: message.reqId, status: status});
})
```
 
 **Above code can be found in green-coast**
 
## To use `res.status` 
in a Node.js child process created with `fork`, it's crucial to understand that the child process has its own independent memory space and cannot directly access the parent process's `res` object (which is part of an HTTP request-response cycle). Communication between the parent and child processes happens through inter-process communication (IPC) channels.

Here's how to achieve the desired outcome:

- Parent Process (e.g., `server.js`):
    - Handles the initial request.
    - Forks a child process using `child_process.fork()`.
    - Sends necessary data to the child process, including a way to identify the request (e.g., a unique ID).
    - Sets up a listener for messages from the child process.
    - When a message is received from the child, it uses the request ID to find the corresponding `res` object and then calls `res.status()` and `res.send()` to send the response.
    
```js
    // server.js
    const express = require('express');
    const { fork } = require('child_process');
    const app = express();

    app.get('/process', (req, res) => {
      const child = fork('child.js');
      const reqId = Math.random().toString(36).substring(2, 15); // Generate a unique request ID

      // Send data to the child process, including the request ID
      child.send({ reqId: reqId, data: "some data to process" });

      // Listen for messages from the child process
      child.on('message', (message) => {
        if (message.reqId === reqId) {
          res.status(message.status).send(message.result);
        }
      });

      // Handle errors
      child.on('error', (err) => {
        console.error(err);
        res.status(500).send('Error processing request');
      });
		//This may seems wrong since, on success you would pass 200 status
		// and on error then handle errors steps in
      child.on('close', (code) => {
          if (code !== 0) {
              console.error(`Child process exited with code ${code}`);
              res.status(500).send('Error processing request');
          }
      });
    });

    app.listen(3000, () => {
      console.log('Server listening on port 3000');
    });
```

Child Process (e.g., `child.js`):
- Receives data from the parent process.
- Performs its task.
- Sends the result back to the parent process, including the request ID and the desired status code.
```js
    // child.js
    process.on('message', (message) => {
      // Process the data
      const result = `Processed: ${message.data}`;
      const status = 200;

      // Send the result and status code back to the parent process, including the request ID
      process.send({ reqId: message.reqId, result: result, status: status });
      process.exit();
    });
```

## To return an exit code
from a Node.js child process created with `fork()`, use `process.exit()` within the child process. The argument passed to `process.exit()` will be the exit code. The parent process can then listen for the `'exit'` event on the child process object to retrieve this code.

```js
// Parent process
const { fork } = require('child_process');

const child = fork('child.js');

child.on('exit', (code, signal) => {
  if (code !== null) {
    console.log(`Child process exited with code ${code}`);
  } else if (signal) {
      console.log(`Child process terminated by signal: ${signal}`)
  }
});

// Child process (child.js)
if (process.argv[2] === 'error') {
  process.exit(1); // Exit with error code 1
} else {
  process.exit(0); // Exit with success code 0
}
```

In this example, the parent process forks a child process using `child.js`. The child process checks if the third argument passed when running the script is "error". If it is, the child exits with code 1, indicating an error. Otherwise, it exits with code 0, indicating success. The parent process listens for the `'exit'` event and logs the exit code received from the child.

When using `child_process.fork()` in Node.js, the **child process's PID** can be accessed directly from the returned object. The `fork()` method returns a `ChildProcess` object, which has a `pid` property representing the process ID of the newly created child process.

```js
const { fork } = require('child_process');

const child = fork('child.js');

console.log(`Child process PID: ${child.pid}`);

// In child.js
process.on('message', (msg) => {
  console.log('Message from parent:', msg);
});

process.send({ message: 'Hello from child!' });

// Back in the parent process
child.on('message', (msg) => {
  console.log('Message from child:', msg);
});

child.on('close', (code) => {
  console.log(`Child process exited with code ${code}`);
});
```