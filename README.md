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

****

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
