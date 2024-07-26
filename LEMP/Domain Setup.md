

On Ubuntu, Nginx has one server block enabled by default and is configured to serve documents out of a directory at `/var/www/html`. While this works well for a single site, it can become difficult to manage if you are hosting multiple sites. Instead of modifying `/var/www/html`, we’ll create a directory structure within `/var/www` for the **your_domain** website, leaving `/var/www/html` in place as the default directory to be served if a client request doesn’t match any other sites.

Create the root web directory for **your_domain** as follows:

```
sudo mkdir /var/www/your_domain

```

Next, assign ownership of the directory with the `$USER` environment variable, which will reference your current system user:

```
sudo chown -R $USER:$USER /var/www/your_domain

```

Then, open a new configuration file in Nginx’s `sites-available` directory using your preferred command-line editor. Here, we’ll use `nano`:

```
sudo nano /etc/nginx/sites-available/your_domain

```

This will create a new blank file. Insert the following bare-bones configuration:

/etc/nginx/sites-available/your_domain

```
server {
    listen 80;
    server_name your_domain www.your_domain;
    root /var/www/your_domain;

    index index.html index.htm index.php;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php8.1-fpm.sock;
     }

    location ~ /\.ht {
        deny all;
    }

}
```

Here’s what each of these directives and location blocks do:

- `listen` — Defines what port Nginx will listen on. In this case, it will listen on port `80`, the default port for HTTP.
- `root` — Defines the document root where the files served by this website are stored.
- `index` — Defines in which order Nginx will prioritize index files for this website. It is a common practice to list `index.html` files with higher precedence than `index.php` files to allow for quickly setting up a maintenance landing page in PHP applications. You can adjust these settings to better suit your application needs.
- `server_name` — Defines which domain names and/or IP addresses this server block should respond for. **Point this directive to your server’s domain name or public IP address.**
- `location /` — The first location block includes a `try_files` directive, which checks for the existence of files or directories matching a URL request. If Nginx cannot find the appropriate resource, it will return a 404 error.
- `location ~ \.php$` — This location block handles the actual PHP processing by pointing Nginx to the `fastcgi-php.conf` configuration file and the `php8.1-fpm.sock` file, which declares what socket is associated with `php8.1-fpm`.
- `location ~ /\.ht` — The last location block deals with `.htaccess` files, which Nginx does not process. By adding the `deny all` directive, if any `.htaccess` files happen to find their way into the document root, they will not be served to visitors.

When you’re done editing, save and close the file. If you’re using `nano`, you can do so by pressing `CTRL+X` and then `Y` and `ENTER` to confirm.

Activate your configuration by linking to the configuration file from Nginx’s `sites-enabled` directory:

```
sudo ln -s /etc/nginx/sites-available/your_domain /etc/nginx/sites-enabled/

```

Then, unlink the default configuration file from the `/sites-enabled/` directory:

```
sudo unlink /etc/nginx/sites-enabled/default

```

**Note**: If you ever need to restore the default configuration, you can do so by recreating the symbolic link, like the following:

```
sudo ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/

```

This will tell Nginx to use the configuration next time it is reloaded. You can test your configuration for syntax errors by running the following:

```
sudo nginx -t

```

If any errors are reported, go back to your configuration file to review its contents before continuing.

When you are ready, reload Nginx to apply the changes:

```
sudo systemctl reload nginx

```

Your new website is now active, but the web root `/var/www/==your_domain==` is still empty. Create an `index.html` file in that location so that you can test that your new server block works as expected:

```
nano /var/www/your_domain/index.html

```

Include the following content in this file:

/var/www/your_domain/index.html

```
<html>
  <head>
    <title>your_domain website</title>
  </head>
  <body>
    <h1>Hello World!</h1>

    <p>This is the landing page of <strong>your_domain</strong>.</p>
  </body>
</html>
```

Now go to your browser and access your server’s domain name or IP address, as listed within the `server_name` directive in your server block configuration file:

```
http://server_domain_or_IP
```

You’ll receive a page like the following:

![Nginx server block](https://assets.digitalocean.com/articles/lemp_ubuntu2004/landing_page.png)

If you receive this page, it means your Nginx server block is working as expected.

You can leave this file in place as a temporary landing page for your application until you set up an `index.php` file to replace it. Once you do that, remember to remove or rename the `index.html` file from your document root, as it would take precedence over an `index.php` file by default.

Your LEMP stack is now fully configured. In the next step, you’ll create a PHP script to test that Nginx is in fact able to handle `.php` files within your newly configured website.