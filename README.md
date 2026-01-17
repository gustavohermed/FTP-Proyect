# FTP Servers Practice
- A simple FTP server configured, for anonymous users only (IP: 192.168.56.10).
- A secure FTP server with a self-signet SSL certificate, for local users (IP: 192.168.56.20).

## Anonymous FTP server features:
- Anonymous access only.
- No write permissions (read-only).
- Max 200 simultaneous connections.
- 50KB/s bandwidth limit per user.
- 30-second inactivity timeout.
- IPv4 only.

## Secure FTP server features:
- Local users access with password.
- Chroot jail for some users.
- Max 15 simultaneous connections.
- 5MB/s bandwidth limit for local users.
- 2MB/s bandwidth limit for anonymous users.
- 720-second inactivity timeout.
- IPv4 only.

## General requirements:
- Virtualbox.
- Vagrant.
- Ansible.
- FTP tool.
- FTP graphic client (optional).
- Internet connection.
If you don’t have them installed, you could set them up with:

### Linux:
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y virtualbox 
sudo apt install -y vagrant
sudo apt install -y ansible
sudo apt install -y ftp
```

### Windows:
Incompatibility because of ansible tool.

## Quick setup.
### 1. Install requirements:
```bash
# install the necesary requirements previusly mentioned...
```
### 2. Clone and run:
```bash
git clone https://github.com/gustavohermed/FTP-Proyect.git
cd FTP-Proyect
vagrant up
```
### 3. Connect to FTP:
```bash
ftp 192.168.56.10
# Username: anonymous
# Password: (press Enter)
-or-
ftp 192.168.56.20
# Username: <luis/maria/miguel>
# Password: "SecurePass123"
```
### 4. Simple FTP usage:
```bash
# List available files
ls

# Download a file
get WELCOME.txt

# Upload a file
put <file name>

# Create a directory
mkdir <directory name>

# Move between directories
cd <route>
```
### (Optional). Shut down and unistallation:
```bash
vagrant halt
vagrant destroy -f
```

## Troubleshooting.
### 1. Conecting with the FTP server:
If you can't stablish connection with any of the FTP servers; firts check if service is running properly in the VMs.
```bash
systemctl status vsftpd
sudo systemctl restart vsftpd
```
If the problem didn't solve, try checking if your 21 port is listening in your host machine.
```bash
ss -tuln | grep :21
```
### 2. Problems with the SSL certifie on graphic client:
If, while trying to establish connection with a graphic client, like fileZilla, you encounter an error about SSL or TLS; check on the official web page of that client, the compatible SSL or TLS versions. Then, in the VMs, go to /etc/vsftpd.conf and change the configuration for a proper ones (the versions stablished rightnow are for the ultimate version of fileZilla client).

## Documentation.

![ vsftpd service active](./screenshots/Screenshot_14.png)
Before doing any testing, and after the vagrant up has finished, we checked that our VMs, vsftpd service, is working properly.
<br>

![port 21 active](./screenshots/Screenshot_15.png)
And ofcourse we checked that the 21 port of our host machine is active and listening. 
<br>

### Anonymous FTP server:

![conection to the server](./screenshots/Screenshot_1.png)
After configuring and setting up the anonymous server, we tried to connect trough the command line of our host, with anon user; this being successfully.  
<br>

![read permisions](./screenshots/Screenshot_2.png)
Then, we tried the read permisions, making sure they work properly.
<br>

![write permisions](./screenshots/Screenshot_3.png)
Now, trying the denied write permiesion, trying to upload a file.
<br>

![trying donwload](./screenshots/Screenshot_4.png)
Also, we tried that we can donwload files normaly...
<br>

![fileZilla conection](./screenshots/Screenshot_5.png)
And finaly, we tried connecting to the server trough "fileZilla".
<br>

### Secure FTP server:

![trying chroot jail (maria)](./screenshots/Screenshot_6.png)
After configuring and setting up the secure server, we connect trough the command line of our host, with "maria" user credentials, and test that she isn't chroot jailed.
<br>

![trying chroot jail (luis)](./screenshots/Screenshot_7.png)
Then, change into "luis" user, and test that he, indeed, is chroot jailed.
<br>

![fileZilla stablishing site](./screenshots/Screenshot_8.png)
![fileZilla conection](./screenshots/Screenshot_9.png)
Now, we connected to fileZilla, firts stablishing the site, and then loging in with the user credentials...
<br>

![TLS certificate](./screenshots/Screenshot_10.png)
Here we can see the certificate details.
<br>

![download 1](./screenshots/Screenshot_11.png)
![download 2](./screenshots/Screenshot_12.png)
After the success login, we tried donwloading a file normaly.
<br>

![download 2](./screenshots/Screenshot_13.png)
And finally, we tried loging in with an anon user.
<br>


## That's all folks.
Thanks for readding, and we hope it works for you all too!

### Created by:
- Gustavo Heredia Medina
- Daniel Rodríguez Cabello

from 2º ASIR-B [[IES Zaidín Vergeles](https://www.ieszaidinvergeles.org/)].
