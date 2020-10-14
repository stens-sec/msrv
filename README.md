# msrv

## description

Msrv is a bash script which allows to easily start simple server types to quickly deliver files via a range of protocols, or spawn a reverse shell listener via netcat.

The following server types are available:
* nc (for reverse shell listener)
* http (for http file transfer)
* ftp (for ftp file transfer)
* tftp (for tftp file transfer)
* smb (for smb file transfer)
* ssh (for ssh login and file transfer)
* smtp (for faking a simple smtp server)

Msrv displays your tun0-IP and useful status information, as well as the used commands, so you can easily include them in reports or scripts.

## installation

### clone github repo

```
git clone https://github.com/stens-sec/msrv.git
```

### install apt dependencies

```
apt install -y sudo iproute2 netcat openssh-server python3 python3-pip
```

### install pip dependencies

```
sudo pip3 install -r requirements.txt 
```

### copy script to PATH directory

```
# copy script to /usr/local/bin and set permissions
sudo cp msrv /usr/local/bin/msrv
sudo chown root:root /usr/local/bin/msrv
sudo chmod 755 /usr/local/bin/msrv
```

### configure sudoers

```
# configure if you want to run msrv passwordless (must be run as root)
sudo MSRV_USER=$(whoami) sh -c 'echo "${MSRV_USER}    ALL=NOPASSWD: /usr/local/bin/msrv" > /etc/sudoers.d/msrv'
```

## usage

```
Specify sever type and port for the server to listen on. If no port is specified, the default port for the service is used.

# msrv SERVER_TYPE PORT
# e.g. 
msrv http 8080

# get help
msrv
```

## uninstallation

```
sudo rm /usr/local/bin/msrv
sudo rm /etc/sudoers.d/msrv
echo "please remove pip3 packages manually via:"
echo "sudo python3-pip uninstall -r requirements.txt"
```
