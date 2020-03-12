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
1.2 Insert SD card to laptop and clone "Raspbian" image
1.3 Inertt SD card to Raspberry Pi
1.4 Power up the Raspberry Pi

### 2. Enable SSH and set up network config

2.1 In Raspberry Pi GUI
2.2 Set up the location setting
2.3 Enable SSH in Raspberry Pi Preference 
2.4 Restart the Raspberry Pi

### 3. SSH into Pi

3.1 Check the Raspberry Pi IP address though IP scanner
3.2 SSH into Raspberry Pi 
`ssh pi@<IP address>`
Default password: `raspberry`

### 4. Add user account and change Pi default password

4.1 Change default password
`passwd`
4.2 Add new user
`sudo adduser <username>`
4.3 Add user to sudo user
`sudo adduser <username> sudo`
4.4 Restart Raspberry Pi

### 5. Install Node.js and PM2

5.1 Update the system package list
`sudo apt-get update`
5.2 Upgrade all installed packages to latest version
`sudo apt-get dist-upgrade`
5.3 Install Node.js
`sudo apt-get install -y nodejs`
5.4 Check Node.js version
`node -v`
5.5 Install PM2
`npm install pm2@latest -g`

### 6. Generate Key for Github

6.1 Generate SSH key
`ls ~/.ssh`
`ssh-keygen`
6.2 Copy the SSH key
`cat ~/.ssh/id_rsa.pub`
6.3 Add the SSH key into Github setting

### 7. Clone the Repo
7.1 Clone from SSH
`git clone <repo>`
