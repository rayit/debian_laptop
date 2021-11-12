# debian howto

Install without desktop minimal on lenovo p50s

```bash
apt install make gcc libx11-dev libxft-dev libxinerama-dev xorg
```

## Wifi

Add a "non-free" component to the apt sources.

Update the list of available packages and install the firmware-iwlwifi package:

apt update && apt install firmware-iwlwifi
As the iwlwifi module is automatically loaded for supported devices, reinsert this module to access installed firmware:

modprobe -r iwlwifi ; modprobe iwlwifi

apt install iwd



vi /etc/modeprobe.d/iwlwifi.conf
and then entering the following content

options iwlwifi enable_ini=N



systemctl --now disable wpa_supplicant

systemctl --now enable iwd



create 
vi /etc/iwd/main.conf

[General]
EnableNetworkConfiguration=true

As non roou:

iwctl


