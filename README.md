# SSH PROTOCOL (SECURE SHELL)==
## Contents
1. Introduction 
2. List of manipulations carried out 
3. Problems encountered and solutions 
4. Theoretical analysis
5. Conclusion
6. Resources 
## 1. Introduction :
The Secure Shell (SSH) protocol is a method of sending commands securely to a computer on an unsecured network. SSH uses cryptography to authenticate with a key and encrypt connections between devices. SSH also enables tunnelling, or port forwarding, i.e. packets can traverse networks that they would not otherwise be able to cross. SSH is often used to control servers remotely, to manage infrastructure and transfer files.

In this step-by-step exercise, I've set up a secure connection between my computer and an ubuntu virtual server on IONOS, using the SSH protocol. 

## 2. List of manipulatios performed:
### 1.create an SSH profile for a remote connection to my IONOS server: 
- connect to the remote server with the following command : `ssh root@ IP-adress` and the password of the remote server that I use in my server account
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
- info: Adding new user `user' to supplemental / extra groups users'...
- info: Adding user `user' to group users' ... (the user is created)

The clear command is used to clear the previous steps and reshape the page. [¹]
- Ssh user@ip-adress (server) - password with which I created the user -----> connection to remote server is established
- The connection to the remote server is checked with the following commands: ls - pwd and whoami

### 2. SSH key authentication

  #### 2.1-Generating and using SSH keys
- /Generate an ssh key to set up authentication and secure connections.
- /The command to type locally is: `ssh-keygen -t ed25519`.

- The ssh-keygen command will now display the SSH key fingerprint and the random image of the public key. Here's what the output should look like from start to finish:

`ssh-keygen -t ed25519`

Generating public/private ed25519 key pair

Enter file in which to save the key (/home/local_username/.ssh/id_ed25519):`

`Enter passphrase (empty for no passphrase):`

Enter the same passphrase again:`

`Your identification has been saved in /home/local_username/.ssh/id_ed25519`

`Your public key has been saved in /home/local_username/.ssh/id_ed25519`

- /The private key is saved in `~/.ssh/id_rsa` and the public key in
`~/.ssh/id_rsa.pub.`

#### 2.2-Disable password authentication 
Install the public key in the remote server with the command: `ssh-copy-id username@IP-adress`.
    
- /Connect to remote server without password from computer in use
- Test connection with SSH key, without password: `ssh username@IP-adress` **it's works**


  ### 3. File transfer with SCP and SFTP
    #### 1. Using SCP (Secure Copy) to transfer files
The purpose of SCP (Secure Copy) is to transfer files between the local machine and a remote server via SCP.

* Create a local file: echo “This is a test file” > toto.txt
* to transfer the file to the remote server, issue the command `scp toto.txt username@server IP address:/home/username/`.
* to check the file on the server, write the command `ssh username@IP-adress “ls -l /home/username/`



    #### 2. Using SFTP for interactive transfer
SFTP (Secure File Transfer Protocol) is a secure file transfer protocol that uses secure shell encryption to provide a high level of security for sending and receiving files. 



* SFTP connection for browsing and transferring files, the command to use is: ` sftp username@server IP address`.

You can navigate with the `ls` command, then `cd/home/username/`. 

Transfer a file to the server with the command: `put fichier.txt`.

  ### 4. SSH tunnel creation and port forwarding
  
 #### 1. Local redirection with SSH to secure a remote service via an SSH tunnel
    
The steps to follow are :

* Install the Nginx web service with the command `sudo apt install nginx`.
* Check UFW status with `sudo ufw status` if it's not enabled, you need to enable it with `sudo ufw enable` or authorize HTTP connections with `sudo ufw allow 80` / HTTPS connections with `sudo ufw allow 443`.

*Note: my command `sudo ufw allow (port number)` configures the firewall to allow the ports we want to allow*.

*To implement the changes made to the server configuration, we can type the command `sudo systemctl reload ssh`.

Redirect local port 8080 to port 80 on a remote server: `ssh -L 8080:localhost:80 username@IP-adress`.
  #### 2.  Access the application via the local port:
 Open a browser and go to http://localhost:8080.

  ### 5. Securing the SSH server
  #### 5-1. change SSH port 
    
 explain 

So I'm going to change the default SSH port 

   1. I delete port 22 in the IONOS remote server panel 
   2. I authorize port 2222 in the IONOS remote server panel 
   3. I reboot the server with the command `sudo reboot`.
   4. Problem -> I can't connect to my remote server since I deleted port 22
**the solution is explained in the problems encountered and solutions found section**.

 #### 5-2. Restart the SSH service 
    
to apply the changes once you have implemented the solutions (see Problems encountered and solutions found). 
Command:  `sudo systemctl restart ssh`

Connect to the new port Command : `ssh -p username@ip address`

And it works



### 3. Problems encountered and solutions found 
  ### 1. redirect local port 8080 to port 80 on my remote server

### Enable UFW :
By default, UFW is configured to deny all incoming traffic and allow all outgoing traffic. This means that no one else can access your system, while you can make outgoing requests from any application or service.

*when I activated the firewall on my IONOS server with the command `sudo ufw enable`, it was impossible to receive requests from the outside (local server)*.

    1. I authorized the SSH port with the command sudo `ufw allow 'OpenSSH`.
    2. I authorized ports 80 and 443 with the command `sudo ufw allow 'Nginx Full`.
    3. I then restarted the firewall to apply the changes with the command: `sudo ufw reload`.

On the local browser, I wrote the command: ssh -L localhost:80 username@IP-adresses

It worked 

  ### 2. Securing the SSH server

    ### change SSH port
By deleting port 22 in the remote server panel, I can't connect to my remote server 

**Solution**:

   1. I connect to my remote server's console root
   2. I uncomment port 22 by removing the #.
   3. I add port 2222 above port 22, then validate with ctrl X -> enter, then reboot the server with the command: `sudo reboot`.
   5. Still in the remote server console, I follow the next steps:
       - I open the ports authorized by my server's firewall :
               with the following command: `sudo ufw status numbered`. 
       - I delete port 2222 with the command: `sudo ufw delete port number`.
       - I add port 2222 again with the command: `sudo ufw allow 2222`.
   6. I restart my remote server with the command: `sudo reboot`.
   7. I enter the command `ssh -p 2222 username@IP-adress` and it works, the port has been successfully changed.


