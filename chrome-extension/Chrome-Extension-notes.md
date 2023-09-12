<!-- notes.md -->
# Chrome-Extension Notes
Also see: 
### [Development basics](https://developer.chrome.com/docs/extensions/mv3/getstarted/development-basics/) ###

and
### [Distributing your extension](https://developer.chrome.com/docs/extensions/mv3/getstarted/extensions-101/#distribution) ###
### Basic steps to creating an extension
1. Create manifest.json file.
2. Add icons to distinguish it from other extensions.
3. Add index.html file.
4. Add index.js
5. Add style.css file for styling.
6. Include ' "content_scripts":[{ index.html, index.js, style.css}] ' in manifest.json.
7. Click extension icon on chrome nav-bar and select Manage Extensions.
8. Toggle developer mode to "On".
9. Click "Load unpacked"

## [Extension files](https://developer.chrome.com/docs/extensions/mv3/getstarted/extensions-101/#extension-files) ##
Extensions contain different files, depending on the functionality provided. The following are some of the most frequently used files:

### The manifest ###
The extension's manifest is the only required file that must have a specific file name: manifest.json . It also has to be located in the extension's root directory. The manifest records important metadata, defines resources, declares permissions, and identifies which files to run in the background and on the page.
### The service worker ###
The extension service worker handles and listens for browser events. There are many types of events, such as navigating to a new page, removing a bookmark, or closing a tab. It can use all the Chrome APIs, but it cannot interact directly with the content of web pages; that’s the job of content scripts.
### Content scripts ###
Content scripts execute Javascript in the context of a web page. They can also read and modify the DOM of the pages they're injected into. Content Scripts can only use a subset of the Chrome APIs but can indirectly access the rest by exchanging messages with the extension service worker.
### The popup and other pages ###
An extension can include various HTML files, such as a popup, an options page, and other HTML pages. All these pages have access to Chrome APIs.

__________
### Manifest V3 is an API that Google will use in its Chrome browser. Manifest V3 introduces significant changes to the rules for extensions, some of which will be the new mainstay from V2.

1. The transition has been ongoing since 2018.
2. Manifest V3 will officially begin rolling out in January 2023.
3. By June 2023 extensions that run Manifest V2 will no longer be available on the Chorome Web site.
4. Extension that don comply with the new rules intruoduced in Manifest V3 will eventually be removed from the Chrom Wev Store, possibly by January 2024.


Google extensions will no longer be allowed to rely on code in the cloud.

It also forces extensions to request permission from Google for the changes they can implement on the browser.

### Key Difference Summary
1. Service workers replace background pages(scripts) in Manifiest V3.
2. Network request modification is handled with the new declarative NetRequest API.
3. In Manifest V3, extensions can only execute JavaScript that is included within their package and cannot use remotely-hosted code.
4. Manifest V3 introduces promise support to many methods, though callbacks are still supported as an alternative.
5. Host permissions in Manifes V3 are a separate element and must be specified in the "host_permissions" field.
6. The content security policy in Manifest V3 is an object with members representing alternative content security policy (CSP) contexts, rather than a string as it was in Man V2.

```
// Manifest V3
{
  "manifest_version": 3,
  "name": "Shane's Extension",
  "version": "1.0",
  "description": "A simple extension that changes the background of a webpage to Shane's face.",
  "background": {
    "service_worker": "background.js"
  },
  "action": {
    "default_popup": "popup.html"
  },
  "permissions": [ "activeTab", ],
  "host_permissions": [ "<all_urls>" ]
  ```
  Source :
  
  `https://css-tricks.com/how-to-transition-to-manifest-v3-for-chrome-extensions/`


  ## Displaying a webpage in an iframe

  An iframe or inline frame is used to display external objects including other web pages within a web page. An iframe pretty much acts like a mini web browser within a web browser. Also, the content inside an iframe exists entirely independent from the surrounding elements.

The basic syntax for adding an iframe to a web page can be given with:

`<iframe src="URL"></iframe>`

### Setting Width and Height of an iFrame

`<iframe src="hello.html" width="400" height="200"></iframe> `

### Using CSS to set width and height

`<iframe src="hello.html" style="width: 400px; height: 200px;"></iframe>`

Note: The width and height attribute values are specified in pixels by default, but you can also set these values in percentage, such as 50%, 100% and so on. The default width of an iframe is 300 pixels, whereas the default height is 150 pixels.

### Removing Default Frameborder

`<iframe src="hello.html" style="border: none;"></iframe>`

### Using an iFrame as Link Target

An iframe can also be used as a target for the hyperlinks.

An iframe can be named using the name attribute. This implies that when a link with a target attribute with that name as value is clicked, the linked resource will open in that iframe.

`<iframe src="demo-page.html" name="myFrame"></iframe>`
`<p><a href="https://www.tutorialrepublic.com" target="myFrame">Open TutorialRepublic.com</a></p>` 

Source: [Tutorial Republic] (https://www.tutorialrepublic.com/html-tutorial/html-iframes.php)

## Targeting tabs
### How to open a webpage in a same tab in an iframe
`<a href="localhost:5000" target="_self>`

### Open the linked document in the parent frame
`<a href="localhost:5000" target="_parent>`

### Opens the linked document in the named iframe
`<a href="localhost:5000" target="framename">`

## [Chrome.tabs](https://developer.chrome.com/docs/extensions/reference/tabs/)
**Description**
:   Use the chrome.tabs API to interact with the browser's tab system. You can use this API to create, modify, and rearrange tabs in the browser.

### # [Permissions](https://developer.chrome.com/docs/extensions/reference/tabs/#perms) ###

Most features do not require any permissions to use. For example: creating a new tab, reloading a tab, navigating to another URL, etc.

There are three permissions developers should be aware of when working with the Tabs API.

**The "tabs" permission**

This permission does not give access to the chrome.tabs namespace. Instead, it grants an extension the ability to call [tabs.query()](https://developer.chrome.com/docs/extensions/reference/tabs/#method-query) against four sensitive properties on [tabs.Tab](https://developer.chrome.com/docs/extensions/reference/tabs/#type-Tab) instances: url, pendingUrl, title, and favIconUrl.

**Host permissions**

[Host permissions](https://developer.chrome.com/docs/extensions/mv3/match_patterns/) allow an extension to read and query a matching tab's four sensitive tabs. Tab properties. They can also interact directly with the matching tabs using methods such as [tabs.captureVisibleTab()](https://developer.chrome.com/docs/extensions/reference/tabs/#method-captureVisibleTab), [tabs.executeScript()](https://developer.chrome.com/docs/extensions/reference/tabs/#method-executeScript), [tabs.insertCSS()](https://developer.chrome.com/docs/extensions/reference/tabs/#method-insertCSS), and [tabs.removeCSS()](https://developer.chrome.com/docs/extensions/reference/tabs/#method-removeCSS).

**The "activeTab" permission**

[activeTab](https://developer.chrome.com/docs/extensions/mv3/manifest/activeTab/) grants an extension temporary host permission for the current tab in response to a user invocation. Unlike host permissions, activeTab does not trigger any warnings.

Manifest
The following are examples of how to declare each permission in the manifest:

Tabs permission
```
{
  "name": "My extension",
  ...
  "permissions": [
    "tabs"
  ],
  ...
}
```
Host Permissions
```
 {
  "name": "My extension",
  ...
  "host_permissions": [
    "http://*/*",
    "https://*/*"
  ],
  ...
}
```

activeTab permission
```
{
  "name": "My extension",
  ...
  "permissions": [
    "activeTab"
  ],
  ...
}
```

## [Use cases](https://developer.chrome.com/docs/extensions/reference/tabs/#examples) ##

### [Opening an extension page in a new tab](https://developer.chrome.com/docs/extensions/reference/tabs/#opening-an-extension-page-in-a-new-tab) ###

### [Get the current tab](https://developer.chrome.com/docs/extensions/reference/tabs/#get-the-current-tab)

### [Mute the specified tab](https://developer.chrome.com/docs/extensions/reference/tabs/#move-the-current-tab-to-the-first-position-when-clicked) ###

### [Move the current tab to the first position when clicked](https://developer.chrome.com/docs/extensions/reference/tabs/#move-the-current-tab-to-the-first-position-when-clicked)

### [Extension examples](https://developer.chrome.com/docs/extensions/reference/tabs/#more-samples) ###

## [chrome.scripting](https://developer.chrome.com/docs/extensions/reference/scripting/#files) ##