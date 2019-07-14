# alpine linux basic installation guide for raspberry pi 3
_Created 11 July 2019_

## Start :
1. Download image from https://alpinelinux.org/downloads/
2. Unzip it.
3. Format SD card `FAT32`
4. Copy All file and paste to SD card
5. Insert SD Card into Pi
6. Power on
7. Login as root ( no password)

## Set Up Pi :

#### Special Note : 
Changes are not persistent. So you should commit them. It will save your changes under `/etc`.
  ```bash
  lbu_commit -d 
  ```
### Initial setup : 
1. You can ran alpine from ram. You can also run it from SD/HDD. For complete setup, you should start with below command. 
  ```bash 
  setup-alpine
  ```
  Set up language, keyboard, time-zone, hostname, network, disk mode etc. 
2. Set root password.

3. Update `/etc/apk/repositories` file. This will allow you to download applications from community.
  ```bash
  vim /etc/apk/repositories
  ```
Remove `#` from `<url>/community`, `<url>/edge/main`, `<url>/edge/community`. 

4. Install some useful applications
  ```bash
  apk add consolekit2 sudo dbus vim
  ```
  
5. Add new user. -h for `HOME DIRECTORY`
  ```bash
  # adduser -h <username> <username>
  ```
6. Give sudo permission. Update `/etc/sudoers` file.
  ```bash
  vim /etc/sudoers
  ```
  Add a line and save.
  ```bash
  <username> ALL=(ALL) ALL
  ```
6. If you want to run Alpine with GUI, XFCE Destop will be best for you. 
`setup-xorg-base` script is a build in script. But it is not include in `setup-alpine` script. So you need to manually run this. `setup-xorg-base` you can run with parameters

  ```bash
  setup-xorg-base xfce4 xf86-video-fbdev xfce4-terminal lightdm-gtk-greeter xfce-polkit xfce4-screensaver xf86-input-mouse     xf86-input-keyboard
  setxkbmap kbd
  rc-update add dbus
  ```
7. Now you can start GUI
  ```bash
  startx
  ```

     
 

