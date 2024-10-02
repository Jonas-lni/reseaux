# SSH PROTOCOL (SECURE SHELL)

## SSH protocol definition:

The Secure Shell (SSH) protocol is a method of sending commands securely to a computer on an unsecured network. SSH uses cryptography to authenticate with a key and encrypt connections between devices. SSH also enables tunnelling, or port forwarding, i.e. packets can traverse networks that they would not otherwise be able to cross. SSH is often used to control servers remotely, to manage infrastructure and transfer files.

In this step-by-step exercise, I've set up a secure connection between my computer and an ubuntu virtual server on IONOS, using the SSH protocol. 

## List of manipulatios performed:
### 1.create an SSH profile for a remote connection to my IONOS server: 
- connect to the remote server with the following command : ssh root@ IP-adress and the password of the remote server that I use in my server account
- I create a user with the following command: adduser "name of the user I want to create" 
- I give a password to the user I've created, then confirm the password by writing it a second time.
  - passwd: Authentication token manipulation error
  - passwd: password unchanged
  - Try again? [Y/N] -> Yes
- I fill in the new user information
  -  Full Name []: 
  -  Room Number []: 
  -  Work Phone []: 
  -  Home Phone []: 
  -  Other []: 
  



