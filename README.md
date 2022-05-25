## server-ssh-access

Firstly, make sure you have a connection with the internet. 
To check the internet connection you can use `ping 8.8.8.8` command. If it "replies back" with no packet loss, then you have a internet connection. 
The address `8.8.8.8` determines the DNS server address of Google.

Secondly, make sure you have a connection with the server.
You can use `ping <server_ip_address>` command to check the connection with the server.

Thirdly, make sure the server has the support for ssh connection. Since you don't have the access to server, you should contact to support center of server provider to check the ssh on the server. Or you can use web style terminals to access your server. For instance Lish for Linode and Droplet Console for DigitalOcean droplets. To check the ssh support use `sudo systemctl status sshd.service` command from terminal.

After troubleshooting ssh service, you can try to connect to your server with `ssh <username>@<server_id_address>`.

If you are using the domain name instead of server IP address, `ssh <username>@<server_doman_name>` can be suitable for you. For example `ssh admin@example.com`. If you can connect using IP address while can't have access with domain address, then it is the problem with DNS server. If this is the case try to flush the DNS on your computer. For example in linux operating system, you can execute following command.
```bash
$ sudo systemd-resolve --flush-caches
$ sudo resolvectl flush-caches
```

After successfully accessing to your server, make sure to generate ssh keys to access easier.
To generate ssh key pairs `ssh-keygen -b 4096`. Keep in mind that, this will overwrite existing your existing keys if you already have them. To check if you already have ssh keys `ls ~/.ssh/`. If you find `id_rsa` and `id_rsa.pub` files from the list. Make sure you are not using these keys to access your another server, because after overwriting them you will lose the access. 

After generating your keys, you should copy your public key to server. You can do that by executing `ssh-copy-id <username>@<server_ip_address>`.

## Listing running servers in server

```bash
#!/bin/bash

ps ux > processes.txt
```
