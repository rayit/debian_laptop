# debian howto

Personal install of Debian Linux 11.1 and tweaks needed on Lenovo p50s
Install without desktop

### Wifi

Will start with this so I can unplug my cable...
I have good experience with iwd, so we will use that.
Add a "non-free" component to the apt sources.
```bash
apt update && apt install firmware-iwlwifi
modprobe -r iwlwifi ; modprobe iwlwifi
apt install iwd
```
To surpress stupid error:
vi /etc/modeprobe.d/iwlwifi.conf
```
options iwlwifi enable_ini=N
```
```bash
systemctl --now disable wpa_supplicant
systemctl --now enable iwd
```
 
vi /etc/iwd/main.conf
```
[General]
EnableNetworkConfiguration=true
```

As non root:
iwctl

### Packages I use

```bash
apt install wget make gcc libx11-dev libxft-dev libxinerama-dev xorg git feh git vim mpv vlc gimp htop fish mupdf neofetch fish slock exa fonts-agave
```

### Suckless
```bash
mkdir -p ~/.local/src
cd ~/.local/src

wget https://dl.suckless.org/dwm/dwm-6.2.tar.gz
wget https://dl.suckless.org/st/st-0.8.2.tar.gz
wget https://dl.suckless.org/tools/dmenu-4.9.tar.gz

tar xf dwm-6.2.tar.gz
tar xf st-0.8.2.tar.gz
tar xf dmenu-4.9.tar.gz

git clone https://git.suckless.org/slstatus ~/.local/src/slstatus
```
For each program.
cp config.def.h -> config.h and change as needed


### chrome (I need it for debugging nodejs)
```bash
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
echo 'deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main' | tee /etc/apt/sources.list.d/google-chrome.list
apt update && sudo apt install -y google-chrome-stable
```

## Sound
```bash
apt install alsa-utils
/sbin/alsactl init
```
