# myDesktop
- **Ubuntu 20.04**
- **Lubuntu 18.04**
### Change default editor
```sh
sudo update-alternatives --config editor
```
### Git configuration

- Change default editor to vim
```sh
 git config --global core.editor vim
```
- Set your email and name
```sh
 git config --global user.name "Hamid Gholami"
 git config --global user.email hamid@linuxmail.org
```
### Disable sudo prompt for ask password

Add a file in `/etc/sudoers.d/<FILE_NAME>`

```sh
hamid ALL=(ALL) NOPASSWD: ALL
```
and
```sh
chmod go-r /etc/sudoers.d/<FILE_NAME>
```
### Add some repository in source.list.d
- Docker
- Ansible

### All requirement packages
```sh
sudo apt install \
vim git \
python3 python3-pip \
terminator tmux tree \
zsh \
vlc \
build-essential gcc Ubuntu-restricted-extras \
ca-certificates \
gnome-tweak-tool \
openjdk-11-jdk \
simplescreenrecorder \
unrar zip unzip p7zip-full p7zip-rar rar \
wine winetricks filezilla \
zim \
sshpass \
openssl \
dnsutils \
traceroute \
virtualbox \
curl \
gnupg-agent \
software-properties-common apt-transport-https \
qemu-kvm \
libvirt-bin virtinst virt-viewer virt-manager \
bridge-utils \
cpu-checker \
spice-client-gtk \
remmina remmina-plugin-vnc remmina-plugin-rdp \
mtr-tiny htop \
virt-top imvirt \
apg at bc rsync ftp \
guake \
x11vnc clipit \
docker-ce docker-ce-cli containerd.io
# packer
# ansible
# vagrant
# docker
# docker-compose
# kubectl
# vncviewer
# pptp, l2tp, sstp, openvpn
# kvm, qemu, libvirtd
# zoipper or jitsi

```
----------
### Docker configuration
- `/etc/docker/daemon.json`
- `.docker/config.json`
### Kubernetes
- `.kube`
### Vagrant
- `.vagrant.d`
### i3wm
### ssh
- `.ssh/config`

----------------

All configuration for my desktop
https://fedoramagazine.org/getting-started-i3-window-manager/


### To Do List
- i3
- i3status
- i3lock
- i3lock-multimonitor
- oh-my-zsh
- zsh
- powerline
