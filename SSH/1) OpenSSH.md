
```sh
sudo apt-get remove --purge openssh-server
```


```sh
sudo apt remove --purge openssh-client
```

```sh

sudo apt install openssh-client
```

```sh
sudo apt install openssh-server
```

```sh
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.original
sudo chmod a-w /etc/ssh/sshd_config.original
```

```sh
sudo sshd -t -f /etc/ssh/sshd_config
```

```sh
sudo systemctl restart sshd.service
```

```sh
sudo ufw status
```

```ssh
journalctl -u ssh
```
