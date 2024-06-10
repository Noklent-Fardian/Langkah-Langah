# Langkah-Langah
## Kelompok 1

BERYL FUNKY MUBAROK (2341720256)  
KHOIROTUN NISA’ (2341720057)  
NOKLENT FARDIAN ERIX (2341720082)



## Yang Akan ditambahkan



1. Theme Whitesur
2. ganti icon aplikasi

3. Tambah detikan pada jam

4. Cursor Hatsume Miku (tidak jadi/Gagal)
5. Grub BootLoader Kobo Kanaeru (Tidak Tentu)



### Install Cubic

```
sudo apt-add-repository universe
sudo apt-add-repository ppa:cubic-wizard/release
sudo apt update
sudo apt install --no-install-recommends cubic
```

## Install Extension

```
apt-get update
apt-get install gnome-session fonts-cantarell adwaita-icon-theme-full -y
apt-get install gnome-shell-extensions gnome-tweaks -y
apt purge ubuntu-desktop gnome-shell-extension-ubuntu-dock ubuntu-session -y
apt autoremove --purge -y

apt-get install git flatpak -y
mkdir /etc/dconf/db/local.d/
echo user-db:user > /etc/dconf/profile/user
echo system-db:local >> /etc/dconf/profile/user
cd /tmp/
```

## Clone Cursor Hatsume Miku dari github (bisa gagal)

```
cd /usr/share/icons/
git clone https://github.com/supermariofps/hatsune-miku-windows-linux-cursors.git 
cd /tmp/
```

## Clone Grub Bootloader theme Kobo Kanaeru (bisa gagal)

```
git clone https://github.com/Noklent-Fardian/Kobo-Clone.git
cd Kobo-Clone
chmod +x install.sh
chroot /path/to/chroot update-grub
cd ..
```

## Clone tema whitesur dari github

```
git clone https://github.com/vinceliuice/WhiteSur-gtk-theme.git --depth=1 
 cd WhiteSur-gtk-theme 
 ./install.sh -d /usr/share/themes
```

## clone icon whitesur

```
cd ..
git clone https://github.com/vinceliuice/WhiteSur-icon-theme.git --depth=1
cd WhiteSur-icon-theme
./install.sh -d /usr/share/icons/
```

## clone wallpaper

```
cd ..
git clone https://github.com/vinceliuice/WhiteSur-wallpapers.git --depth=1
cd WhiteSur-wallpapers
```

## Setting

```
nano install-wallpapers.sh
INI DI GANTI
WALLPAPER_DIR="$HOME/.local/share/backgrounds"
## PAKE INI
WALLPAPER_DIR="/etc/skel/.local/share/backgrounds"
^x
mkdir /etc/skel/.local/
cd /etc/skel/.local/
mkdir share
cd share/
mkdir backgrounds
cd /tmp/
cd WhiteSur-wallpapers
./install-wallpapers.sh
```

## Setting tampilan dengan tweak

```
echo 'export GTK_THEME="WhiteSur-Light"' >> /etc/skel/.profile
flatpak override --filesystem=xdg-config/gtk-4.0
echo [org/gnome/shell/extensions/user-theme] > /etc/dconf/db/local.d/tweaks
echo "name= 'whitesur-Light-solid-pink'" >> /etc/dconf/db/local.d/tweaks
dconf update

echo [org/gnome/desktop/interface] >> /etc/dconf/db/local.d/tweaks
echo "clock-show-seconds=true" >> /etc/dconf/db/local.d/tweaks
echo "icon-theme='WhiteSur' " >> /etc/dconf/db/local.d/tweaks
echo "gtk-theme='WhiteSur-Light-solid-pink'" >> /etc/dconf/db/local.d/tweaks
dconf update
```

```
echo "cursor-theme='Miku-cursor-linux'" >> /etc/dconf/db/local.d/tweaks
```

## Install Extension dash dock

```
cd ..
wget https://extensions.gnome.org/extension-data/dash-to-dockmicxgx.gmail.com.v92.shell-extension.zip -O dash.zip
mkdir -p /usr/share/gnome-shell/extensions/dash-to-dock@micxgx.gmail.com
unzip dash.zip -d /usr/share/gnome-shell/extensions/dash-to-dock@micxgx.gmail.com
chmod o+rx /usr/share/gnome-shell/extensions/dash-to-dock@micxgx.gmail.com/*
echo [org.gnome.shell.extensions.dash-to-dock] > /etc/dconf/db/local.d/dashdock
echo dock-fixed=false  >> /etc/dconf/db/local.d/dashdock
echo custom-theme-shrink=true >> /etc/dconf/db/local.d/dashdock
dconf update
```

## setting extension

```
echo [org/gnome/desktop/background] > /etc/dconf/db/local.d/background
echo "picture-uri='file:///etc/skel/.local/share/backgrounds/WhiteSur-light.jpg'" >> /etc/dconf/db/local.d/background
echo [org/gnome/shell] > /etc/dconf/db/local.d/extensions
echo "enabled-extensions=['apps-menu@gnome-shell-extensions.gcampax.github.com', 'user-theme@gnome-shell-extensions.gcampax.github.com', 'dash-to-dock@micxgx.gmail.com', 'drive-menu@gnome-shell-extensions.gcampax.github.com']" >> /etc/dconf/db/local.d/extensions
glib-compile-schemas /usr/share/glib-2.0/schemas/
dconf update
```



