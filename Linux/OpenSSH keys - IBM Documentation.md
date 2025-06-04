When SSH authentication for CLI sessions uses a CA-signed user certificate, you must create and manage various SSH certificates.

The following information shows examples to manage keys with the OpenSSH authentication key utility, ssh-keygen. You use this utility on a client system, you cannot use it on the appliance.

![](https://www.ibm.com/docs/en/SS5K6E_9.4.0/mqa/ng934.gif)Note: From 9.3.4, the appliance supports SSH certificates that have either an RSA SHA1 or SHA2 signature. Before 9.3.4, the appliance only supported RSA SHA1 signatures. To generate a SHA2 signature using OpenSSH version 8 or later, specify the `-t rsa-sha2-256` or `-t rsa-sha2-512` argument to the ssh-keygen commands. To generate a SHA1 signature using OpenSSH version 8 or later, specify `-t ssh-rsa`. To generate a SHA1 signature using OpenSSH version 7 or earlier, specify `-t rsa`.

For more information, visit the ssh-keygen manual page, [https://man.openbsd.org/ssh-keygen.1](https://www.ibm.com/links?url=https%3A%2F%2Fman.openbsd.org%2Fssh-keygen.1 "(Opens in a new tab or window)")

## Create CA key to sign certificates[](https://www.ibm.com/docs/en/mq-appliance/9.4?topic=sessions-openssh-keys#concept_gbf_ww4_mxb__title__2 "Copy to clipboard")

The following examples show how to create a 4096-bit `mqa-ssh-user-ca` CA key to sign user certificates.

OpenSSH version 7 - RSA SHA1

```
ssh-keygen -t rsa -b 4096 -f mqa-ssh-user-ca -C mqa-ssh-user-ca
```

OpenSSH version 8 - RSA SHA1

```
ssh-keygen -t ssh-rsa -b 4096 -f mqa-ssh-user-ca -C mqa-ssh-user-ca
```

![](https://www.ibm.com/docs/en/SS5K6E_9.4.0/mqa/ng934.gif)OpenSSH version 8 - RSA SHA2

```
ssh-keygen -t rsa-sha2-256 -b 4096 -f mqa-ssh-user-ca -C mqa-ssh-user-ca
```

or:

```
ssh-keygen -t rsa-sha2-512 -b 4096 -f mqa-ssh-user-ca -C mqa-ssh-user-ca
```

Two files are created: one for the public key and one for the private key. The name of the private key file matches the value of the -f parameter. The name of the public key file is the same, but with a file extension of ".pub".

You must upload the public key to the cert: directory on the appliance.

## Create unsigned user certificates and associate CA key to sign them[](https://www.ibm.com/docs/en/mq-appliance/9.4?topic=sessions-openssh-keys#concept_gbf_ww4_mxb__title__3 "Copy to clipboard")

The following examples show how to create a 4096-bit `admin` user certificate and associate it with the `mqa-ssh-user-ca` CA key.

OpenSSH version 7 - RSA SHA1

```
ssh-keygen -t rsa -b 4096 -f admin-key -C admin
ssh-keygen -s mqa-ssh-user-ca -I admin -n admin admin-key.pub
```

OpenSSH version 8 - RSA SHA1

```
ssh-keygen -t ssh-rsa -b 4096 -f admin-key -C admin
ssh-keygen -t ssh-rsa -s mqa-ssh-user-ca -I admin -n admin admin-key.pub
```

![](https://www.ibm.com/docs/en/SS5K6E_9.4.0/mqa/ng934.gif)OpenSSH version 8 - RSA SHA2

```
ssh-keygen -t rsa-sha2-256 -b 4096 -f admin-key -C admin
ssh-keygen -t rsa-sha2-256 -s mqa-ssh-user-ca -I admin -n admin admin-key.pub
```

or:

```
ssh-keygen -t rsa-sha2-512 -b 4096 -f admin-key -C admin
ssh-keygen -t rsa-sha2-512 -s mqa-ssh-user-ca -I admin -n admin admin-key.pub
```

In total, there are three files for the user:

-   admin-key
    
    The user's private SSH key
    
-   admin-key.pub
    
    The user's public SSH key
    
-   admin-key-cert.pub
    
    The user's SSH certificate that has been signed by the CA.
    

## Validate contents of user certificates[](https://www.ibm.com/docs/en/mq-appliance/9.4?topic=sessions-openssh-keys#concept_gbf_ww4_mxb__title__4 "Copy to clipboard")

The following examples show how to validate that the admin user certificate supports SHA1 or SHA2, as appropriate.

OpenSSH version 7 - RSA SHA1

```
ssh-keygen -L -f admin-key-cert.pub

admin-key-cert.pub:
        Type: ssh-rsa-cert-v01@openssh.com user certificate
        Public key: RSA-CERT SHA256:mMQUALHY3b7GaffRU8D6/5spidqWaKarjSYhPNSXvFE
        Signing CA: RSA SHA256:uoD2k6OMf7+0okmzynf3P2XqE3/8osTt4HnloxpguG4
        Key ID: "admin"
        Serial: 0
        Valid: forever
        Principals:
                admin
        Critical Options: (none)
        Extensions:
                permit-X11-forwarding
                permit-agent-forwarding
                permit-port-forwarding
                permit-pty
                permit-user-rc
```

OpenSSH version 8 - RSA SHA1

```
ssh-keygen -L -f admin-key-cert.pub

admin-key-cert.pub:
        Type: ssh-rsa-cert-v01@openssh.com user certificate
        Public key: RSA-CERT SHA256:mMQUALHY3b7GaffRU8D6/5spidqWaKarjSYhPNSXvFE
        Signing CA: RSA SHA256:uoD2k6OMf7+0okmzynf3P2XqE3/8osTt4HnloxpguG4 (using ssh-rsa)
        Key ID: "admin"
        Serial: 0
        Valid: forever
        Principals:
                admin
        Critical Options: (none)
        Extensions:
                permit-X11-forwarding
                permit-agent-forwarding
                permit-port-forwarding
                permit-pty
                permit-user-rc
```

![](https://www.ibm.com/docs/en/SS5K6E_9.4.0/mqa/ng934.gif)OpenSSH version 8 - RSA SHA2

```
ssh-keygen -L -f admin-key-cert.pub

admin-key-cert.pub:
        Type: ssh-rsa-cert-v01@openssh.com user certificate
        Public key: RSA-CERT SHA256:RDfeeSB+5eM7lKi+1Ni614lJ1HSzZ8b3Dltxq5u5Ywk
        Signing CA: RSA SHA256:srgLP5dSyBxu61N3uRjC7GvjQBUCi/g+L2rK5XdnA3k (using rsa-sha2-512)
        Key ID: "admin"
        Serial: 0
        Valid: forever
        Principals:
                admin
        Critical Options: (none)
        Extensions:
                permit-X11-forwarding
                permit-agent-forwarding
                permit-port-forwarding
                permit-pty
                permit-user-rc
```

(Includes the string `(using rsa-sha2-256)` or `(using rsa-sha2-512)`.)

## Using the signed SSH certificate[](https://www.ibm.com/docs/en/mq-appliance/9.4?topic=sessions-openssh-keys#concept_gbf_ww4_mxb__title__5 "Copy to clipboard")

To use the signed SSH certificate:

1.  Upload the CA public key file (`mqa-ssh-user-ca.pub`) to the cert:/// directory on the appliance and configure the appliance to use it
2.  Copy the user's private key file (`admin-key`), their public key file (`admin-key.pub`), and their signed certificate file (`admin-key-cert.pub`) to a directory on the SSH client.
3.  Create and authorize a user on the appliance that matches the identity of the certificate.
4.  Log in to the appliance from the SSH client as the user by specifying the path to their private key file. The signed certificate must be located in the same directory as their private key, and it is used automatically if it exists.
    
    ```
    ssh -i path/admin-key admin@hostname
    ```
    
    You can also copy your user public keys to the appliance so that they are available to the revoke keys procedure when you need to modify access to the appliance (see [Managing the SSH revoked keys list for authenticating CLI sessions](https://www.ibm.com/docs/en/SS5K6E_9.4.0/mqa/security/revoked_keys.html "You can revoke specific OpenSSH keys when you need to update access to the appliance.").