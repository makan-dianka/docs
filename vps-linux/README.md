# Secure VPS (Virtual Private Server)

This doc help to secure your vps on OVH, AWS, DIGITALOCEAN etc.

After Created your server and ssh into it, make sure to execute these commande first of all.


## update and upgrade the packages

```
sudo apt upgrade && sudo apt upgrade -y
```

## Change default port of ssh (22)

open ```/etc/ssh/sshd_config``` found the port and change it to your choice between ```49152``` and ```65535```



```
sudo nano /etc/ssh/sshd_config
```

Save the file and restart ssh service

```
sudo systemctl restart ssh.service
```


Now you have to reboot your VPS


```
sudo reboot
```


After reboot your VPS you can connect to it with your new port number such as


```
ssh user@host -p portnumber
```

- Note: For each connection with ssh you have to indicate your port number with flag ```-p``` follow the port number 






## Create User with less privilege

This user will not have the sudo privilege.


```
sudo adduser newUserName
```


Create password for newUserName


```
sudo passwd newUserName
```

This user can't execute the commande with sudo. 
- Note: Connect with this user when you use the third-party applications


## Add the user to sudoers

To add an user to sudo user.


```
sudo usermod -aG sudo userName
```

- Note: (Warning!)  This user can execute any commande with sudo


## Switch between users

Switch to an other user 


```
sudo su userName
```


## Deactivate user

Deactivate an user to be unable to connect the server

```
sudo passwd -dl userName
```


## Reactivate user

Reactivate an user to be able to connect the server

```
sudo usermod userName -p temporaryPassword
```


## Delete user 

Delete an user with his files definitely

```
sudo userdel -r -f username
```
