# [How to pass command line arguments to a Node.js app?](https://dev.to/bobbyiliev/how-to-pass-command-line-arguments-to-a-nodejs-app-5294)


## Introduction

Similar to a Bash script where you can pass arguments to a script using the `$1` syntax, you can also pass arguments to a Node.js app.

In this quick tutorial, you will learn how to pass arguments to a Node.js app using the [`process.argv` array](https://nodejs.org/docs/latest/api/process.html#process_process_argv).

## Prerequisites

Before you get started, you will need to have Node.js installed:

- [Download Node.js](https://nodejs.org/en/download/)

## Pass arguments to a Node.js app

Let's start by creating a new file called `script.js` and adding the following code to it:  

```js
const process = require('process');

console.log(process.argv[2]);
```

A quick rundown of the `process.argv` array:

- `process.argv[0]` is the path to the Node.js executable
- `process.argv[1]` is the path to the script file
- `process.argv[2]` is the first argument passed to the script
- `process.argv[3]` is the second argument passed to the script and so on

Let's run the script with the following command:  

```bash
node script.js DevDojo

# Output:
DevDojo
```

### Printing all arguments

To print all arguments, you can use a `forEach` loop just as you would with a standard array:  

```js
const process = require('process');

process.argv.forEach((val, index) => {
  console.log(`${index}: ${val}`);
});
```

Let's run the script with the following command:  

```bash
node script.js hi there devs
```

We are now passing 3 arguments to the script and in this case, the output of this script will be:  

```
0: /opt/homebrew/Cellar/node@16/16.16.0/bin/node
1: /Users/bobby/dev/script.js
2: hi
3: there
4: devs
```