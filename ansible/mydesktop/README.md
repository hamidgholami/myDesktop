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

Sample of git `sparse-checkout`
```bash
git clone --filter=blob:none --sparse git@github.com:ryanoasis/nerd-fonts
cd nerd-fonts
git sparse-checkout add patched-fonts/JetBrainsMono
```

```groovy
checkout([$class                           : 'GitSCM',
          branches                         : [[name: 'refs/heads/' + gitBranch]],
          doGenerateSubmoduleConfigurations: false,
          extensions                       : [
                  [$class: 'LocalBranch', localBranch: gitBranch],
                  [$class: 'PruneStaleBranch'],
                  [$class: 'CheckoutOption', timeout: 3],
                  [$class   : 'CloneOption',
                   depth    : 1,
                   noTags   : true,
                   reference: '',
                   shallow  : true,
                   timeout  : 3,
                   honorRefspec: true],
                  pruneTags(true)
          ],
          submoduleCfg                     : [],
          userRemoteConfigs                : [
                  [
                          credentialsId: gitCreds,
                          url          : gitUrl,
                          refspec      : "+refs/heads/$gitBranch:refs/remotes/origin/$gitBranch"
                  ]
          ]
])
```

```groovy
def getChangedFiles(String filter = '.*') {
  def res = []
  try {
    res = sh(script: "git diff HEAD~1 --name-only | grep -E '${filter}'", returnStdout: true).split().collect{it as String}
  } catch (Exception e) {
      println "Exception: '$e', probably filter '$filter' finds no files"
  }
  return res
}
```