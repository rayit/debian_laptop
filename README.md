# debian howto

Personal install of Debian Linux 11.1 and tweaks needed on Lenovo p50s
Install without desktop

## Wifi

I have good experience with iwd, so we will use that.
Add a "non-free" component to the apt sources.
```bash
apt update && apt install firmware-iwlwifi
modprobe -r iwlwifi ; modprobe iwlwifi
apt install iwd
```
To surpress stupid error:
vi /etc/modeprobe.d/iwlwifi.conf
...
options iwlwifi enable_ini=N
...
```bash
systemctl --now disable wpa_supplicant
systemctl --now enable iwd
```
 
vi /etc/iwd/main.conf
...
[General]
EnableNetworkConfiguration=true
...

As non root:
iwctl

## Packages I use

```bash
apt install make gcc libx11-dev libxft-dev libxinerama-dev xorg git feh git vim mpv vlc gimp htop fish mupdf neofetch fish slock exa
```
Installing chrome (I need it for debugging nodejs)
```bash
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
echo 'deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main' | tee /etc/apt/sources.list.d/google-chrome.list
apt update && sudo apt install -y google-chrome-stable
```
