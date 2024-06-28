Introduction

MySQL is an [open-source](https://phoenixnap.com/glossary/what-is-open-source) relational database management system that utilizes [SQL](https://phoenixnap.com/glossary/sql-definition) for managing and manipulating data. This essential part of the [LAMP stack](https://phoenixnap.com/kb/what-is-a-lamp-stack) is known for its speed, simplicity, and [scalability](https://phoenixnap.com/glossary/scalability), making it a popular choice for various applications and websites.

**The following tutorial explains how to install MySQL on [Ubuntu 22.04](https://phoenixnap.com/kb/ubuntu-22-04-lts) in five steps.**

![How to Install MySQL on Ubuntu 22.04](https://phoenixnap.com/kb/wp-content/uploads/2023/12/how-to-install-mysql-on-ubuntu-22-04.png)

Prerequisites

-   Ubuntu 22.04.
-   Access to the terminal.
-   [Sudo privileges](https://phoenixnap.com/kb/how-to-create-sudo-user-on-ubuntu).

The MySQL installation process on Ubuntu 22.04 involves five steps that ensure a secure and well-configured setup. Follow the instructions below to install MySQL and enhance the Ubuntu 22.04 system functionality.

### Step 1: Update/Upgrade Package Repository

To ensure the latest MYSQL [version](https://phoenixnap.com/kb/how-to-check-mysql-version) installation, update the package [repository](https://phoenixnap.com/glossary/what-is-a-repository). Run the following command:

```
sudo apt update
```

![sudo apt update terminal output](https://phoenixnap.com/kb/wp-content/uploads/2023/12/sudo-apt-update-terminal-output.png)

Next, upgrade the installed packages to the latest versions:

```
sudo apt upgrade
```

![sudo apt upgrade terminal output](https://phoenixnap.com/kb/wp-content/uploads/2023/12/sudo-apt-upgrade-terminal-output-1.png)

### Step 2: Install MySQL

Once the repository is updated, install MySQL with the following command:

```
sudo apt install mysql-server
```

![sudo apt install mysql-server terminal-output](https://phoenixnap.com/kb/wp-content/uploads/2023/12/sudo-apt-install-mysql-server.png)

Verify the installation with:

```
mysqld --version
```

![mysqld –version terminal output](https://phoenixnap.com/kb/wp-content/uploads/2023/12/mysqld-version-terminal-output.png)

The output confirms that the 8.0.35 version of MySQL is successfully installed on Ubuntu.

### Step 3: Securing MySQL

After installing MySQL, the next step is to perform an initial security setup for your MySQL installation. Securing includes setting a [strong password](https://phoenixnap.com/blog/strong-great-password-ideas), removing unnecessary accounts and [databases](https://phoenixnap.com/kb/what-is-a-database), and restricting access to enhance overall security.

To secure the installation, run the following command:

```
sudo mysql_secure_installation
```

![sudo mysql_secure_installation terminal output](https://phoenixnap.com/kb/wp-content/uploads/2023/12/sudo-mysql-secure-installation-terminal-output.png)

The output shows the command establishes a connection to MySQL without a password. Depending on the system, users might be prompted to provide a root password in this step.

The rest of the configuration consists of several parts.

#### Part 1: Password Validation

The first part is password validation. Press the **y** key to confirm password validation.

![validate password terminal output](https://phoenixnap.com/kb/wp-content/uploads/2023/12/validate-password-terminal-output.png)

Users have three options for password policy:

-   **0** - low.
-   **1** - medium.
-   **2** - strong.

Select one option and hit **Enter**.

![Select password strength terminal output ](https://phoenixnap.com/kb/wp-content/uploads/2023/12/select-password-strenhgt-terminal-output.png)

Depending on the system, the next step either asks to set up the password or is skipped completely.

In the first case, set up a new password by typing it once and then once again to validate. Finally, press **Enter** to confirm the change.

![adding new password terminal output](https://phoenixnap.com/kb/wp-content/uploads/2023/12/adding-new-password-terminal-output.png)

Another scenario is that the command skips setting the password where the [operating system](https://phoenixnap.com/glossary/operating-system) credentials are used for [authentication](https://phoenixnap.com/glossary/what-is-authentication).

![password validation policy levels](https://phoenixnap.com/kb/wp-content/uploads/2023/12/password-validation-policy-levels.png)

The root user logs in without providing a password. In this case, the authentication method **`auth_socket`** is used by default.

**Note:** In case **`auth_socket`** is used, users still have the option to set the password after logging in to the MySQL server. The command is **`ALTER USER root@localhost IDENTIFIED BY [password]`**. The command produces no output.

#### Part 2: Remove Anonymous Users

Upon installation, MySQL automatically incorporates an anonymous user, permitting unrestricted access without a dedicated user account. While initially designed for testing and streamlined installations, it is advisable to remove this user for security reasons.

Users can revisit this step by running the **`sudo mysql_secure_installation`** command and responding with **y** to ensure a more secure MySQL setup.

![Remove anonymous users terminal output](https://phoenixnap.com/kb/wp-content/uploads/2023/12/remove-anonimous-user-terminal-output.png)

#### Part 3: Disallow Root Login Remotely

The following action involves preventing [remote login](https://phoenixnap.com/kb/mysql-remote-connection) for the root user. By default, limiting the root user's connection to the local machine (localhost) is advisable to mitigate potential security risks, such as credential [brute-force attacks](https://phoenixnap.com/blog/brute-force-attack).

![Disallow root login remotely terminal output](https://phoenixnap.com/kb/wp-content/uploads/2023/12/disallow-root-login-remotely-terminal-output.png)

While you can skip this step during the initial setup, it is widely considered a crucial security practice for production environments. This precaution ensures that even if an unauthorized user gains network access, they would require physical machine access or authorized network privileges to attempt logging in as the root user.

#### Part 4: Remove Test Database

Having a test database accessible to anyone poses a security risk. The safest way is to remove it. Once prompted, type **y**.

![Remove test database terminal output](https://phoenixnap.com/kb/wp-content/uploads/2023/12/remove-test-database-terminal-output.png)

#### Part 5: Reload Privilege Tables

The privilege tables in MySQL store information about user privileges and access rights. Reloading the privilege tables is necessary to apply the changes made throughout the **`mysql_secure_installation`** process.

![Reloading the privilege tables terminal output](https://phoenixnap.com/kb/wp-content/uploads/2023/12/reload-privilege-tables-terminal-output.png)

Reloading privilege tables was the last step in securing MySQL installation.

### Step 4: Check if MySQL Service Is Running

After the installation, the MySQL service starts automatically. To verify that the server is working, run the following command:

```
sudo systemctl status mysql
```

![sudo systemctl status mysql terminal output](https://phoenixnap.com/kb/wp-content/uploads/2023/12/sudo-systemctl-status-mysql-terminal-output.png)

The output shows that the service is active and running.

### Step 5: Log in to MySQL Server

The final step is to log in to the MySQL server:

```
sudo mysql -u root -p
```

The above command will prompt you for a password. I could never log-in without -p and entering  a password as shown below. **See "Password Required - Attempted  Fixes"** below.

![sudo mysql -u root terminal output](https://phoenixnap.com/kb/wp-content/uploads/2023/12/sudo-mysql-u-root-terminal-output.png)

When executed, the command gives the root user access to the MySQL command-line interface and the ability to interact with the MySQL database server using SQL [commands and queries](https://phoenixnap.com/kb/mysql-commands-cheat-sheet). If the user has set a password for the root, the command prompts for the root user's password. Once provided, the user gets full access.

Conclusion

After reading this article, you know how to install MySQL on Ubuntu 22.04 using five steps.

Next, learn how to [start, stop, and restart the MySQL server](https://phoenixnap.com/kb/start-mysql-server).

**See "Password Required - Attempted  Fixes"**
first
```
sudo systemctl stop mysql.service
```
Then
```
sudo systemctl set-environment MYSQLD_OPTS="--skip-networking --skip-grant-tables"
```
Then
```
sudo systemctl start mysql.service
```
Then if you still can't login with out a password
```
sudo mysqld_safe --skip-grant-tables
```

If you get an error like this

![[Pasted image 20240613094937.png]]

```
sudo systemctl stop mysql.service
```

Then re-run
```
sudo mysqld_safe --skip-grant-tables
```

This hung the terminal