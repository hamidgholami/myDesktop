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
- vscode
- qbittorrent

### All requirement packages
```sh
sudo apt-get install \
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
curl ipython3 \
openssh-server openssh-client \
gnupg-agent code \
software-properties-common apt-transport-https \
qemu-kvm \
libvirt-bin virtinst virt-viewer virt-manager \
bridge-utils \
cpu-checker \
spice-client-gtk \
remmina remmina-plugin-* \
mtr-tiny htop \
virt-top imvirt \
apg at bc rsync ftp \
guake chromium-browser \
x11vnc clipit cups-pdf \
docker-ce docker-ce-cli containerd.io \
openvpn network-manager-openvpn \
network-manager-openvpn-gnome network-manager-vpnc \
network-manager-l2tp network-manager-l2tp-gnome \
qbittorrent mlocate net-tools cpu-checker \
font-farsiweb fonts-powerline \
gnome-twaek-tool zsh-syntax-highlighting \

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
### Install packer
[Offical packer installation](https://learn.hashicorp.com/tutorials/packer/getting-started-install)

- Add HashiCorp GPG.

```sh
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
```
- Add HashiCorp repository.

```sh
sudo apt-add-repository \
     "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
```
- Update and install.

```sh
sudo apt-get update && sudo apt-get install packer
```
### Install KVM, qemu, libvirt
Before continuing with the installation, make sure your Ubuntu host machine supports KVM virtualization. The system should have either an Intel processor with the VT-x (vmx), or an AMD processor with the AMD-V (svm) technology support.

Run the following grep command to verify that your processor supports hardware virtualization:
```sh
grep -Eoc '(vmx|svm)' /proc/cpuinfo
```
If the CPU supports hardware virtualization, the command will output a number greater than zero, which is the number of the CPU cores. Otherwise, if the output is 0 it means that the CPU doesn’t support hardware virtualization.

On some machines, the virtual technology extensions may be disabled in the BIOS by the manufacturers.

- To check if VT is enabled in the BIOS, use the kvm-ok tool.

```sh
kvm-ok
```
```ini
output

INFO: /dev/kvm exists
KVM acceleration can be used
```
- Install packages

```sh
sudo apt install qemu libvirt-daemon-system \
libvirt-clients libxslt-dev libxml2-dev libvirt-dev \
zlib1g-dev ruby-dev ruby-libvirt ebtables dnsmasq-base \
qemu-kvm libvirt-daemon-system libvirt-clients \
bridge-utils virtinst virt-manager libvirt-bin libvirt-doc
```
- Start and enable libvirtd daemon service.

```sh
sudo systemctl is-active libvirtd
```
- To be able to create and manage virtual machines, you’ll need to add your user to the “libvirt” and “kvm” groups. To do that, enter:

```sh
sudo usermod -aG libvirt $USER
sudo usermod -aG kvm $USER
```
### Install Vagrant
Download deb/rpm package from [vagrant official website](https://www.vagrantup.com/downloads).
- Install vagrant package.

```sh
sudo dpkg -i vagrant_2.2.13_i686.deb
# or
sudo apt install ./vagrant_2.2.13_i686.deb
```
- Now, install **vagrant-libvirt** plugin using command:

```sh
vagrant plugin install vagrant-libvirt
```
- You also need to install **vagrant-mutate** plugin which converts vagrant boxes to work with different providers.

```sh
vagrant plugin install vagrant-mutate
```
### Install Docker
[Official docker installation](https://docs.docker.com/engine/install/ubuntu/)
- Remove old docker versions.

```sh
sudo apt-get remove docker docker-engine docker.io containerd runc
```
- Install docker repository

```sh
sudo apt-get update
```
```sh
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```

- Add Docker’s official GPG key:

```sh
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

- Add docker repository

```sh
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```
- Install docker engine

```sh
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```
- Add user in docker goup.

```sh
sudo usermod -aG docker $USER
```

- Install docker-compose

```sh
pip3 install docker-compose
```

- Docker configuration<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`/etc/docker/daemon.json`<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`~/.docker/config.json`

### Install ansible

```sh
pip3 install ansible
pip3 install ansible-cmdb
```

### Kubernetes
- `.kube`
### Vagrant
- `.vagrant.d`
### i3wm
### ssh
- `.ssh/config`

----------------
### oh-my-zsh
- Firstly, you should install `zsh`.

```sh
sudo apt install zsh
```
- After the installation is complete, change the default shell of the root user to zsh with the chsh command below.

```sh
chsh -s /usr/bin/zsh root
```
- Now logout from the root user, log in again, and you will get the zsh shell. Check the current shell used with the command below.

```sh
echo $SHELL
```

- Install `oh-my-zsh` from its official github repository or website.

```sh
sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```
- So, oh-my-zsh is installed in the home directory `~/.oh-my-zsh`. Copy the template .zshrc.zsh-template configuration file to the home directory .zshrc and apply the configuration by running the source command, as shown below

```sh
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
source ~/.zshrc
```
- My `.zshrc` config.


[Install zsh syntax highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)


### Install powerline

[Powerline official installation](https://devpro.media/install-powerline-ubuntu/#)

### Instal NeoVim

[NeoVim official installation](https://github.com/neovim/neovim/wiki/Installing-Neovim)

### Install Nerd Font

[Nerd Font Official installation](https://www.nerdfonts.com/)


All configuration for my desktop<br />
https://fedoramagazine.org/getting-started-i3-window-manager/<br />
https://www.bretfisher.com/shell/<br />


### To Do List
- i3
- i3status
- i3lock
- i3lock-multimonitor
- oh-my-zsh
- zsh
- powerline
