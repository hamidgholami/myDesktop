# myDesktop
- **Ubuntu 20.04**
- **Lubuntu 18.04**

## Table of content

- [Git configuration](#Git configuration)
- [Disable sudo prompt for ask password](#Disable sudo prompt for ask password)
- [All requirement packages](#All requirement packages)
- [Install qbittorrent](#Install qbittorrent)

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
### All requirement packages
```sh
sudo apt-get install \
vim git python3 python3-pip terminator tmux tree neovim xpad \
zsh vlc build-essential gcc Ubuntu-restricted-extras \
ca-certificates openjdk-11-jdk simplescreenrecorder shutter kazam \
unrar zip unzip p7zip-full p7zip-rar rar dnsutils \
wine winetricks filezilla zim sshpass openssl mosh \
traceroute virtualbox curl ipython3 openssh-server openssh-client \
gnupg-agent code software-properties-common apt-transport-https \
qemu-kvm libvirt-bin virtinst virt-viewer virt-manager bridge-utils \
cpu-checker spice-client-gtk remmina remmina-plugin-* \
mtr-tiny htop virt-top imvirt apg at bc rsync ftp \
guake chromium-browser x11vnc clipit cups-pdf \
docker-ce docker-ce-cli containerd.io openvpn network-manager-openvpn \
network-manager-openvpn-gnome network-manager-vpnc \
network-manager-l2tp network-manager-l2tp-gnome \
mlocate net-tools cpu-checker font-farsiweb fonts-powerline \
gnome-twaek-tool zsh-syntax-highlighting \
```
### Install qbittorrent

* Add stable repository .

```bash
sudo add-apt-repository ppa:qbittorrent-team/qbittorrent-stable
```

* Run follow commands for install.

```bash
sudo apt-get update && sudo apt-get install qbittorrent 
```

### Install VSCode

* Download and import the Microsoft signing GPG key using the curl command.

```bash
curl -sSL https://packages.microsoft.com/keys/microsoft.asc -o microsoft.asc
sudo apt-key add microsoft.asc
```

* Now, add the Visual Studio Code repository to your system.

```bash
echo "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"  | sudo tee /etc/apt/sources.list.d/vscode.list
```

* Once you have added the repository to the system, do not forget to update the repository index. Use the apt command to install Visual Studio Code.

```bash
sudo apt update && sudo apt install code
```

### Install Typora

[Official Typora installation](https://support.typora.io/Typora-on-Linux/)

* Add `typora` GPG key.

```bash
wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -
# or use
# sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE
```

* Add Typora's repository.

```bash
sudo add-apt-repository 'deb https://typora.io/linux ./'
sudo apt-get update
```

* Install Typora.

```bash
sudo apt install typora
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

### Install VNCViewer

* Download deb/rpm file from official [VNC website](https://www.realvnc.com/en/connect/download/viewer/linux/) and then install it.

```shell
sudo apt install ./VNC-Viewer-6.20.529-Linux-x86.deb
# or
sudo dpkg -i VNC-Viewer-6.20.529-Linux-x86.deb
```

### Install i3wm

* To begin, open a terminal and run the following command.

```bash
sudo apt-get install i3 i3status dmenu i3lock xbacklight feh conky
```

**i3** is the main window manager package.

**i3status** is a utility to generate a string with information to be displayed in the i3bar.

**dmenu** is a utility to launch our apps in the i3 desktop.

**xbacklight** is a utility to set our laptop’s screen brightness.

**feh** is a utility to set a wallpaper.

**conky** is a utility to display information of the system in a awesome way.

* If you have dual monitor maybe you want use image in dual monitor when you lock your system. 

  So you must install `i3lock-multimonitor` from its [repository](https://github.com/ShikherVerma/i3lock-multimonitor).

* This is my `i3/config` file as an instance.

### Kubernetes

* Install `kubectl` on your machine

```bash
sudo apt install kubectl
```

- This is my `.kube`  configuration as an instance.
### Vagrant
- `.vagrant.d`
### ssh
- `.ssh/config`

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

* Add the *Universe* repository.

```bash
sudo add-apt-repository universe
```

* Install Powerline

```bash
sudo apt install powerline
```

### Install SpaceVim plugin

[Official installation for linux](https://spacevim.org/quick-start-guide/#linux-and-macos)

### Install Nerd Font

[Nerd Font Official installation](https://www.nerdfonts.com/)

* Select and install Nerd Font from official website.

--------------------------------

#### To Do List

- [ ] Check all this configuration on Fedora and make a README file for it.
- [ ] Insert my configuration file for some tools such as: docker, kubectl, i3, ssh and etc.

**************

**Author**: Hamid Gholami (hidgholami@gmail.com)

[![Linkedin](https://i.stack.imgur.com/gVE0j.png) LinkedIn](https://www.linkedin.com/in/hamid-gholami)
&nbsp;
[![GitHub](https://i.stack.imgur.com/tskMh.png) GitHub](https://github.com/hamidgholami)
&nbsp;
[![Twitter](http://i.imgur.com/wWzX9uB.png) Twitter](https://www.twitter.com/045_hamid)
