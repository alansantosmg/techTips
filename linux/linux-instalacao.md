# Linux - Instalação

## create ssh-key

```bash
cd ~
ssh-keygen
```

## add signal IM

```bash
wget -O- https://updates.signal.org/desktop/apt/keys.asc |\\\n  sudo apt-key add -

echo "deb [arch=amd64] https://updates.signal.org/desktop/apt xenial main" |\\\n  sudo tee -a /etc/apt/sources.list.d/signal-xenial.list
```

## Adicionando pacotes essenciais

```bash
# Add slimbook battery repo
sudo add-apt-repository ppa:slimbook/slimbook
sudo apt-get update
sudo apt install git vim-gtk3 imwheel exuberant-ctags curl fish synaptic fzf fonts-powerline mpv mplayer slimbookbattery   ttf-mscorefonts-installer vscode htop remmina calibre
sudo snap install color-picker glow draw.io shortwave anki flameshot goodvibes Stacer scribus signal-desktop
```

## Corrige problema do phone bluetooth que faz internet wifi ficar lenta linux mint

```bash  
sudo echo "options iwlwifi 11n_disable=1 bt_coex_active=1" >> /etc/modprobe.d/iwlwifi.conf
```

## Set fish as default shell

```bash
chsh -s /usr/bin/fish
```

## Install spacefish

```bash
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \\\n    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
curl -sL https://git.io/fisher | source && fisher install jorgebucaran/fisher
fisher install matchai/spacefish
```

## Git setup

```bash
cd ~
mkdir src
cd src
mkdir github.com
cd github.com
git config --global user.name alansantosmg
git config --global user.email alansantosmg@hotmail.com
```

## Update themes

```bash
cd ~
gtk-update-icon-cache /home/alan/icons/Papirus-Dark
gtk-update-icon-cache /home/alan/.icons/Papirus-Dark
gtk-update-icon-cache /home/alan/.icons/Flat-Remix-Blue-Dark
```

## Update font cache

```bash
sudo fc-cache -v -f
```

## Intall golang

```bash
cd ~/Downloads
sudo tar -C /usr/local -xzf go1.15.6.linux-amd64.tar.gz
```

## Corrigir erro init-ramfs ubuntu e mint

```bash
cd /etc/initramfs-tools/
sudo vim initramfs.conf
COMPRESS=gzip
sudo update-initramfs -u
```

## Corrigir erro pci laptop hp

```bash
cd /etc/default
sudo vim grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nomsi,noaer"
GRUB_CMDLINE_LINUX="pci=nomsi,noaer"
sudo update-grub
```

## Install Hugo

```bash
cd ~/src/github.com/hugo
hugoCGO_ENABLED=1 go install --tags extended
```

## Corrigir erro monitoramento arquivos vscode

```bash
 cat /proc/sys/fs/inotify/max_user_watches
 echo "fs.inotify.max_user_watches=32768" >> /etc/sysctl.conf
```

## Corrigir erro wifi after suspend mode - xubuntu / mint xfce

### Solução 1

```bash
sudo iwconfig wlo1 power off
```

### Solução 2

```bash
sudo vim /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf.
# File to be place under /etc/NetworkManager/conf.d
#
[connection]
# Values are 0 (use default), 1 (ignore/don't touch), 2 (disable) or 3 (enable).[connection]
wifi.powersave = 2
```

### Solução 3

```bash
# criar o arquivo:
sudo vim /etc/systemd/system/wifi-resume.service
```

```bash
# conteudo do arquivo
 [Unit]
Description=Local system resume actions
After=suspend.target
[Service]
Type=oneshot
ExecStart=/bin/systemctl restart network-manager.service
[Install]
WantedBy=suspend.target
 ```

 ```bash
 # Tornar arquivo executavel
 sudo chmod +x  /etc/systemd/system/wifi-resume.service`
 # habilitar inicio automatico pelo sysctl
 `sudo systemctl enable wifi-resume.service` 
 ```

## Corrigir erro DNS e lentidão wifi - xubuntu

```bash
 sudo vim /etc/nsswitch.conf
# hosts:          files mdns4_minimal [NOTFOUND=return] dns
hosts files dns
```

## Correção teclas F no Vscode

* Para Vscode funcionar corretamente, desativar Workspace Ctrl+Fn em settings/window manager/Keyboard

## Setar tecla Windows no - Xubuntu

```bash

xfce4-popup-whiskermenu = tecla windows

```

## Setar segundo monitor à esquerda - Xubuntu e MintX

* Para funcionar com segundo monitor a esquerda ir em `panel preferences`, desmarcar  `span monitors`.
* Escolher o monitor que deve aparecer o painel em output.

## Acertar hora no Mintx e Xubuntu em máquinas dual boot com Windows

* Execute um destes dois comandos que correspondem à sua hora local

```bash
timedatectl set-local-rtc 1 --adjust-system-clock
# ou: 
timedatectl set-local-rtc 0 --adjust-system-clock
```
