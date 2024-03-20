
You should use [npm-run-all](https://github.com/mysticatea/npm-run-all) (or `concurrently`, `parallelshell`), because it has more control over starting and killing commands. The operators `&`, `|` are bad ideas because you'll need to manually stop it after all tests are finished.
```
 npm i -D npm-run-all
```

# or 

 ```
yarn add npm-run-all --dev
```

This is an example for protractor testing through npm:

```javascript
scripts: {
  "webdriver-start": "./node_modules/protractor/bin/webdriver-manager update && ./node_modules/protractor/bin/webdriver-manager start",
  "protractor": "./node_modules/protractor/bin/protractor ./tests/protractor.conf.js",
  "http-server": "./node_modules/http-server/bin/http-server -a localhost -p 8000",
  "test": "npm-run-all -p -r webdriver-start http-server protractor"
}
```

`-p` = Run commands in parallel.

`-r` = Kill all commands when one of them finishes with an exit code of zero.

Running `npm run test` will start Selenium driver, start http server (to serve you files) and run protractor tests. Once all tests are finished, it will close the http server and the selenium driver.