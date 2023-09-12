  

## 1\. Introduction[](https://www.baeldung.com/linux/ssh-name-resolution-ip#introduction)

Since humans are generally better at remembering names rather than [IP address](https://www.baeldung.com/cs/ipv4-vs-ipv6#ip-address) numbers, many technologies convert the latter to the former. Further, some even exist for the sole purpose of that conversion. Still, others implement the function for internal use.

In this tutorial, **we look at the local [SSH](https://www.baeldung.com/cs/ssh-intro) protocol implementation of hostname to IP address mapping**. First, we do a quick refresh on the classic methods for resolving names. Next, we combine one of them with SSH and discuss the results. Finally, we configure and use the internal SSH client name resolution.

For brevity and security reasons, **we only consider the newest iteration of SSH version 2 (SSHv2) implemented by [OpenSSH](https://www.baeldung.com/linux/ssh-key-types-convert-ppk#1-openssh)**.

We tested the code in this tutorial on Debian 11 (Bullseye) with GNU Bash 5.1.4 and OpenSSH 8.4p1. It should work in most POSIX-compliant environments.

Generally, there are two common ways to resolve names to IP addresses in Linux:

[![freestar](https://a.pub.network/core/imgs/fslogo-green.svg)](https://ads.freestar.com/?utm_campaign=branding&utm_medium=banner&utm_source=baeldung.com&utm_content=baeldung_leaderboard_mid_1)

-   [Domain Name System (DNS)](https://www.baeldung.com/cs/dns-intro): domain name to IP address
-   [_hosts_ file](https://www.baeldung.com/linux/wildcard-subdomain-hosts-file#modifyingetchosts): [hostname](https://www.baeldung.com/linux/set-or-change-system-hostname) to IP address

Let’s briefly look at both.

### 2.1. Domain Name System (DNS)[](https://www.baeldung.com/linux/ssh-name-resolution-ip#1-domain-name-system-dns)

Often, DNS only refers to the global, public servers that provide name resolution via the [Internet](https://www.baeldung.com/cs/non-routable-ip-address#internet).

Yet, a [DNS server](https://www.baeldung.com/cs/dns-authoritative-server-ip) can be global or local. Still, not every system has a global domain name, which is paid for and maintained by a network of servers that broadcast it. While there are dynamic DNS services like _[NoIP.com](https://www.noip.com/),_ their configuration can be tedious and demanding.

On the other hand, local DNS servers aren’t that common and are limited by their nature. On top of that, using one system to query another about the address of a third can be a convoluted and burdening way to communicate.

These **drawbacks of DNS can force alternate solutions**.

[![freestar](https://a.pub.network/core/imgs/fslogo-green.svg)](https://ads.freestar.com/?utm_campaign=branding&utm_medium=banner&utm_source=baeldung.com&utm_content=baeldung_leaderboard_mid_2)

### 2.2. Hosts Files and _/etc/hosts_[](https://www.baeldung.com/linux/ssh-name-resolution-ip#2-hosts-files-and-etchosts)

Hosts files are the simplest form of name-to-address mapping. In fact, DNS servers can be seen as huge remotely-queried hosts files.

**The default _hosts_ file for most Linux distributions is _/etc/hosts_**. Essentially, **a _hosts_ file is a list of rows, each containing a name and its corresponding address or addresses, all delimited in some way**:

```
$ cat /etc/hosts
127.0.0.1       localhost

::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

Here, we see the standard [_localhost_](https://www.baeldung.com/cs/127-0-0-1-vs-localhost#what-is-localhost) mappings for [IPv4 and IPv6](https://www.baeldung.com/cs/ipv4-vs-ipv6) addresses. Each line has an IP and a hostname, which we can resolve back to it:

```
$ ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
```

In this case, [_ping_](https://www.baeldung.com/linux/ping-command) resolves [_localhost_ to _127.0.0.1_](https://www.baeldung.com/cs/127-0-0-1-vs-localhost).

Importantly, even for mappings to remote addresses, **the _hosts_ file only works for the local system**. Indeed, this can be inconvenient when switching environments.

[![freestar](https://a.pub.network/core/imgs/fslogo-green.svg)](https://ads.freestar.com/?utm_campaign=branding&utm_medium=banner&utm_source=baeldung.com&utm_content=baeldung_leaderboard_mid_3)

In all cases, domain and host names can and often differ between themselves and from other names for the same system, like those provided within certain protocol configurations.

## 3\. SSH Name Resolution[](https://www.baeldung.com/linux/ssh-name-resolution-ip#ssh-name-resolution)

After refreshing our knowledge about the general concepts, let’s see how we can resolve names via SSH. Since DNS is usually [the Linux default](https://www.baeldung.com/linux/resolve-conf-systemd-avahi) and also an involved solution, we won’t be talking about it for SSH.

When checking the name resolution, we employ the [_\-v_ verbose switch](https://man.openbsd.org/ssh#v) of our SSH client. It provides additional information during session setup.

### 3.1. SSH and _/etc/hosts_[](https://www.baeldung.com/linux/ssh-name-resolution-ip#1-ssh-and-etchosts)

Of course, **simply adding a line to _/etc/hosts_ should work for SSH clients as well**:

```
$ ssh -v baeldung@xost
[...]
ssh: Could not resolve hostname xost: Name or service not known
$ ping xost
ping: xost: Name or service not known
$ echo '192.168.6.66 xost' >> /etc/hosts
```

The name _xost_ was unidentified, so we added an entry for it to our _hosts_ file. Now, we can repeat our tests:

```
$ ping xost
PING xost (192.168.6.66) 56(84) bytes of data.
[...]
$ ssh -v baeldung@xost
[...]
debug1: Connecting to xost [192.168.6.66] port 22.
[...]
```

Here, **once added to _/etc/hosts_, we see that a previously unknown name _xost_ is identified as _192.168.6.66_ by both our SSH client and _ping_**.

### 3.2. _ssh\_config_[](https://www.baeldung.com/linux/ssh-name-resolution-ip#2-sshconfig)

As an alternative to classic approaches, **we can leverage the [_ssh\_config_](https://man.openbsd.org/ssh_config) file to configure name resolution only for SSH**.

Although potentially limiting, this method can provide several benefits:

[![freestar](https://a.pub.network/core/imgs/fslogo-green.svg)](https://ads.freestar.com/?utm_campaign=branding&utm_medium=banner&utm_source=baeldung.com&utm_content=baeldung_incontent_1)

-   even more localized resolution of names
-   set via the SSH protocol configuration
-   **internal client names can set [multiple SSH parameters](https://www.baeldung.com/linux/ssh-automate-commands-upon-connection#ssh-remotecommand) of a connection**

By using the [_Hostname_](https://man.openbsd.org/ssh_config#Hostname) statement within a [_Host_](https://man.openbsd.org/ssh_config#Host) block in our SSH client configuration file, we can create a mapping:

```
Host xost
  Hostname 192.168.6.66
```

Conveniently, we can use other names that the system recognizes as well (such as a domain name). Moreover, there are [_TOKENS_](https://man.openbsd.org/ssh_config#TOKENS), which work similarly to the format specifiers of the [_printf_](https://www.baeldung.com/linux/printf-echo#printf) command. They allow us to avoid hardcoding dynamic values.

Let’s test our setup so far:

```
$ ssh -v xost
[...]
debug1: Connecting to xost [192.168.6.66] port 22.
[...]
```

Evidently, our settings work for [_ssh_](https://man.openbsd.org/ssh). Now, let’s try the same name with _ping_:

```
$ ping xost
ping: xost: Name or service not known
[...]<code>
```

As expected, **other tools are unaffected by the SSH protocol setup**.

## 4\. Summary[](https://www.baeldung.com/linux/ssh-name-resolution-ip#summary)

In this article, we explored the main ways to use name resolution with SSH.

In conclusion, while we have many alternatives, including the classic DNS and _hosts_ files, we can usually achieve the greatest flexibility via the direct configuration of our SSH client alone.