2. In Linux how would we allow a machine to connect automatically through ssh?

If we want to create an SSH connection requires both a client and a server component, we need to make sure they are installed on the local and the remote, machine, respectively. Installing OpenSSH is relatively easy. It requires access to the therminal on the server and the computer that we use for connecting. Ununtu does NOT have SSH server installed by default.
How to Install an OpenSSH Client
Before we procceed with installing an SSH client, we need to make sure it is not already installed. For Windows we can install Putty etc. to gain access to a server. 
We need to check if the client is available on our Linux system. 
    i. We load SSH terminal. 
        Either we search for "terminal"
        or
        we press CTRL+ALT+T
    ii. we type : ssh and then we press ENTER
    iii. If it is installed the we will recieve a response looking like this : 
        username@host:~$ ssh

        usage: ssh [-1246AaCfGgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
        [-D [bind_address:]port] [-E log_file] [-e escape_char]
        [-F configfile] [-I pkcs11] [-i identity_file]
        [-J [user@]host[:port]] [-L address] [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port] [-Q query_option] [-R address] [-S ctl_path] [-W host:port] [-w local_tun[:remote_tun]]
        [user@]hostname [command]

        username@host:~$
This means that we are ready to remotely connect to a phsical or virtual machine. 
Otherwise we will have to install the OpenSSH client:
    1. We run the following command to install the OpenSSH client on our computer.
    sudo apt-get install openssh-client
    2. We type our superuser password when asked.
    3. We hit ENTER to complete the installation
We are now able to SSH into any machine with server-side app on it, provided that we have the necessary privileges to gain access, as well as the hostname or IP address

How to Connect via SSH
Now that we have the OpenSSH client installed on our machine, we can establish a secure remote connection with the servers. To do so:

    i.      Open the SSH terminal on our machine and run the following command: ssh our_username@host_ip_address 
            If the username on our local machine matches the one on the server we are trying to connect to, we can just type: ssh host_ip_address And hit Enter.
    ii.     Type in our password and hit Enter. Note that we will not get any feedback on the screen while typing. If we are pasting our password, make sure it is stored safely and not in a text file.
    iii.    When we are connecting to a server for the very first time, it will ask we if we want to continue connecting. Just type yes and hit Enter. 
            This message appears only this time since the remote server   is not identified on our local machine.
    iv.     An ECDSA key fingerprint is now added and we are connected to the remote server.
            If the computer we are trying to remotely connect to is on the same network, then it is best to use the private IP address instead of the public IP address. Otherwise, we will have to use the public IP address only. Additionally, make sure that we know the correct TCP port OpenSSH is listening to for connection requests and that the port forwarding settings are correct. The default port is 22 if nobody changed configuration in the sshd_config file. we may also just append the port number after the host IP address.

Here is the example of a connection request using the OpenSSH client. We will specify the port number as well:

username@machine:~$ ssh phoenixnap@185.52.53.222 –p7654 phoenixnap@185.52.53.222’s password:

The authenticity of host '185.52.53.222 (185.52.53.222)' can't be established. ECDSA key fingerprint is SHA256:9lyrpzo5Yo1EQAS2QeHy9xKceHFH8F8W6kp7EX2O3Ps. Are we sure we want to continue connecting (yes/no)? yes
Warning: Permanently added ' 185.52.53.222' (ECDSA) to the list of known hosts. 

username@host:~$


We are now able to manage and control a remote machine using our terminal. If we have trouble connecting to a remote server, we make sure that:

The IP address of the remote machine is correct.
The port SSH daemon is listening to is not blocked by a firewall or forwarded incorrectly.
our username and password are correct.
The SSH software is installed properly.