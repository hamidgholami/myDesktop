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

Sample of git `sparse-checkout`
```bash
git clone --filter=blob:none --sparse git@github.com:ryanoasis/nerd-fonts
cd nerd-fonts
git sparse-checkout add patched-fonts/JetBrainsMono
```