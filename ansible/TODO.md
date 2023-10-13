TODO
=========
- [ ] gpg,ssh,sudo,bashrc,tmux
- [ ] git
- [ ] fonts,nerdfont
- [ ] IntelliJ,VSCode,
- [ ] virtualization,virtualbox,libvirt,packer,vagrant
- [ ] Containerization,docker,kuber
- [ ] Multimedia
- [ ] dnsmasq
- [ ] openvpn
- [ ] backup to googleDrive,dropbox
- [ ] create an inbox directory
- [ ] [passwordstore_1](https://docs.ansible.com/ansible/latest/collections/community/general/passwordstore_lookup.html)
- [ ] [passwordstore_2](https://docs.ansible.com/ansible/2.9/plugins/lookup/passwordstore.html)
- [ ] [OpenVpn 3](https://openvpn.net/cloud-docs/owner/connectors/connector-user-guides/openvpn-3-client-for-linux.html)
- [ ] [KOR](https://github.com/yonahd/kor)
- [ ] [ssh-add](https://junyonglee.me/ssh/How-to-permanently-add-private-key-passphrase-to-ssh-agent/)
      - https://askubuntu.com/questions/1356352/how-to-install-ssh-keychain-on-ubuntu-with-wsl
      - https://www.funtoo.org/Funtoo:Keychain
- [ ] [Docker Daemon](https://docs.docker.com/config/containers/logging/configure/)
  - https://docs.docker.com/engine/reference/commandline/dockerd/
    https://docs.docker.com/engine/reference/commandline/dockerd/
    https://docs.docker.com/engine/reference/commandline/commit/
    https://docs.docker.com.zh.xy2401.com/v17.09/engine/userguide/networking/default_network/custom-docker0/
    https://www.devopsschool.com/blog/how-to-configure-docker-daemon-with-a-configuration-file/
    https://gist.github.com/jhazelwo-charter/ec4048da0b363ff69b607993f271be4f
    https://gist.github.com/egeneralov/163deb3cb9de34ac144b8737ab80023c
    https://gist.github.com/vkushnir/92f12865ee3a21ab9bc47088a681d165

Sample of git `sparse-checkout`
```bash
git clone --filter=blob:none --sparse git@github.com:ryanoasis/nerd-fonts
cd nerd-fonts
git sparse-checkout add patched-fonts/JetBrainsMono
```