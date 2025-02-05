
## [Getting Started with Node.js and Mocha](https://semaphoreci.com/community/tutorials/getting-started-with-node-js-and-mocha)

We will install our testing framework, and an expectation library called [Chai](http://chaijs.com/) that serves as a nice replacement for [Node’s standard `assert` function](http://nodejs.org/api/assert.html).

```bash
$ npm install --save mocha chai
```

Note that we are using the `--save` option to automatically save these dependencies in our `package.json` file.

During the server testing phase, we will need a way to send HTTP requests. This tutorial suggests a deprecated library called Request. I substituted Axios
```
npm i axios
```

Finally, we will also need the [Express](http://expressjs.com/) package that defines a simple DSL (domain-specific language) for routing and handling incoming HTTP requests:

```bash
$ npm install --save express
```
At this point, we are finished with the bootstrap process. However, we will configure one more thing to make running the test suite easier. We will set up the `test` command inside the `package.json` file, in order to run our tests simply by executing `npm test` from the command line.

The following command is used to invoke the Mocha binary installed locally in the `./node_modules` directory:

```bash
npx mocha --reporter spec
```

Note: This command seem's to expect a test: `Error: No test files found`

Note that we have many different report formats to choose from. You can explore [other reporters on Mocha’s official website](http://mochajs.org/#reporters).

I would choose  to use markdown
`npx mocha --reporter markdown`

There is [mocha-multi-reporters](https://www.npmjs.com/package/mocha-multi-reporters) that allows for multiple reporters
```
npm install mocha-multi-reporters --save-dev
```

Next, we will update the `test` command in `package.json` to contain the above command. That file should now look like this:

```json
{
  "name": "converter",
  "version": "0.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "mocha --reporter spec",
    "mark": "mocha --reporter markdown"
  },
  "author": "",
  "license": "ISC"
}
```

## Describing the Color Converter
`~/webdev/Mocha-nodejs-semephore-Igor-S/converter`\