### [Hayley Codes - Deploying a Node.js site to Vultr](https://dev.to/hayleycodes/deploying-a-node-js-site-to-vultr-j8d)
Cloud Compute                                                                       $2.50/mo
Server Size 25 GB `SSD,` 1 `vCPU`  1 GB memory, 1 TB BW + $5/mo
													   **total $7.50/mo**
#### from Control Panel
- Select to install Ubuntu 22.05 from 
- Disable Backups
- enable IPv6
- Create Server Host name
-  Click Deploy now
#### In CL:
- copy IP address
- enter `ssh root@your.ip.add.here` in CL
- you will be prompted for you password
#### Update and install Nginx:
- `Sudo apt-get update`
- `sudo apt-get install nginx`
- If you see pending `kernal update` popup, tab through
#### Configure `Ufw`
- `sudo ufw allow 'Nginx HTTP'`
- `sudo ufw allow 'OpenSSH`
- `sudo ufw enable`
#### Starting `nginx`
- `systemctl status nginx`
- you should see `active (running)`
#### Restarting `nginx`
- `sudo systemctl restart nginx`
#### Installing `Certbot` 
==`Certbot` and Let's Encrypt are closely related, but not the same==. Let's Encrypt is a free, automated, and open certificate authority (CA) that provides digital certificates for enabling `HTTPS` on websites. `Certbot`, on the other hand, is a specific software tool developed by the Electronic Frontier Foundation (EFF) to automate the process of obtaining and installing Let's Encrypt certificates. Essentially, you use `Certbot` to interact with Let's Encrypt's service and get your website secured with `HTTPS`
- `sudo apt install certbot python3-certbot-nginx
- `sudo nano /etc/nginx/sites-available/default
- scroll down to server_name attribute

![[Pasted image 20250630152539.png]]

#### Replace the underscore with your domain name
To configure Nginx to handle multiple domains, you need to create separate `server` blocks within your Nginx configuration file, each with a unique `server_name` directive that corresponds to a domain or subdomain. These blocks specify how Nginx should respond to requests for each domain
1. Create [Server Blocks](https://www.google.com/search?client=ubuntu-sn&channel=fs&cs=1&sca_esv=45911bb8ff09c0be&sxsrf=AE3TifMF3aSMJYXENanLHI7OVFRrG8WO2Q%3A1751321772762&q=Server+Blocks&sa=X&ved=2ahUKEwi4ytCAlpqOAxVJIjQIHbGGMnAQxccNegQIDBAC&mstk=AUtExfDZINvyNRkZsU63Bdwm4xf1oANneX4vgxQIoNhsYTnP3tNg8XgMGNj7g1qj0pdWp6NBllNhRn_IbR-Tx0Puu8GRbd_sWHv5AAshqzpRwr0Crr6Zo7Du_JeOTmg1rrom79uitV8VKI5zuvU1aYRR-vzq6uxo9aa9w8hBrP7ywOiNQD0&csui=3):
- Navigate to the Nginx configuration directory, typically `/etc/nginx/sites-available`. 
- Create a new configuration file for each domain (e.g., `domain1.com.conf`, `domain2.com.conf`). 
- Open each file in a text editor and define the server block. 

Example Server Block Configuration:
```sh
server {
  listen 80;
  server_name domain1.com www.domain1.com;
  root /var/www/domain1;
  index index.html;

  location / {
    try_files $uri $uri/ =404;
  }
}

server {
  listen 80;
  server_name domain2.com www.domain2.com;
  root /var/www/domain2;
  index index.html;

  location / {
    try_files $uri $uri/ =404;
  }
}
```

#### Explanation:
- `listen 80`: Specifies the port (80 for HTTP) that the server block listens on.
- `server_name`: Defines the domain names or subdomains that this block handles. You can list multiple names separated by spaces, including `www` versions.
- `root`: Specifies the document root directory for the website.
- `index`: Specifies the default index file (e.g., `index.html`).
- `location /`: Defines how to handle requests for the root path (`/`). 

#### 2. [Enable](https://www.google.com/search?client=ubuntu-sn&channel=fs&cs=1&sca_esv=45911bb8ff09c0be&sxsrf=AE3TifMF3aSMJYXENanLHI7OVFRrG8WO2Q%3A1751321772762&q=Enable&sa=X&ved=2ahUKEwi4ytCAlpqOAxVJIjQIHbGGMnAQxccNegQIPRAC&mstk=AUtExfDZINvyNRkZsU63Bdwm4xf1oANneX4vgxQIoNhsYTnP3tNg8XgMGNj7g1qj0pdWp6NBllNhRn_IbR-Tx0Puu8GRbd_sWHv5AAshqzpRwr0Crr6Zo7Du_JeOTmg1rrom79uitV8VKI5zuvU1aYRR-vzq6uxo9aa9w8hBrP7ywOiNQD0&csui=3) Server Blocks:
- Create symbolic links from the `sites-available` directory to the `sites-enabled` directory (e.g., `/etc/nginx/sites-enabled`).
- Use the `ln -s` command:
#### Verify the sites-available default
- `sudo nginx -t`
- `sudo systectl reload nginx`

#### Modify firewall rules
- `sudo ufw allow 'Nginx full'`
- `sudo ufw delete allow 'Nginx HTTP'`
![[Pasted image 20250630163158.png]]
#### Go to domain registrar in 'name server section'
- Find domain name
- Find `DNS`
- Add two records
![[Pasted image 20250630154038.png]]
Where the IP address is the same as above** (`your.ip.add.here`) not sure why the dot at the end of 2nd record--- ^

#### At the terminal:
- `sudo  certbot --nginx -d your-domain.name -d www.your-domain.name`

#### `Cd` to the root directory
```sh
$ cd ~/
```
### Installation Instructions (DEB)
**Node.js 23.x**:

##### [Using Ubuntu (Node.js 23)](https://github.com/nodesource/distributions?tab=readme-ov-file#using-ubuntu-nodejs-23)

Before you begin, ensure that `curl` is installed on your system. If `curl` is not installed, you can install it using the following command:
```sh
sudo apt-get install -y curl
```

1.  **Download the setup script:**
```sh
curl -fsSL https://deb.nodesource.com/setup_23.x -o nodesource_setup.sh
```

2.  **Run the setup script with sudo:**
```sh
sudo -E bash nodesource_setup.sh
```

3.  **Install Node.js:**
```sh
sudo apt-get install -y nodejs
```

4. **Verify the installation:**
```sh
node -v
```