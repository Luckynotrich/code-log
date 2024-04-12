# [How to Update NPM Dependencies](https://www.freecodecamp.org/news/how-to-update-npm-dependencies/)

## How to Use the `npm outdated` Command

```bash
npm outdated
```

This command will check every installed dependency and compare the current version with the latest version in the [npm registry](https://www.npmjs.com/). It is printed out into a table outlining available versions.

With this method, to install updates for every package, you just need to run:

```
npm update
```

Keep in mind that with `npm update` it will never update to a major breaking-changes version. It updates the dependencies in package.json and package-lock.json. It will use the "wanted" version.

To obtain the "latest" version append `@latest`to individual installs, for example `npm install react@latest`.

## How to Use `npm-check-updates`

For an advanced and customizable upgrading experience, I'd recommend [`npm-check-updates`](https://www.npmjs.com/package/npm-check-updates). This package can do everything `npm outdated` and `npm upgrade` can do with some added customization options. It does require a package installation, however.

To get started, install the [`npm-check-updates`](https://www.npmjs.com/package/npm-check-updates) package globally:

```
npm install -g npm-check-updates
```

Then, run `ncu` to display packages to upgrade. Similar to `npm outdated` it will not apply any changes.

```
ncu
Checking package.json
[====================] 12/12 100%

 @testing-library/user-event    ^13.5.0  →  ^14.2.1
 @types/jest                    ^27.5.2  →  ^28.1.4
 @types/node                  ^16.11.42  →  ^18.0.1

Run ncu -u to upgrade package.json
```

To upgrade dependencies, you just need to run:

```
ncu --upgrade

// or 
ncu -u
```
