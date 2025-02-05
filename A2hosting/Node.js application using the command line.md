
Users familiar with SSH and the bash shell may find the command line process faster and easier than navigating the cPanel interface. To set up a node.js application from the command line, follow these steps:

1. Log in to your account [using SSH](https://www.a2hosting.com/kb/getting-started-guide/accessing-your-account/using-ssh-secure-shell).
2. Create the application with the following command:
     **This didn't work. I had to create it using this** [tutorial](https://www.a2hosting.com/kb/cpanel/cpanel-domain-features/cpanel-domains-tool/#Creatingaddon-domains)
```
cloudlinux-selector create --json --interpreter nodejs --version 11 --app-root ~/greenthecoast.com/ --domain greenthecoast.com --app-uri ~/greenthecoast.com/app

```    
3.  Change to the application directory:  
```sh
 cd ~/app
```    

4.  Open the vi editor and create the _package.json_ file:  
```sh
 vi package.json
```   
5 . press i to change to insert mode and paste the following text into the editor:  
```sh

      {
        "name": "app",
        "version": "1.0.0",
        "description": "My App",
        "main": "app.js",
        "scripts": {
          "test": "echo \"Error: no test specified\" && exit 1"
        },
        "author": "",
        "license": "ISC"
      }
```

6.  Press escape followed by : to enter command mode.
7.  Press x followed by Enter to save and exit the editor.
8. To install npm, type the following command:
```

cloudlinux-selector install-modules --json --interpreter nodejs --user richar65 --app-root ~/greenthecoast.com/app
```
	
**To install packages with npm and do other command-line tasks related to the application, log in using SSH, and then type the following command to enter the virtual environment for the application:** 
```sh

source /home/richar65/nodevenv/greenthecoast.com/20/bin/activate && cd /home/richar65/greenthecoast.com

```    
9. To control the running state of the application, do the following:  
    
    - To stop the application, type the following command:
```sh        
cloudlinux-selector stop --json --interpreter nodejs --app-root ~/app
```    
- To start the application, type the following command:  
```sh   
cloudlinux-selector start --json --interpreter nodejs --app-root ~/app
```    
- To restart (stop and start in one step) the application, type the following command:  
    ```sh
	 cloudlinux-selector restart --json --interpreter nodejs --app-root ~/app 
```

[Get cPanel Hosting](https://www.a2hosting.com/cpanel-hosting/)

### Article Details

- Product: Drive Web Hosting Turbo Web Hosting
- Level: Intermediate

#### Other Articles in This Category

- [PHP PEAR packages](https://www.a2hosting.com/kb/cpanel/cpanel-software/php-pear-packages/)
- [Installing Perl modules](https://www.a2hosting.com/kb/cpanel/cpanel-software/perl-modules/)
- [Changing PHP versions and settings using PHP Selector](https://www.a2hosting.com/kb/cpanel/cpanel-software/changing-php-versions-and-settings-in-cpanel/)
- [Using the Python Selector](https://www.a2hosting.com/kb/cpanel/cpanel-software/using-the-python-selector/)
- [Changing PHP versions and settings using MultiPHP](https://www.a2hosting.com/kb/cpanel/cpanel-software/changing-php-versions-and-settings-using-multiphp/)
- [Optimize Website feature](https://www.a2hosting.com/kb/cpanel/cpanel-software/optimize-website-feature/)
- [Creating a Node.js application with cPanel using the Node.js Selector](https://www.a2hosting.com/kb/cpanel/cpanel-software/create-application-with-nodejs-selector/)
- [Migrating a Node.js application to Node.js Selector](https://www.a2hosting.com/kb/cpanel/cpanel-software/migrating-a-node-js-application-to-node-js-selector/)
- [Node.js application error message: "Cannot GET" URL](https://www.a2hosting.com/kb/cpanel/cpanel-software/node-js-application-error-message-cannot-get-url/)
- [Using the Application Manager to deploy applications with Passenger](https://www.a2hosting.com/kb/cpanel/cpanel-software/using-the-application-manager-to-deploy-applications-with-passenger/)
- [Migrating an existing application from Node.js Selector to a manual installation](https://www.a2hosting.com/kb/cpanel/cpanel-software/migrating-an-existing-application-from-node.js-selector-to-a-manual-installation/)
- [Migrating a Next.js application to the Node.js Selector in cPanel](https://www.a2hosting.com/kb/cpanel/cpanel-software/migrating-a-next.js-application-to-the-node.js-selector-in-cpanel/)

Show More

#### Related Articles

- [Node.js application error message: “Cannot GET” URL](https://www.a2hosting.com/kb/cpanel/cpanel-software/node-js-application-error-message-cannot-get-url/)
- [Connecting to MySQL using Node.js](https://www.a2hosting.com/kb/developer-corner/mysql/connecting-to-mysql-using-node-js/)

Show More

- [SUGGEST AN ARTICLE](https://my.a2hosting.com/?m=a2_suggestionbox)

#### Grow Your Web Business

Subscribe to receive weekly cutting edge tips, strategies, and news you need to grow your web business.

No charge. Unsubscribe anytime.