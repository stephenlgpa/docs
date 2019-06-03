# SSH NOTES

References: 

1. [How To Use SSH to Connect to a Remote Server in Ubuntu][1]

----

## Connecting using `ssh`


```
ssh remote_username@remote_host
```

`remote_username@remote_host` for my vps is `steve@206.189.40.192`. 

You will be asked for a password. Use `exit` to come back to the local session.

## How does it work?

SSH works by connecting a client program to an ssh server, which is running on the remote host already. In this case, the client program is `ssh` on the local host.

To start the ssh server on the remote host, use the command `sudo service ssh start`.

To configure SSH (changing the settings of the sshd server), open the file `/etc/ssh/sshd_config`

Back up the file first: `sudo cp /etc/ssh/sshd_config{,.bak}`

## Possible options to play with (in `/etc/ssh/sshd_config`)

`Port 22`

See later for changing the port ssh listens to, but otherwise, Leave It Alone!

```
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
```

The host key declarations specify where to look for global host keys (see later).

```
SyslogFacility AUTH
LogLevel INFO`	
```

The level of logging that should occur

```
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes
```

- LoginGraceTime: how many seconds to keep the connection alive without successfully logging in
- PermitRootLogin: whether root can login remotely (usually no once an account with sudo privivleges is created)
- strictModes: will refuse a login attempt if the authentication files are readable by everyone (yes)

```
X11Forwarding yes
X11DisplayOffset 10
```

Configures X11 Forwarding, allowing the local machine to view the remote system's GUI. This option must be enabled on the server and given with the SSH client during connection with the -X option.

After changing options to `sshd_config`, restart the sshd server to implement the changes:

` sudo systemctl restart ssh` (on Ubuntu, Debian)

or

` sudo service ssh restart` (on other systems)

## Logging in with SSH Keys

This allows you to log in without a password. The *private key* is located on the client machine (e.g. this laptop) and is secured and kept secret. The *public key* is located on the server (e.g. the vps) you wish to access and can be given to anyone.

When attempting to connect to the server, it will use the public key to create a message for the client that can only be read with the private key. The client then sends the appropriate response back to the server, which then knows the client is legitimate. 

## Creating SSH Keys

```
ssh-keygen -t rsa
```

This creates keys at:
- `~/.ssh/id_rsa.pub` (public key)
- `~/.ssh/id_rsa` (private key)

## Transfer your Public Key to the server

```
ssh-copy-id remote_host
```

The server checks to see if it has the key already. You will first need to authenticate with your password. If not on the serer, the public key will be transferred to the host.

## Client ssh options

```
ssh -p port_number remote host
```

If the port number for ssh has been changed on the host, match it with the port number option when using client ssh.

## Disabling Password Authentication

For greater security.

On the host, as root or sudo user, open the sshd configuration file: `sudo vim /etc/ssh/sshd_config`

Locate `PasswordAuthentication`, uncomment it and change the value to 'no'.


[1]: https://www.digitalocean.com/community/tutorials/how-to-use-ssh-to-connect-to-a-remote-server-in-ubuntu
