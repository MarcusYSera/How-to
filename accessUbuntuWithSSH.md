# Access Ubuntu Through SSH

[Source](https://phoenixnap.com/kb/ssh-to-connect-to-remote-server-linux-or-windows)

---

### OpenSSH

---

##### Client

Check to see if OpenSSH is already installed by entering the following in terminal

`ssh`

If installed the response should look similar to this

```
username@host:~$ ssh

usage: ssh [-1246AaCfGgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
[-D [bind_address:]port] [-E log_file] [-e escape_char]
[-F configfile] [-I pkcs11] [-i identity_file]
[-J [user@]host[:port]] [-L address] [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port] [-Q query_option] [-R address] [-S ctl_path] [-W host:port] [-w local_tun[:remote_tun]]
[user@]hostname [command]

username@host:~$
```

If error use this to install it (many don't recommend using sudo w/apt-get)

`sudo apt-get install openssh-client`

---

##### Server

From within the virtual machine/server, you need to set it up to recieve the connection from your client

Use this to check if it is already installed

`ssh localhost`

If you get 'connection refused', then SSH server is not yet installed

`sudo apt-get install openssh-server ii.`

To check for installation

`sudo service ssh status`

If installed correctly, the response should look like this

```
username@host:-$ sudo service ssh status
• ssh.service - OpenBSD Secure Shell server
Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enab
Active: active (running) since Fr 2018-03-12 10:53:44 CET; 1min 22s ago Process: 1174 ExecReload=/bin/kill -HUP $MAINPID (code=exited, status=0/SUCCES

Main PID: 3165 (sshd)
```

Alternatively, you can do

`ssh localhost`

The response should look similar to this.

```
username@host:~$ ssh localhost

The authenticity of host 'localhost (127.0.0.1)' can't be established. ECDSA key fingerprint is SHA256:9jqmhko9Yo1EQAS1QeNy9xKceHFG5F8W6kp7EX9U3Rs. Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'localhost' (ECDSA) to the list of known hosts.

username@host:~$
```

---

##### Connecting to Server/Virtual Machine

`ssh your_username@host_ip_address`

Sample response and following authorizations such as password and adding it list of known hosts

```
username@machine:~$ ssh phoenixnap@185.52.53.222 –p7654 phoenixnap@185.52.53.222’s password:

The authenticity of host '185.52.53.222 (185.52.53.222)' can't be established. ECDSA key fingerprint is SHA256:9lyrpzo5Yo1EQAS2QeHy9xKceHFH8F8W6kp7EX2O3Ps. Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added ' 185.52.53.222' (ECDSA) to the list of known hosts. 

username@host:~$
```
