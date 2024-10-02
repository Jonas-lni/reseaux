# SSH PROTOCOL (SECURE SHELL)

## SSH protocol definition:

The Secure Shell (SSH) protocol is a method of sending commands securely to a computer on an unsecured network. SSH uses cryptography to authenticate with a key and encrypt connections between devices. SSH also enables tunnelling, or port forwarding, i.e. packets can traverse networks that they would not otherwise be able to cross. SSH is often used to control servers remotely, to manage infrastructure and transfer files.

In this step-by-step exercise, I've set up a secure connection between my computer and an ubuntu virtual server on IONOS, using the SSH protocol. 

## List of manipulatios performed:
### 1.create an SSH profile for a remote connection to my IONOS server: 
- connect to the remote server with the following command : ssh root@ IP-adress and the password of the remote server that I use in my server account
- I create a user with the following command: adduser "name of the user I want to create" 
- I give a password to the user I've created, then confirm the password by writing it a second time
  - passwd: password unchanged
  - Try again? [Y/N] -> Yes
- I fill in the new user information
  -  Full Name []: 
  -  Room Number []: 
  -  Work Phone []: 
  -  Home Phone []: 
  -  Other []: 
  -  Is the information correct? [Y/n] ---> yes
- info: Adding new user `user' to supplemental / extra groups `users' ...
- info: Adding user `user' to group `users' ... (the user is created)
The clear command is used to clear the previous steps and reshape the page. [¹]
- ssh user@ip-adress (server) - password with which I created the user -----> connection to remote server is established
    - the connection to the remote server is checked with the following commands: ls - pwd and whoami

### 2.SSH key authentication: 
- First, generate SSH keys locally (from your laptop) with the command "ssh-keygen -t ed25519"
- secondly, copy the public key generated with the command ssh-keygen -t ed25519 to the remote server with the command: "ssh-copy-id username@IP address"
- disable password authentication for more secure connection with : "ssh -i id-ed25519 username@IP adress"

### 3.file transfer with SCP and SFTP:
SCP differs from other file transfer methods by using SSH for data transfer, offering security through encryption. The SFTP protocol enables you to transfer files securely. It secures files using SSH encryption only
 
 




