
We can add any new script under the scripts object. Just remove the default one (named test) and add the following:

json
```
"scripts": {
  "sass-dev": "sass --watch --update --style=expanded assets/scss:assets/css",
  "sass-prod": "sass --no-source-map --style=compressed assets/scss:assets/css"
}
```

As you see, we set up two scripts to compile Sass:

    Dev: which is for development purposes. It isn’t compressed, has a source map and a watcher (to run until we stop it and watch for changes).
    Prod: which is making our production code. It is compressed, doesn’t have a source map, and runs only once.

What is a source map? A particular file that allows the browser to map back from the processed, concatenated files to the original ones. It is helpful because we can see the original file names when we debug the CSS in the developer tools.

Our project’s folder structure (should) look like this:
```
sass-compile/
├── assets/
│   ├── css/
│   │   └── main.css
│   └── scss/
│       ├── assets/
│       │   ├── _footer.scss
│       │   └── _header.scss
│       └── main.scss
├── node-modules/
└── package.json
```

We compile our Sass files from the scss to the css folder. We don’t have to specify file names explicitly (necessarily); the script will watch for all translatable files (the ones which don’t have a _ prefix).


ALL SCRIPTS

npm install::
first initialize npm with package.json
```
npm init
```
then install the node sass
```
npm install node-sass --save-dev
```
if already have the package.json initialized with node-sass then just run
```
npm install
```

for install live server globally
```
npm install live-server -g
```
for watching the css changes
```
"watch:sass": "node-sass sass/main.scss css/main.css -w"
```
for run live server
```
"devserver" : "live-server"
```
for run all npm scripts

first install [npm-run-all](https://www.npmjs.com/package/npm-run-all)
```
npm install npm-run-all --save-dev
```
then the scripts
```
"start" : "npm-run-all --parallel devserver watch:sass"
```
then build process

first compile the sass to compile css file
```
"compile:sass": "node-sass sass/main.scss css/main.comp.css"
```
then install the concat package
```
npm install [concat](https://www.npmjs.com/package/concat) --save-dev
```
then concat the css file
```
"concat:css": "concat -o css/main.concat.css css/main.css"
```
the add prefixer for all browser

first install [autoprefixer](https://www.npmjs.com/package/autoprefixer) package
```
npm install autoprefixer --save-dev
```
then run to autoprefixer we need postcss
```
npm install postcss-cli --save-dev
```
then add prefix css
```
"prefix:css": "postcss --use autoprefixer -b 'last 10 versions' css/main.concat.css -o css/main.prefix.css",
```
then compress all the css file
```
"compress:css": "node-sass css/main.concat.css --output-style compressed"
```
the build script
```
"build:css" : "npm-run-all compile:sass concat:css prefix:css compress:css"
```

it will look like
```
"watch:sass": "node-sass sass/main.scss css/main.css -w",
    "compile:sass": "node-sass sass/main.scss css/main.comp.css",
    "concat:css": "concat -o css/main.concat.css css/main.css",
    "prefix:css": "postcss --use autoprefixer -b 'last 10 versions' css/main.concat.css -o css/main.prefix.css",
    "compress:css": "node-sass css/main.concat.css --output-style compressed",
    "build:css" : "npm-run-all compile:sass concat:css prefix:css compress:css"
```

then run

 `npm run build:css'
