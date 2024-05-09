# a2-node-instructions

Create the application with the following command: 
##### none of these cloudlinux-selectors worked during `futureonreview.com` startup. I used the GUI to create a new domain and then create an app. 

cloudlinux-selector example
```bash

cloudlinux-selector create --interprete=nodejs --json --app-root=<USER_NAME> --app-uri=<APP_NAME> --app-mode=develompent --version=<VERSION> --domain=<DOMAIN>

```

a2 hosting example
```bash

cloudlinux-selector create --json --interpreter nodejs --version 11 --app-root app --domain example.com --app-uri app

```
 
 Newledo setup
```sh

cloudlinux-selector create --json --interpreter nodejs --version 16.17.1 --app-mode=develompent --app-root newledohub.org --domain newledohub.org --app-uri newledo_back

```
 
  'future on review' setup
  ```shell
  
cloudlinux-selector create --json --interpreter nodejs --version 16.20.2 --app-mode=develompent --app-root futureself --domain futureonreview.com --app-uri futureself 

```

cd into app
```bash

cd new-app

```

Create a package.json
  Insert the contents of package.json

```js
{
  "name": "futureonreview",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "axios": "^1.6.8",
    "bcrypt": "^5.1.1",
    "connect-pg-simple": "^9.0.1",
    "cors": "^2.8.5",
    "date-and-time": "^3.1.1",
    "dotenv": "^16.4.5",
    "ejs": "^3.1.9",
    "express": "^4.19.2",
    "express-flash": "^0.0.2",
    "express-promise-router": "^4.1.1",
    "express-session": "^1.18.0",
    "http-proxy-middleware": "^3.0.0",
    "moment": "^2.30.1",
    "multiparty": "^4.2.3",
    "passport": "^0.7.0",
    "passport-local": "^1.0.0",
    "pg": "^8.11.5",
    "uuid": "^9.0.1",
    "web-vitals": "^3.5.2"
  },
  "devDependencies": {
    "jest": "^29.7.0",
    "open": "^10.1.0"
  },
  "scripts": {
    "start": "node app.js",
    "safe": "node server_https.js",
    "check-env": "node -e 'console.log(process.env)' | grep npm",
    "test": "jest"
  },
  "eslintConfig": {
    "extends": [
      "react-app",
      "react-app/jest"
    ]
  },
  "browserslist": {
    "production": [
      ">0.2%",
      "not dead",
      "not op_mini all"
    ],
    "development": [
      "last 1 chrome version",
      "last 1 firefox version",
      "last 1 safari version"
    ]
  }
}

```

Edit it to match your app and upload it to app directory

  

To install npm, type the following command:
```js

cloudlinux-selector install-modules --json --interpreter nodejs --user richar65 --app-root futureonreview.com
```


To install packages with npm and do other command-line tasks 
related to the application, log in using SSH, and then type the
 following command to enter the virtual environment for the application: 
```shell

source /home/richar65/nodevenv/futureonreview.com/16/bin/activate && cd /home/richar65/futureonreview.com

```
 enter: 

`deactivate` - to return from virtual environment 
To control the running state of the application, do the following:

  To stop the application, type the following command:
```bash

cloudlinux-selector stop --json --interpreter nodejs --app-root ~/futureonreview.com

```
  

To start the application, type the following command:
```bash
cloudlinux-selector start --json --interpreter nodejs --app-root ~/futureonreview.com
```
  
To restart (stop and start in one step) the application, type the following command:
```bash
cloudlinux-selector restart --json --interpreter nodejs --app-root ~/futureonreview.com
```
  
* Get cPanel Hosting
 * Article Details
 
 * Product: Drive Web Hosting Turbo Web Hosting
 * Level: Intermediate

* Other Articles in This Category
* Optimize Website feature
* Creating a Node.js application with cPanel using the Node.js Selector
* Migrating a Node.js application to Node.js Selector
* Node.js application error message: "Cannot GET" URL

* Show More
* Related Articles

* Node.js application error message: “Cannot GET” URL
* Connecting to MySQL using Node.js

* Show More
* SUGGEST AN ARTICLE
* Grow Your Web Business

* Subscribe to receive weekly cutting edge tips, strategies, and news you need to grow your web business.
* No charge. Unsubscribe anytime.
```bash
cloudlinux-selector read-config --json --interpreter nodejs --user user1 --app-root app_dir/app1 --config-file package.json
```
```bash
cloudlinux-selector create --interprete=nodejs --json --app-root=<USER_NAME> --app-uri=<APP_NAME> --app-mode=develompent --version=<VERSION> --domain=<DOMAIN>
```