# Setup SSH
This project explain how to create ssh keys and link them to a server.

---
## 1. Create ssh keys
In your local machine you must create ssh keys with the following command:
```bash
ssh-keygen
```

This will create a pair keys with the default options, but we can define our options:
```bash
ssh-keygen -t rsa -b 4096 -f ~/.ssh/test -C "This is a comment"
```

`-t` Define algorithm to encrypt.
`-b` Length of then key.
`-f` Where you want to save pair keys and their name.

There are more, but this is the most used.

### 1.1 Algorith
I recommend use algorithm `Ed25519` because is most efficient and secure than rsa 1024 or 2048.
```bash
ssh-keygen -t ed25519 -f ~/.ssh/test -C "This is a comment"
```

---
## 2. Link to a server
In this step you can do it by password or with other ssh key.

Use the following command:
```bash
ssh-copy-id -i /path/to/puclic-key <user>@<host>
```
When you put the command, the shell ask you for the user password if you dont have other ssh key.

---
# 3. Connect with server

```bash
ssh -i /path/to/private-key <user>@<host>
```

---
## 4. Alias config
Create `~/.ssh/config` file, in this file you can define alias for connect to remote host.
Example:
```txt
Host RH
        HostName 192.168.1.254
        IdentityFile /home/user/.ssh/id_rsa
        User jake
        ProxyJump esfw
        Port 22
```
Now you can connect to remote host by command:
```bash
ssh RH
```