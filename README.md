# FTP Servers Practice
Simple FTP server configured for anonymous users only.

## Features:
- Anonymous FTP access only
- No write permissions (read-only)
- Max 200 simultaneous connections
- 50KB bandwidth limit per user
- 30-second inactivity timeout
- IPv4 only

## Requirements:
- Virtualbox.
- Vagrant.
- Ansible.
- FTP tool.
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
Incompatible because of ansible...

## Quick Start.
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
```
### 4. Simple FTP usage:
```bash
# List available files
ls
# Download welcome file
get WELCOME.txt
# Try to upload a file (should fail)
put <anyfile>.txt
# Try to create directory (should fail)
mkdir <filename>
```
### (Optional). Shut down and unistallation:
```bash
vagrant halt
vagrant destroy -f
```


  
## That's all folks.
Thanks for readding, and we hope it works for you all too!

### Created by:
- Gustavo Heredia Medina
- Daniel Rodríguez Cabello

from 2º ASIR-B [[IES Zaidín Vergeles](https://www.ieszaidinvergeles.org/)].
