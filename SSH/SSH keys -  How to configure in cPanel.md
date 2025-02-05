# How to configure SSH keys using cPanel

This article describes how to create and deploy SSH keys using cPanel. With SSH keys, you can automate logins to your A2 Hosting account, or use two-factor authentication for increased security.

This article describes how to configure SSH keys using cPanel. If your hosting account does not include cPanel, or if you want to use the command line to configure SSH keys, please see [this article](https://www.a2hosting.com/kb/getting-started-guide/accessing-your-account/using-ssh-keys).

Table of Contents

- [Using SSH keys](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/configuring-ssh-keys-with-cpanel/#Using-SSH-keys)
- [Configuring SSH keys in cPanel](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/configuring-ssh-keys-with-cpanel/#Configuring-SSH-keys-in-cPanel)
    - [Option #1: Generating a new key](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/configuring-ssh-keys-with-cpanel/#Option-1.3A-Generating-a-new-key)
    - [Option #2: Importing an existing key](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/configuring-ssh-keys-with-cpanel/#Option-2.3A-Importing-an-existing-key)
- [Connecting to your account using the SSH keys](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/configuring-ssh-keys-with-cpanel/#Connecting-to-your-account-using-the-SSH-keys)
    - [Windows operating systems](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/configuring-ssh-keys-with-cpanel/#Windows-operating-systems)
        - [Using PuTTY](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/configuring-ssh-keys-with-cpanel/#Using-PuTTY)
        - [Using the native Windows SSH client](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/configuring-ssh-keys-with-cpanel/#Using-the-native-Windows-SSH-client)
    - [Mac OS X and Linux operating systems](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/configuring-ssh-keys-with-cpanel/#Mac-OS-X-and-Linux-operating-systems)

#### Using SSH keys

When you log in to your account interactively using an SSH client as described in [this article](https://www.a2hosting.com/kb/getting-started-guide/accessing-your-account/using-ssh-secure-shell), you must enter a password every time. But what if you want to run an automated process? Perhaps you want to automatically download a database backup at certain times to your local computer. In this scenario, you don't want to have to manually type your SSH password every time the backup process runs.

Or what if you want to allow multiple users to transfer files securely using SFTP, as described in [this article](https://www.a2hosting.com/kb/getting-started-guide/accessing-your-account/setting-up-sftp-access-for-multiple-users)? You would need to give them your cPanel password, which would give them complete access to your account.

You can solve these problems by using SSH keys to connect to your account. SSH keys enable your computer to log in to your A2 Hosting account automatically without you typing a password. To use SSH keys, you must first create a public key and private key (also known as a key pair). The client's private key stays on your local computer, while the public key resides on the A2 Hosting server.

Alternatively, you can also create SSH keys and protect them with a passphrase for two-factor authentication. Although this configuration does not enable automatic logins, it does provide an extra layer of security, because you must have the correct key file _and_ know the correct passphrase to access the account.

#### Configuring SSH keys in cPanel

When you configure SSH keys in cPanel, you can create a new key pair, or import an existing key.

##### Option #1: Generating a new key

To generate a new SSH key pair for your account, follow these steps:

1. Log in to cPanel.
    
    If you do not know how to log in to your cPanel account, please see [this article](https://www.a2hosting.com/kb/cpanel/getting-started-with-cpanel/accessing-cpanel).
    
2. Open the SSH Access tool:
    - If you are using the Jupiter theme, on the Tools page, in the Security section, click SSH Access:
        
        ![](https://www.a2hosting.com/images/uploads/knowledgebase_images/kb-cpanel-jupiter-SSHaccess.png)
        
 
        
3. On the SSH Access page, under Manage SSH Keys, click Manage SSH Keys.
4. Click Generate a New Key.
5. Confirm the Key Name is set to id_rsa.
6. In the Key Password and Reenter Password text boxes, type a password for the key. Alternatively, you can click Password Generator and cPanel generates a strong password for you.
7. Confirm the Key Type is set to RSA.
8. Confirm the Key Size is set to 2048.
9. Click Generate Key. cPanel generates the public and private keys and saves them in the _/home/username/.ssh_ directory, where _username_ represents your A2 Hosting account username.
10. Click Go Back.
11. Under Public Keys, locate the name of the key you just created. Under Actions, click Manage.
12. Click Authorize, and then click Go Back. To connect to your account using the new key, read **Connecting to your account using the SSH keys** below.

##### Option #2: Importing an existing key

If you have already generated SSH keys for your account and want to re-use them, you can use cPanel to import them. To do this, follow these steps:

1. Log in to cPanel.
    
    If you do not know how to log in to your cPanel account, please see [this article](https://www.a2hosting.com/kb/cpanel/getting-started-with-cpanel/accessing-cpanel).
    
2. Open the SSH Access tool:
    - If you are using the Jupiter theme, on the Tools page, in the Security section, click SSH Access:
        
        ![](https://www.a2hosting.com/images/uploads/knowledgebase_images/kb-cpanel-jupiter-SSHaccess.png)
        
   
3. On the SSH Access page, under Manage SSH Keys, click Manage SSH Keys.
4. Click Import Key.
5. In the Choose a name for this key (defaults to id_dsa) text box, type the name for the key.  
    
    If your server runs OpenSSH version 7 or later, for security reasons you cannot use DSA keys. (To determine the OpenSSH version installed on your server, type ssh -V at the command prompt.) You should use RSA keys instead.
    
6. Under Paste the public key into the following text box, paste the text of the public key into the text box.
7. Click Import. cPanel imports the key.
8. Click Back to Manage Keys.
9. Under Public Keys, locate the name of the key you just imported. Under Actions, click Manage.
10. Click Authorize, and then click Go Back. To connect to your account using the new key, read **Connecting to your account using the SSH keys** below.

#### Connecting to your account using the SSH keys

Before you can connect to your account, you must deploy the private key to your local computer (unless you imported a public key into cPanel, in which case you presumably already have the private key on your computer). To do this, follow these steps:

1. Log in to cPanel.
    
    If you do not know how to log in to your cPanel account, please see [this article](https://www.a2hosting.com/kb/cpanel/getting-started-with-cpanel/accessing-cpanel).
    
2. Open the SSH Access tool:
    - If you are using the Jupiter theme, on the Tools page, in the Security section, click SSH Access:
        
        ![](https://www.a2hosting.com/images/uploads/knowledgebase_images/kb-cpanel-jupiter-SSHaccess.png)
        
        
3. On the SSH Access page, under Manage SSH Keys, click Manage SSH Keys.
4. On the SSH Access page, under Private Keys, locate the name of the key you created, and then click View/Download.
5. Click Download Key, and then save the _id_rsa_ file on your local computer in the _/home/username/.ssh_ directory. Replace _username_ with your own username.

At this point, you have created the SSH key pair and deployed the private key to your local computer. You are now ready to connect to your SSH account using the keys.

To connect to your SSH account using the keys, follow these steps:

1. Open a terminal window. The procedure to do this depends on the operating system and desktop environment.
    - On Mac OS X, click Applications, click Utilities, and then click Terminal.
2. At the command prompt, type the following command. Replace _username_ with your A2 Hosting username, and replace _example.com_ with your site's domain name:
    

`ssh -p 7822 _username_@_example.com_`

In this command, we explicitly specify the port number, the username, and the hostname. However, you can also define the settings for a remote host in your _~/.ssh/config_ file as follows:
```
Host _example_
    Hostname _example.com_
    Port 7822
    User _username_
```
The **Host** value can be any name you want; it is simply a label for the other settings. The **Hostname** value is the remote host you want to access, the port number is 7822, and the **User** value specifies your A2 Hosting account username. With this configuration defined, you can connect to the account by simply using the **Host** value. You do not have to type the port number, username, and hostname each time. The following command demonstrates how to do this:

1. ssh example
    
2. The SSH client should connect without asking you to type your account password. If you set a passphrase for the key, however, you must type the key passphrase.
    
    _If you are using a passphrase,_ you may not want to have to re-type it every time you connect to the remote server. If your computer has OpenSSH version 7.2 or later, you can automatically store the passphrase in the SSH authentication agent. (To determine the OpenSSH version installed on your computer, type ssh -V at the command prompt.) Then when you connect to the remote server, you must type the passphrase the first time, but not for any subsequent connections.  
    To do this, add the following lines to your _~/.ssh/config_ file:
    
    Host *
        ```
        AddKeysToAgent yes
        ```
    If you are using Mac OS X, add the following line as well: 
    
        UseKeychain yes
    
    Alternatively, if you have an older version of OpenSSH installed on your computer, you can type the ssh-add command to manually store the passphrase in the SSH authentication agent for the duration of your login session.
    
    **If your computer has OpenSSH version 8.8 or later, you may be unable to connect to the server. (To determine the OpenSSH version installed on your computer, type ssh -V at the command prompt.) This is because by default, OpenSSH 8.8 and later versions disable RSA signatures using the SHA-1 hash algorithm.  
    To enable RSA signatures with SHA-1 hashes so you can connect to the server, add the following lines to your _~/.ssh/config_ file:
    

    `HostKeyAlgorithms +ssh-rsa,ssh-dss`
    `PubkeyAcceptedAlgorithms +ssh-rsa,ssh-dss`
    
    
    
    
    
    #### Other Articles in This Category

 [Securing a cPanel-enabled account with a Let's Encrypt SSL certificate](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/securing-a-cpanel-enabled-account-with-a-lets-encrypt-ssl-certificate/)
- [Installing a third-party SSL certificate with cPanel](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/install-a-third-party-ssl-certificate-with-cpanel/)
- [Installing a self-signed SSL certificate in cPanel](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/how-to-install-a-self-signed-ssl-certificate-in-cpanel/)
- [Configuring SSH keys with cPanel](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/configuring-ssh-keys-with-cpanel/)
- [IP Blocker](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/ip-blocker/)
- [Directory privacy](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/directory-privacy/)
- [Leech Protection](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/leech-protection/)
- [Hotlink Protection](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/hotlink-protection/)
- [Managing GnuPG keys in cPanel](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/gnupg-key-management/)
- [Securing a cPanel-enabled account with a cPanel SSL certificate](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/securing-a-cpanel-enabled-account-with-a-sectigo-ssl-certificate/)
- [Reconfiguring AutoSSL on domains](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/reconfiguring-autossl-on-domains/)
- [Two-factor authentication for cPanel](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/two-factor-authentication-for-cpanel/)
- [Imunify360](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/imunify360/)
- [Managing the ModSecurity module in cPanel](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/managing-the-modsecurity-module-in-cpanel/)
- [Using Imunify Email](https://www.a2hosting.com/kb/cpanel/cpanel-security-features/using-imunify-email/)

Show More

#### Related Articles

- [Using SSH (Secure Shell)](https://www.a2hosting.com/kb/getting-started-guide/accessing-your-account/using-ssh-secure-shell/)
- [Using SSH keys](https://www.a2hosting.com/kb/getting-started-guide/accessing-your-account/using-ssh-keys/)
- [Using SSHFS (Secure Shell Filesystem)](https://www.a2hosting.com/kb/getting-started-guide/accessing-your-account/using-sshfs-secure-shell-filesystem/)
- [Accessing cPanel](https://www.a2hosting.com/kb/cpanel/getting-started-with-cpanel/accessing-cpanel/)

Show More

- [SUGGEST AN ARTICLE](https://my.a2hosting.com/?m=a2_suggestionbox)

#### Grow Your Web Business

Subscribe to receive weekly cutting edge tips, strategies, and news you need to grow your web business.

No charge. Unsubscribe anytime.