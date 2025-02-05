
## Solution: problem with the server "returning with an error ''cagefs_enter: Unable to fork"


```sh
Include /etc/ssh/sshd_config.d/*.conf
Port 22345
KbdInteractiveAuthentication no
UsePAM yes
X11Forwarding yes
PrintMotd no

Banner issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

# override default of no subsystems
Subsystem       sftp    /usr/lib/openssh/sftp-server

```





```sh
sudo ssh -p 7822 username@remotehost
The authenticity of host '[remotehost]:7822 ([000.0.00.00]:7822)' can't be established.
ED25519 key fingerprint is SHA256:wcoWSc###############8UY+qFON91gHBjMzjEOvUA.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[remotehost]:7822' (ED25519) to the list of known hosts.
username@remotehost's password: 
client_loop: send disconnect: Broken pipe

```

```sh 
OpenSSH_8.9p1 Ubuntu-3ubuntu0.10, OpenSSL 3.0.2 15 Mar 2022
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: include /etc/ssh/ssh_config.d/*.conf matched no files
debug1: /etc/ssh/ssh_config line 21: Applying options for *
debug1: Connecting to remotehost [000.0.00.00] port 7822.
debug1: Connection established.
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_rsa-cert type -1
debug1: identity file /root/.ssh/id_ecdsa type -1
debug1: identity file /root/.ssh/id_ecdsa-cert type -1
debug1: identity file /root/.ssh/id_ecdsa_sk type -1
debug1: identity file /root/.ssh/id_ecdsa_sk-cert type -1
debug1: identity file /root/.ssh/id_ed25519 type -1
debug1: identity file /root/.ssh/id_ed25519-cert type -1
debug1: identity file /root/.ssh/id_ed25519_sk type -1
debug1: identity file /root/.ssh/id_ed25519_sk-cert type -1
debug1: identity file /root/.ssh/id_xmss type -1
debug1: identity file /root/.ssh/id_xmss-cert type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: identity file /root/.ssh/id_dsa-cert type -1
debug1: Local version string SSH-2.0-OpenSSH_8.9p1 Ubuntu-3ubuntu0.10
debug1: Remote protocol version 2.0, remote software version OpenSSH_8.0
debug1: compat_banner: match: OpenSSH_8.0 pat OpenSSH* compat 0x04000000
debug1: Authenticating to remotehost:7822 as 'username'
debug1: load_hostkeys: fopen /root/.ssh/known_hosts2: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts2: No such file or directory
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: algorithm: curve25519-sha256
debug1: kex: host key algorithm: ssh-ed25519
debug1: kex: server->client cipher: aes128-ctr MAC: umac-128@openssh.com compression: none
debug1: kex: client->server cipher: aes128-ctr MAC: umac-128@openssh.com compression: none
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: SSH2_MSG_KEX_ECDH_REPLY received
debug1: Server host key: ssh-ed25519 SHA256:wcoWSc8VXzSRHRyLTdyzM8UY+qFON91gHBjMzjEOvUA
debug1: load_hostkeys: fopen /root/.ssh/known_hosts2: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts2: No such file or directory
debug1: Host '[remotehost]:7822' is known and matches the ED25519 host key.
debug1: Found key in /root/.ssh/known_hosts:1
debug1: ssh_packet_send2_wrapped: resetting send seqnr 3
debug1: rekey out after 4294967296 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: ssh_packet_read_poll2: resetting read seqnr 3
debug1: SSH2_MSG_NEWKEYS received
debug1: rekey in after 4294967296 blocks
debug1: Will attempt key: /root/.ssh/id_rsa 
debug1: Will attempt key: /root/.ssh/id_ecdsa 
debug1: Will attempt key: /root/.ssh/id_ecdsa_sk 
debug1: Will attempt key: /root/.ssh/id_ed25519 
debug1: Will attempt key: /root/.ssh/id_ed25519_sk 
debug1: Will attempt key: /root/.ssh/id_xmss 
debug1: Will attempt key: /root/.ssh/id_dsa 
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<ssh-ed25519,ssh-rsa,rsa-sha2-256,rsa-sha2-512,ssh-dss,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521>
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,password
debug1: Next authentication method: gssapi-with-mic
debug1: No credentials were supplied, or the credentials were unavailable or inaccessible
No Kerberos credentials available (default cache: FILE:/tmp/krb5cc_0)


debug1: No credentials were supplied, or the credentials were unavailable or inaccessible
No Kerberos credentials available (default cache: FILE:/tmp/krb5cc_0)


debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/id_rsa
debug1: Trying private key: /root/.ssh/id_ecdsa
debug1: Trying private key: /root/.ssh/id_ecdsa_sk
debug1: Trying private key: /root/.ssh/id_ed25519
debug1: Trying private key: /root/.ssh/id_ed25519_sk
debug1: Trying private key: /root/.ssh/id_xmss
debug1: Trying private key: /root/.ssh/id_dsa
debug1: Next authentication method: password
username@remotehost's password: 
Authenticated to remotehost ([000.0.00.00]:7822) using "password".
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: pledge: filesystem
client_loop: send disconnect: Broken pipe
```

```sh

journalctl -u ssh
Nov 07 11:08:16 lucky-Precision-3551 systemd[1]: Starting OpenBSD Secure Shell server...
Nov 07 11:08:16 lucky-Precision-3551 sshd[12241]: Server listening on 0.0.0.0 port 22.
Nov 07 11:08:16 lucky-Precision-3551 sshd[12241]: Server listening on :: port 22.
Nov 07 11:08:16 lucky-Precision-3551 systemd[1]: Started OpenBSD Secure Shell server.
Nov 07 16:17:32 lucky-Precision-3551 sshd[12241]: Received signal 15; terminating.
Nov 07 16:17:32 lucky-Precision-3551 systemd[1]: Stopping OpenBSD Secure Shell server...
Nov 07 16:17:32 lucky-Precision-3551 systemd[1]: ssh.service: Deactivated successfully.
Nov 07 16:17:32 lucky-Precision-3551 systemd[1]: Stopped OpenBSD Secure Shell server.
Nov 07 16:17:32 lucky-Precision-3551 systemd[1]: Starting OpenBSD Secure Shell server...
Nov 07 16:17:32 lucky-Precision-3551 sshd[17952]: Server listening on 0.0.0.0 port 22345.
Nov 07 16:17:32 lucky-Precision-3551 sshd[17952]: Server listening on :: port 22345.
Nov 07 16:17:32 lucky-Precision-3551 systemd[1]: Started OpenBSD Secure Shell server.
Nov 07 17:00:03 lucky-Precision-3551 sshd[17952]: Received signal 15; terminating.
Nov 07 17:00:03 lucky-Precision-3551 systemd[1]: Stopping OpenBSD Secure Shell server...
Nov 07 17:00:03 lucky-Precision-3551 systemd[1]: ssh.service: Deactivated successfully.
Nov 07 17:00:03 lucky-Precision-3551 systemd[1]: Stopped OpenBSD Secure Shell server.
Nov 07 17:00:03 lucky-Precision-3551 systemd[1]: Starting OpenBSD Secure Shell server...
Nov 07 17:00:03 lucky-Precision-3551 sshd[18469]: Server listening on 0.0.0.0 port 22.
Nov 07 17:00:03 lucky-Precision-3551 sshd[18469]: Server listening on :: port 22.
Nov 07 17:00:03 lucky-Precision-3551 systemd[1]: Started OpenBSD Secure Shell server.
Nov 07 17:03:12 lucky-Precision-3551 sshd[18469]: Received signal 15; terminating.
Nov 07 17:03:12 lucky-Precision-3551 systemd[1]: Stopping OpenBSD Secure Shell server...
Nov 07 17:03:12 lucky-Precision-3551 systemd[1]: ssh.service: Deactivated successfully.
Nov 07 17:03:12 lucky-Precision-3551 systemd[1]: Stopped OpenBSD Secure Shell server.
Nov 07 17:03:12 lucky-Precision-3551 systemd[1]: Starting OpenBSD Secure Shell server...
Nov 07 17:03:12 lucky-Precision-3551 sshd[18495]: Server listening on 0.0.0.0 port 22.
Nov 07 17:03:12 lucky-Precision-3551 sshd[18495]: Server listening on :: port 22.
Nov 07 17:03:12 lucky-Precision-3551 systemd[1]: Started OpenBSD Secure Shell server.

```