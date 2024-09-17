npM
[Vite - Getting Started](https://vitejs.dev/guide/)
1)
```
npm init vite
```
   this will prompt you for project name, and template
or 

2)
``` bash
npm create vite@latest project-name -- --template react 
```

this will prompt you to run - 
								`cd project-name/
                                 ` npm install
                                  `npm run dev`

To use `sass/scss` enter `npm add -D sass`

Remove "style.css" from project and create "style.scss"

Clear main.js code and add "import './style.scss';"

Edit html and scss file and check results 

Use Eslint. Vite relys on strict formating and strict js
Vite also expects spaces between elements(a neatness thing)

If building from multiple .scss files, put all @import file.scss in style.scss


 Its also possible to create to vite.config.js in the root directory of the project. 

    The most basic config file looks like this:

    //vite.config.js
    export default {
        vanilla:'scss/main.css' <!-- UNPROVEN -->
    }
 Note Vite supports using ES modules syntax in the config file even if the project is not using native Node ESM, e.g. type: "module" in package.json. In this case, the config file is auto pre-processed before load.
![[Pasted image 20230816110740.png]]


