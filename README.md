# CloneRaspberryPi
Quick manual of combined resource for clone RapsberryPi from scratch 

|Session|Topic|
|---|---|
|1|Clone RaspberryPi image|
|2|Enable SSH and set up network config|
|3|SSH into Pi|
|4|Add user account and change Pi default password|
|5|Install Node.js and PM2|
|6|Generate Key for Github|
|7|Clone the Repo|

### 1. Clone RaspberryPi image

1.1 Downlaod and install Raspberry Pi Imager (https://www.raspberrypi.org/downloads/)  
1.2 Insert SD card to laptop and clone `Raspbian` OR `Ubuntu LTS 64-bit`  
1.3 Extract and re-insert the SD card  
1.4 Enable SSH setting  
```
cd /Volumes/<SD>
```
1.5 Add SSH enable setting file
```
touch ssh
```
1.6 Insert SD card to Raspberry Pi  
1.7 Power up the Raspberry Pi  

### 2. Enable SSH and set up network config (skip if 1.4 - 1.5 comply)

2.1 In Raspberry Pi GUI  
2.2 Set up the location setting  
2.3 Enable SSH in Raspberry Pi Preference  
2.4 Restart the Raspberry Pi  

### 3. SSH into Pi

3.1 Check the Raspberry Pi IP address though IP scanner  
3.2 SSH into Raspberry Pi (for Raspbian)
```
ssh pi@<IP address>
```  
Default password: `raspberry`  
3.3 SSH into Raspberry Pi (for Ubuntu)  
```
ssh ubuntu@<IP address>
```  
Default password: `ubuntu`  
Change password at first login are required for ubuntu

### 4. Add user account and change Pi default password

4.1 Change default password  
```
passwd
```  
4.2 Add new user  
```
sudo adduser <username>
```  
4.3 Add user to sudo user  
```
sudo adduser <username>
```
4.4 Restart Raspberry Pi  

### 5. Install Node.js and PM2

5.1 Update the system package list  
```
sudo apt-get update
```  
5.2 Upgrade all installed packages to latest version  
```
sudo apt-get dist-upgrade
```  
5.3 Install Node.js  
```
sudo apt-get install -y nodejs
```  
5.4 Check Node.js version  
```
node -v
```  
5.5 Install NPM
```
sudo apt install npm
```
5.6 Install PM2  
```
sudo npm install pm2@latest -g
```  

### 6. Generate Key for Github

6.1 Generate SSH key  
```
ls ~/.ssh
ssh-keygen
```  
6.2 Copy the SSH key  
```
cat ~/.ssh/id_rsa.pub
```  
6.3 Add the SSH key into Github setting  

### 7. Clone the Repo  
7.1 Clone from SSH  
```
git clone <repo>
```  

### 8. Network Config
8.1 For Raspbian, use `raspi-config` tool
```
sudo raspi-config
```
8.2 For Ubuntu, edit netplan config
```
sudoedit /etc/netplan/50-cloud-init.yaml
```
![alt text](https://github.com/PolaKuroda/CloneRaspberryPi/blob/master/img/netplan.png?raw=true)

for save and exit, `^X` confirm with `Y` then `Enter`  

Deploy setting

```
sudo netplan apply
```

### 9. Add Pi Box control
9.1 Install Argno One program on Ubuntu
https://github.com/meuter/argon-one-case-ubuntu-20.04

9.2 Install Argno One program on Raspbian
```
curl https://download.argon40.com/argon1.sh | bash
```

### 10. Get Pi Serial Number

```
cat /proc/cpuinfo
```

### 11. Revoke SSH key from previous address

```
ssh-keygen -R <Target IP>
```

### 12. Install on screen keyboard

```
sudo apt install matchbox-keyboard
```

if `Accessories` -> `Keyboard` did not shown up

1. Restart the pi OR
2. in terminal

```
DISPLAY=:0 matchbox-keyboard &
```

### 13. Fix for Anydesk cannot start up (update at 2021/12/30)

in terminal,

```
sudo apt install libgles-dev libegl-dev
sudo ln -s /usr/lib/arm-linux-gnueabihf/libGLESv2.so /usr/lib/libbrcmGLESv2.so
sudo ln -s /usr/lib/arm-linux-gnueabihf/libEGL.so /usr/lib/libbrcmEGL.so
```

Source of trick: [anydesk: error while loading shared libraries libbrcmglesv2.so](https://raspberrypi.stackexchange.com/a/133496)
