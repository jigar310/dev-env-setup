# dev-env-setup
This is an ansible playbook project that automates the setup of a java development enviornment.

Minimum version of Ansible required to run this successfully is 2.6

## Prerequisites

To install all the dev tools in a fresh enviornment, Install an Ubuntu to your computer as a virtual machine and make sure the correct network settings are applied so that it is accessible fron outside network (Prefrably - Bridged Adapter for Oracle VirtualBox). Then make sure you have openssh-server is installed in your ubuntu. Below is the command to install openssh-server.

```
sudo apt install openssh-server
```

If you do not already have SSH keys generated, Generate an SSH key in your machine from where you are going to run this ansible playbook.

```
# ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/ylo/.ssh/id_rsa): mykey
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in mykey.
Your public key has been saved in mykey.pub.
The key fingerprint is:
SHA256:GKW7yzA1J1qkr1Cr9MhUwAbHbF2NrIPEgZXeOUOz3Us ylo@klar
The key's randomart image is:
+---[RSA 2048]----+
|.*++ o.o.        |
|.+B + oo.        |
| +++ *+.         |
| .o.Oo.+E        |
|    ++B.S.       |
|   o * =.        |
|  + = o          |
| + = = .         |
|  + o o          |
+----[SHA256]-----+
#
```

Copy the public key of the machine from where you are going to run this ansible playbook to the target machine.
```
ssh-copy-id -i ~/.ssh/mykey user@target
```

If above command shows error saying permission denied then login to your target machine with root user
1. As root, edit the sshd_config file in /etc/ssh/sshd_config:
```
sudo vim /etc/ssh/sshd_config
```
2. Change the PasswordAuthentication to yes from no
```
PasswordAuthentication yes
```
3. Press Escape, save the file and exit
```
wq!
```
4. Restart the ssh server
```
sudo service ssh restart
```

Now try again to copy the ssh keys.
